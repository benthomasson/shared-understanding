---
name: gcmd
description: Export and access Google Drive files (docs, sheets, meeting notes)
---

# Google Drive CLI (gcmd) Skill

Quick reference for using `gcmd` CLI tool to work with Google Drive files.

**Repository:** https://github.com/shanemcd/gcmd

## Quick Start

The easiest way to use `gcmd` is with `uvx` - no installation or repository cloning required:

```bash
# Export a Google Doc as markdown
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "https://docs.google.com/document/d/FILE_ID/edit" -o /tmp/

# Export a Google Sheet as CSV (one file per sheet)
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "https://docs.google.com/spreadsheets/d/FILE_ID/edit" -o /tmp/

# List recent files
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list

# Search for files
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -q "quarterly report"

# View file info and comments
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info -v "https://docs.google.com/document/d/FILE_ID/edit"
```

**Tip**: Add an alias to your shell for convenience:
```bash
alias gcmd='uvx --from "git+https://github.com/shanemcd/gcmd" gcmd'

# Then use it simply:
gcmd export "https://docs.google.com/document/d/FILE_ID/edit" -o /tmp/
```

## Overview

`gcmd` is a Python CLI tool for working with Google Drive from the command line. Useful for:
- Exporting Google Docs as markdown for processing/archival
- Exporting Google Sheets as CSV (one file per sheet)
- Listing and searching Drive files
- Downloading files
- Viewing file metadata, permissions, and comments
- Reviewing document feedback and collaboration

## When to Use This Skill

Use this skill when:
- User asks to export Google Docs as markdown
- User asks to export Google Sheets as CSV
- User provides a Google Drive URL and wants to read/access the content
- User asks to search for files in Google Drive
- User wants to view file permissions or comments on Google Docs
- User mentions "meeting notes" or "Gemini notes" from Google Meet
- User asks to list recent Google Drive files

## Common Commands

### Export Google Docs as Markdown

**RECOMMENDED: Export to /tmp/ for easy reading by Claude Code**

```bash
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "https://docs.google.com/document/d/FILE_ID/edit" -o /tmp/
# Creates: /tmp/Document Title.md (uses document title as filename)
```

**Export to specific file path:**
```bash
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export FILE_ID -o /tmp/meeting-notes.md
# Creates: /tmp/meeting-notes.md
```

**Export all tabs as separate files:**
```bash
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export --all-tabs FILE_ID -o /tmp/
# Creates: /tmp/Document Title - Tab1.md, /tmp/Document Title - Tab2.md, etc.
```

**How `-o` works:**
- **Without `-o`**: Saves to current directory using document title + `.exported.md`
- **With `-o /tmp/`** (directory): Saves to `/tmp/` using document title + `.md` extension (no `.exported`)
- **With `-o /tmp/file.md`** (file): Saves to exact path `/tmp/file.md`

After exporting, ALWAYS read the file to provide the user with the content.

### Export Google Sheets as CSV

**Export creates a directory with one CSV file per sheet:**

```bash
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "https://docs.google.com/spreadsheets/d/FILE_ID/edit" -o /tmp/
# Creates: /tmp/Spreadsheet Title/
#   Sheet1.csv
#   Sheet2.csv
#   ...
```

**How it works:**
- Auto-detects Google Sheets vs Docs based on URL/file type
- Creates a directory named after the spreadsheet
- Exports each sheet/tab as a separate CSV file
- Includes retry logic with exponential backoff for rate limiting

After exporting, read the CSV files to provide the user with the content.

### List and Search Files

```bash
# List recent files (default 20, sorted by modified date)
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list

# Search for files by name or content
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -q "quarterly report"

# List only Google Docs
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -t docs

# List with verbose details
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -v -n 10

# List only folders
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -t folders

# List Google Sheets
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -t sheets
```

### View File Info

```bash
# Basic file metadata
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info "https://docs.google.com/document/d/FILE_ID/edit"

# Detailed info with permissions, tabs, structure, and comments
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info -v "https://docs.google.com/document/d/FILE_ID/edit"

# Show only comments (without other verbose details)
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info --show-comments "https://docs.google.com/document/d/FILE_ID/edit"

# Also works with just file ID
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info FILE_ID -v
```

**Detailed info shows:**
- File metadata (name, type, size, dates)
- Owner and last modifier
- All permissions (users, groups, domains, public links)
- Your capabilities (can edit, comment, share, download, etc.)
- Document tabs (for multi-tab Google Docs)
- Document outline with all headings
- **Comments and replies** with quoted text, authors, timestamps, and status (resolved/deleted)

### Download Files

```bash
# Download to current directory
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd download FILE_ID

# Download to specific path
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd download FILE_ID -o ~/Downloads/myfile.pdf

# Works with URLs
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd download "https://drive.google.com/file/d/FILE_ID/view"
```

## URL Format Support

All commands accept multiple URL formats:

```bash
# Google Docs
https://docs.google.com/document/d/FILE_ID/edit
https://docs.google.com/document/d/FILE_ID/edit?tab=t.0

# Google Sheets
https://docs.google.com/spreadsheets/d/FILE_ID/edit

# Google Slides
https://docs.google.com/presentation/d/FILE_ID/edit

# Drive files
https://drive.google.com/file/d/FILE_ID/view

# Just the file ID
FILE_ID
```

## Workflow Example

When user provides a Google Drive URL:

1. **Export the document to /tmp/**:
   ```bash
   uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "URL" -o /tmp/
   ```

2. **Read the exported file**:
   The file will be in `/tmp/` with the document title as filename.

3. **Provide the content to the user** or answer their questions about it.

4. **Optional cleanup**: After helping the user, you can delete the exported file:
   ```bash
   rm /tmp/exported-filename.md
   ```

## Common Workflow Examples

### Find and export a document

```bash
# Search for the document
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -q "MCP Server Analysis" -t docs

# Get detailed info (tabs, structure)
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info -v "https://docs.google.com/document/d/FILE_ID/edit"

# Export all tabs to /tmp/ for easy reading
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export --all-tabs FILE_ID -o /tmp/
```

### Check permissions on shared docs

```bash
# View detailed permissions
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info -v FILE_ID

# Shows:
# - Who has access (users, groups, domains, public)
# - Permission levels (owner, writer, reader, commenter)
# - Your capabilities (can edit, share, download, etc.)
```

### Review document feedback

```bash
# View all comments and replies on a document
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd info --show-comments "https://docs.google.com/document/d/FILE_ID/edit"

# Shows:
# - All comments with quoted/highlighted text
# - Authors and timestamps
# - Replies with their authors
# - Status (resolved, deleted)
# - Total comment count
```

### List recent work documents

```bash
# List recent Google Docs with details
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list -t docs -v -n 20
```

### Export a spreadsheet for analysis

```bash
# Export all sheets to CSV
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "https://docs.google.com/spreadsheets/d/FILE_ID/edit" -o /tmp/

# List the exported files
ls /tmp/Spreadsheet\ Title/

# Read a specific sheet
cat "/tmp/Spreadsheet Title/Sheet1.csv"
```

## Key Features

- **URL support**: All commands accept full Google Drive URLs or file IDs
- **Native markdown export**: Preserves formatting (headings, tables, links, bold, italic)
- **Sheets CSV export**: Export Google Sheets to CSV (one file per sheet in a directory)
- **Multi-tab documents**: Use `--all-tabs` to export each tab separately
- **Detailed info**: View permissions, sharing, capabilities, document structure
- **Comments access**: View all comments and replies with quoted text, authors, and timestamps
- **Auto-naming**: Exported files use `.exported.md` extension (auto-ignored by git) when no `-o` specified
- **Rate limit handling**: Automatic retries with exponential backoff for API rate limits

## Authentication

### First-Time Setup

Before first use, you need OAuth credentials:

1. Go to [Google Cloud Console](https://console.cloud.google.com/apis/credentials)
2. Create a new project or select existing
3. Enable APIs:
   - [Google Drive API](https://console.cloud.google.com/apis/library/drive.googleapis.com)
   - [Google Docs API](https://console.cloud.google.com/apis/library/docs.googleapis.com)
   - [Google Sheets API](https://console.cloud.google.com/apis/library/sheets.googleapis.com)
4. Create OAuth 2.0 Client ID credentials:
   - Click "+ CREATE CREDENTIALS" → "OAuth client ID"
   - Application type: "Desktop app"
   - Name: "gcmd" (or anything)
5. Download the JSON file
6. Save to: `~/.config/gcmd/credentials.json`

### First Run

On first use, your browser will open for authentication:
```bash
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list
# Browser opens → sign in → grant permissions → done!
```

Token is cached at `~/.config/gcmd/token.json` for future use.

### Troubleshooting Authentication

If authentication fails, delete token and re-authenticate:
```bash
rm ~/.config/gcmd/token.json
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list  # Will trigger new auth flow
```

## Important Notes

1. **Always use `/tmp/` for exports** - Makes files easy to find and read
2. **No installation required** - Use `uvx` to run directly from GitHub
3. **Read exported files** - After exporting, read the file and provide content to user
4. **Clean up after** - Delete exported files from /tmp/ when done

## Troubleshooting

**"credentials.json not found"**: Follow the Authentication setup steps above to create OAuth credentials

**"Authentication failed"**: Delete token and re-authenticate:
```bash
rm ~/.config/gcmd/token.json
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list
```

**"Not a Google Doc"**: Use `download` command instead of `export` for non-Doc files

**Browser won't open**: The CLI will provide a manual URL to paste in your browser

## Tips

1. **Add a shell alias** for convenience:
   ```bash
   alias gcmd='uvx --from "git+https://github.com/shanemcd/gcmd" gcmd'
   ```

2. **Export location:** Always use `-o /tmp/` when exporting so files are in a predictable location for easy reading

3. **File naming:** Without `-o`, exported files use `.exported.md` extension. With `-o /dir/`, uses `.md`

4. **Multi-tab documents:** Use `--all-tabs` to export each tab as a separate file

5. **Verbose mode:** Use `-v` for detailed information (permissions, structure, comments, etc.)

6. **Comments:** Use `--show-comments` to view just comments without other verbose details

7. **Search:** The `-q` flag searches both file names and content

## Links

- **Repository**: https://github.com/shanemcd/gcmd
- **Issues**: https://github.com/shanemcd/gcmd/issues

---

*Last updated: 2026-01-20*
