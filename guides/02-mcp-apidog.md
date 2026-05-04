# Guide 02 — Apidog MCP Setup

Apidog is the API documentation and testing platform. The Apidog MCP
lets Claude Code read endpoint definitions, retrieve shareable endpoint
URLs, and create or update API specifications directly from the editor.

## Create an Apidog account and project

1. Go to https://apidog.com and sign up or log in.
2. Click **New Project** and name it after your project.
3. In the left sidebar go to **Project Settings → Basic Settings**.
4. Copy the **Project ID** (a number, e.g. `648291`).
   This ID is safe to commit in `.mcp.json` — it is not a secret.

## Generate an API Access Token

1. Hover over your profile picture (top-right corner).
2. Click **Account Settings → API Access Token**.
3. Click **+ New Token**, name it `claude-code`, and copy the token.
   Store it — it will not be shown again.

## Add the token to your shell profile

Add to `~/.zshrc` or `~/.bashrc`:

```bash
export APIDOG_ACCESS_TOKEN="apk_your_actual_token_here"
```

Reload:

```bash
source ~/.zshrc
```

## Import your OpenAPI contract (if it exists)

If the project has an existing `openapi.yaml` or `openapi.json`:

1. Open the Apidog project.
2. Click **+ → Import → Import OpenAPI Spec**.
3. Upload the file. All endpoints are created automatically.

## Verify the MCP is working

After adding the project ID to `.mcp.json` and restarting Claude Code:

"Use the Apidog MCP to count the total number of endpoints in this project"

A successful response returns a number. Zero is correct for a new
empty project.

## Getting shareable endpoint URLs

For any endpoint in Apidog, the shareable URL format is:

`https://app.apidog.com/project/{project-id}/apis/api-{endpoint-id}`

The Apidog MCP can retrieve these URLs programmatically. When writing
Trello task descriptions that reference an API endpoint, always use
the MCP to fetch the URL rather than constructing it manually.
