# Tilda MCP Server

**Control your Tilda websites directly from Claude using the Model Context Protocol.**

[![npm](https://img.shields.io/npm/v/@theyahia/tilda-mcp)](https://www.npmjs.com/package/@theyahia/tilda-mcp)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-green)](https://modelcontextprotocol.io)
[![Node.js](https://img.shields.io/badge/Node.js-16%2B-brightgreen)](https://nodejs.org)

---

## What is this?

Tilda MCP is a [Model Context Protocol](https://modelcontextprotocol.io) server that connects [Claude AI](https://claude.ai) to your [Tilda](https://tilda.cc) account. Once set up, you can manage your entire website through natural language — no browser needed.

```
You: "Create a landing page with a contact form and publish it"
Claude: Done. Your page is live at yoursite.tilda.ws
```

---

## Features

| Capability | Description |
|---|---|
| **Projects** | List, create, and publish projects |
| **Pages** | Create, update, and delete pages |
| **Content Blocks** | Add text, images, buttons, forms, galleries, and video |
| **Publishing** | Publish projects directly from Claude |
| **Natural Language** | No commands to memorize — just describe what you want |

---

## Quick Start

### Prerequisites

- [Node.js](https://nodejs.org) 16 or higher
- A [Tilda](https://tilda.cc) account with API access
- [Claude Desktop](https://claude.ai/download)

### 1. Get your Tilda API keys

1. Log in to [tilda.cc](https://tilda.cc)
2. Go to **Account → Settings → Integrations → API**
3. Copy your **Public Key** and **Secret Key**

### 2. Configure the MCP server

Open `.mcp.json` and replace the placeholder values:

```json
{
  "mcpServers": {
    "tilda": {
      "type": "stdio",
      "command": "cmd",
      "args": ["/c", "npx", "-y", "@theyahia/tilda-mcp"],
      "env": {
        "TILDA_PUBLIC_KEY": "your_public_key_here",
        "TILDA_SECRET_KEY": "your_secret_key_here"
      }
    }
  }
}
```

> **macOS / Linux:** replace `"command": "cmd"` and `"args": ["/c", "npx", ...]` with `"command": "npx"` and `"args": ["-y", "@theyahia/tilda-mcp"]`

### 3. Add to Claude Desktop

**Windows:** Open `%APPDATA%\Claude\claude.json`  
**macOS:** Open `~/Library/Application Support/Claude/claude.json`

Paste the contents of `.mcp.json` into that file, then restart Claude.

### 4. Verify it works

Ask Claude:
```
Show me all my Tilda projects
```

---

## Usage Examples

### Create a website from scratch
```
Help me build a portfolio site:
- Create a project called "MyPortfolio"
- Add pages: Home, Work, About, Contact
- Add a heading "My Portfolio" to the Home page
- Add a contact form to the Contact page
- Publish when ready
```

### Update an existing site
```
In project 12345:
- Change the main page title to "Welcome"
- Add a testimonials section
- Update the call-to-action button text to "Get Started"
- Publish the changes
```

### Build a landing page
```
Create a landing page for my product:
- Hero section with headline and description
- Three key benefits
- Email signup form
- "Buy Now" button
- Publish it
```

---

## Documentation

- [Quick Start Guide](QUICKSTART.md)
- [Full Examples](EXAMPLES.md)
- [API Reference](API_REFERENCE.md)
- [Windows Setup](WINDOWS_SETUP.md)
- [macOS / Linux Setup](MACOS_LINUX_SETUP.md)

---

## Security

**Never commit your real API keys to Git.**

The `.mcp.json` file in this repo contains placeholder values only. Keep your actual keys in a local copy of the file that is not tracked by Git, or use environment variables.

See [`.gitignore`](.gitignore) — it is already configured to exclude `.env` files.

---

## Contributing

Pull requests are welcome. For major changes, please open an issue first to discuss what you'd like to change.

---

## License

[MIT](LICENSE) © AlbinaResearcher
