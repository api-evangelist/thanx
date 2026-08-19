---
generated: '2026-08-13'
method: generated
name: Apply loyalty at POS checkout
description: Look up a guest's rewards and points at the register, apply them to the basket, and settle the order so loyalty accrues.
api: openapi/thanx-account-api-openapi.yml, openapi/thanx-baskets-api-openapi.yml
operations: [getAccount, createUpdateBasket]
source: >-
  operationIds verified verbatim in openapi/thanx-account-api-openapi.yml and
  openapi/thanx-baskets-api-openapi.yml; flow and header rules from
  https://docs.thanx.com/overview/guides/pos-kiosk, https://docs.thanx.com/loyalty/headers and
  https://docs.thanx.com/overview/guides/basket-lifecycle.
---

# Apply loyalty at POS checkout

The Loyalty API is the POS / kiosk / online-ordering surface. It runs on its own host and its
own header set — do not reuse the Consumer API headers here.

## Host
- Production `https://loyalty.thanx.com/api/`, sandbox `https://loyalty.thanxsandbox.com/api/`.
- AWS PrivateLink is available for this API (https://docs.thanx.com/loyalty/private-link).

## Auth
- `Merchant-Key: <merchant key>` on every request.
- `Authorization: Bearer <user access token>` to identify the guest, OR `Reward-Redemption-Token`
  for token-only redemption. **Never both** — sending the token alongside a bearer returns 404
  (merchant has no indirect loyalty integration) or 401 (token resolves to no reward).
- `Accept: application/vnd.thanx-v1+json` — the Loyalty API versions by media type, not by
  `Accept-Version`.
- `User-Agent: {partner}/1.0.0` is required and is how Thanx traces your traffic.
- See `authentication/thanx-authentication.yml` and `conventions/thanx-conventions.yml`.

## Steps
1. **Read the guest's loyalty state** — `getAccount` (`GET /api/account`). Returns the account
   with `rewards[]` (id, value, label, state, type) and `points_products[]` (id, label, cost)
   plus `points_balances[]`. This is everything redeemable at the register in one call.
2. **Offer only what applies** — filter to rewards in an applicable state before showing them to
   the cashier. Thanx also publishes a read-only dry run,
   `POST /api/baskets/qualifying` (https://docs.thanx.com/loyalty/qualifying-baskets), which
   returns the subset of rewards and points products that would actually discount THIS basket
   without mutating anything. Not yet captured in `openapi/`, so call it by path.
3. **Send the basket** — `createUpdateBasket` (`POST /api/baskets`) with `BasketInput`:
   `id`, `state`, `order_timestamp`, `location_uid`, `items[]`, `subtotal`, `payments[]`, plus
   `rewards[]` and `points_products[]` as arrays of IDs. The response `Basket` carries the
   resulting `discount`.
4. **Progress the basket state** — call the same operation again as the order moves through its
   lifecycle, ending at `billed`. Accrual happens on the billed basket; there is no separate
   "commit" call.

## Idempotency
- Resending the same basket is safe: it will not redeem a reward twice. There is no
  `X-Idempotency-Key` on this endpoint (that header is Partner-API only).

## Errors
- `401` — missing/invalid bearer, or a `Reward-Redemption-Token` that resolves to no reward.
- `404` — `Reward-Redemption-Token` sent to a merchant without indirect loyalty enabled.
- `REWARD_INAPPLICABLE` / `REWARD_EXPIRED` / `REWARD_ALREADY_USED` — re-read the account before
  retrying; do not retry a redemption that already succeeded.
- Full catalog: `errors/thanx-problem-types.yml`.

## Rate limits
- 5 requests/second and 2,000 requests/15 minutes, hard, `429` on exhaustion, no rate-limit
  response headers. Back off exponentially. See `rate-limits/thanx-rate-limits.yml`.

## Sandbox notes
- Sandbox basket ingestion is slow — a `billed` basket takes 15–30+ minutes to surface.
- Array filters need bracket notation (`states[]=available&states[]=active`).
- See `sandbox/thanx-sandbox.yml`.
