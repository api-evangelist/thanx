# Thanx (thanx)
Thanx is a customer engagement, loyalty, and marketing automation platform for restaurants and other offline businesses, built to acquire, engage, and retain best customers and grow customer lifetime value. The platform combines data infrastructure, lifecycle marketing, loyalty and CRM, and digital ordering experiences. Thanx is API-first and publishes a public developer portal documenting a Consumer API for custom consumer experiences, a Partner API for privileged integration use cases, and a Loyalty API for digital ordering and kiosk providers, along with webhooks and Connex data-export integrations to warehouses like Snowflake and BigQuery. Thanx serves roughly 500 brands and processes over a billion transactions annually. It also publishes a hosted Docs MCP server for natural-language API search and an open agent-skills starter kit.

**URL:** [Visit APIs.json URL](https://raw.githubusercontent.com/api-evangelist/thanx/refs/heads/main/apis.yml)

**Run:** [Capabilities Using Naftiko](https://github.com/naftiko/fleet?utm_source=api-evangelist&utm_medium=readme&utm_campaign=company-api-evangelist&utm_content=repo)

## Tags:

 - Restaurant, Loyalty, Guest Engagement, Marketing, CRM, Online Ordering, Webhooks, Points, Rewards, Campaigns

## Timestamps

- **Created:** 2026-06-02
- **Modified:** 2026-06-03

## APIs

### Thanx Consumer API
The Thanx Consumer API lets brands integrate Thanx into a custom consumer experience, covering users and authentication, cards, gift cards, rewards, purchases, points and loyalty balances, locations, and feedback. It powers branded apps and digital experiences built on top of the Thanx loyalty and CRM platform. Endpoints are protected and authorized via end-user access tokens acquired through Thanx SSO.

**Human URL:** [https://docs.thanx.com/consumer/overview](https://docs.thanx.com/consumer/overview)

**Base URL:** `https://api.thanx.com`

#### Tags:

 - Loyalty, Rewards, Users, Gifts, Points, Purchases, Cards

#### Properties

- [OpenAPI](openapi/thanx-consumer-api-openapi.yml)
- [Documentation](https://docs.thanx.com/consumer/overview)
- [APIReference](https://docs.thanx.com/consumer/overview)
- [Authentication](https://docs.thanx.com/consumer/usage/headers)
- [SDK](https://github.com/thanx/thanx-sdk-ios)
- [SDK](https://github.com/thanx/thanx-sdk-android)
- [BestPractices](https://docs.thanx.com/consumer/best-practices/design)
- [Errors](https://docs.thanx.com/consumer/usage/errors)
- [NaftikoCapability](capabilities/consumer-api-cards.yaml)
- [NaftikoCapability](capabilities/consumer-api-gift-cards.yaml)
- [NaftikoCapability](capabilities/consumer-api-locations.yaml)
- [NaftikoCapability](capabilities/consumer-api-points.yaml)
- [NaftikoCapability](capabilities/consumer-api-purchases.yaml)
- [NaftikoCapability](capabilities/consumer-api-rewards.yaml)
- [NaftikoCapability](capabilities/consumer-api-users.yaml)
- [JSONSchema](json-schema/consumer-api-authorization-schema.json)
- [JSONSchema](json-schema/consumer-api-birth-date-schema.json)
- [JSONSchema](json-schema/consumer-api-card-envelope-schema.json)
- [JSONSchema](json-schema/consumer-api-card-schema.json)
- [JSONSchema](json-schema/consumer-api-gift-card-schema.json)
- [JSONSchema](json-schema/consumer-api-location-schema.json)
- [JSONSchema](json-schema/consumer-api-pagination-schema.json)
- [JSONSchema](json-schema/consumer-api-purchase-schema.json)
- [JSONSchema](json-schema/consumer-api-reward-envelope-schema.json)
- [JSONSchema](json-schema/consumer-api-reward-schema.json)
- [JSONSchema](json-schema/consumer-api-user-envelope-schema.json)
- [JSONSchema](json-schema/consumer-api-user-input-schema.json)
- [JSONSchema](json-schema/consumer-api-user-schema.json)
- [JSONStructure](json-structure/consumer-api-authorization-structure.json)
- [JSONStructure](json-structure/consumer-api-birth-date-structure.json)
- [JSONStructure](json-structure/consumer-api-card-envelope-structure.json)
- [JSONStructure](json-structure/consumer-api-card-structure.json)
- [JSONStructure](json-structure/consumer-api-gift-card-structure.json)
- [JSONStructure](json-structure/consumer-api-location-structure.json)
- [JSONStructure](json-structure/consumer-api-pagination-structure.json)
- [JSONStructure](json-structure/consumer-api-purchase-structure.json)
- [JSONStructure](json-structure/consumer-api-reward-envelope-structure.json)
- [JSONStructure](json-structure/consumer-api-reward-structure.json)
- [JSONStructure](json-structure/consumer-api-user-envelope-structure.json)
- [JSONStructure](json-structure/consumer-api-user-input-structure.json)
- [JSONStructure](json-structure/consumer-api-user-structure.json)
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
- [JSONLD](json-ld/thanx-consumer-api-context.jsonld)

### Thanx Partner API
The Thanx Partner API provides privileged endpoints supporting custom integration use cases, including end-user token issuance, campaign management and reward issuance, subscriber ingestion, feedback handling, tags, and metadata lookups for merchants, locations, and scopes. It is intended for approved partners building deeper integrations with the Thanx engagement and marketing platform.

**Human URL:** [https://docs.thanx.com/partner/overview](https://docs.thanx.com/partner/overview)

**Base URL:** `https://api.thanx.com`

#### Tags:

 - Campaigns, Subscribers, Marketing, Rewards, Merchants

#### Properties

- [OpenAPI](openapi/thanx-partner-api-openapi.yml)
- [Documentation](https://docs.thanx.com/partner/overview)
- [APIReference](https://docs.thanx.com/partner/overview)
- [Authentication](https://docs.thanx.com/consumer/usage/headers)
- [GettingStarted](https://docs.thanx.com/overview/guides/campaign-reward-issuance)
- [GettingStarted](https://docs.thanx.com/overview/guides/subscriber-ingestion)
- [NaftikoCapability](capabilities/partner-api-auth.yaml)
- [NaftikoCapability](capabilities/partner-api-campaigns.yaml)
- [NaftikoCapability](capabilities/partner-api-issuance-jobs.yaml)
- [NaftikoCapability](capabilities/partner-api-metadata.yaml)
- [NaftikoCapability](capabilities/partner-api-subscribers.yaml)
- [NaftikoCapability](capabilities/partner-api-users.yaml)
- [JSONSchema](json-schema/partner-api-campaign-input-schema.json)
- [JSONSchema](json-schema/partner-api-campaign-schema.json)
- [JSONSchema](json-schema/partner-api-campaign-variant-input-schema.json)
- [JSONSchema](json-schema/partner-api-issuance-job-schema.json)
- [JSONSchema](json-schema/partner-api-partner-user-schema.json)
- [JSONStructure](json-structure/partner-api-campaign-input-structure.json)
- [JSONStructure](json-structure/partner-api-campaign-structure.json)
- [JSONStructure](json-structure/partner-api-campaign-variant-input-structure.json)
- [JSONStructure](json-structure/partner-api-issuance-job-structure.json)
- [JSONStructure](json-structure/partner-api-partner-user-structure.json)
- [Example](examples/partner-api-campaign-example.json)
- [Example](examples/partner-api-campaign-input-example.json)
- [Example](examples/partner-api-campaign-variant-input-example.json)
- [Example](examples/partner-api-issuance-job-example.json)
- [Example](examples/partner-api-partner-user-example.json)
- [JSONLD](json-ld/thanx-partner-api-context.jsonld)

### Thanx Loyalty API
The Thanx Loyalty API supports integrations with digital ordering and kiosk providers, exposing account lookup and basket lifecycle operations so external ordering systems can connect to a brand's Thanx loyalty program, apply rewards and points products, and track loyalty progress. All endpoints are authorized via end-user access tokens and a merchant key.

**Human URL:** [https://docs.thanx.com/loyalty/overview](https://docs.thanx.com/loyalty/overview)

**Base URL:** `https://loyalty.thanx.com`

#### Tags:

 - Loyalty, Points, Online Ordering, Baskets

#### Properties

- [OpenAPI](openapi/thanx-loyalty-api-openapi.yml)
- [Documentation](https://docs.thanx.com/loyalty/overview)
- [APIReference](https://docs.thanx.com/loyalty/overview)
- [Authentication](https://docs.thanx.com/consumer/usage/headers)
- [GettingStarted](https://docs.thanx.com/overview/guides/pos-kiosk)
- [Regions](https://docs.thanx.com/loyalty/private-link)
- [NaftikoCapability](capabilities/loyalty-api-account.yaml)
- [NaftikoCapability](capabilities/loyalty-api-baskets.yaml)
- [JSONSchema](json-schema/loyalty-api-account-schema.json)
- [JSONSchema](json-schema/loyalty-api-basket-input-schema.json)
- [JSONSchema](json-schema/loyalty-api-basket-item-schema.json)
- [JSONSchema](json-schema/loyalty-api-basket-schema.json)
- [JSONSchema](json-schema/loyalty-api-loyalty-reward-schema.json)
- [JSONSchema](json-schema/loyalty-api-payment-schema.json)
- [JSONSchema](json-schema/loyalty-api-points-product-schema.json)
- [JSONStructure](json-structure/loyalty-api-account-structure.json)
- [JSONStructure](json-structure/loyalty-api-basket-input-structure.json)
- [JSONStructure](json-structure/loyalty-api-basket-item-structure.json)
- [JSONStructure](json-structure/loyalty-api-basket-structure.json)
- [JSONStructure](json-structure/loyalty-api-loyalty-reward-structure.json)
- [JSONStructure](json-structure/loyalty-api-payment-structure.json)
- [JSONStructure](json-structure/loyalty-api-points-product-structure.json)
- [Example](examples/loyalty-api-account-example.json)
- [Example](examples/loyalty-api-basket-example.json)
- [Example](examples/loyalty-api-basket-input-example.json)
- [Example](examples/loyalty-api-basket-item-example.json)
- [Example](examples/loyalty-api-loyalty-reward-example.json)
- [Example](examples/loyalty-api-payment-example.json)
- [Example](examples/loyalty-api-points-product-example.json)
- [JSONLD](json-ld/thanx-loyalty-api-context.jsonld)

## Common Properties

- [Website](https://www.thanx.com/)
- [DeveloperPortal](https://docs.thanx.com/overview)
- [Documentation](https://docs.thanx.com/overview)
- [GettingStarted](https://docs.thanx.com/overview/integrating)
- [Pricing](https://www.thanx.com/pricing)
- [GitHubOrganization](https://github.com/thanx)
- [LLMsTxt](https://docs.thanx.com/llms.txt)
- [ChangeLog](https://docs.thanx.com/data/changelog)
- [BestPractices](https://docs.thanx.com/consumer/best-practices/design)
- [Errors](https://docs.thanx.com/consumer/usage/errors)
- [Webhooks Overview](https://docs.thanx.com/webhooks/overview)
- [Data Exports (Connex)](https://docs.thanx.com/data/overview)
- [MCP Server](https://docs.thanx.com/mcp)
- [AI Integration](https://docs.thanx.com/ai/overview)
- [Claude Code Skills (Agent Starter)](https://github.com/thanx/thanx-agent-starter)
- [Postman API Collections](https://docs.thanx.com/overview/api_collections)
- [SpectralRules](rules/thanx-spectral-rules.yml)
- [Vocabulary](vocabulary/thanx-vocabulary.yaml)
- [Plans](plans/thanx-plans-pricing.yml)
- [RateLimits](rate-limits/thanx-rate-limits.yml)
- [FinOps](finops/thanx-finops.yml)

## Features

| Name | Description |
|------|-------------|
| Loyalty & Rewards | Configurable loyalty programs with points, tiers, rewards, multipliers, and reward templates across in-store and online venues. |
| Lifecycle Marketing | Campaign creation with treatment/control variants and batched reward issuance to targeted audiences. |
| CRM & Data Infrastructure | Unified customer profiles, communication settings, tags, and NPS feedback backed by warehouse data exports. |
| Digital Ordering & Pay | Basket lifecycle and account APIs for digital ordering, kiosk, and pay-at-table integrations. |
| Card-Linked Loyalty | Register payment cards to attribute purchases automatically for card-linked loyalty earning. |
| Webhooks | Real-time events for purchases, reward issuance, reward batch completion, SMS subscriptions, and communication settings. |

## Use Cases

| Name | Description |
|------|-------------|
| Branded Loyalty App | Build a custom branded app on the Consumer API with SSO, rewards, points, and purchase history. |
| Targeted Reward Campaigns | Partners create campaigns and issue rewards to large audiences via batched issuance jobs. |
| Kiosk & Online Ordering Loyalty | Ordering and kiosk providers connect baskets to a brand loyalty program to apply rewards and points. |
| Warehouse Analytics | Export Thanx data models to Snowflake, BigQuery, Redshift, or Databricks for analytics. |

## Integrations

| Name | Description |
|------|-------------|
| Olo | Online ordering provider referenced in purchase order providers. |
| Toast | POS / ordering provider referenced in purchase order providers. |
| Snowflake | Connex data-export destination. |
| Google BigQuery | Connex data-export destination. |
| Amazon Redshift | Connex data-export destination. |
| Databricks | Connex data-export destination. |
| AWS PrivateLink | Private connectivity option for the Loyalty API. |

## Artifacts

Machine-readable API specifications organized by format.

### OpenAPI

- [Thanx Consumer API](openapi/thanx-consumer-api-openapi.yml)
- [Thanx Loyalty API](openapi/thanx-loyalty-api-openapi.yml)
- [Thanx Partner API](openapi/thanx-partner-api-openapi.yml)

### JSON Schema

25 JSON Schema files in [json-schema/](json-schema/).

### JSON Structure

25 JSON Structure files in [json-structure/](json-structure/).

### JSON-LD

- [thanx-consumer-api-context.jsonld](json-ld/thanx-consumer-api-context.jsonld)
- [thanx-loyalty-api-context.jsonld](json-ld/thanx-loyalty-api-context.jsonld)
- [thanx-partner-api-context.jsonld](json-ld/thanx-partner-api-context.jsonld)

### Examples

25 example payloads in [examples/](examples/).

## Naftiko Capabilities

Self-contained Naftiko capabilities (one per business surface), each exposing both a REST and an MCP adapter.

| Capability | Owning API | Tools |
|------------|-----------|-------|
| [Thanx Consumer API — Cards](capabilities/consumer-api-cards.yaml) | Thanx Consumer API | 3 |
| [Thanx Consumer API — Gift Cards](capabilities/consumer-api-gift-cards.yaml) | Thanx Consumer API | 2 |
| [Thanx Consumer API — Locations](capabilities/consumer-api-locations.yaml) | Thanx Consumer API | 1 |
| [Thanx Consumer API — Points](capabilities/consumer-api-points.yaml) | Thanx Consumer API | 1 |
| [Thanx Consumer API — Purchases](capabilities/consumer-api-purchases.yaml) | Thanx Consumer API | 2 |
| [Thanx Consumer API — Rewards](capabilities/consumer-api-rewards.yaml) | Thanx Consumer API | 4 |
| [Thanx Consumer API — Users](capabilities/consumer-api-users.yaml) | Thanx Consumer API | 2 |
| [Thanx Loyalty API — Account](capabilities/loyalty-api-account.yaml) | Thanx Loyalty API | 1 |
| [Thanx Loyalty API — Baskets](capabilities/loyalty-api-baskets.yaml) | Thanx Loyalty API | 1 |
| [Thanx Partner API — Auth](capabilities/partner-api-auth.yaml) | Thanx Partner API | 1 |
| [Thanx Partner API — Campaigns](capabilities/partner-api-campaigns.yaml) | Thanx Partner API | 4 |
| [Thanx Partner API — Issuance Jobs](capabilities/partner-api-issuance-jobs.yaml) | Thanx Partner API | 2 |
| [Thanx Partner API — Metadata](capabilities/partner-api-metadata.yaml) | Thanx Partner API | 3 |
| [Thanx Partner API — Subscribers](capabilities/partner-api-subscribers.yaml) | Thanx Partner API | 1 |
| [Thanx Partner API — Users](capabilities/partner-api-users.yaml) | Thanx Partner API | 2 |

## Vocabulary

- [Thanx Vocabulary](vocabulary/thanx-vocabulary.yaml) — Unified taxonomy mapping 14 resources, 3 actions, 15 workflows, and 3 personas across operational (OpenAPI) and capability (Naftiko) dimensions

## Rules

- [Thanx Spectral Ruleset](rules/thanx-spectral-rules.yml) — 33 rules enforcing Thanx API conventions

## Commercial

- [Plans & Pricing](plans/thanx-plans-pricing.yml) — API Commons Plans 0.1 (custom / contact-sales)
- [Rate Limits](rate-limits/thanx-rate-limits.yml) — API Commons Rate Limits 0.1
- [FinOps](finops/thanx-finops.yml) — FOCUS-aligned FinOps Framework 1.0

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com
