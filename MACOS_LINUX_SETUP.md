# macOS & Linux Setup

Step-by-step guide for setting up Tilda MCP on macOS and Linux.

---

## 1. Install Node.js

### macOS

**With Homebrew (recommended):**
```bash
brew install node
```

**Without Homebrew** — download the installer from [nodejs.org](https://nodejs.org).

### Linux (Ubuntu / Debian)
```bash
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt-get install -y nodejs
```

### Linux (Fedora / RHEL)
```bash
sudo dnf install nodejs npm
```

**Verify:**
```bash
node --version   # v16 or higher
npm --version
```

---

## 2. Get your Tilda API keys

1. Log in at [tilda.cc](https://tilda.cc)
2. Go to **Account → Settings → Integrations → API**
3. Copy your **Public Key** and **Secret Key**

---

## 3. Configure .mcp.json

Open `.mcp.json` from this project. On macOS / Linux, use `npx` directly instead of `cmd`:

```json
{
  "mcpServers": {
    "tilda": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@theyahia/tilda-mcp"],
      "env": {
        "TILDA_PUBLIC_KEY": "your_public_key",
        "TILDA_SECRET_KEY": "your_secret_key"
      }
    }
  }
}
```

---

## 4. Add to Claude Desktop

| OS | Config file |
|---|---|
| macOS | `~/Library/Application Support/Claude/claude.json` |
| Linux | `~/.config/Claude/claude.json` |

Open the file (create it if it doesn't exist) and paste the contents of `.mcp.json` into it.

**macOS — quick open:**
```bash
open ~/Library/Application\ Support/Claude/
```

**Linux — edit with nano:**
```bash
nano ~/.config/Claude/claude.json
```

---

## 5. Restart Claude

- **macOS:** `Cmd + Q`, then reopen
- **Linux:** Close the window, then reopen

---

## 6. Test

Ask Claude:
```
Show me all my Tilda projects
```

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `command not found: node` | Install Node.js — see step 1 |
| `command not found: npx` | Run `npm install -g npx` |
| `401 Unauthorized` | Re-check your API keys |
| Claude doesn't see Tilda | Verify the config file path and restart Claude |
| JSON parse error | Validate your config at [jsonlint.com](https://jsonlint.com) |
