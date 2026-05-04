# Guide 07 — The Spec Flow with Apidog and Trello

This guide documents the full spec-driven development loop including
the Apidog and Trello steps that wrap every spec.

## The complete loop for every feature

```
/speckit.specify      Define the feature
/speckit.clarify      Close all open questions
/speckit.plan         Technical implementation plan
/speckit.tasks        Ordered task list
        ↓
[Apidog step]         Create new API endpoints in Apidog
[Trello step]         Create task cards in Backlog
        ↓
/speckit.implement    Execute tasks
        ↓
[Trello step]         Move cards to Working On as work begins
[Trello step]         Move cards to Testing when implementation done
```

---

## Apidog step — Create new API endpoints

Run this step after `/speckit.plan` and before `/speckit.implement`.

For every new API endpoint defined in the spec plan:

1. Use the Apidog MCP to create the endpoint in the Apidog project.
   Include:
   - HTTP method and path (e.g. POST /api/auth/change-password/)
   - Request body schema with all fields, types, and required flags
   - Response schemas for all status codes (200, 400, 401, 403, etc.)
   - Authentication: Bearer token (if JWT required)
   - Description from the spec

2. After creation, use the Apidog MCP to retrieve the shareable URL
   for each new endpoint. Store these URLs — they go into Trello cards.

3. If the endpoint already exists in Apidog (imported from openapi.yaml),
   retrieve its shareable URL only. Do not duplicate it.

Skip this step if the spec introduces no new API endpoints (e.g. a
pure UI spec or a refactoring spec with no contract changes).

---

## Trello step — Create task cards in Backlog

Run this step after the Apidog step.

### Card creation rules

1. Use the Trello MCP to read all existing cards on the board first.
   Do not create a card with an identical title to one that already exists.

2. Create one card per implementation task from the spec's task list.
   Group tasks into cards at a meaningful granularity — not one card
   per line of code, but one card per logical unit of work.

3. Every new card starts in the **📋 Backlog** list.

4. Every card must have at least one label from:
   Backend, Mobile, Frontend, UI/UX, DevOps, Business.
   A card may have multiple labels (e.g. Backend + Mobile for a
   full-stack feature).

### Card title format

```
[SPEC-XXX] Short description of the task
```

Example: `[SPEC-024] Change password endpoint with token refresh`

### Card description format

```markdown
## What
One sentence describing what this task delivers.

## Spec reference
Spec: {spec number and name}
Task: T{task number from tasks.md}

## API Endpoint (if Backend label)
[METHOD /api/path/](apidog-shareable-url)

## Design reference (if Mobile or Frontend label)
[Screen Name](figma-frame-url)

## Pre-conditions
- bullet list of what must be true before starting

## Implementation notes
- key decisions from the spec plan
- any gotchas or constraints

## Done condition
Exact criterion from tasks.md that marks this task complete.

## Simulation mode
Note which flags apply: EMAIL_SIMULATION / ESIM_ACCESS_SIMULATION /
FCM_SIMULATION — or "N/A" if no simulation flags relevant.
```

### Label assignment guide

| Work type | Labels to apply |
|---|---|
| Django model, view, serializer, URL | Backend |
| Flutter screen, BLoC, widget | Mobile |
| Web frontend component or page | Frontend |
| Figma design, design system update | UI/UX |
| Docker, CI/CD, environment, deployment | DevOps |
| BRD, spec, stakeholder document | Business |
| Full-stack feature (API + mobile screen) | Backend + Mobile |

### Trello card lifecycle

```
📋 Backlog     ← card created here by /speckit.implement prompt
      ↓
🔨 Working On  ← developer moves card here when starting the task
      ↓
🔍 Testing     ← developer moves card here when implementation is
                done and ready for QA verification
      ↓
✅ Done        ← QA moves card here after passing all test cases
```

The spec-driven prompt only creates cards (Backlog). Moving cards
is a manual action by the developer as they work.

---

## Full example prompt for a new spec with Apidog + Trello

Use this prompt structure when running `/speckit.implement` for any
spec that introduces new APIs:

```
/speckit.implement

Spec: {spec-number}-{spec-name}

Before executing any task:

Step A — Apidog:
  Read docs/openapi.yaml and the spec plan to identify any new API
  endpoints introduced by this spec that do not yet exist in Apidog.
  For each new endpoint: use the Apidog MCP to create it in the
  project with full request/response schemas.
  For all endpoints (new and existing) referenced in this spec:
  use the Apidog MCP to retrieve the shareable URL.

Step B — Trello:
  Use the Trello MCP to read all existing cards on the board.
  For each task in the spec's tasks.md that does not already have
  a matching card on the board: create a new card in 📋 Backlog
  using the card format from guides/07-spec-flow.md.
  Apply labels: {list the relevant labels for this spec}.
  For Backend cards: embed the Apidog URL from Step A.
  For Mobile or Frontend cards: embed the Figma frame URL for the
  relevant screen from the Figma file.

After Step A and Step B are complete, execute tasks T001 onward.
```
