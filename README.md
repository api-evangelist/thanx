# Thanx (thanx)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Thanx is a customer engagement, loyalty, and marketing automation platform for restaurants and other offline businesses, built to acquire, engage, and retain best customers and grow customer lifetime value. The platform combines data infrastructure, lifecycle marketing, loyalty and CRM, and digital ordering experiences. Thanx is API-first and publishes a public developer portal documenting a Consumer API for custom consumer experiences, a Partner API for privileged integration use cases, and a Loyalty API for digital ordering and kiosk providers, along with webhooks and Connex data-export integrations to warehouses like Snowflake and BigQuery. Thanx serves roughly 500 brands and processes over a billion transactions annually. It also publishes a hosted Docs MCP server for natural-language API search and an open agent-skills starter kit.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/thanx/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/thanx/refs/heads/main/apis.yml)

## Scope

- **Type:** Index

## Tags

- Restaurant
- Loyalty
- Guest Engagement
- Marketing
- CRM
- Online Ordering
- Webhooks
- Points
- Rewards
- Campaigns

## Timestamps

- **Created:** 2026-06-02
- **Modified:** 2026-06-03

## APIs

### Thanx Consumer API

The Thanx Consumer API lets brands integrate Thanx into a custom consumer experience, covering users and authentication, cards, gift cards, rewards, purchases, points and loyalty balances, locations, and feedback. It powers branded apps and digital experiences built on top of the Thanx loyalty and CRM platform. Endpoints are protected and authorized via end-user access tokens acquired through Thanx SSO.

- **Human URL:** [https://docs.thanx.com/consumer/overview](https://docs.thanx.com/consumer/overview)
- **Base URL:** `https://api.thanx.com`

#### Tags

- Loyalty
- Rewards
- Users
- Gifts
- Points
- Purchases
- Cards

#### Properties

- [OpenAPI](openapi/thanx-consumer-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/thanx-consumer-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/thanx-consumer-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.thanx.com/consumer/overview)
- [API Reference](https://docs.thanx.com/consumer/overview)
- [Authentication](https://docs.thanx.com/consumer/usage/headers)
- [SDK](https://github.com/thanx/thanx-sdk-ios)
- [SDK](https://github.com/thanx/thanx-sdk-android)
- [Best Practices](https://docs.thanx.com/consumer/best-practices/design)
- [Errors](https://docs.thanx.com/consumer/usage/errors)
- [JSON Schema](json-schema/consumer-api-authorization-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-birth-date-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-card-envelope-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-card-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-gift-card-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-location-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-pagination-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-purchase-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-reward-envelope-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-reward-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-user-envelope-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-user-input-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/consumer-api-user-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/consumer-api-authorization-structure.json)
- [JSON Structure](json-structure/consumer-api-birth-date-structure.json)
- [JSON Structure](json-structure/consumer-api-card-envelope-structure.json)
- [JSON Structure](json-structure/consumer-api-card-structure.json)
- [JSON Structure](json-structure/consumer-api-gift-card-structure.json)
- [JSON Structure](json-structure/consumer-api-location-structure.json)
- [JSON Structure](json-structure/consumer-api-pagination-structure.json)
- [JSON Structure](json-structure/consumer-api-purchase-structure.json)
- [JSON Structure](json-structure/consumer-api-reward-envelope-structure.json)
- [JSON Structure](json-structure/consumer-api-reward-structure.json)
- [JSON Structure](json-structure/consumer-api-user-envelope-structure.json)
- [JSON Structure](json-structure/consumer-api-user-input-structure.json)
- [JSON Structure](json-structure/consumer-api-user-structure.json)
- [Example](examples/consumer-api-authorization-example.json)
- [Example](examples/consumer-api-birth-date-example.json)
- [Example](examples/consumer-api-card-envelope-example.json)
- [Example](examples/consumer-api-card-example.json)
- [Example](examples/consumer-api-gift-card-example.json)
- [Example](examples/consumer-api-location-example.json)
- [Example](examples/consumer-api-pagination-example.json)
- [Example](examples/consumer-api-purchase-example.json)
- [Example](examples/consumer-api-reward-envelope-example.json)
- [Example](examples/consumer-api-reward-example.json)
- [Example](examples/consumer-api-user-envelope-example.json)
- [Example](examples/consumer-api-user-example.json)
- [Example](examples/consumer-api-user-input-example.json)
- [JSON-LD](json-ld/thanx-consumer-api-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Thanx Partner API

The Thanx Partner API provides privileged endpoints supporting custom integration use cases, including end-user token issuance, campaign management and reward issuance, subscriber ingestion, feedback handling, tags, and metadata lookups for merchants, locations, and scopes. It is intended for approved partners building deeper integrations with the Thanx engagement and marketing platform.

- **Human URL:** [https://docs.thanx.com/partner/overview](https://docs.thanx.com/partner/overview)
- **Base URL:** `https://api.thanx.com`

#### Tags

- Campaigns
- Subscribers
- Marketing
- Rewards
- Merchants

#### Properties

- [OpenAPI](openapi/thanx-partner-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/thanx-partner-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/thanx-partner-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.thanx.com/partner/overview)
- [API Reference](https://docs.thanx.com/partner/overview)
- [Authentication](https://docs.thanx.com/consumer/usage/headers)
- [Getting Started](https://docs.thanx.com/overview/guides/campaign-reward-issuance)
- [Getting Started](https://docs.thanx.com/overview/guides/subscriber-ingestion)
- [JSON Schema](json-schema/partner-api-campaign-input-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/partner-api-campaign-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/partner-api-campaign-variant-input-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/partner-api-issuance-job-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/partner-api-partner-user-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/partner-api-campaign-input-structure.json)
- [JSON Structure](json-structure/partner-api-campaign-structure.json)
- [JSON Structure](json-structure/partner-api-campaign-variant-input-structure.json)
- [JSON Structure](json-structure/partner-api-issuance-job-structure.json)
- [JSON Structure](json-structure/partner-api-partner-user-structure.json)
- [Example](examples/partner-api-campaign-example.json)
- [Example](examples/partner-api-campaign-input-example.json)
- [Example](examples/partner-api-campaign-variant-input-example.json)
- [Example](examples/partner-api-issuance-job-example.json)
- [Example](examples/partner-api-partner-user-example.json)
- [JSON-LD](json-ld/thanx-partner-api-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

### Thanx Loyalty API

The Thanx Loyalty API supports integrations with digital ordering and kiosk providers, exposing account lookup and basket lifecycle operations so external ordering systems can connect to a brand's Thanx loyalty program, apply rewards and points products, and track loyalty progress. All endpoints are authorized via end-user access tokens and a merchant key.

- **Human URL:** [https://docs.thanx.com/loyalty/overview](https://docs.thanx.com/loyalty/overview)
- **Base URL:** `https://loyalty.thanx.com`

#### Tags

- Loyalty
- Points
- Online Ordering
- Baskets

#### Properties

- [OpenAPI](openapi/thanx-loyalty-api-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/thanx-loyalty-api.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/thanx-loyalty-api.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)
- [Documentation](https://docs.thanx.com/loyalty/overview)
- [API Reference](https://docs.thanx.com/loyalty/overview)
- [Authentication](https://docs.thanx.com/consumer/usage/headers)
- [Getting Started](https://docs.thanx.com/overview/guides/pos-kiosk)
- [Regions](https://docs.thanx.com/loyalty/private-link)
- [JSON Schema](json-schema/loyalty-api-account-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/loyalty-api-basket-input-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/loyalty-api-basket-item-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/loyalty-api-basket-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/loyalty-api-loyalty-reward-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/loyalty-api-payment-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Schema](json-schema/loyalty-api-points-product-schema.json) — [JSON Schema](https://json-schema.org/specification)
- [JSON Structure](json-structure/loyalty-api-account-structure.json)
- [JSON Structure](json-structure/loyalty-api-basket-input-structure.json)
- [JSON Structure](json-structure/loyalty-api-basket-item-structure.json)
- [JSON Structure](json-structure/loyalty-api-basket-structure.json)
- [JSON Structure](json-structure/loyalty-api-loyalty-reward-structure.json)
- [JSON Structure](json-structure/loyalty-api-payment-structure.json)
- [JSON Structure](json-structure/loyalty-api-points-product-structure.json)
- [Example](examples/loyalty-api-account-example.json)
- [Example](examples/loyalty-api-basket-example.json)
- [Example](examples/loyalty-api-basket-input-example.json)
- [Example](examples/loyalty-api-basket-item-example.json)
- [Example](examples/loyalty-api-loyalty-reward-example.json)
- [Example](examples/loyalty-api-payment-example.json)
- [Example](examples/loyalty-api-points-product-example.json)
- [JSON-LD](json-ld/thanx-loyalty-api-context.jsonld) — [JSON-LD](https://www.w3.org/TR/json-ld11/)

## Common Properties

- [Website](https://www.thanx.com/)
- [Developer Portal](https://docs.thanx.com/overview)
- [Documentation](https://docs.thanx.com/overview)
- [Getting Started](https://docs.thanx.com/overview/integrating)
- [Pricing](https://www.thanx.com/pricing)
- [GitHub Organization](https://github.com/thanx)
- [L L Ms Txt](https://docs.thanx.com/llms.txt)
- [Changelog](https://docs.thanx.com/data/changelog)
- [Best Practices](https://docs.thanx.com/consumer/best-practices/design)
- [Errors](https://docs.thanx.com/consumer/usage/errors)
- [Documentation](https://docs.thanx.com/webhooks/overview)
- [Documentation](https://docs.thanx.com/data/overview)
- [Tools](https://docs.thanx.com/mcp)
- [Documentation](https://docs.thanx.com/ai/overview)
- [Tools](https://github.com/thanx/thanx-agent-starter)
- [Code Examples](https://docs.thanx.com/overview/api_collections)
- [Spectral Rules](rules/thanx-spectral-rules.yml)
- [Vocabulary](vocabulary/thanx-vocabulary.yaml)
- [Plans](plans/thanx-plans-pricing.yml)
- [Rate Limits](rate-limits/thanx-rate-limits.yml)
- [Fin Ops](finops/thanx-finops.yml)
- [Features](undefined)
- [Use Cases](undefined)
- [Integrations](undefined)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
