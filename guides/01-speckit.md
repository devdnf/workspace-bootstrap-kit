# Guide 01 — speckit Setup

spec-kit is a specification-driven development toolkit that enforces
the loop: specify → clarify → plan → tasks → implement for every
feature. Claude Code reads slash commands (`/speckit.constitution`,
`/speckit.specify`, etc.) and produces spec artefacts under `.specify/`.

## Installation

spec-kit is installed globally via uv (the fast Python package manager).
If you do not have uv installed, install it first:

```bash
curl -LsSf https://astral.sh/uv/install.sh | sh
```

Install specify-cli:

```bash
uv tool install specify-cli --from git+https://github.com/github/spec-kit.git
```

Verify:

```bash
specify --version
```

## Initialise in your project

Run this from the project root (the directory where Claude Code
will operate — the workspace root, not a sub-directory):

```bash
specify init . --ai claude --ai-skills
```

This creates:

```
.specify/
├── memory/
│   └── constitution.md    ← written by /speckit.constitution
├── specs/                 ← one folder per feature spec
└── templates/             ← speckit prompt templates
```

## Run the constitution

In Claude Code, run:

```
/speckit.constitution
```

Paste the filled-in `constitution-template.md` from this kit.
The constitution is the single source of truth for all architectural
decisions, conventions, and tooling rules for the project.

## The spec-driven loop (every feature)

```
/speckit.specify   → define what to build and why
/speckit.clarify   → close all open questions before planning
/speckit.plan      → technical implementation plan
/speckit.tasks     → ordered task list with done conditions
/speckit.implement → execute all tasks
```

Never skip to implement without a spec and plan in place.

## Slash commands reference

| Command | Purpose |
|---|---|
| `/speckit.constitution` | Write or update the project constitution |
| `/speckit.specify` | Define a new feature (what + why) |
| `/speckit.clarify` | Answer coverage questions before planning |
| `/speckit.plan` | Create technical implementation plan |
| `/speckit.tasks` | Break plan into ordered dependency-aware tasks |
| `/speckit.implement` | Execute all tasks |
| `/speckit.analyze` | Cross-artifact consistency check |
