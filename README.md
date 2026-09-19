# Zoho Marketing Automation MCP server — through HeyMetra

> **Unofficial.** This is not Zoho Marketing Automation's own MCP server and this repository is not affiliated with, endorsed by or supported by Zoho Marketing Automation. It documents how [HeyMetra](https://heymetra.com/), a remote MCP server built by Zeisoft, reads Zoho Marketing Automation.

**What each email campaign sent, delivered and drew back — not open yet.**

[![MCP Registry](https://img.shields.io/badge/MCP_Registry-com.heymetra%2Fheymetra-1f6feb)](https://registry.modelcontextprotocol.io/v0/servers/com.heymetra%2Fheymetra/versions)
[![Transport](https://img.shields.io/badge/transport-Streamable_HTTP-444)](https://modelcontextprotocol.io/)
[![Auth](https://img.shields.io/badge/auth-OAuth_2.1-444)](https://heymetra.com/security/)
[![Connector page](https://img.shields.io/badge/heymetra.com-zoho-marketing-automation-1f6feb)](https://heymetra.com/connectors/zoho-marketing-automation/)

---

## What Zoho Marketing Automation is

Zoho Marketing Automation is the email marketing side of Zoho: the lists, the campaigns and what each send did.

## What HeyMetra reads from Zoho Marketing Automation

Not open yet: this is a third Zoho sign-in, separate from the CRM and from SalesIQ, and it has not been proven end to end. When it opens, your MCP client gets two tools — one that lists the recent campaigns with the key each is addressed by, and one that returns what a single campaign did: emails sent and delivered, opens, unique clicks, bounces, unsubscribes and spam complaints. A figure Zoho did not state comes back as unknown rather than as zero. Who received or opened a campaign is not available and is not asked for: this connection carries one permission, to read campaign results, and nothing that reaches a mailing list. Read-only: no tool creates, edits or sends a campaign.

## What you can ask

Once connected, in your own assistant, in plain language:

> Which campaigns have we sent recently?

> How did the September newsletter do — how many opened it, how many clicked?

> How many people unsubscribed from our last send?

## Permissions

You switch these on per connection, and a permission you leave off is a tool your assistant never sees.

| Permission | What it covers | Changes anything? |
|---|---|---|
| **Campaigns** | Read which campaigns went out and what each one did. Recipients are never read. | No, read only |

<details>
<summary>What each permission lets an assistant do, in full</summary>

- Reads one campaign's sends, deliveries, opens, unique clicks, bounces, unsubscribes and spam complaints. Who received or opened it is not available.
- Lists your most recent campaigns with each one's name and status, and the key the performance report needs. It reads no recipient list.
</details>

## What it can change

- Zoho Marketing Automation is a read-only source — HeyMetra reads it to answer questions and never changes the account.

## Connect Zoho Marketing Automation

1. When Marketing Automation opens, choose it on the Connections screen in HeyMetra — separately from Zoho CRM and SalesIQ.
2. Sign in on Zoho's own screen with an account that can read your campaigns. Your password stays with Zoho.
3. Review what Zoho shows: one permission, to read campaign results. Nothing that can create or send a campaign, and nothing that reaches your mailing lists.
4. Add HeyMetra to your MCP client — Claude, ChatGPT, Cursor or Codex — with the details HeyMetra gives you; the campaign tools appear there.

## Then add HeyMetra to your assistant

Add HeyMetra once and it is there in every conversation. The address is the same everywhere:

```
https://mcp.heymetra.com/mcp
```

<details>
<summary><b>Claude</b> — Settings → Customize → Connectors → Add custom connector</summary>

Paste the address above into Settings → Customize → Connectors → Add custom connector.

_On Team and Enterprise plans only an owner can add it, under Organization settings._

Full walkthrough: [heymetra.com/mcp/claude/](https://heymetra.com/mcp/claude/)
</details>

<details>
<summary><b>ChatGPT</b> — Settings → Security and login → Developer mode, then chatgpt.com/plugins</summary>

Paste the address above into Settings → Security and login → Developer mode, then chatgpt.com/plugins.

_The endpoint has to include its /mcp path here._

Full walkthrough: [heymetra.com/mcp/chatgpt/](https://heymetra.com/mcp/chatgpt/)
</details>

<details>
<summary><b>Grok</b> — grok.com/connectors → New Connector → Custom</summary>

Paste the address above into grok.com/connectors → New Connector → Custom.

_XAI calls this “bring your own MCP”._

Full walkthrough: [heymetra.com/mcp/grok/](https://heymetra.com/mcp/grok/)
</details>

<details>
<summary><b>Perplexity</b> — Settings → Connectors → Custom connector → Remote</summary>

Paste the address above into Settings → Connectors → Custom connector → Remote.

_Perplexity documents it as a Pro, Max and Enterprise feature._

Full walkthrough: [heymetra.com/mcp/perplexity/](https://heymetra.com/mcp/perplexity/)
</details>

<details>
<summary><b>Claude Code</b> — claude mcp add --transport http</summary>

```bash
claude mcp add --transport http heymetra https://mcp.heymetra.com/mcp
```

_Or a .mcp.json in the project root; /mcp inside a session shows what connected._

Full walkthrough: [heymetra.com/mcp/claude-code/](https://heymetra.com/mcp/claude-code/)
</details>

<details>
<summary><b>Codex</b> — ~/.codex/config.toml</summary>

```toml
[mcp_servers.heymetra]
url = "https://mcp.heymetra.com/mcp"
```

_Under an [mcp_servers.<name>] section, then codex mcp login._

Full walkthrough: [heymetra.com/mcp/codex/](https://heymetra.com/mcp/codex/)
</details>

<details>
<summary><b>Cursor</b> — ~/.cursor/mcp.json, or .cursor/mcp.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "url": "https://mcp.heymetra.com/mcp" }
  }
}
```

_Leave the static OAuth fields empty — they exist for servers that cannot register themselves._

Full walkthrough: [heymetra.com/mcp/cursor/](https://heymetra.com/mcp/cursor/)
</details>

<details>
<summary><b>Antigravity</b> — ~/.gemini/config/mcp_config.json, or .agents/mcp_config.json in a project</summary>

```json
{
  "mcpServers": {
    "heymetra": { "serverUrl": "https://mcp.heymetra.com/mcp" }
  }
}
```

_The key is serverUrl, not url — the one every other JSON client spells differently._

Full walkthrough: [heymetra.com/mcp/antigravity/](https://heymetra.com/mcp/antigravity/)
</details>

## Everything else HeyMetra reads

One connection answers across accounts — which is the point, because spend lives in one place and revenue in another:

**Ads** — [Google Ads](https://heymetra.com/connectors/google-ads/) · [Meta](https://heymetra.com/connectors/meta-ads/)

**Analytics** — [Google Analytics 4](https://heymetra.com/connectors/google-analytics-4/) · [Google Search Console](https://github.com/zeisoft/google-search-console-mcp)

**Ecommerce** — [Shopify](https://heymetra.com/connectors/shopify/) · [Trendyol](https://github.com/zeisoft/trendyol-mcp) · [WooCommerce](https://github.com/zeisoft/woocommerce-mcp)

**Revenue & CRM** — [Stripe](https://heymetra.com/connectors/stripe/) · [HubSpot](https://heymetra.com/connectors/hubspot/) · [Zoho CRM](https://github.com/zeisoft/zoho-crm-mcp) · [Zoho SalesIQ](https://github.com/zeisoft/zoho-salesiq-mcp) · **Zoho Marketing Automation**

**Mobile** — [AppsFlyer](https://github.com/zeisoft/appsflyer-mcp) · [RevenueCat](https://heymetra.com/connectors/revenuecat/) · [Adapty](https://github.com/zeisoft/adapty-mcp) · [App Store Connect](https://github.com/zeisoft/app-store-connect-mcp)

**Channels** — [Slack](https://github.com/zeisoft/slack-mcp) · [Telegram](https://github.com/zeisoft/telegram-mcp)

The full catalogue, with what each one can do today, is at [heymetra.com/connectors/](https://heymetra.com/connectors/).

## Links

- [Zoho Marketing Automation connector page](https://heymetra.com/connectors/zoho-marketing-automation/) — the source this page is generated from
- [HeyMetra](https://heymetra.com/) — what the product is
- [Setup per assistant](https://heymetra.com/mcp/) — eight clients, step by step
- [Security and limits](https://heymetra.com/security/)
- [Pricing](https://heymetra.com/pricing/) — paid, no free plan and no trial
- [HeyMetra's own repository](https://github.com/zeisoft/heymetra-mcp)

---

<sub>This README is generated from HeyMetra's live connector catalogue and refreshed daily; it is committed only when something in it actually changed. Corrections are welcome as issues. Built by <a href="https://zeisoft.com">Zeisoft</a>.</sub>
