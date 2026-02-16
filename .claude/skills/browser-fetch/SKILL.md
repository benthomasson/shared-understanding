---
name: browser-fetch
description: Fetch authenticated web content (SSO, internal pages) via browser session
---

# Browser Fetch Skill

Fetch web content from authenticated sites using a real browser with persistent session cookies.

**Repository:** https://github.com/benthomasson/browser-fetch

## Quick Start

```bash
# Start server (recommended for Claude)
uvx --from "git+https://github.com/benthomasson/browser-fetch" browser-fetch --serve https://internal.example.com

# Server prints a security token. Use it to fetch:
curl 'http://localhost:8080/fetch?token=TOKEN&url=https://internal.example.com/page&text=true'
```

## When to Use This Skill

Use this skill when:
- User needs to access content behind SSO authentication
- User wants to fetch internal company pages
- User provides a URL that requires login (returns login page with WebFetch)
- User mentions needing authenticated browser access

## Server Mode (Recommended)

The server keeps a browser open and exposes an HTTP API.

### Workflow

1. **Check if server is running:**
   ```bash
   curl -s localhost:8080/health
   ```

2. **If not running, ask user to start it:**
   ```bash
   uvx --from "git+https://github.com/benthomasson/browser-fetch" browser-fetch --serve https://internal.example.com
   ```

3. **Ask user for the security token** (printed on startup)

4. **Fetch pages:**
   ```bash
   curl -s 'http://localhost:8080/fetch?token=TOKEN&url=URL&text=true'
   ```

5. **For large pages, save to file:**
   ```bash
   curl -s 'http://localhost:8080/fetch?token=TOKEN&url=URL&text=true' > /tmp/page.txt
   ```

### Query Parameters

| Parameter | Description |
|-----------|-------------|
| `token` | Security token (required) |
| `url` | URL to fetch (required) |
| `text=true` | Extract text only (recommended) |
| `selector=CSS` | Extract specific element |
| `wait=N` | Wait N seconds for slow pages |

### Server Endpoints

```bash
# Health check (no token needed)
curl 'http://localhost:8080/health'

# Fetch page
curl 'http://localhost:8080/fetch?token=TOKEN&url=URL&text=true'

# Shutdown server
curl 'http://localhost:8080/shutdown?token=TOKEN'
```

## Single-Fetch Mode

For one-off fetches without keeping browser open:

```bash
# First: login to save session
uvx --from "git+https://github.com/benthomasson/browser-fetch" browser-fetch --login https://internal.example.com

# Then: fetch headlessly
uvx --from "git+https://github.com/benthomasson/browser-fetch" browser-fetch --headless --text https://internal.example.com/page

# Extract specific element
uvx --from "git+https://github.com/benthomasson/browser-fetch" browser-fetch --headless --selector "main" --text URL

# Save to file
uvx --from "git+https://github.com/benthomasson/browser-fetch" browser-fetch --headless -o /tmp/page.html URL
```

## Options

| Option | Description |
|--------|-------------|
| `--serve` | Run as HTTP server (browser stays open) |
| `--login` | Open browser for manual login |
| `--headless` | Run without visible browser |
| `--text` | Extract text only (no HTML) |
| `--selector CSS` | Extract specific element |
| `-o FILE` | Save output to file |
| `--wait N` | Wait N seconds after load (default: 5) |
| `--timeout N` | Page load timeout (default: 30) |
| `--port N` | Server port (default: 8080) |

## Troubleshooting

**401 Unauthorized**: Token missing or wrong. Ask user for token from server output.

**Connection refused**: Server not running. Ask user to start with `--serve`.

**Login page returned**: User needs to log in via the browser window that opened.

**Session expired**: Re-run with `--login` to refresh session.

## How It Works

1. Uses Playwright with Chromium for real browser rendering
2. Stores cookies/session in `~/.config/browser-fetch/profile`
3. Server mode generates random security token on startup
4. Binds to localhost only (not network accessible)

## Links

- **Repository**: https://github.com/benthomasson/browser-fetch

---

*Last updated: 2026-02-12*
