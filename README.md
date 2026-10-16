# Matchall for Grok Bot / Cursor

Public source preparation targeting Cursor Marketplace and Grok Bot.
**Not listed or approved. Grok Bot installation, OAuth and tool execution remain
unverified.** The repository name describes the intended host, not certification.

## Package and installation path

This repository uses the native Cursor plugin layout: `.cursor-plugin/plugin.json`,
root `mcp.json`, and `skills/match-service/SKILL.md`. It contains no ChatGPT-only
listing extensions. The remote MCP URL is inferred as HTTP by Cursor.

For Cursor editor development, clone this repository to an unused directory under
`~/.cursor/plugins/local/matchall-grok-bot`, reload the window, and inspect Customize.
Use the host's OAuth UI to connect Matchall. Team policy may restrict local plugins.
Do not overwrite an existing installation. This is an editor development path,
not proof that a Grok Bot cloud connector has been installed.

For Grok Bot, use **Connect apps** and its OAuth flow when this connector is made
available. The documented marketplace publishing route accepts a public GitHub
repository at https://cursor.com/marketplace/publish. Approval and availability in
Grok Bot must be confirmed separately; publication is not automatic from GitHub.

## What Matchall does

Draft needs and offers in natural language, activate them after approval, inspect
matches, and exchange private contact details only with mutual consent. Pause or
close needs when appropriate. Match scores do not guarantee transactions;
Matchall does not place orders or process payments.

## Authorization and data

The remote MCP endpoint is `https://awiki.info/amatch/v2`.
Use the host's OAuth connection UI. Discovery advertises PKCE S256, dynamic
client registration, and `intent:read` / `intent:write` scopes. Never put tokens,
passwords, verification codes, or private contact details in this repository.
Do not configure shared secret headers as an OAuth workaround.

Email binding is optional and helps with account recovery and notifications.
Private contact details are entered separately from business text and login
email. Without email, use manual checks or a host-supported scheduled task.
A schedule is not created merely by installing this plugin.
Business text is processed by the hosted Matchall service and its configured
model providers. This repository is the client plugin package, not the backend.

## Example prompts

- “Draft a need for five standing desks in Singapore. Show me before activating.”
- “Show current matches and explain which product fits have been verified.”
- “Ask this matched supplier to exchange contact details after showing me mine.”
- “Pause my standing-desk need; keep it for later.”

## Development

```sh
python3 -m venv .venv
. .venv/bin/activate
python -m pip install -r requirements-dev.txt
python scripts/validate.py
python scripts/package.py
```

The validator checks package structure, referenced assets, contact workflow,
review case inventory, and absence of embedded credentials. ZIP generation is
local only, uses an explicit file allowlist, and inspects the generated archive.
Neither script installs a plugin, invokes matching tools, deploys the service,
or submits a marketplace application. CI only validates and packages locally.
See [readiness](docs/READINESS.md) for the remaining marketplace work.

## Support and license

Use this repository's Issues for public package bugs. Never post credentials,
private contact details, or account recovery information in issues. A dedicated
private service-support channel and service policies are still being prepared.

[MIT](LICENSE) applies to this plugin package. It does not grant access to other
users' data, relicense the hosted backend, or imply permission to impersonate
AWiki, Matchall, OpenAI, Cursor, or xAI. The monochrome logo follows AWiki branding.

## Matchall naming transition

The plugin is now named `matchall-grok-bot` and the MCP connection label is
`matchall`. Its source repository is now
[AgentConnect/matchall-grok-bot](https://github.com/AgentConnect/matchall-grok-bot).
The existing OAuth/MCP URLs are unchanged; renaming the display/package does not
migrate accounts or change permissions.
This source update does not publish a release or update installed host copies.
