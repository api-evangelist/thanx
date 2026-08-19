---
generated: '2026-08-13'
method: generated
name: Ingest subscribers from an external channel
description: Verify scope, mint a partner token, and push email/SMS marketing subscribers into a Thanx merchant.
api: openapi/thanx-subscribers-api-openapi.yml, openapi/thanx-metadata-api-openapi.yml
operations: [createToken, getScopes, getMerchants, getPartnerLocations, createSubscriber]
source: >-
  operationIds verified verbatim in openapi/thanx-auth-api-openapi.yml,
  openapi/thanx-metadata-api-openapi.yml and openapi/thanx-subscribers-api-openapi.yml; flow and
  scope requirements from https://docs.thanx.com/overview/guides/subscriber-ingestion,
  https://docs.thanx.com/partner/subscribers/create-subscriber and
  https://docs.thanx.com/partner/metadata/get-scopes.
---

# Ingest subscribers from an external channel

Partner API flow for pushing marketing opt-ins (a kiosk signup, a web form, a third-party CRM)
into Thanx. Host `https://api.thanx.com` (sandbox `https://api.thanxsandbox.com`), endpoints
under `/partner/*`.

## Auth and scope
- `createToken` (`POST /partner/oauth/token`) for the access token — needs `auth.create`.
- `createSubscriber` requires the **`subscribers.write`** scope.
- Headers: `Authorization: Bearer <token>`, `X-ClientId`, `Accept-Version: v4.0`,
  `Content-Type: application/json`.

## Steps
1. **Confirm your scopes** — `getScopes` (`GET /partner/scopes`) returns the list your credential
   holds, e.g. `{"scopes": ["subscribers.write"]}`. Do this first during onboarding; it turns a
   later `403` into a five-second diagnosis.
2. **Resolve the merchant** — `getMerchants` (`GET /partner/metadata/merchants`) returns every
   merchant the credential can reach. `getPartnerLocations`
   (`GET /partner/metadata/locations`) does the same for locations if you need to attribute the
   signup to a store.
3. **Create the subscriber** — `createSubscriber` (`POST /partner/subscribers`) with the merchant
   id and the subscriber's identifiers. Returns `201`; `400` on a validation failure with an
   error `code` such as `USER_EMAIL_INVALID` or `USER_PHONE_INVALID`.
4. **Reconcile downstream** — subscribe to the `sms_subscription` webhook to catch opt-ins that
   originate inside Thanx. Note Thanx does **not** synchronize downstream SMS opt-in status and
   prompts a guest for a phone number only once; the SMS marketing partner owns consent
   confirmation. See `asyncapi/thanx-webhooks.yml`.

## Data rules
- Phone numbers must be **E.164** (`+12025551234`).
- Thanx IDs are alphanumeric lowercase strings.

## Rate limits
- 5 requests/second, 2,000 requests/15 minutes, hard, `429`. Ingesting a large list one
  subscriber per request will hit this — pace the writes and back off exponentially on `429`.
- `createSubscriber` accepts no `X-Idempotency-Key`; make your own writer idempotent by keying on
  the source identifier before you call.
- See `rate-limits/thanx-rate-limits.yml`.

## Errors
- `403 FORBIDDEN` — missing `subscribers.write`.
- `400 USER_EMAIL_INVALID` / `USER_PHONE_INVALID` / `USER_NAME_REQUIRED` — validate before
  sending.
- See `errors/thanx-problem-types.yml`.

## Certification
Production credentials are issued only after Thanx certifies the integration against the
sandbox, and each new use-case is re-certified. See `lifecycle/thanx-lifecycle.yml`.
