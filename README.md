# DAT Freight & Analytics (dat-freight)

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
