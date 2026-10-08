# Goldbeater for AI agents

Goldbeater is Google Ads analysis software for people who run their own accounts. Every day it checks the whole account for 250+ problems, and each week an AI agent follows up on what it finds and shows every query it ran. Each finding comes with its evidence, and each change it drafts waits for a person to approve and apply it. Plans start at $249 a month, with a 7-day trial.

This repository holds what an AI agent needs to read Goldbeater's findings: a skill, and the address of Goldbeater's MCP server. The server is hosted by Goldbeater, and its code is not here.

## Install the skill

```sh
npx skills add pressroom-ai/goldbeater-skill
```

The skill is [`skills/goldbeater/SKILL.md`](skills/goldbeater/SKILL.md): when to use Goldbeater, how to connect, and the rules for reading a finding. The same file is served at https://goldbeater.ai/.well-known/agent-skills/goldbeater/SKILL.md.

## Connect the MCP server

- Address: `https://api.goldbeater.ai/mcp`, remote MCP over Streamable HTTP.
- Sign-in: OAuth 2.1. You sign in to Goldbeater and allow read access on a consent screen; a client with OAuth built in does the rest.
- In the official MCP Registry: `ai.goldbeater/goldbeater`.
- Steps for Claude, ChatGPT and Cursor: https://goldbeater.ai/mcp

The tools only read. A change to an account is made in Goldbeater, where a person approves it and presses Apply.

| Tool | What it gives back |
|---|---|
| `list_accounts` | Every account you can open in Goldbeater, with its currency, when its checks last ran and how many findings are open. |
| `list_findings` | What the checks found on one account, most severe and costly first, each with its evidence, what it’s worth and its drafted fix. |
| `what_ran` | Every check that ran on an account’s latest pass, how each judges, and whether it found anything. |

## What is in here

- `skills/goldbeater/SKILL.md`: the skill.
- `plugin.json` and `mcp.json`: the same skill and server as an [Agent Plugins](https://agent-plugins.org) package.

These files are written from goldbeater.ai's own content, so a change is made there and a pull request here isn't merged. Questions go to support@goldbeater.ai.

Goldbeater is built and run by PressRoom, Inc.
