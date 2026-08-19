---
generated: '2026-08-13'
method: generated
name: Create a campaign and issue rewards in bulk
description: Create a Thanx campaign with variants, issue rewards to up to 10,000 identifiers in one call, then track or revoke the issuance job.
api: openapi/thanx-campaigns-api-openapi.yml, openapi/thanx-issuance-jobs-api-openapi.yml
operations: [createToken, createCampaign, listCampaigns, getCampaign, issueRewards, getIssuanceJob, revokeIssuanceJob]
source: >-
  operationIds verified verbatim in openapi/thanx-auth-api-openapi.yml,
  openapi/thanx-campaigns-api-openapi.yml and openapi/thanx-issuance-jobs-api-openapi.yml;
  scope, idempotency, batching and webhook rules from
  https://docs.thanx.com/overview/guides/campaign-reward-issuance,
  https://docs.thanx.com/partner/campaigns/issue-rewards and
  https://docs.thanx.com/webhooks/reward-batch-completed.
---

# Create a campaign and issue rewards in bulk

Server-to-server flow on the Partner API. Host `https://api.thanx.com` (sandbox
`https://api.thanxsandbox.com`), all Partner endpoints under `/partner/*`.

## Auth and scope
- `createToken` (`POST /partner/oauth/token`) mints the access token. Requires the `auth.create`
  scope.
- Every operation in this flow requires the **`rewards.issue`** scope. Verify with `getScopes`
  (`GET /partner/scopes`) before you build — a missing scope returns `403 FORBIDDEN`.
- Headers: `Authorization: Bearer <token>`, `X-ClientId`, `Accept-Version: v4.0`,
  `Content-Type: application/json`.
- See `scopes/thanx-scopes.yml` and `authentication/thanx-authentication.yml`.

## Steps
1. **Pick a reward template** — `GET /partner/reward_templates` returns the merchant's published
   templates. (Documented but not yet in `openapi/`; call it by path.)
2. **Create the campaign** — `createCampaign` (`POST /partner/campaigns`) with `CampaignInput`:
   `merchant_id`, `name`, `objective`, `fine_print`, `start_at`/`end_at`,
   `redeemable_from`/`redeemable_to`, and `variants[]` where each `CampaignVariantInput` binds a
   `name` to a `reward_template_id`. Returns a `Campaign` with `id` and its variant ids.
   Use `listCampaigns` / `getCampaign` to re-read.
3. **Issue the rewards** — `issueRewards` (`POST /partner/campaigns/issue`) with the campaign id,
   `merchant_id`, the `variant_id` (must belong to that campaign) and an `identifiers[]` array of
   `{type: email|phone, value}` — phone numbers in E.164. **Batch up to 10,000 identifiers per
   request.** Returns `202 Accepted` with an `IssuanceJob`.
4. **Track completion** — `getIssuanceJob` (`GET /partner/issuance_jobs/{id}`) returns `state`,
   `requested_count`, `issued_count`, `failed_count`. Prefer the webhooks: `reward.issued` fires
   per successful reward and `reward_batch.completed` fires once with the failure list. See
   `asyncapi/thanx-webhooks.yml`.
5. **Undo if needed** — `revokeIssuanceJob` (`POST /partner/issuance_jobs/{id}/revoke`) revokes
   every reward the job issued.

## Idempotency
- Send `X-Idempotency-Key: <uuid>` on `issueRewards`. A replay with the same key returns the
  CACHED original response instead of issuing again; a replay with a **different body** returns
  `422`. This is the safety net that keeps a network retry from double-issuing to 10,000 guests.
- Retention window is not published. See `conventions/thanx-conventions.yml`.

## Rate limits
- 5 requests/second, 2,000 requests/15 minutes, hard, `429` on exhaustion. Issuing one request
  per user instead of batching is explicitly called out as the way integrations hit this wall.
- See `rate-limits/thanx-rate-limits.yml`.

## Errors
- `403 FORBIDDEN` — credential lacks `rewards.issue`.
- `422` — idempotency key replayed with a different body.
- Error envelope is `{"error": {"code", "message"}}` — match on `code`, never on `message`.
  See `errors/thanx-problem-types.yml`.

## Sandbox
- To test redemption without waiting for a campaign to fire, use the sandbox-only
  `POST /rewards/grant` with the campaign **hashid** (not the numeric program id).
  See `sandbox/thanx-sandbox.yml`.
