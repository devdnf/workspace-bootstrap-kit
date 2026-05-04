# Master Setup Checklist

Work through this list top to bottom. Every item must be checked
before moving to the next. Estimated total time: 25–30 minutes.

---

## Phase 1 — speckit (5 minutes)

- [ ] Install specify-cli globally
      `uv tool install specify-cli --from git+https://github.com/github/spec-kit.git`
      Verify: `specify --version`

- [ ] Initialise speckit in the project root
      `cd your-project && specify init . --ai claude --ai-skills`
      Verify: `.specify/` directory created with `memory/` and `specs/` inside

- [ ] Run the constitution command
      `/speckit.constitution`
      Paste the filled-in `constitution-template.md` when prompted.
      Verify: `.specify/memory/constitution.md` exists and is non-empty

See [guides/01-speckit.md](./guides/01-speckit.md) for full detail.

---

## Phase 2 — Apidog MCP (5 minutes)

- [ ] Create or log into Apidog account at https://apidog.com
- [ ] Create a project for this codebase (or identify the existing one)
- [ ] Copy the Project ID from Project Settings → Basic Settings
- [ ] Generate an API Access Token from Account Settings → API Access Token
- [ ] Add APIDOG_ACCESS_TOKEN to your shell profile
- [ ] Add Apidog project ID to .mcp.json (see Phase 5)

See [guides/02-mcp-apidog.md](./guides/02-mcp-apidog.md) for full detail.

---

## Phase 3 — Figma MCP (5 minutes)

- [ ] Locate or create the Figma design file for this project
- [ ] Copy the Figma file key from the file URL
      URL format: figma.com/design/{FILE_KEY}/...
- [ ] Generate a Figma personal access token
      Figma → Account Settings → Personal access tokens → Generate
- [ ] Add FIGMA_ACCESS_TOKEN to your shell profile
- [ ] Add Figma file key to .mcp.json (see Phase 5)

See [guides/03-mcp-figma.md](./guides/03-mcp-figma.md) for full detail.

---

## Phase 4 — GitHub MCP (3 minutes)

- [ ] Generate a GitHub personal access token (classic)
      GitHub → Settings → Developer settings → Personal access tokens
      Scopes required: repo, read:org, read:user
- [ ] Add GITHUB_TOKEN to your shell profile
- [ ] Add GitHub repo name(s) to .mcp.json (see Phase 5)

See [guides/04-mcp-github.md](./guides/04-mcp-github.md) for full detail.

---

## Phase 5 — Trello MCP (3 minutes)

- [ ] Go to https://trello.com/power-ups/admin
- [ ] Create a Power-Up → Generate API Key → copy it
- [ ] Click "Token" on the same page → authorise → copy token
- [ ] Find the board ID from the board URL: trello.com/b/{BOARD_ID}
- [ ] Add TRELLO_API_KEY and TRELLO_TOKEN to your shell profile
- [ ] Add Trello board ID to .mcp.json (see Phase 5)

See [guides/05-mcp-trello.md](./guides/05-mcp-trello.md) for full detail.

---

## Phase 6 — Project IDs and .mcp.json (3 minutes)

- [ ] Copy .mcp.json.example to your project root as .mcp.json
- [ ] Fill in all project-specific IDs (Apidog, Figma, Trello, GitHub)
- [ ] Reload your shell: `source ~/.zshrc` (or ~/.bashrc)
- [ ] Restart Claude Code
- [ ] Verify Apidog MCP:
      "Use the Apidog MCP to count endpoints in this project"
- [ ] Verify Figma MCP:
      "Use the Figma MCP to list pages in the design file"
- [ ] Verify GitHub MCP:
      "Use the GitHub MCP to list open pull requests on this repo"
- [ ] Verify Trello MCP:
      "Use the Trello MCP to list all columns on the board"

See [guides/06-project-ids.md](./guides/06-project-ids.md) for full detail.

---

## Phase 7 — Update the constitution (2 minutes)

- [ ] Open .specify/memory/constitution.md
- [ ] Confirm the MCP tooling section is present (it is included
      in the constitution template — fill in the IDs)
- [ ] Commit the constitution:
      `git add .specify/memory/constitution.md && git commit -m "chore: project constitution"`

See [guides/07-spec-flow.md](./guides/07-spec-flow.md) for the full
spec loop including how to create Apidog endpoints and Trello tasks.

---

## Verification

All four MCPs working + speckit initialised = setup complete.
You are ready to start the spec-driven development loop.
