# Quick Start Guide

Get Tilda MCP running in under 5 minutes.

---

## Step 1 — Install Node.js

If you already have Node.js 16+, skip this step.

Download from [nodejs.org](https://nodejs.org) and install the **LTS version**.

Verify:
```bash
node --version   # should print v16 or higher
```

---

## Step 2 — Get your Tilda API keys

1. Log in at [tilda.cc](https://tilda.cc)
2. Navigate to **Account → Settings → Integrations → API**
3. Copy your **Public Key** and **Secret Key**

---

## Step 3 — Configure the server

Open `.mcp.json` and paste your keys:

```json
{
  "mcpServers": {
    "tilda": {
      "type": "stdio",
      "command": "cmd",
      "args": ["/c", "npx", "-y", "@theyahia/tilda-mcp"],
      "env": {
        "TILDA_PUBLIC_KEY": "your_public_key",
        "TILDA_SECRET_KEY": "your_secret_key"
      }
    }
  }
}
```

**macOS / Linux only** — change the command section to:
```json
"command": "npx",
"args": ["-y", "@theyahia/tilda-mcp"]
```

---

## Step 4 — Connect to Claude Desktop

| OS | Config file location |
|---|---|
| Windows | `%APPDATA%\Claude\claude.json` |
| macOS | `~/Library/Application Support/Claude/claude.json` |
| Linux | `~/.config/Claude/claude.json` |

Open the config file and paste the contents of `.mcp.json` into it.

If the file already has other MCP servers, add `tilda` inside the existing `mcpServers` object.

---

## Step 5 — Restart Claude

Close Claude Desktop completely, then reopen it.

---

## Step 6 — Test

Type this in Claude:

```
Show me all my Tilda projects
```

If you see your project list — you're all set.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| `node: command not found` | Install Node.js and restart your terminal |
| Claude doesn't see the Tilda tool | Check that the config file path is correct and restart Claude |
| `401 Unauthorized` | Re-check your API keys — no extra spaces |
| `Cannot find module` | Run `npm install` in the project folder |

For detailed OS-specific instructions:
- [Windows Setup](WINDOWS_SETUP.md)
- [macOS / Linux Setup](MACOS_LINUX_SETUP.md)
