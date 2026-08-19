---
generated: '2026-08-13'
method: searched
source: https://docs.thanx.com/.well-known/agent-skills/thanx/skill.md
x-provenance: Provider-published Agent Skill, fetched 2026-08-13 (HTTP 200, text/markdown). Body below is verbatim; only these three provenance keys were added to the existing frontmatter.
name: Thanx
description: Use when building loyalty integrations for merchants and consumers — including consumer UX (mobile/web apps), POS/kiosk systems, partner-initiated campaigns, and data exports. Reach for this skill when integrating reward redemption, points accrual, user authentication, campaign management, or loyalty data pipelines.
metadata:
    mintlify-proj: thanx
    version: "1.0"
---

# Thanx Loyalty API Skill

## Product Summary

Thanx is a loyalty platform that provides APIs for merchants, partners, and ordering systems to integrate loyalty features — reward redemption, points accrual, user authentication, and campaign management. The platform offers three primary API families: **Consumer API** (for custom mobile/web apps), **Partner API** (for server-to-server integrations like campaign creation and reward issuance), and **Loyalty API** (for POS/kiosk/ordering systems). All APIs use OAuth 2.0 authentication with bearer tokens and require specific headers including `Accept-Version: v4.0`, `X-ClientId`, and `Content-Type: application/json`. Base URLs are `https://api.thanxsandbox.com` (sandbox) and `https://api.thanx.com` (production). Postman collections are available for each API family. See the primary docs at https://docs.thanx.com.

## When to Use

**Consumer API**: Building custom mobile apps or web ordering experiences where users need to authenticate, view rewards, redeem rewards, earn points, manage cards, and complete purchases with loyalty benefits.

**Partner API**: Creating server-to-server integrations for campaign creation, reward issuance (by email/phone), subscriber ingestion, or merchant/location metadata retrieval. Use when partners need to issue rewards programmatically on behalf of merchants.

**Loyalty API**: Integrating with POS systems, kiosks, or online ordering platforms that need to look up user rewards, apply discounts, and accrue points at checkout.

**Webhooks**: Responding in real-time to purchase events, reward issuance completion, or communication preference changes. Design consumers to be idempotent and deduplicate on stable identifiers.

**Data Exports**: Accessing raw Thanx data via SFTP (daily CSV snapshots), Snowflake Secure Data Sharing, or Thanx Connex (managed loading to 15+ destinations including BigQuery, Redshift, Postgres, S3).

## Quick Reference

### Required Headers (All APIs)

| Header | Value | Required |
|--------|-------|----------|
| `Authorization` | `Bearer {access_token}` | Yes (except unauthenticated endpoints) |
| `X-ClientId` | `{client_id}` | Yes (Partner & Loyalty APIs) |
| `Accept-Version` | `v4.0` | Yes |
| `Content-Type` | `application/json` | Yes |
| `User-Agent` | `{partner}/1.0.0` | Yes |

### API Base URLs

| Environment | Consumer/Partner | Loyalty |
|-------------|------------------|---------|
| Sandbox | `https://api.thanxsandbox.com` | `https://loyalty.thanxsandbox.com/api/` |
| Production | `https://api.thanx.com` | `https://loyalty.thanx.com/api/` |

### Consumer API Core Endpoints

- **Authentication**: `POST /oauth/authorize`, `POST /oauth/token`, `POST /users` (create)
- **User Management**: `GET /users/{id}`, `PUT /users/{id}`, `DELETE /users/{id}`
- **Cards**: `POST /cards`, `GET /cards`, `DELETE /cards/{id}`
- **Rewards**: `GET /rewards`, `POST /rewards/{id}/activate`, `POST /rewards/{id}/finalize`
- **Points**: `GET /points/balance`, `GET /points/experiences`, `GET /points/products`, `POST /points/products/{id}/exchange`
- **Tiers**: `GET /tiers/configs`, `GET /tiers/statuses`
- **Purchases**: `POST /purchases`, `GET /purchases`

### Partner API Core Endpoints

- **Metadata**: `GET /merchants`, `GET /locations`, `GET /scopes`
- **Campaigns**: `POST /campaigns`, `GET /campaigns`, `POST /campaigns/{id}/issue-rewards`
- **Reward Templates**: `GET /reward-templates`
- **Issuance Jobs**: `GET /issuance-jobs/{id}`, `POST /issuance-jobs/{id}/revoke`
- **Subscribers**: `POST /subscribers`

### Loyalty API Core Endpoints

- **Account**: `GET /account` (retrieve user's rewards and points balance)
- **Baskets**: `POST /baskets` (submit basket with reward/points redemption)

### Common Error Codes

| Code | Meaning |
|------|---------|
| `AUTHENTICATION_GENERIC` | Invalid or missing auth token |
| `RESOURCE_NOT_FOUND` | Endpoint or resource does not exist |
| `REWARD_ALREADY_USED` | Reward has been redeemed |
| `REWARD_EXPIRED` | Reward is no longer valid |
| `REWARD_INAPPLICABLE` | Required item not in basket |
| `USER_EMAIL_INVALID` | Email format is invalid |
| `POINTS_EXCHANGE_FAILURE` | Points exchange failed |

## Decision Guidance

### When to Use Consumer API vs Partner API

| Scenario | Use Consumer API | Use Partner API |
|----------|------------------|-----------------|
| Building a branded mobile/web app for end users | ✓ | |
| Server-to-server campaign creation and reward issuance | | ✓ |
| Integrating with a merchant's CRM or feedback system | | ✓ |
| Handling user authentication and account management | ✓ | |
| Issuing rewards programmatically by email/phone | | ✓ |
| Syncing newsletter subscribers into loyalty | | ✓ |

### When to Use Loyalty API vs Consumer API

| Scenario | Use Loyalty API | Use Consumer API |
|----------|-----------------|-----------------|
| POS/kiosk integration for reward lookup and redemption | ✓ | |
| Online ordering platform checkout integration | ✓ | |
| Custom mobile/web app with full loyalty features | | ✓ |
| Displaying user account and tier information | | ✓ |
| Reward activation and finalization workflows | | ✓ |

### Authentication: Thanx SSO vs Custom Auth

| Approach | Pros | Cons |
|----------|------|------|
| **Thanx SSO** (recommended) | Passwordless magic link, card networks approved, full Thanx marketing tools available | Requires email verification flow |
| **Custom Auth** | Full control over UX | Limits Thanx marketing tools, you manage account creation |

## Workflow

### Consumer UX Integration (Mobile/Web App)

1. **Understand the project**: Determine if you're building card-linked loyalty, check-in loyalty, or points-based. Identify required features (rewards, points, tiers, cards, receipts).

2. **Set up authentication**: Implement Thanx SSO using `POST /oauth/authorize` and `POST /oauth/token`, or create users via `POST /users` if using custom auth. Store access tokens securely (server-side, not in app).

3. **Implement user flows**:
   - Display onboarding slideshow, then home page
   - Gate rewards/account pages behind authentication
   - Show simplified auth at checkout
   - Use progressive data capture (email → card → name/phone)

4. **Build reward redemption**: Call `GET /account` at checkout to retrieve available rewards and points products. Display them to the user. Submit basket via Loyalty API `POST /baskets` with selected rewards/points.

5. **Implement bonus points activation**: Fetch rewards via `GET /rewards`, automatically activate bonus points with `POST /rewards/{id}/activate` when user opens the app logged in.

6. **Add card management** (card-linked only): Implement `POST /cards`, `GET /cards`, `DELETE /cards/{id}`. Display legal text on card enrollment screens.

7. **Test in sandbox**: Use sandbox credentials and base URL. Verify all flows work. Download pre-certification checklist.

8. **Submit for certification**: Provide TestFlight (iOS), Google Console (Android), or web URL to developer.support@thanx.com. Include product guide with screenshots and screen recording. Expect 10 business days feedback.

9. **Go live**: Once certified, swap sandbox URL and credentials for production. Launch with Partnerships team coordination.

### Partner API: Campaign & Reward Issuance

1. **Discover merchants and templates**: Call `GET /merchants` to list accessible merchants. For each, call `GET /reward-templates` to see available reward types. Cache this data.

2. **Create a campaign**: Call `POST /campaigns` with merchant ID, campaign name, time window, and 1–4 variants. Each variant references a reward template (or is a control variant for A/B testing).

3. **Issue rewards**: Call `POST /campaigns/{id}/issue-rewards` with user identifiers (email or phone in E.164 format). Submit up to 10,000 identifiers per job. Use `X-Idempotency-Key` header to prevent duplicates.

4. **Monitor completion**: Poll `GET /issuance-jobs/{id}` until status is `completed` or `failed`. Check `summary` for success/failure counts and error details. Alternatively, subscribe to webhooks (`reward.issued`, `reward.batch_completed`).

5. **Handle failures**: Surface failure details to merchants. Retry failed identifiers or investigate invalid emails/phones.

6. **Revoke if needed**: Call `POST /issuance-jobs/{id}/revoke` to revoke all rewards from a job (only if completed/failed state).

7. **Test in sandbox**: Use sandbox credentials. Verify campaign creation, issuance, and job monitoring.

8. **Submit for certification**: Demo the integration with developer.support@thanx.com. Show merchant discovery, campaign creation, reward issuance, and error handling. Include product guide.

9. **Go live**: Swap credentials and URLs. Monitor rate limits (5 req/sec, 2000 req/15min).

### Loyalty API: POS/Kiosk Integration

1. **Authenticate user**: Retrieve user's access token via Thanx SSO or your own auth system.

2. **Look up rewards at checkout**: Call `GET /account` with user's access token and merchant key. Response includes available rewards, points balance, and points products.

3. **Display options**: Show user their available rewards and points products. Let them select which to redeem.

4. **Submit basket**: Call `POST /baskets` with order details, selected reward/points, and Thanx `location_uid` (retrieve via `GET /locations` from Partner API). Response includes discount amount.

5. **Apply discount**: Apply the discount returned by the API to the user's order total.

6. **Handle refunds**: If user requests refund, resubmit basket with `refund: true`. Redeemed rewards are restored and exchanged points are reverted.

7. **Verify location mapping**: Ensure you're sending the correct Thanx `location_uid` for each POS location. Use Partner API `GET /locations` to automate mapping.

8. **Test in sandbox**: Verify reward lookup, redemption, and refund flows.

9. **Submit for certification**: Demo all reward types (amount-off, item-based), points products, refunds, and error handling. Verify all required headers are sent.

10. **Go live**: Swap credentials and URLs.

## Common Gotchas

- **Expired tokens**: Consumer API access tokens should not expire. If you expire them, users must re-authenticate on every device. Avoid this.

- **Shared test cards**: When testing fraud-protected reward types (intro, invite, birthday, winback, newsletter), use unique real cards per test account. Shared test cards (e.g., Visa `4111…`) match on fingerprint and flag rewards as fraudulent.

- **Webhook duplicates**: Webhooks are not exactly-once. A single purchase fires multiple times as it moves through authorization and settlement. Deduplicate on `id` and treat later deliveries as updates.

- **Webhook retries**: Webhooks are best-effort and do not retry. If your endpoint fails, data is not re-sent. Design idempotent consumers and use bulk data exports as fallback.

- **Rate limits**: Partner API has hard limits: 5 req/sec, 2000 req/15min. Requests exceeding limits return `429 Too Many Requests`. Use exponential backoff for retries.

- **Asynchronous issuance**: Partner API reward issuance is async. The endpoint returns `202 Accepted` immediately. Poll `GET /issuance-jobs/{id}` or subscribe to webhooks to track completion.

- **Idempotency keys**: Use `X-Idempotency-Key` header on `POST /campaigns/{id}/issue-rewards` to prevent duplicate issuance jobs if requests are retried.

- **Missing location_uid**: Loyalty API baskets must include the correct Thanx `location_uid`. Omitting it or sending the wrong ID causes purchases to be unattributed or filtered incorrectly.

- **SSO vs custom auth**: If you use custom auth instead of Thanx SSO, Thanx marketing tools (email campaigns, push notifications) are unavailable. Card networks also require SSO for card-linked loyalty.

- **Legal text on card screens**: Card enrollment screens must display specific legal text (approved by Visa, Mastercard, Amex). Changing wording delays certification. Use the provided text as-is.

- **Bonus points activation**: Bonus points are immediately redeemed when activated. Do not call finalize on them. Activate only when user opens the app logged in.

- **Reward expiry**: Always check reward expiry before displaying or redeeming. Expired rewards return `REWARD_EXPIRED` error.

- **Certification product guide**: Submit a product guide with screenshots and screen recording of all use cases. This is mandatory and reduces back-and-forth.

## Verification Checklist

Before submitting for certification:

- [ ] All API requests include required headers (`Authorization`, `X-ClientId`, `Accept-Version`, `Content-Type`, `User-Agent`)
- [ ] Authentication flow works (SSO or custom auth)
- [ ] User can create account, view profile, update info, delete account
- [ ] Card enrollment displays legal text and has "Register card" button
- [ ] Rewards display correctly and can be activated/finalized
- [ ] Bonus points activate automatically without finalize call
- [ ] Points balance and products display correctly
- [ ] Tier info displays with thresholds and perks
- [ ] Purchases display with correct amounts
- [ ] Basket submission includes correct `location_uid`
- [ ] Refunds restore rewards and revert points
- [ ] Error messages display to user (not silent failures)
- [ ] No unnecessary API polling (only on user action)
- [ ] Webhook consumers are idempotent (deduplicate on `id`)
- [ ] Rate limits respected (5 req/sec, 2000 req/15min for Partner API)
- [ ] Sandbox testing complete
- [ ] Product guide with screenshots and screen recording ready
- [ ] Pre-certification checklist downloaded and completed

## Resources

**Comprehensive page-by-page navigation**: https://docs.thanx.com/llms.txt

**Critical documentation pages**:
- [Consumer API Overview](https://docs.thanx.com/consumer/overview) — Start here for mobile/web app integrations
- [Partner API Overview](https://docs.thanx.com/partner/overview) — Start here for server-to-server integrations
- [Loyalty API Overview](https://docs.thanx.com/loyalty/overview) — Start here for POS/kiosk integrations
- [Integration Guide](https://docs.thanx.com/overview/integrating) — Roles, integration paths, certification process
- [Consumer UX Guide](https://docs.thanx.com/overview/guides/consumer-ux) — Detailed workflow for mobile/web apps
- [Campaign & Reward Issuance Guide](https://docs.thanx.com/overview/guides/campaign-reward-issuance) — Detailed workflow for partner-initiated campaigns
- [Webhooks Overview](https://docs.thanx.com/webhooks/overview) — Webhook delivery semantics and verification
- [Data Exports Overview](https://docs.thanx.com/data/overview) — SFTP, Snowflake, and Connex options

---

> For additional documentation and navigation, see: https://docs.thanx.com/llms.txt