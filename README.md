# Smile.io (smile-io)

Smile.io is a loyalty, rewards, and referrals platform for e-commerce brands, widely used on Shopify. Merchants run points programs, referral programs, and VIP tiers, and can integrate them programmatically through the Smile.io REST API (base `https://api.smile.io/v1`). The REST API is organized around resource-oriented URLs, returns JSON, uses standard HTTP status codes, and is authenticated with an HTTP Bearer token.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/smile-io/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/smile-io/refs/heads/main/apis.yml)

## Access Model (Important)

The Smile.io REST API is **plan-gated**. Based on Smile's published pricing, programmatic REST API access is only available on the **Plus** plan (listed at $999/mo) and **Enterprise** (custom) tiers; the Free, Essential, Standard, and Growth plans run points/referral/VIP programs through the app and integrations but do **not** unlock the REST API. Enterprise adds custom API rate limits and data-warehouse sync. Pricing and plan boundaries change often - treat the figures here as a snapshot and confirm on the pricing page.

Authentication uses an `Authorization: Bearer <token>` header, where the token is a **merchant API key** (managed in the Smile admin) or, for apps, the **OAuth access token** received after a merchant completes the OAuth flow. All requests must use HTTPS.

## Tags

- Loyalty
- Rewards
- Referrals
- E-commerce
- Points
- Customer Retention
- Shopify

## Timestamps

- **Created:** 2026-07-10
- **Modified:** 2026-07-10

## APIs

The logical APIs below are grounded on the endpoints documented in Smile's published OpenAPI spec (`https://dev.smile.io/schemas/rest-api.json`) and reference docs at [dev.smile.io](https://dev.smile.io/api/introduction).

### Smile.io Customers API

List and retrieve loyalty program members with their point balances and state (`candidate`, `member`, `disabled`), and create or update a customer from an external system via the customer identities endpoint.

- **Human URL:** [https://dev.smile.io/api/resources/customers/list-customers](https://dev.smile.io/api/resources/customers/list-customers)
- **Base URL:** `https://api.smile.io/v1`
- **Endpoints:** `GET /customers`, `GET /customers/{id}`, `POST /customer_identities/create_or_update`

### Smile.io Points Transactions API

Create, list, and retrieve points transactions - the point balance changes (earn, redeem, adjust) applied to a customer - and read program-level points settings.

- **Human URL:** [https://dev.smile.io/api/resources/points-transactions/list-points-transactions](https://dev.smile.io/api/resources/points-transactions/list-points-transactions)
- **Base URL:** `https://api.smile.io/v1`
- **Endpoints:** `POST /points_transactions`, `GET /points_transactions`, `GET /points_transactions/{id}`, `GET /points_settings`

### Smile.io Points Products API

List and retrieve points products - the redeemable products a customer can purchase with points - and purchase a points product on behalf of a customer.

- **Human URL:** [https://dev.smile.io/api/resources/points-products/list-points-products](https://dev.smile.io/api/resources/points-products/list-points-products)
- **Base URL:** `https://api.smile.io/v1`
- **Endpoints:** `GET /points_products`, `GET /points_products/{id}`, `POST /points_products/{id}/purchase`

### Smile.io Reward Fulfillments API

List reward fulfillment records - the fulfillment of rewards a customer has redeemed (for example a discount code issued for a redemption). The reward object is surfaced through these fulfillments.

- **Human URL:** [https://dev.smile.io/api/resources/reward-fulfillments/list-reward-fulfillments](https://dev.smile.io/api/resources/reward-fulfillments/list-reward-fulfillments)
- **Base URL:** `https://api.smile.io/v1`
- **Endpoints:** `GET /reward_fulfillments`

### Smile.io Earning Rules API

List the earning rules that define how customers earn points in a program (for example points for placing an order, creating an account, or a birthday).

- **Human URL:** [https://dev.smile.io/api/resources/earning-rules/list-earning-rules](https://dev.smile.io/api/resources/earning-rules/list-earning-rules)
- **Base URL:** `https://api.smile.io/v1`
- **Endpoints:** `GET /earning_rules`

### Smile.io VIP Tiers API

List the VIP tiers configured for a program, including their thresholds and perks. VIP tier changes for a customer are represented by the VIP Tier Change object.

- **Human URL:** [https://dev.smile.io/api/resources/vip-tiers/list-vip-tiers](https://dev.smile.io/api/resources/vip-tiers/list-vip-tiers)
- **Base URL:** `https://api.smile.io/v1`
- **Endpoints:** `GET /vip_tiers`

### Smile.io Activities API

Record a custom customer activity so it can earn points via a matching earning rule - the programmatic way to reward behavior that happens outside Smile's built-in triggers.

- **Human URL:** [https://dev.smile.io/api/resources/activities/create-activity](https://dev.smile.io/api/resources/activities/create-activity)
- **Base URL:** `https://api.smile.io/v1`
- **Endpoints:** `POST /activities`

## A Note on Referrals and Rewards

Smile is marketed on Points, **Referrals**, and Rewards. In the current public REST API, Referral and Reward are documented as **objects** (schemas), but there is no dedicated top-level `GET /referrals` or `GET /rewards` collection endpoint. Referral outcomes surface through customers, points transactions, and activities; reward outcomes surface through the Reward Fulfillments endpoint. This entry models the endpoints that actually exist rather than inventing referral/reward CRUD surfaces.

## Client SDKs and Widgets

Beyond the REST API, Smile publishes a browser **JavaScript SDK** (`Smile.js`) and **Smile UI** components for building on-store loyalty experiences, plus **webhooks** for reacting to loyalty events. Those are storefront/customer-facing surfaces and are separate from the server-side REST API documented here.

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/smile-rewards)
- [Website](https://smile.io)
- [Documentation](https://dev.smile.io/api/introduction)
- [Plans](plans/smile-io-plans-pricing.yml)
- [Rate Limits](rate-limits/smile-io-rate-limits.yml)
- [Fin Ops](finops/smile-io-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
