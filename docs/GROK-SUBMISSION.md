# Matchall · Grok Bot submission preparation

Date: 2026-10-19. **Partial host acceptance; not submitted.**
Source version stays 0.1.2; this is an unpublished preparation.

## Copy-ready form values

Use https://x.ai/bot/marketplace/submit-a-plugin. Exact field values are in
[grok-submission.json](grok-submission.json).

| Field | Prepared value |
| --- | --- |
| First Name / Last Name | Supplied by the publisher in the form; not reproduced here |
| Work Email | Supplied by the publisher in the form; not reproduced here |
| Organization Name / Handle | Supplied by the publisher in the form |
| Website URL | https://matchall.net |
| Logotype URL | https://raw.githubusercontent.com/AgentConnect/matchall-grok-bot/62128fadedbce63aaa0b45184e3d889d28c3bed3/assets/logo.png |
| Where to be listed | Grok Bot |
| MCP Server URL or Public GitHub Repository | https://github.com/AgentConnect/matchall-grok-bot |

The repository includes the consent skill as well as MCP configuration. PR #1
merged into main on 2026-10-19 at `b80dea044c6ee0764745ae20db81954585a2f668`;
its tree matches reviewed source `cd86c18c1acb2079c316a681752d029492052022`.
The direct MCP endpoint is https://matchall.net/amatch/v2 if the reviewer asks.

**Brief Description**

> Matchall helps users draft needs and offers, review matching opportunities, and
> exchange private contact details only after both sides agree. Review each draft
> before activating matching. Intents stay private unless the user separately
> approves public visibility. Pause matching when plans change. Matchall does not
> place orders or process payments.

**Testing Instructions**

Use the reviewed source revision and configure the matchall MCP server at
https://matchall.net/amatch/v2 through Grok Bot's supported development connector
flow. Complete OAuth in the host UI with a dedicated test account. Discover tools
and call get_profile first. Do not provide passwords, codes or tokens in chat.
Run [five positive and three negative cases](review-cases.json):

1. Save and inspect a synthetic standing-desk draft with separate private contact
   details. In a separate turn, approve confirmation and activation for matching.
   Verify the same intent stays private and off the public feed.
2. With a compatible offer in a separate demo seller account, inspect actual
   matches and product-fit status without disclosing contacts.
3. Review the current own contact version and explicitly request exchange for
   that particular demo match. Pending requests must withhold counterpart contacts.
4. From the receiving account, review the exact request and explicitly accept it.
   Verify contacts are visible only after both parties consent.
5. Pause the buyer intent and verify the returned lifecycle; do not close or mark
   fulfilled. Decline payment, non-consensual contact export and unsupported
   complete-account-erasure requests without fabricating successful actions.

Record actual tools, arguments, results and pass/fail/blocked status. See
[the dated host report](host-validation-2026-10-19.md) for executed checks and
remaining cases. A validator or anonymous HTTP probe does not satisfy the form's
application-testing declaration. Exact setup details are in the cases.

## Development connection prompt

Use this only when choosing to configure and authorize a development connection:

> Help me connect Matchall for Grok Bot testing at
> https://matchall.net/amatch/v2 using your supported custom MCP or plugin flow.
> Source: https://github.com/AgentConnect/matchall-grok-bot. Use the reviewed
> Matchall source revision, not an older aMatch default-branch snapshot. Load its
> skills/match-service/SKILL.md. Keep existing awiki.info connections and accounts
> unchanged. Use OAuth through the host UI and let me complete login/consent.
> Never ask for passwords, verification codes or tokens in chat. After connecting,
> discover tools and call only get_profile. Report installation, authorization and
> that call separately. Do not create an intent, request contact exchange, create
> a schedule, or claim marketplace availability during this connectivity check.

## Reviewer and recording plan

Prepare dedicated buyer and seller accounts and unique REVIEW run labels. Buyer:
five electric standing desks in Singapore, total SGD 3300 including delivery;
synthetic contact review-buyer@example.com. Seller: five electric standing desks
in Singapore, SGD 3000 including delivery; synthetic contact review-seller@example.com.
Use separate matched pairs for the outgoing-request and incoming-acceptance cases
as specified in their setup. Keep fixtures private; use only actual returned IDs.
The example.com contacts are synthetic strings, not login or notification inboxes.
Choose an actual controlled sign-in method for reviewers; never put credentials
or access-bearing URLs in this package or a public form description.

In the tested Grok host, adding the same MCP URL under another connection name
reused its existing authorization. Use **Add Another Account** in connection
details and an isolated browser session for the second reviewer. After signing
in, compare both native `get_profile` identities before creating fixtures; if
they are the same, stop. Never work around an account-link conflict by merging
accounts or changing backend identity records.

Rehearse in Grok Bot before recording. Then capture about 2–3 minutes: connected
tools, draft and separate approval, real match, consent-gated exchange, pause and
one unsupported-payment example. Omit login codes, tokens and unrelated account
data. Play back the recording to check legibility and real results. Host it at a
reviewer-accessible destination chosen by the publisher. This is a script, not a
recording. Recording awaits a working development connection and dedicated review
setup. No demo-URL field is present on the inspected form; retain it for follow-up.

## Publication boundary

PR #1 is merged and the publisher has supplied the form's identity fields. A
separate Matchall development connection was added through Grok Bot's native
custom MCP flow on 2026-10-19. OAuth, discovery of 25 tools, native `get_profile`,
private draft creation, separate confirmation and activation, empty-match listing
and pause passed. A separately authorized seller identity was verified and a
private supply draft created. Populated matching and bilateral contact exchange
remain unexecuted; the buyer is paused and the seller remains a draft. The
existing legacy connector was preserved.

No form has been submitted, Publisher Terms accepted, or package release created.
Complete target-host acceptance before attesting to in-app testing. Submission
for review and later publication are separate.
