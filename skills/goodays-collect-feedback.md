---
name: Collect customer feedback into Goodays
description: Send a solicitation asking a customer for feedback, or submit a participation directly as a collection source, then read it back.
api: openapi/goodays-openapi-original.json
operations: [places_list, solicitations_create, solicitations_read, responses_collect]
generated: '2026-07-19'
method: generated
---

# Collect customer feedback into Goodays

Goodays (formerly Critizr) collects customer feedback either by **soliciting** a
customer (Goodays sends the email/SMS survey) or by **collecting** a participation
you already gathered as a first-party collection source.

## Auth
Every request goes to `https://api.goodays.co/v2/` with the access token in the
`Authorization` header, supplied verbatim (no `Bearer` prefix). Obtain the token
from your Goodays account manager.

## Steps
1. **Find the place.** Call `places_list` (`GET /places`) to get the `id` of the
   point of sale the feedback belongs to. Paginate with `cursor` / `page_size`.
2. **Solicit the customer** (Goodays sends the survey). Call `solicitations_create`
   (`POST /solicitations`) with the customer contact and the target place/survey.
   For batches use `solicitations_bulk` (`POST /solicitations/bulk`).
3. **Or collect directly** (you already have the feedback). Call `responses_collect`
   (`POST /responses/collect`) to push a participation in as a collection source.
4. **Confirm.** Read the solicitation back with `solicitations_read`
   (`GET /solicitations/{id}`) to check delivery/state.

## Conventions
- Pagination is cursor-based (`cursor`, `page_size`, `sort`) — see `conventions/goodays-conventions.yml`.
- No idempotency key is documented; avoid blind retries on `POST /solicitations`.
