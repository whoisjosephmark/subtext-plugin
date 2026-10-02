# Subtext for Claude

Subtext is a personal context graph — the people, organisations, projects, tools and
topics that make up one person's working life, kept current by them and by Claude.
This plugin connects Claude to it.

Installing gives you two things at once:

- **The Subtext MCP connection** (`https://mcp.subtext.wiki/mcp`), which is how Claude
  reads and writes your graph: briefs, search, page compilation, notes and edits.
- **The Subtext skill**, which is how Claude knows what to do with that connection —
  pull your context before it asks or assumes, and write things down as they come up
  rather than only when told to.

Without the skill, the tools are there but Claude uses them like any other API. With
it, Claude works from your context by default.

## Install

```
/plugin install subtext-wiki
```

Then connect your account when Claude prompts for authorisation. You'll need a Subtext
account — sign up at [subtext.wiki](https://subtext.wiki/).

## What it connects to, and what it sends

This plugin ships two files and nothing else: a skill and a single MCP server entry.
It has no hooks, no commands, no agents, no scripts and no bundled executables, so it
runs no code of its own on your machine and installs no packages.

The one network destination is the Subtext MCP server:

| | |
|---|---|
| Endpoint | `https://mcp.subtext.wiki/mcp` |
| Transport | Streamable HTTP |
| Authorisation | OAuth 2.1, discovered from `https://mcp.subtext.wiki/.well-known/oauth-protected-resource/mcp`. Claude prompts you to sign in; no token is stored in this repository |
| Operator | Josephmark, who also operates Subtext itself |

Nothing is sent anywhere else. Claude sends a request to that endpoint only when it
calls one of the Subtext tools, and what it sends is the arguments of that call —
a search query, a page slug, or the prose you asked it to record. Reads
(`brief`, `search`, `scope`, `compile`, `get_page`, `traverse`, `graph_snapshot`)
return content from your own graph. Writes (`edit_page_body`, `rename_page`,
`link_pages`) change pages in your graph, and the skill directs Claude to use them on
its own initiative when you tell it something worth keeping — see
[Data and privacy](https://subtext.wiki/docs/data-and-privacy.html) for what is
stored, where, and for how long. Access is scoped by the key you authorise with, and
you can pause or revoke it at any time from the Connections page in Subtext.

## Documentation

- [Connecting Claude](https://subtext.wiki/docs/connect/claude.html)
- [Tools reference](https://subtext.wiki/docs/tools.html)
- [Data and privacy](https://subtext.wiki/docs/data-and-privacy.html)
- [Troubleshooting](https://subtext.wiki/docs/troubleshooting.html)

## Support

[hello@josephmark.com.au](mailto:hello@josephmark.com.au) ·
[Terms](https://subtext.wiki/terms.html) ·
[Privacy](https://subtext.wiki/privacy.html)

## About this repository

This is a packaging repository. `skills/subtext/SKILL.md` is generated: it is kept in
step with the instructions the Subtext MCP server ships, so edits belong upstream and
anything changed here is overwritten on the next release.

Licensed under the [MIT License](LICENSE).
