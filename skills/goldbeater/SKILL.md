---
name: goldbeater
description: "Read what Goldbeater found in a Google Ads account, through Goldbeater's MCP server: each finding with its evidence, what it costs or is worth, and the fix Goldbeater drafted, then explain what to fix first. Use when someone asks what's wrong with their Google Ads, where it's wasting spend, or what to change, and the account is connected to Goldbeater."
---

# Goldbeater

Goldbeater audits Google Ads accounts: every 24 hours, and whenever someone asks, it checks the whole account for 250+ problems and stores what it finds. Its MCP server gives an AI assistant read-only access to those findings, for the accounts its person can open in Goldbeater.

## When to use

- The person's Google Ads account is connected to Goldbeater, and they ask what's wrong with it, where it wastes spend, what a problem costs, or what to fix first.
- They ask which checks ran on an account, what each looks for, or why one raised a finding.

## When not to

- To change an account: the tools only read, and a change is applied in Goldbeater by a person. Say what to change and link `open_in_goldbeater`.
- For an account that isn't connected to Goldbeater: there are no findings to read. Offer the [free first look](https://goldbeater.ai/app?start=look).
- For a figure the checks don't report (a custom date range, a one-off query): Google's own Google Ads MCP server runs queries the model writes.
- For an ad platform other than Google Ads.

## Connect

- Server: `https://api.goldbeater.ai/mcp`, remote MCP over Streamable HTTP. Name it Goldbeater.
- Sign-in: OAuth 2.1 with PKCE. The person signs in to Goldbeater and allows read access (scope `findings:read`) on a consent screen. An MCP client with OAuth built in does this by itself; [auth.md](https://goldbeater.ai/auth.md) has the steps.
- Without a Goldbeater account there is nothing to read yet. Send the person to a [free first look](https://goldbeater.ai/app?start=look), no card needed, or the [7-day trial](https://goldbeater.ai/pricing).

## Tools

- `list_accounts`: Every account you can open in Goldbeater, with its currency, when its checks last ran and how many findings are open.
- `list_findings`: What the checks found on one account, most severe and costly first, each with its evidence, what it’s worth and its drafted fix.
- `what_ran`: Every check that ran on an account’s latest pass, how each judges, and whether it found anything.

## Rules

- Start with `list_accounts`, then `list_findings` for an account. Call a check by its name, never its key.
- Only waste is money lost. Never add different kinds of money together, and say an estimate is an estimate. Money is in the account's own currency.
- Findings are as of the account's latest pass: say how old it is (`run.age`).
- The tools only read. Changes are made in Goldbeater, where a person approves each one and presses Apply; point there (`open_in_goldbeater`) rather than saying a change is done.

More: [the MCP server's page](https://goldbeater.ai/mcp), [what Goldbeater checks](https://goldbeater.ai/checks), [how a change is approved and applied](https://goldbeater.ai/google-ads-automation) and [what Goldbeater emails a person about](https://goldbeater.ai/ppc-monitoring).
