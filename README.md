# Mitchell 1 (mitchell1)

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
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

Mitchell 1 is a division of Snap-on Incorporated providing repair information (ProDemand, TruckSeries) and shop management software (Manager SE, SocialCRM) to independent auto repair shops. Mitchell 1 is a legacy enterprise software provider, not an API-first company - it has no public, self-serve REST API reference. It does operate a gated Web-Intent / Data API integration program for approved third-party partners (shop management systems, CRM, parts and marketing platforms) to embed or link into ProDemand labor, parts, and maintenance data, fronted by a token-based (TAPE) auth flow and an Intent Registry discovery service. Access requires submitting an integration request, a Mitchell 1 review (roughly two weeks), and a signed partner agreement; no public API reference, OpenAPI document, or SDK is published.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/mitchell1/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/mitchell1/refs/heads/main/apis.yml)

## Ownership note

Mitchell 1 (mitchell1.com) is a Snap-on Incorporated division. It is a **separate company** from Mitchell International (mitchell.com, part of the Enlyte family of businesses), which runs its own public developer portal at developer.mitchell.com for a REST/OData "RepairCenter" API used in collision claims and estimating. The two share a historical "Mitchell" name and lineage but are distinct, separately owned businesses today. This repository covers Mitchell 1 (Snap-on) only.

## Access model

Mitchell 1 is not an API-first company. There is no self-serve developer signup, no published API reference, and no OpenAPI/Postman/AsyncAPI artifact to source honestly:

- **Web-Intent integration** - a partner application obtains a token via the TAPE (transfer application public extension) flow and presents it to the Secure Intents website to consume specific "intents" - self-contained sub-flows for labor, parts, fluids, and maintenance data - keyed by VIN, ACES ID, or year/make/model, with the selected data returned to the calling application.
- **Website Launcher (pass-through)** - a lighter integration where a partner app passes a vehicle identifier straight into full ProDemand (or ProDemand Truck) using the shop's own credentials or account number; the user works inside the Mitchell 1 UI rather than getting data back programmatically.
- **Data API for labor times** - advertised by name for both light-duty automotive (ProDemand) and medium/heavy-duty trucks (TruckSeries), but with no public base URL, schema, or reference published; disclosed only to approved partners.
- A small, publicly reachable sandbox Help index at `testintents.mitchell1.com/Help/Api` lists a handful of plain REST endpoints (see APIs below) with minimal documentation and no auth/schema details - useful for confirming the underlying protocol is REST, not evidence of a full public API.

Getting any of this requires submitting a company/use-case application through [mitchell1.com/resources/api-request](https://mitchell1.com/resources/api-request/), a roughly two-week Mitchell 1 review, and a signed partner agreement before developer portal access is granted.

## Tags

- Automotive
- Repair Information
- Shop Management
- Labor Guide
- VIN Decode
- Snap-on
- Partner API
- Gated

## Timestamps

- **Created:** 2026-07-04
- **Modified:** 2026-07-04

## APIs

### Mitchell 1 Intent Registry Discovery API

Discovery endpoint (`GET api/service/v1/discovery`) that a partner application calls on startup to resolve the current RESTful URI patterns for the Web-Intent resources it needs, rather than hardcoding them. Confirmed on Mitchell 1's public sandbox API help index; production access requires an approved integration partner account.

- **Human URL:** [https://testintents.mitchell1.com/Help/Api](https://testintents.mitchell1.com/Help/Api)
- **Base URL:** `https://testintents.mitchell1.com/api`

#### Properties

- [Documentation](https://mitchell1.com/resources/api-request/)
- [API Reference](https://testintents.mitchell1.com/Help/Api)

### Mitchell 1 Intent Resolve API

Resolve endpoint (`POST api/intent/v1/resolve`) used to securely look up where a specific Web-Intent should be routed, as part of the TAPE token flow that hands a partner application a token it presents to the Secure Intents website to consume ProDemand labor, parts, fluids, and maintenance intents.

- **Human URL:** [https://testintents.mitchell1.com/Help/Api](https://testintents.mitchell1.com/Help/Api)
- **Base URL:** `https://testintents.mitchell1.com/api`

#### Properties

- [Documentation](https://mitchell1.com/resources/api-request/)
- [API Reference](https://testintents.mitchell1.com/Help/Api)

### Mitchell 1 Integration Script Services API

Two GET endpoints (`api/script/v1/integrationclient` and `api/script/v1/integrationserver`) listed in the sandbox Intent Registry index with no published documentation beyond their names; they appear to serve client- and server-side integration script assets for embedding Mitchell 1 Web-Intent flows inside a partner shop management system. Listed here for completeness, not confirmed behavior.

- **Human URL:** [https://testintents.mitchell1.com/Help/Api](https://testintents.mitchell1.com/Help/Api)
- **Base URL:** `https://testintents.mitchell1.com/api`

#### Properties

- [API Reference](https://testintents.mitchell1.com/Help/Api)


#### Properties

- [Documentation](https://mitchell1.com/resources/api-request/)
- [Documentation](https://mitchell1.com/resources/api-request/attachment/api-integration/)

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/mitchell-1/)
- [Website](https://mitchell1.com/)
- [Documentation](https://mitchell1.com/resources/api-request/)
- [Plans](plans/mitchell1-plans-pricing.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
