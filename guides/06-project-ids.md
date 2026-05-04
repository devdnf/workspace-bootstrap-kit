# Guide 06 — Project IDs and .mcp.json

This guide explains what each project-specific ID is, where to find
it, whether it is safe to commit, and where it lives in the config.

## ID reference table

| ID | Where to find it | Commit to repo? | Where it lives |
|---|---|---|---|
| Apidog Project ID | Apidog → Project Settings → Basic Settings | ✅ Yes | .mcp.json args |
| Figma File Key | Figma file URL between /design/ and next / | ✅ Yes | .mcp.json args |
| Trello Board ID | Trello board URL between /b/ and next / | ✅ Yes | .mcp.json env |
| GitHub Repo name(s) | github.com/{owner}/{repo} | ✅ Yes | constitution.md |
| Apidog Access Token | Apidog Account Settings → API Access Token | ❌ No | Shell env var |
| Figma Access Token | Figma Settings → Personal access tokens | ❌ No | Shell env var |
| GitHub Token | GitHub → Developer settings → PAT | ❌ No | Shell env var |
| Trello API Key | trello.com/power-ups/admin → API Key | ❌ No | Shell env var |
| Trello Token | trello.com/power-ups/admin → Token link | ❌ No | Shell env var |

## The .mcp.json.example file

Copy `.mcp.json.example` to `.mcp.json` in your project root.
Replace every `YOUR_*` placeholder with the real value.
Commit `.mcp.json` (it contains no secrets).
Add `.env` to `.gitignore` but NOT `.mcp.json`.

## Shell environment variables

Each developer must set these in their personal shell profile.
They are never committed to any file.

```bash
# ~/.zshrc or ~/.bashrc

# Apidog
export APIDOG_ACCESS_TOKEN="apk_..."

# Figma
export FIGMA_ACCESS_TOKEN="figd_..."

# GitHub
export GITHUB_TOKEN="ghp_..."

# Trello
export TRELLO_API_KEY="..."
export TRELLO_TOKEN="..."
```

After editing the shell profile: `source ~/.zshrc`
After editing `.mcp.json`: restart Claude Code.

## Multiple projects

If you work on multiple projects with different Apidog projects,
Figma files, or Trello boards, each project has its own `.mcp.json`
with its own hardcoded IDs. The shell environment variables
(tokens) are shared across all projects — you only set them once.
