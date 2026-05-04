# Guide 04 — GitHub MCP Setup

The GitHub MCP lets Claude Code create and manage repositories, open
and merge pull requests, create branches, commit files, and read
repository contents — all without leaving the editor.

## Generate a GitHub personal access token

1. Go to GitHub → Settings → Developer settings →
   Personal access tokens → Tokens (classic).
2. Click **Generate new token (classic)**.
3. Name: `claude-code-mcp`.
4. Expiration: 90 days (or No expiration for a team shared machine).
5. Select scopes:
   - `repo` (full control of private repositories)
   - `read:org`
   - `read:user`
   - `workflow` (if the project uses GitHub Actions)
6. Click **Generate token** and copy it.

## Add the token to your shell profile

Add to `~/.zshrc` or `~/.bashrc`:

```bash
export GITHUB_TOKEN="ghp_your_actual_token_here"
```

Reload:

```bash
source ~/.zshrc
```

## GitHub MCP configuration in .mcp.json

```json
"github": {
  "command": "npx",
  "args": ["-y", "@modelcontextprotocol/server-github"],
  "env": {
    "GITHUB_TOKEN": "${GITHUB_TOKEN}"
  }
}
```

Note: unlike Apidog, Trello, and Figma, the GitHub MCP does not
require a project-specific ID hardcoded in the config. It operates
on whatever repository is active via natural language (e.g. "create
a PR on owner/repo-name"). The repo names are documented in the
constitution, not in .mcp.json.

## Verify the MCP is working

After restarting Claude Code:

"Use the GitHub MCP to list the open pull requests on {owner}/{repo}"

A successful response lists open PRs or confirms there are none.

## Repository naming in the constitution

All repository names for the project are documented in the project
constitution under the "Repository structure" section. Claude Code
reads the constitution at the start of every session and knows which
repos belong to the project.
