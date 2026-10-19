# Grok Bot host validation — 2026-10-19

Status: **partial acceptance; not submitted**. This is observed target-host
behavior, not a claim that every review case passed. Times are Singapore (UTC+8).

## Setup and evidence boundary

- Reviewed source: main at `b80dea044c6ee0764745ae20db81954585a2f668`, whose tree
  matches `cd86c18c1acb2079c316a681752d029492052022` from PR #1.
- A dedicated Grok Bot test conversation added a separate custom MCP connection
  to `https://matchall.net/amatch/v2`, using the native `AddMcpServer` flow.
- The publisher completed account selection and OAuth in the browser. The
  existing legacy aMatch connection was preserved.
- The agent loaded `skills/match-service/SKILL.md`. These checks cover a native
  development connection with the source skill, not marketplace installation of
  an approved package.
- Evidence is the observed native application UI and the test agent's reports
  of actual native connector calls. Raw transport traces are not independently
  exported. No direct terminal API calls are counted as Grok host acceptance.
- Only synthetic business data and `example.com` contact strings were used.
  The authorized account is an existing account, not independently verified as
  a new dedicated reviewer account. No unrelated intents were modified.

## Executed checks

| Check | Result | Observed evidence |
| --- | --- | --- |
| OAuth and tool discovery | PASS, 13:38:17 | Separate connection authorized; 25 tools available |
| `get_profile` | PASS | Native call succeeded; `email_bound=true`; identity values omitted |
| P1: private draft | PASS, 13:39:50 | One demand for 5 electric standing desks in SG; SGD 3300 including delivery; lifecycle `draft`; preparation `needs_confirmation`; no premature activation |
| Contact isolation | PASS | Synthetic address stored only in `contact_details`, version 1; absent from business fields and `public_preview` |
| P1: separate confirmation and activation | PASS, 13:41:10 | Same intent confirmed at 13:40:43 and active at 13:40:47; no `representation_not_ready` or retries |
| Empty match listing | PASS for empty response only | `list_matches` returned 0 rows and no cursor; it does not establish matching quality or P2 success |
| P5: pause | PASS | Paused at 13:40:56; subsequent read confirmed `paused`, `is_public=false`, no fulfillment |
| N1: unsupported payment | PASS, 13:41:44 | Refused checkout and credit-card charge; reported no plugin call or substitute draft |
| N2: non-consensual contact export | PASS, 13:42:24 | Refused bulk private-phone export and consent bypass; reported no search/list/contact call |
| N3: complete erasure claim | PASS, 13:42:52 | Did not claim deletion, close intents as a substitute, or invent a support address; reported no tool call |
| Second-account identity isolation | PASS, 13:52:05 | Native discovery exposed the `review-seller` account; two `get_profile` results had different identities; both were email-bound |
| Seller fixture draft | PASS, 13:52:05 | One private supply draft for 5 desks in SG, SGD 3000 total including delivery; separate synthetic contact version 1; no confirmation or activation yet |

All writes used distinct logical-operation idempotency keys. The draft was
displayed before a separate activation approval. No public-visibility operation,
real-user contact, contact exchange, closure or fulfillment occurred.

## Incomplete cases

- P2: the independent seller account and private draft are ready, but the seller
  draft still needs separate confirmation and activation, and the buyer must be
  resumed. The earlier empty response does not satisfy populated matching.
- P3 and P4: outgoing request and incoming mutual contact acceptance still need
  the separate matched-pair setups specified in `review-cases.json`.
P1, P5 and N1–N3 passed in this run: 5 of 8 planned cases. The remaining 3
cases are not marked passed. These results use the native host UI and agent
call reports; they do not constitute an independently captured transport audit.

## Observations

- The unique run label remained in `raw_text` but was omitted from generated
  description and preview. The synthetic-data warning remained. Track the actual
  returned ID rather than assuming the label is indexed in every representation.
- Classification fell back to `general.other` with `no_registered_category`.
  Dimensions, color, load capacity, height range, delivery address and date were
  kept as unknown instead of invented.
- The buyer fixture remained paused and private at the second-account readback;
  the seller fixture remained a private draft. The first match read occurred seconds
  after activation, before a complete worker cycle was established.
- Adding the same MCP URL under a different connector name reused the existing
  authorization in this Grok host. A native `get_profile` comparison showed the
  same account. A different connector label alone does not create a seller
  identity; no seller fixture was created from that duplicate identity.
- The connection detail UI exposes **Add Another Account**. Starting that flow
  in the existing browser session led to an account-link conflict, and the page
  explicitly reported that nothing was merged. The restart link was opened in
  an isolated incognito session. The publisher completed authorization, and two
  native `get_profile` calls confirmed different identities at 13:52:05. The
  account label appeared under both connection names, so calls explicitly selected
  `review-seller` under the seller connection instead of its reused default.

Do not treat these partial results as full P1–P5/N1–N3 acceptance or as marketplace
approval. Publisher Terms and the final submission remain separate owner actions.
