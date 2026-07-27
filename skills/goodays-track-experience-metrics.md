---
name: Track customer-experience metrics in Goodays
description: Pull NPS, satisfaction, relationship, Google score, dissatisfaction, remarks, and retained-customers statistics for the account or a survey.
api: openapi/goodays-openapi-original.json
operations: [stats_nps_list, stats_satisfaction_list, stats_relationship_list, stats_google_score_list, stats_dissatisfaction_list, stats_remarks_list, stats_retained_customers_list, stats_surveys_read]
generated: '2026-07-19'
method: generated
---

# Track customer-experience metrics in Goodays

Goodays exposes aggregate CX metrics under `/stats/*`.

## Auth
`https://api.goodays.co/v2/` with the access token in the `Authorization` header
(verbatim, no `Bearer` prefix).

## Steps
1. **Net Promoter Score** — `stats_nps_list` (`GET /stats/nps`).
2. **Satisfaction (CSAT)** — `stats_satisfaction_list` (`GET /stats/satisfaction`).
3. **Relationship score** — `stats_relationship_list` (`GET /stats/relationship`).
4. **Google score** — `stats_google_score_list` (`GET /stats/google_score`).
5. **Dissatisfaction** — `stats_dissatisfaction_list` (`GET /stats/dissatisfaction`).
6. **Remarks** — `stats_remarks_list` (`GET /stats/remarks`).
7. **Retained customers** — `stats_retained_customers_list` (`GET /stats/retained_customers`).
8. **Per-survey stats** — `stats_surveys_read` (`GET /stats/surveys/{id}`).

## Conventions
- All are `GET`; scope/filter with query parameters and paginate where supported.
- Auth and pagination follow `conventions/goodays-conventions.yml`.
