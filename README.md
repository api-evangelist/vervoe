# Vervoe (vervoe)

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
