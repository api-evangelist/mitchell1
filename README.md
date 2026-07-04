# Mitchell 1 (mitchell1)

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

### Mitchell 1 ProDemand Labor & Parts Data API

Honestly-modeled entry, not a confirmed public spec. Mitchell 1's API Request program advertises a "Data API for labor times" for both light-duty automotive (ProDemand) and medium/heavy-duty trucks (TruckSeries), alongside Website UI Integration (intents for labor, parts, fluids, and maintenance data) and a full Website Launcher pass-through into ProDemand keyed by VIN, ACES ID, or year/make/model. No base URL, request/response schema, or public API reference is published for this data API; it is disclosed only in partner integration materials after an approved application.

- **Human URL:** [https://mitchell1.com/resources/api-request/](https://mitchell1.com/resources/api-request/)

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
