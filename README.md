# UK Civil Aviation Authority (uk-caa)

The UK Civil Aviation Authority (CAA) is the United Kingdom's independent aviation regulator and a public corporation of the Department for Transport. It licenses UK airlines, registers UK civil aircraft on the G-INFO register, regulates airspace and airports, economically regulates Heathrow and Gatwick, enforces UK air passenger rights, and — the part that matters most to travel distribution — runs the Air Travel Organiser's Licence (ATOL) scheme, which is the statutory gate every business selling flight-inclusive packages to UK consumers must pass through, including sellers established outside the UK. The CAA sits above the distribution chain rather than inside it: it does not distribute inventory, does not operate a GDS or NDC connection, and has no NDC posture of its own. Its API posture is thin and honest to record — there is no developer portal, no OpenAPI, and no published aviation data API. The only documented, self-serve, key-free public API on a CAA domain is the Citizen Space (Delib) consultation API at consultations.caa.co.uk/api, a vendor platform API rather than an aviation data API. The aviation surfaces that do exist — the G-INFO aircraft register search and the Check an ATOL search — are undocumented ASP.NET JSON backends whose CORS policy is locked to www.caa.co.uk and which are reCAPTCHA-gated. Bulk aviation data is delivered as CSV, PDF and XLSX files behind opaque GUID download URLs, and the full G-INFO aircraft register is a paid subscription emailed as an MS Excel file licensed for use on a single PC. Home market is the United Kingdom.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/uk-caa/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/uk-caa/refs/heads/main/apis.yml)

## Tags

- Travel
- United Kingdom
- Aviation
- Airline
- Airports
- Regulator
- Government
- Distribution
- Consumer Protection
- Open Data

## Timestamps

- **Created:** 2026-07-28
- **Modified:** 2026-07-28

## APIs

### CAA Consultations API

The Citizen Space (Delib) public consultation API deployed on the CAA's consultations domain. Two documented methods — `json_search_results` and `json_consultation_details` — return published CAA consultation activities as JSON with no API key and no signup. Versions 2.0 through 2.4 are served concurrently. Verified live 2026-07-28 (HTTP 200, JSON array). This is the only documented, publicly callable API on a caa.co.uk domain; it is the vendor's platform API, not a CAA aviation data API.

- **Human URL:** [https://consultations.caa.co.uk/api/2.4/](https://consultations.caa.co.uk/api/2.4/)
- **Base URL:** `https://consultations.caa.co.uk/api/2.4`

#### Tags

- Consultations
- Government
- United Kingdom

#### Properties

- [Documentation](https://consultations.caa.co.uk/api/2.4/)
- [Documentation](https://consultations.caa.co.uk/api/)
- [API Reference](https://consultations.caa.co.uk/api/2.3/)
- [Website](https://consultations.caa.co.uk/)

## Common Properties

- [Website](https://www.caa.co.uk/)
- [Documentation](https://www.caa.co.uk/data-and-analysis/)
- [Blog](https://www.caa.co.uk/newsroom/news/)
- [LinkedIn](https://www.linkedin.com/company/civil-aviation-authority)
- [X](https://x.com/UK_CAA)
- [YouTube](https://www.youtube.com/user/UKCAA)
- [Instagram](https://www.instagram.com/uk.caa)
- [Vulnerability Disclosure](https://www.caa.co.uk/website-policies/vulnerability-disclosure-policy/)
- [security.txt](https://www.caa.co.uk/.well-known/security.txt)
- [Portal](https://portal.caa.co.uk)
- [Registry — G-INFO UK aircraft register](https://www.caa.co.uk/aircraft-register/g-info/search-g-info/)
- [Registry — Check an ATOL](https://www.caa.co.uk/atol-protection/check-an-atol/search-atol-holders/)
- [Dataset — UK airport data](https://www.caa.co.uk/data-and-analysis/uk-aviation-market/airports/uk-airport-data/)
- [Dataset — UK flight punctuality statistics](https://www.caa.co.uk/data-and-analysis/uk-aviation-market/flight-punctuality/uk-flight-punctuality-statistics/)
- [Dataset — ATOL reports](https://www.caa.co.uk/atol-protection/check-an-atol/atol-reports/)
- [Dataset — data.gov.uk organisation record](https://ckan.publishing.service.gov.uk/api/3/action/organization_show?id=civil-aviation-authority)
- [Legal — Do I need an ATOL](https://www.caa.co.uk/atol-protection/atol-requirements-for-the-travel-industry/do-i-need-an-atol/)
- [Legal — Airline ticket agents](https://www.caa.co.uk/atol-protection/atol-compliance/requirements-legal-obligations/airline-ticket-agents/)
- [Legal — Accessing information held by the CAA](https://www.caa.co.uk/about-us/information-requests/accessing-information-held-by-the-caa/)

## Switching Cost

Recorded in full in [`review.yml`](review.yml). In short:

| Dimension | Finding |
| --- | --- |
| Interface shape | `proprietary-undocumented` — no OpenAPI, no AIXM, no open standard; the one documented API is Delib's Citizen Space v2.4 |
| Second source | `no-alternative` — the CAA is the statutory source for the UK aircraft register, ATOL licensing and UK aviation statistics |
| Exit path | `export-on-request` — no export operation; paid Excel orders, opaque GUID file downloads, and FOI/EIR/UK GDPR requests |
| Identifier portability | Registration mark, ICAO 24-bit address, ICAO Doc 8643 type designator, serial number — portable; ATOL licence number and free-text airport names — not |
| Contractual lock-in | "No statistical data provided by CAA maybe sold on to a third party"; G-INFO "authorised for use on a single PC only"; data.gov.uk licence "not specified" (not OGL) |
| Access gate | `self-serve` for the consultation API; everything aviation is paid order, origin-locked, or FOI |
| Distribution model | `not-applicable` — regulator; NDC posture not applicable; the lever is ATOL licensing, not NDC |

## Maintainers

- Kin Lane — kin@apievangelist.com
