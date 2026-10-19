# Grok Bot submission readiness

Checked 2026-10-17. **Preparation only; not submitted, listed or approved.**
Use [the form draft](grok-submission.json), [submission guide](GROK-SUBMISSION.md),
[status](readiness.json) and [review cases](review-cases.json).

## Confirmed

- Public repository: https://github.com/AgentConnect/matchall-grok-bot.
- Native Cursor plugin structure with a skill, MCP configuration and MIT license.
- Current product homepage: https://matchall.net.
- Current dedicated MCP endpoint: https://matchall.net/amatch/v2.
- Public OAuth metadata identifies that exact resource and intent:read / intent:write.
  The advertised issuer's discovery endpoint returns PKCE S256 and dynamic
  registration metadata. Anonymous initialize/tools/list return 401.
- Existing 512 × 512 white-backed PNG logo is publicly readable and matches the
  local asset. No new logo, release or hosted policy was published.
- The official Grok form accepts a public repository or MCP URL, with separate
  options for Grok Bot, Cursor and Grok (coming soon).

## Required before submitting this preparation

1. Supply publisher first/last name, work email, organization name and lowercase
   organization handle. Do not infer a legal publisher from GitHub.
2. Finish Grok Bot installation, authorization and application tests for the
   current Matchall endpoint. The observed legacy aMatch connection uses awiki.info,
   needs authentication and reports zero tools. It is a separate instance.
3. Run the prepared cases with private synthetic fixtures in dedicated accounts.
   Keep the local-and-in-app testing declaration unchecked until supported.
4. Reconcile the reviewed source with the repository default branch: PR #1 carries
   the Matchall changes while main still contains the old aMatch package.
5. At an authorized submission step, the publisher reviews and accepts the
   Publisher Terms. Preparing code/materials does not submit the form.

## Additional preparation, not verified form fields

The inspected form does not ask for a ZIP, country list, commerce declaration,
demo URL or four separate listing URLs. Do not treat OpenAI portal metadata,
test-case counts or reviewer email addresses as Grok requirements. Keep review
cases, demo plans and access instructions for follow-up. A real recording,
reviewer access, private support and service policies remain unverified. Unknown
publisher, data-retention, deletion and commerce facts must not be invented.

## OAuth verification boundary

Discovery does not test client registration, actual Grok callback URIs, consent,
code exchange, refresh or tools. Check the current host's exact redirect request
and server allowlist if authorization fails; never introduce wildcard callbacks
or shared tokens. The stable issuer is https://www.amatch.me/oauth/match, while
public authorization/token/registration endpoints are on matchall.net. Existing
awiki.info accounts and connections are not silently migrated.

## Sources

- [Grok submission form](https://x.ai/bot/marketplace/submit-a-plugin)
- [Grok app connections](https://docs.x.ai/grok-bot/computer-and-apps#connect-an-app)
- [Cursor plugin format](https://cursor.com/docs/reference/plugins)
- [Publisher Terms linked by the form](https://cursor.com/marketplace-publisher-terms)
- [Matchall homepage](https://matchall.net)
