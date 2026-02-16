---
name: curl
description: Fetch web content using curl (faster alternative to WebFetch)
---

# curl Skill

Quick reference for fetching web content with curl instead of WebFetch tool.

## When to Use This Skill

Use this skill when:
- WebFetch is slow, hanging, or unreliable
- You need to fetch web pages or API responses
- You want more control over request headers and options

## Quick Start

```bash
# Basic fetch (silent, follow redirects)
curl -sL "https://example.com"

# Fetch with timeout (30 seconds)
curl -sL --max-time 30 "https://example.com"

# Fetch JSON API
curl -sL "https://api.github.com/repos/owner/repo" | jq .

# Convert HTML to readable text
curl -sL "https://example.com" | lynx -stdin -dump -nolist
```

## Common Commands

### Fetch and Read HTML

```bash
# Fetch raw HTML
curl -sL "https://example.com"

# Fetch and convert to readable text (requires lynx)
curl -sL "https://example.com" | lynx -stdin -dump -nolist

# Fetch and save to file
curl -sLo /tmp/page.html "https://example.com"
```

### Fetch JSON APIs

```bash
# Fetch and pretty-print JSON
curl -sL "https://api.example.com/endpoint" | jq .

# Fetch with authentication header
curl -sL -H "Authorization: Bearer TOKEN" "https://api.example.com/endpoint" | jq .

# Fetch specific JSON fields
curl -sL "https://api.github.com/repos/owner/repo" | jq '{name, description, stars: .stargazers_count}'
```

### POST Requests

```bash
# POST JSON data
curl -sL -X POST -H "Content-Type: application/json" \
  -d '{"key":"value"}' "https://api.example.com/endpoint"

# POST form data
curl -sL -X POST -d "field1=value1&field2=value2" "https://example.com/form"
```

### Debugging

```bash
# Show response headers
curl -sL -I "https://example.com"

# Show final URL after redirects
curl -sLw "%{url_effective}\n" -o /dev/null "https://example.com"

# Verbose output (for debugging)
curl -sLv "https://example.com" 2>&1 | head -50
```

## Common Flags

| Flag | Description |
|------|-------------|
| `-s` | Silent mode (no progress bar) |
| `-L` | Follow redirects |
| `-o file` | Output to file |
| `-O` | Save with remote filename |
| `-H "Header: value"` | Add request header |
| `-d "data"` | POST data |
| `-X METHOD` | HTTP method (GET, POST, PUT, DELETE) |
| `--max-time N` | Timeout in seconds |
| `-w "format"` | Write-out format string |
| `-I` | Headers only (HEAD request) |
| `-v` | Verbose output |

## Workflow Example

When user asks to read a web page:

1. **Fetch the content**:
   ```bash
   curl -sL --max-time 30 "https://example.com" | lynx -stdin -dump -nolist > /tmp/page.txt
   ```

2. **Read the content**:
   Use the Read tool to read `/tmp/page.txt`

3. **Answer the user's question** based on the content

## Tips

1. **Always use `-sL`** - Silent mode and follow redirects
2. **Set a timeout** - Use `--max-time 30` to avoid hanging
3. **Pipe to `jq`** for JSON - Much easier to read
4. **Pipe to `lynx`** for HTML - Converts to readable text
5. **Save to /tmp/** - Easy to find and read

## Comparison with WebFetch

| Aspect | curl | WebFetch |
|--------|------|----------|
| Speed | Fast | Can be slow |
| Reliability | Very reliable | Sometimes hangs |
| Output | Raw content | Summarized |
| Control | Full headers, methods | Limited |
| Processing | Pipe to jq, lynx, etc. | Built-in |

---

*Last updated: 2026-02-10*
