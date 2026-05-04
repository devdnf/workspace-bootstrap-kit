# Guide 05 — Trello MCP Setup

The Trello MCP lets Claude Code create and manage cards, move cards
between lists, add labels, attach descriptions and checklists, and
read the full board state.

## Get your Trello API credentials

1. Go to https://trello.com/power-ups/admin.
2. Click **New** to create a Power-Up.
   Name: `Claude Code Integration`. Submit.
3. On the Power-Up page click **Generate a new API Key**.
   Copy the **API Key**.
4. On the same page click the **Token** link next to the key display.
   An authorisation page opens. Click **Allow**. Copy the **Token**.

## Find your board ID

The board ID is in the board URL:

```
https://trello.com/b/{BOARD_ID}/board-name
```

Example: for `trello.com/b/nT40m0sy/esim-platform-qa`
the board ID is `nT40m0sy`.

This ID is safe to commit in `.mcp.json`.

## Add credentials to your shell profile

Add to `~/.zshrc` or `~/.bashrc`:

```bash
export TRELLO_API_KEY="your_trello_api_key_here"
export TRELLO_TOKEN="your_trello_token_here"
```

Reload:

```bash
source ~/.zshrc
```

## Trello MCP configuration in .mcp.json

```json
"trello": {
  "command": "npx",
  "args": ["-y", "@delorenj/mcp-server-trello"],
  "env": {
    "TRELLO_API_KEY": "${TRELLO_API_KEY}",
    "TRELLO_TOKEN": "${TRELLO_TOKEN}",
    "TRELLO_BOARD_ID": "YOUR_BOARD_ID"
  }
}
```

The board ID is hardcoded in the args — it belongs to this project.

## Required board columns (lists)

Every project board must have these columns in this order:

| Column | Purpose |
|---|---|
| 📋 Backlog | All new tasks start here |
| 🔨 Working On | Task is actively being implemented |
| 🔍 Testing | Implementation complete, awaiting QA verification |
| ✅ Done | QA passed, task closed |

If these columns do not exist on the board, create them before
running any spec-driven task creation.

## Required labels

Create these labels on the board before creating any task cards:

| Label | Colour | Applies to |
|---|---|---|
| Backend | Green | Django API, Celery, database work |
| Mobile | Blue | Flutter app screens and BLoCs |
| Frontend | Sky | Web frontend (if applicable) |
| UI/UX | Pink | Design work, Figma updates |
| DevOps | Orange | Docker, CI/CD, infrastructure |
| Business | Yellow | Requirements, BRD, stakeholder tasks |

## Verify the MCP is working

After adding the board ID to `.mcp.json` and restarting Claude Code:

"Use the Trello MCP to list all columns on the board"

A successful response lists the column names from your board.
