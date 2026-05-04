# Workspace Bootstrap Kit

A step-by-step setup guide for spec-driven development projects
using Claude Code with speckit and the full MCP toolchain.

## What this kit sets up

| Tool | Purpose |
|---|---|
| spec-kit (specify-cli) | Spec-driven development loop |
| Apidog MCP | API documentation and shareable endpoint URLs |
| Figma MCP | Design file access and component inspection |
| GitHub MCP | Repository operations from within Claude Code |
| Trello MCP | QA task board management |

## Who this is for

- Developers starting a new project who want the full toolchain
  wired from day one.
- Developers joining an existing project who need to configure
  their local environment to match the team's setup.

## Quick start

1. Read [SETUP.md](./SETUP.md) — the master checklist.
2. Follow guides in the `guides/` directory in numbered order.
3. Copy `.mcp.json.example` to your project root as `.mcp.json`
   and fill in the project-specific IDs.
4. Copy `constitution-template.md` and fill in all `{{PLACEHOLDER}}`
   values to generate your project's constitution.
5. Copy `templates/CLAUDE.md.template` to your project root as
   `CLAUDE.md` and fill in all `{{PLACEHOLDER}}` values.

## Prerequisites

- Node.js 18 or later (`node --version` to check)
- Claude Code installed and running
- Accounts on: Apidog, Figma, GitHub, Trello
