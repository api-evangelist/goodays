---
name: Respond to customer reviews in Goodays
description: List incoming customer reviews for a place, read one, and reply, close, message, call back, or flag it as spam.
api: openapi/goodays-openapi-original.json
operations: [places_list, places_responses_list, responses_read, responses_reply, responses_close, responses_message, responses_call, responses_spam]
generated: '2026-07-19'
method: generated
---

# Respond to customer reviews in Goodays

A "response" in Goodays is a customer review/feedback participation. This skill
closes the loop: read reviews and take an action on each.

## Auth
`https://api.goodays.co/v2/` with the access token in the `Authorization` header
(verbatim, no `Bearer` prefix).

## Steps
1. **List reviews for a place.** Call `places_responses_list`
   (`GET /places/{place_pk}/responses`), or `responses_list` (`GET /responses`)
   across the account. Paginate with `cursor` / `page_size`.
2. **Read one.** Call `responses_read` (`GET /responses/{id}`).
3. **Take an action** on `{id}`:
   - `responses_reply` (`PUT /responses/{id}/reply`) — public reply to the customer.
   - `responses_message` (`PUT /responses/{id}/message`) — private message.
   - `responses_call` (`PUT /responses/{id}/call`) — log a call-back.
   - `responses_close` (`PUT /responses/{id}/close`) — close the conversation.
   - `responses_spam` (`PUT /responses/{id}/spam`) — flag as spam.

## Conventions
- Actions are `PUT` on the sub-resource of a specific response id.
- Pagination and auth follow `conventions/goodays-conventions.yml`.
