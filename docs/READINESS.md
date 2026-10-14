# Marketplace readiness

Repository preparation date: 2026-10-14. This public repository is a preparation
artifact, not evidence of marketplace approval or a successful target-host test.
See [machine-readable status](readiness.json) and [review cases](review-cases.json).
The cases are designed scenarios, not passed tests. Do not seed them into live
user accounts or publish real contact information as fixtures.

## Remaining work

- Target-host OAuth, tool discovery and authenticated tool calls
- Five positive and three negative cases in isolated reviewer accounts
- Product website, support channel, privacy policy and service terms
- Confirmed publisher identity, availability countries and commerce declarations
- Reviewer access and a real demo recording
- Backend tool-annotation audit and any required corrections
- Verify exact Grok Bot DCR callback set against server configuration
- Confirm Cursor approval includes intended Grok Bot directory availability
- Complete publisher application and legal review when authorized

## Grok Bot OAuth compatibility

A Cursor support response reported three DCR redirect URIs: the exact
`cursor://anysphere.cursor-mcp/oauth/callback`,
`https://www.cursor.com/agents/mcp/oauth/callback`, and
`http://localhost:8787/callback`. This is a compatibility observation, not a
request to allow arbitrary redirects. Verify the current host request and exact
server allowlist before changing configuration. The current Gateway test covers
the HTTPS and localhost pair; that alone does not prove the full host flow.
Never broaden to wildcard callbacks or embed a service token to bypass OAuth.
[Support thread](https://forum.cursor.com/t/grok-bot-custom-mcp-oauth-fails-before-sign-in-redirect-uri-not-allowed/171877).

## Sources

- [Cursor plugin reference](https://cursor.com/docs/reference/plugins)
- [Grok Bot plugin connection](https://cursor.com/help/grok-bot/connect-plugins)
- [Cursor publisher terms](https://cursor.com/marketplace-publisher-terms)
- [OpenAI plugin submission](https://developers.openai.com/plugins/deploy/submission)
- [Agent Plugins standard](https://agent-plugins.org/)
