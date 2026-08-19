---
generated: '2026-08-13'
method: generated
name: Enroll a guest and redeem a reward in a consumer app
description: Authenticate a guest through Thanx SSO, enroll them, enroll a payment card, then list, activate and finalize a reward in a custom mobile or web app.
api: openapi/thanx-users-api-openapi.yml, openapi/thanx-cards-api-openapi.yml, openapi/thanx-rewards-api-openapi.yml
operations: [createUser, getUser, createCard, getCards, getRewards, getReward, activateReward, finalizeReward, getPointsBalance]
source: >-
  operationIds verified verbatim in openapi/thanx-users-api-openapi.yml,
  openapi/thanx-cards-api-openapi.yml, openapi/thanx-rewards-api-openapi.yml and
  openapi/thanx-points-api-openapi.yml; the SSO flow and reward state machine from
  https://docs.thanx.com/consumer/sso/overview,
  https://docs.thanx.com/consumer/rewards/overview and
  https://docs.thanx.com/consumer/best-practices/onboarding-authentication.
---

# Enroll a guest and redeem a reward in a consumer app

The Consumer API backs custom mobile apps and web ordering experiences. Host
`https://api.thanx.com` (sandbox `https://api.thanxsandbox.com`).

## Auth
- Thanx SSO is **passwordless OAuth 2.0, authorization code grant** (RFC 6749 §4.1):
  `POST /oauth/authorize` emails the guest a link, the redirect carries a `code`, and
  `POST /oauth/token` exchanges it for an access token. `POST /oauth/authorize-cross-domain`
  issues a code for an already-authenticated user with no email, for domain-to-domain handoff.
  These four endpoints are documented but not yet captured in `openapi/` — call them by path.
- Every subsequent call sends `Authorization: Bearer <token>`, `X-ClientId`,
  `Accept-Version: v4.0`, `Accept: application/json`.
- See `authentication/thanx-authentication.yml`.

## Steps
1. **Authenticate or create** — if `POST /oauth/authorize` returns `401`, no account exists for
   that email; create one with `createUser` (`POST /users`, `UserInput`: email, phone,
   first_name, last_name, birth_date, zip_code, signup_program_id).
   **SSO authenticates but does not enroll** — a user who signs in without a membership gets
   empty tier and reward responses until `createUser` enrolls them with the merchant.
2. **Confirm the session** — `getUser` (`GET /users/me`) returns the `UserEnvelope`.
3. **Enroll a card** — `createCard` (`POST /cards`) registers the card with Thanx and enrolls it
   with Visa/Mastercard/Amex so in-store spend is detected automatically. `getCards`
   (`GET /cards`) lists them; `deleteCard` (`DELETE /cards/{id}`) archives and unenrolls.
   Only `last4` and `type` come back — Thanx never returns a PAN.
4. **Show what the guest has** — `getRewards` (`GET /rewards`), filtered with bracket notation:
   `GET /rewards?states[]=available&states[]=active`. `getPointsBalance`
   (`GET /points_experiences/{id}/balance`) returns the points side.
5. **Activate at the moment of use** — `activateReward` (`POST /rewards/{id}/activate`) moves the
   reward `available -> active`. Bonus-point (static) rewards go straight to `used` here.
6. **Finalize once redeemed** — `finalizeReward` (`POST /rewards/{id}/finalize`) moves it
   `active -> used`. Re-read with `getReward` (`GET /rewards/{id}`) if the UI needs the
   post-redemption state.

## Reward state machine
`available -> active -> used`. Never offer a reward whose `retire_at` has passed, and treat
`REWARD_ALREADY_USED` as a terminal state, not a retryable failure.

## Errors
- `AUTHENTICATION_GENERIC` (401) — re-acquire the token; check all four headers.
- `REWARD_EXPIRED`, `REWARD_ALREADY_USED`, `REWARD_INAPPLICABLE`, `REWARD_FRAUDULENT` — surface a
  neutral message and re-read the reward list.
- `CARD_INVALID` / `CARD_GENERIC` — unsupported network, or an upstream failure at Visa.
- See `errors/thanx-problem-types.yml`.

## Conventions
- Every payload is wrapped in a top-level resource key (`user`, `card`, `reward`) — the SSO
  endpoints are the exception.
- With a bearer token present, any `user_id` filter is ignored; the token defines the subject.
- Collections paginate with `total_page` / `per_page` / `current_page`.
- See `conventions/thanx-conventions.yml`.

## Sandbox
- Use a **unique card number per test user** for fraud-protected reward types (intro, birthday,
  winback, signup) — shared test PANs are flagged by the fraud engine and the reward silently
  never appears. See `sandbox/thanx-sandbox.yml`.
