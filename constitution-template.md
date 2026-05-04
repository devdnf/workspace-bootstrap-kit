# Project Constitution — {{PROJECT_NAME}}

> Read this document entirely before responding to any message.
> This is the single source of truth for this project.

---

## Project overview

**Project name:** {{PROJECT_NAME}}
**Type:** {{PROJECT_TYPE}}
**Purpose:** {{PROJECT_PURPOSE}}

---

## Repository structure

| Repository | Remote URL | Purpose |
|---|---|---|
| {{REPO_1_NAME}} | {{REPO_1_URL}} | {{REPO_1_PURPOSE}} |
| {{REPO_2_NAME}} | {{REPO_2_URL}} | {{REPO_2_PURPOSE}} |

---

## MCP tooling

This project uses four MCP servers configured in `.mcp.json`.

### Project-specific IDs (committed to .mcp.json)

| Tool | ID | Value |
|---|---|---|
| Apidog | Project ID | {{APIDOG_PROJECT_ID}} |
| Figma | File key | {{FIGMA_FILE_KEY}} |
| Trello | Board ID | {{TRELLO_BOARD_ID}} |
| GitHub | Repo name(s) | {{GITHUB_REPOS}} |

### Personal credentials (shell environment variables only — never committed)

| Variable | Purpose |
|---|---|
| APIDOG_ACCESS_TOKEN | Apidog API access |
| FIGMA_ACCESS_TOKEN | Figma design file access |
| GITHUB_TOKEN | GitHub repository operations |
| TRELLO_API_KEY | Trello board read/write |
| TRELLO_TOKEN | Trello board authorisation |

### MCP server names (as referenced in Claude Code)

| Server name | Purpose |
|---|---|
| "API Specification" | Read endpoint specs, retrieve shareable URLs |
| "figma" | Inspect design files, extract tokens, generate UI code |
| "github" | Repository operations, PRs, branches, commits |
| "trello" | Create and manage QA/task cards on the board |

---

## Spec-driven development

Every feature follows this loop. No step may be skipped.

1. `/speckit.specify` — define what to build and why
2. `/speckit.clarify` — close all open questions
3. `/speckit.plan` — technical implementation plan
4. `/speckit.tasks` — ordered task list with done conditions
5. **Apidog step** — create new endpoints in Apidog, retrieve shareable URLs
6. **Trello step** — create task cards in 📋 Backlog with Apidog/Figma links
7. `/speckit.implement` — execute tasks
8. **Trello** — developer moves cards to 🔨 Working On / 🔍 Testing

Implementation never begins until steps 1–6 are complete.

### Spec flow — Apidog step

For every new API endpoint in the spec:
- Create the endpoint in Apidog via the "API Specification" MCP.
- Include full request/response schemas matching the spec plan.
- Retrieve the shareable endpoint URL via MCP.
- Embed the URL in the corresponding Trello task card description.

Skip if the spec introduces no new API endpoints.

### Spec flow — Trello step

For every task in tasks.md:
- Check existing board cards first — no duplicates.
- Create card in 📋 Backlog.
- Apply labels: Backend / Mobile / Frontend / UI/UX / DevOps / Business.
- For Backend cards: include Apidog URL.
- For Mobile/Frontend cards: include Figma frame URL.

### Trello card lifecycle

📋 Backlog → 🔨 Working On → 🔍 Testing → ✅ Done

Cards created by speckit. Movement is manual by the developer.

---

## Trello board labels

| Label | Applies to |
|---|---|
| Backend | API, database, infrastructure, Celery tasks |
| Mobile | Flutter screens, BLoCs, widgets |
| Frontend | Web UI components and pages |
| UI/UX | Figma designs, design system work |
| DevOps | Docker, CI/CD, deployment, environment |
| Business | BRD, specs, stakeholder documentation |

---

## Architecture invariants

{{ARCHITECTURE_INVARIANTS}}

---

## Technology stack

{{TECHNOLOGY_STACK}}

---

## Simulation / environment flags

{{SIMULATION_FLAGS}}

---

## Testing requirements

{{TESTING_REQUIREMENTS}}

---

## Out of scope (v1)

{{OUT_OF_SCOPE}}
