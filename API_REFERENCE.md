# API Reference

Complete reference for all available Tilda MCP commands.

---

## Projects

### List all projects
**Prompt:** `Show me all my Tilda projects`

Returns a list of all projects in your account with ID, title, URL, status, and page count.

---

### Get project details
**Prompt:** `Give me details about project {id}`

Returns full project information including description, URL, status, and creation date.

---

### Create a project
**Prompt:** `Create a new project called "{name}"`

| Parameter | Required | Description |
|---|---|---|
| `title` | Yes | Project name |
| `domain` | No | Custom domain (optional) |

---

### Publish a project
**Prompt:** `Publish project {id}`

Publishes all pages in the project and makes them live.

---

## Pages

### List pages
**Prompt:** `Show all pages in project {id}`

Returns all pages with ID, title, URL alias, status, and block count.

---

### Get page details
**Prompt:** `Get info about page {id}`

Returns full page details including project ID, blocks, and timestamps.

---

### Create a page
**Prompt:** `Create a page called "{name}" in project {id}`

| Parameter | Required | Description |
|---|---|---|
| `project_id` | Yes | Parent project ID |
| `title` | Yes | Page title |
| `alias` | No | URL path (auto-generated if omitted) |

---

### Update a page
**Prompt:** `Rename page {id} to "{new name}"`

| Parameter | Required | Description |
|---|---|---|
| `page_id` | Yes | Page to update |
| `title` | No | New title |
| `content` | No | New HTML content |

---

### Delete a page
**Prompt:** `Delete page {id}`

Permanently removes the page. This action cannot be undone.

---

## Content Blocks

### Add a block
**Prompt:** `Add a {type} block to page {id}`

Available block types:

| Type | Example prompt |
|---|---|
| `text` | `Add a text block with "Welcome to my site"` |
| `image` | `Add an image to page 67890` |
| `button` | `Add a button labeled "Get Started"` |
| `form` | `Add a contact form to page 67890` |
| `gallery` | `Add an image gallery to page 67890` |
| `video` | `Add a video to page 67890` |

---

## Error Codes

| Code | Meaning | How to fix |
|---|---|---|
| `401` | Invalid API key | Check your keys in `.mcp.json` |
| `404` | Project or page not found | Verify the ID |
| `400` | Bad request parameters | Check the format of your input |
| `429` | Rate limit exceeded | Wait a moment and try again |
| `500` | Tilda server error | Try again later |

---

## Data Objects

### Project
```json
{
  "id": "12345",
  "title": "My Website",
  "description": "...",
  "url": "https://example.com",
  "status": "published",
  "pages_count": 5,
  "created": "2024-01-01T00:00:00Z"
}
```

### Page
```json
{
  "id": "67890",
  "title": "Home",
  "alias": "index",
  "project_id": "12345",
  "status": "published",
  "blocks_count": 10,
  "created": "2024-01-01T00:00:00Z",
  "updated": "2024-04-06T15:00:00Z"
}
```
