# Vervoe (vervoe)

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

Vervoe is an AI-powered skills assessment and skills-based hiring platform. Employers build their own assessment content or select from a public Assessment Library — assessments can include video, spreadsheets, presentations, and code challenges that simulate real work — then invite candidates and let Vervoe's AI grade and rank them by predicted on-the-job performance in "Talent Trials".

Vervoe offers a **partner/integration API**, documented on Stoplight, that lets an external system (typically an ATS or internal hiring dashboard) list an employer's assessments, invite candidates to complete an assessment, retrieve candidate assessment reports and scores, and receive real-time report notifications through a signed webhook. The Introduction states that *"All Vervoe APIs are based on REST architecture and are accessed via HTTPS at specific URLs."*

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/vervoe/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/vervoe/refs/heads/main/apis.yml)

## Access model — important

The API is **partner/gated**. Vervoe's public documentation describes the API and provides worked Example Scenarios, but it does **not** publish concrete REST endpoint paths, an OpenAPI definition, or an interactive reference. Access (credentials) is provisioned by Vervoe — the documentation directs partners to contact `sales+api@vervoe.com` to set up access, and the listed product contact is Nicole Bowes (Head of Product).

Because exact endpoint paths are not published, each API in this entry is marked with `endpointsModeled: true`. The logical APIs below are modeled honestly from Vervoe's own documented Example Scenarios and webhook reference — **no endpoint URLs have been fabricated**. The confirmed REST base host is `https://api.vervoe.com` (observed in the documented webhook example payload).

## Tags

- Hiring
- Recruitment
- Skills Assessment
- Talent
- HR Tech
- AI Grading
- ATS Integration

## Timestamps

- **Created:** 2026-07-10
- **Modified:** 2026-07-10

## APIs (modeled from documented scenarios)

### Vervoe Assessments API

Retrieve the assessments available to an employer — both authored content and items selected from the public Assessment Library — so an external system can display and organize them. Per documented **Example Scenario 1**, an integration calls the API to *"get list of assessments"*.

- **Documentation:** [Introduction](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjQ4ODIx-introduction)
- **API Reference:** [Example Scenarios](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjExMzY5ODk-example-scenarios)
- **Base URL:** `https://api.vervoe.com`
- **Endpoints modeled:** yes (exact paths not published)

### Vervoe Candidates API

Invite a candidate (email, first name, last name) to complete a specific assessment and monitor their progress. Per documented **Example Scenario 2**, the integration issues a *"POST Invite candidate to complete assessment"* call and receives back a candidate-specific URL to access the assessment, which the employer can email or embed in a button.

- **Documentation:** [Introduction](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjQ4ODIx-introduction)
- **API Reference:** [Example Scenarios](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjExMzY5ODk-example-scenarios)
- **Base URL:** `https://api.vervoe.com`
- **Endpoints modeled:** yes (exact paths not published)

### Vervoe Candidate Reports API

Retrieve a candidate's assessment results and scores so an external system can load and display them. Per documented **Example Scenario 3**, the integration issues a *"GET Get candidate assessment report"* call and Vervoe returns the result details, including AI and manual scores.

- **Documentation:** [Introduction](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjQ4ODIx-introduction)
- **API Reference:** [Example Scenarios](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjExMzY5ODk-example-scenarios)
- **Base URL:** `https://api.vervoe.com`
- **Endpoints modeled:** yes (exact paths not published)

### Vervoe Report Notification Webhook

An employer can configure a reporting webhook to which Vervoe sends an Assessment Report. Fourteen documented events fire updates (candidate started, candidate completed, first AI grade, AI score updated, first manual team score, manual score updated, hired, unhired, rejected, un-rejected, expired, screening in progress, failed screening, passed screening). Payloads carry `candidateAssessmentUuid`, `status`, timestamps, and a `score` object (`type`, `score`, `scoreByFormat`). Vervoe signs each delivery with an HMAC SHA-256 signature in a `Vervoe-Signature` header (`t` timestamp and `hash`); consumers must return HTTP 200 or Vervoe retries. This is a **server-to-endpoint HTTP callback, not a WebSocket**.

- **Documentation:** [Report Notification WebHook](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjExMzY5ODc-report-notification-web-hook)
- **Base URL:** `https://api.vervoe.com`

## Errors

Vervoe uses standard HTTP response codes: **200** OK, **400** Bad Request (malformed/missing parameters), **403** Forbidden (insufficient permissions), **404** Not Found, and **500** Server Error.

## Common Properties

- [LinkedIn](https://www.linkedin.com/company/vervoe)
- [Website](https://vervoe.com)
- [Documentation](https://vervoe.stoplight.io/docs/api-docs/ZG9jOjQ4ODIx-introduction)
- [API Landing Page](https://vervoe.com/api/)
- [Plans](plans/vervoe-plans-pricing.yml)
- [Rate Limits](rate-limits/vervoe-rate-limits.yml)
- [Fin Ops](finops/vervoe-finops.yml)
- [Blog](https://vervoe.com/blog/)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
