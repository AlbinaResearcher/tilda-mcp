# Windows Setup

Step-by-step guide for setting up Tilda MCP on Windows.

---

## 1. Install Node.js

1. Go to [nodejs.org](https://nodejs.org)
2. Download the **LTS version**
3. Run the installer — keep all default settings
4. Restart your computer

**Verify the installation:**
```
Win + R → type "cmd" → press Enter
```
```
node --version
```
You should see a version number like `v20.x.x`.

---

## 2. Get your Tilda API keys

1. Log in at [tilda.cc](https://tilda.cc)
2. Go to **Account → Settings → Integrations → API**
3. Copy your **Public Key** and **Secret Key**

---

## 3. Configure .mcp.json

Open `.mcp.json` from this project and paste in your keys:

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

---

## 4. Add to Claude Desktop

1. Press `Win + R`, type `%APPDATA%\Claude`, press Enter
2. Open `claude.json` (create it if it doesn't exist)
3. Paste the contents of `.mcp.json` into this file

If `claude.json` already contains other MCP servers, add `tilda` inside the existing `mcpServers` block:

```json
{
  "mcpServers": {
    "existing-server": { "..." },
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

---

## 5. Restart Claude

Close Claude Desktop completely (including the system tray icon), then reopen it.

---

## 6. Test

Ask Claude:
```
Show me all my Tilda projects
```

If you see your projects listed — setup is complete.

---

## Troubleshooting

| Problem | Solution |
|---|---|
| `node is not recognized` | Reinstall Node.js and restart |
| `401 Unauthorized` | Check that API keys are copied correctly, no extra spaces |
| Claude doesn't see Tilda | Verify the path in `claude.json` and restart Claude |
| JSON parse error | Validate your `claude.json` at [jsonlint.com](https://jsonlint.com) |
