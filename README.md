# UK Civil Aviation Authority (uk-caa)

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
