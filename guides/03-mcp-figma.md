# Guide 03 — Figma MCP Setup

The Figma MCP lets Claude Code read design files, inspect components
and styles, extract design tokens, and generate UI code from designs.

## Find or create the Figma design file

Every project should have a dedicated Figma file. If one does not
exist, create it at https://figma.com.

The **Figma file key** is in the file URL:

```
https://www.figma.com/design/{FILE_KEY}/Your-File-Name
```

Copy everything between `/design/` and the next `/`.
Example: for `figma.com/design/2zcHhTNknNOuy9HINa6xpk/eSIM-White-Label`
the file key is `2zcHhTNknNOuy9HINa6xpk`.

This key is safe to commit in `.mcp.json`.

## Generate a Figma personal access token

1. Open Figma and click your profile picture (top-left).
2. Go to **Settings → Security → Personal access tokens**.
3. Click **Generate new token**, name it `claude-code`, set expiry.
4. Copy the token — it will not be shown again.

## Add the token to your shell profile

Add to `~/.zshrc` or `~/.bashrc`:

```bash
export FIGMA_ACCESS_TOKEN="figd_your_actual_token_here"
```

Reload:

```bash
source ~/.zshrc
```

## Figma MCP configuration in .mcp.json

The Figma MCP is configured with your file key as a fixed argument:

```json
"figma": {
  "command": "npx",
  "args": ["-y", "@figma/mcp-server", "--file-key=YOUR_FILE_KEY"],
  "env": {
    "FIGMA_ACCESS_TOKEN": "${FIGMA_ACCESS_TOKEN}"
  }
}
```

## Verify the MCP is working

After adding the file key to `.mcp.json` and restarting Claude Code:

"Use the Figma MCP to list all pages in the design file"

A successful response lists the page names from your Figma file.

## Using Figma URLs in Trello tasks

For any mobile or frontend Trello task card, include the Figma frame
URL for the screen being implemented. To get a frame URL in Figma:
right-click any frame → Copy → Copy link.
