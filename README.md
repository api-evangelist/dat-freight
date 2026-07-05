# DAT Freight & Analytics (dat-freight)

DAT Freight & Analytics operates the largest truckload freight marketplace in North America - the DAT One load board - along with **RateView**, the industry's benchmark for spot and contract freight rates drawn from hundreds of billions of dollars in real transactions. DAT exposes these products to Transportation Management Systems (TMS) and freight platforms through the **DAT Developer Portal** (developer.dat.com) as a RESTful API suite covering load posting and search, RateView rate lookups, BookNow instant booking, and shipment tracking.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/dat-freight/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/dat-freight/refs/heads/main/apis.yml)

## Access Model (Read This First)

DAT's API is **not** a self-serve, publicly documented API. Access is gated on two fronts:

- **The developer portal is behind an account login.** developer.dat.com is a Redocly-hosted portal that redirects to an OIDC sign-in; you must have a DAT account and request developer access (developersupport@dat.com) to read the reference.
- **Access is subscription-gated.** A RESTful integration requires a **DAT One load board subscription** plus a **service (organization) account**. The **RateView Rate Lookup API** additionally requires a **Combo Pro** or **Combo Premium** subscription. **CarrierWatch** and **OnBoard** do **not** currently support RESTful API integration.

Authentication is a documented **two-tier token model**: an **organization token** is minted from service-account (organization) credentials, and a **user token** is minted for the specific user account making requests. The user token is then sent as a Bearer token on data requests.

### Endpoints are MODELED

Because the portal reference could not be inspected during this catalog build (account-gated), the OpenAPI, Postman, and Open Collection artifacts here are **honestly modeled** from DAT's publicly documented capabilities (LoadSearch for postings, RateView for analytics, BookNow, Tracking) and its documented organization/user token auth. The host split - `identity.api.dat.com`, `freight.api.dat.com`, `analytics.api.dat.com` - and the exact paths and schemas are a plausible model, **not confirmed facts**, and should be reconciled once portal access is granted. See `review.yml` (`endpointsModeled: true`).

## Tags

- Freight
- Trucking
- Load Board
- Logistics
- Freight Rates
- RateView
- Supply Chain
- Transportation
- Analytics

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### DAT Identity & Token API

Issues the two-tier access tokens every other DAT API requires - an organization token from service-account credentials plus a user token for the requesting user. *Endpoints modeled.*

- **Human URL:** [https://developer.dat.com/](https://developer.dat.com/)
- **Base URL:** `https://identity.api.dat.com` *(modeled host)*

### DAT Load Board Search API

Search the DAT One marketplace for available loads and trucks by lane, equipment type, and age - the LoadSearch surface used by TMS integrations. Available with any DAT One load board subscription. *Endpoints modeled.*

- **Human URL:** [https://www.dat.com/api-integration](https://www.dat.com/api-integration)
- **Base URL:** `https://freight.api.dat.com` *(modeled host)*

### DAT Freight Posting API

Create, update, refresh, and remove load and truck postings on the DAT One load board directly from a TMS. *Endpoints modeled.*

- **Human URL:** [https://www.dat.com/api-integration](https://www.dat.com/api-integration)
- **Base URL:** `https://freight.api.dat.com` *(modeled host)*

### DAT RateView Rate Lookup API

Look up RateView benchmark freight rates - spot and contract linehaul rates by origin, destination, and equipment type - for rate benchmarking, historical analysis, and lane-level performance. Requires a RateView Combo Pro or Combo Premium subscription plus Connexion and RateView seats. *Endpoints modeled.*

- **Human URL:** [https://www.dat.com/resources/shipper-api-integrations](https://www.dat.com/resources/shipper-api-integrations)
- **Base URL:** `https://analytics.api.dat.com` *(modeled host)*

### DAT BookNow API

Instant, digital load booking (BookNow) so carriers can accept a posted load at a set rate without a phone call, and brokers can offer bookable freight programmatically. *Endpoints modeled.*

- **Human URL:** [https://www.dat.com/api-integration](https://www.dat.com/api-integration)
- **Base URL:** `https://freight.api.dat.com` *(modeled host)*

### DAT Tracking API

DAT Tracking shipment visibility - register loads for tracking and retrieve location and status updates for in-transit freight. *Endpoints modeled.*

- **Human URL:** [https://www.dat.com/api-integration](https://www.dat.com/api-integration)
- **Base URL:** `https://freight.api.dat.com` *(modeled host)*

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/dat-solutions)
- [Website](https://www.dat.com)
- [Documentation](https://developer.dat.com/)
- [Sign Up](https://www.dat.com/api-integration)
- [Plans](plans/dat-freight-plans-pricing.yml)
- [Rate Limits](rate-limits/dat-freight-rate-limits.yml)
- [Fin Ops](finops/dat-freight-finops.yml)
- [Blog](https://www.dat.com/blog)

## Artifacts

- [OpenAPI (modeled)](openapi/dat-freight-openapi.yml)
- [Postman Collection (modeled)](collections/dat-freight.postman_collection.json)
- [Open Collection (modeled)](collections/dat-freight.opencollection.json)
- [Review](review.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
