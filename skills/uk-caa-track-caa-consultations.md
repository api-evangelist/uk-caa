---
name: Track UK CAA consultations
description: >-
  Find open, forthcoming or closed UK Civil Aviation Authority consultations by
  topic, audience or date window, then pull the full detail record for one of them —
  including the closing date, contact, supporting documents and the direct
  participation link.
api: openapi/uk-caa-consultations-api-openapi.yml
provider: uk-caa
operations:
  - json_search_results
  - json_consultation_details
auth: none
generated: '2026-07-28'
method: generated
source: >-
  Grounded in openapi/uk-caa-consultations-api-openapi.yml (both operationIds
  verified present), conventions/uk-caa-conventions.yml and
  errors/uk-caa-problem-types.yml. Written by API Evangelist; not published by the
  UK CAA.
---

# Track UK CAA consultations

The UK Civil Aviation Authority runs its public consultations on Citizen Space at
`https://consultations.caa.co.uk`. Its version 2.4 API is anonymous, read-only and
returns JSON. Use it to monitor regulatory consultations — airspace change, ATOL
reform, licensing, drones, economic regulation — and to pull the detail record for
any one of them.

## Before you start

- **No authentication.** No key, no signup, no header. The API exposes exactly what
  a public visitor to the site can see.
- **Base URL:** `https://consultations.caa.co.uk/api/2.4`
- Requests are plain HTTPS `GET` with url-encoded query arguments.
- `access-control-allow-origin: *`, so this is callable from a browser as well as a
  server. Server-side integration with a cache is the pattern the vendor guide
  recommends.

## Step 1 — search for activities (`json_search_results`)

```
GET https://consultations.caa.co.uk/api/2.4/json_search_results?st=open&fields=all
```

Useful parameters (all optional; supplying none returns every published activity):

| Parameter | Use |
|---|---|
| `st` | `open`, `forthcoming` or `closed` |
| `tx` | free-text search across title and overview, case-insensitive |
| `de` | workspace/department id, e.g. `corporate-communications` |
| `au` / `in` / `ar` | audience / interest / area id |
| `at` | activity type id |
| `dk` + `fd` + `td` | date window: `dk=op` (open date) or `dk=cl` (close date), then `fd`/`td` as `dd/mm/yyyy` |
| `fields` | `basic` (default), `extended`, or `all` |

Ask for `fields=all` when you need the closing date reasoning, contact details,
supporting documents, audiences and interests. Ask for `basic` when you only need
title, status and dates — it is the cheaper response.

**Critical:** unsupported arguments are silently ignored. A misspelt filter does not
error — it returns HTTP 200 with an unfiltered result set. Always assert that the
result set actually matches the filter you asked for (e.g. every returned
`status == "open"` when you sent `st=open`) before acting on it.

There is **no pagination**. The whole result set comes back in one JSON array.

## Step 2 — read the fields you need

Each element of the array is an activity. Key fields:

- `id` — the activity slug
- `dept` — the workspace/department slug (needed for step 3)
- `title`, `status`, `startdate`, `enddate` (dates are `yyyy/mm/dd`)
- `overview` — HTML, not plain text; strip or render it, do not treat it as a string
- `participate_url` — direct link to the survey, skipping the overview page
- `supporting_documents[]` — `{url, title, size}`
- `audiences[]`, `interests[]`, `areas[]` — `{id, name}` terms you can feed back into
  `au` / `in` / `ar` on the next search

Two field names differ from the published reference: the docs say
`participation_url` and `resultsdate`, but the live 2.4 response emits
`participate_url` and `resultdate`. Read the observed names, and tolerate both.

## Step 3 — pull one activity in full (`json_consultation_details`)

```
GET https://consultations.caa.co.uk/api/2.4/json_consultation_details?dept={dept}&id={id}&fields=all
```

Both `dept` and `id` are **required** and together form the composite key. Take them
from the `dept` and `id` fields of a search result — never guess them, and never use
the human-readable department name.

The response has the same shape as one element of the search array.

## Errors

- **404** — "If dept or id are not specified or do not exist, a 404 status code is
  returned." That is the only documented error, and it has no JSON body: branch on
  the status code, do not try to parse an error object.
- There is no `application/problem+json`, no error code, and no request id, so a
  failure cannot be reported back to the CAA with a reference.
- A 404 on the version path itself means the version does not exist. Versions 2.0
  through 2.4 are served concurrently; 2.5 does not exist.

## Conventions to respect

- Read-only. There is no write surface, therefore no idempotency contract.
- No rate limits are published and no rate-limit headers are returned. The vendor
  guide explicitly permits caching results — cache them, and poll at a sane cadence
  (daily is plenty for a consultation calendar).
- Survey *contents* are not available through this API. Only activity metadata is.

## What this skill does NOT reach

This is the consultation-platform API deployed on a CAA domain. It carries no
aviation data. The UK aircraft register (G-INFO), Check an ATOL, airport and
punctuality statistics are **not** reachable here: G-INFO and Check an ATOL run on
undocumented POST-only backends that are origin-locked to `https://www.caa.co.uk`
and reCAPTCHA-gated, and the statistical series are CSV/PDF files behind opaque
`/Documents/Download/{siteId}/{guid}/{docId}` URLs with no index. Do not attempt to
call those backends as if they were a public API.
