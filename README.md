
# ~~How to create a Hive Mind~~
# ~~How to create a Collective Intelligence~~
# How to create a Shared Understanding

This repository is a framework for building shared understanding of problems or topics within teams through structured documentation and external tool integration. It facilitates knowledge capture, organization, and collaboration using a chronological entry system and modular skills for external services.

## Quick Start

### Creating Your First Entry

Use the `new_entry` script to create structured documentation:

```bash
# Basic usage - creates file with today's date
./new_entry investigation-findings

# With custom title
./new_entry saas-routing-analysis "SaaS Routing Analysis"

# Open in editor after creation
./new_entry --edit meeting-notes "Meeting Notes"
```

This will create a markdown file in the `entries/YYYY/MM/DD/` directory with a standardized template.

### Finding and Organizing Entries

```bash
# Find entries from a specific date
find entries/2026/01/30 -name "*.md"

# Search across all entries
grep -r "keyword" entries/

# List all entries from current month
find entries/2026/01 -name "*.md" | sort
```

## Core Features

### 📁 Chronological Organization
- Automatic date-based directory structure (`entries/YYYY/MM/DD/`)
- Standardized markdown templates for consistency
- Cross-referencing support for linking related content

### 🔧 External Tool Integration (Skills)
Integration with common workplace tools through CLI interfaces:

- **Google Drive** (`gcmd`): Export docs as markdown, manage sheets and files
- **Jira** (`jirahhh`): Create, update, and search issues with wiki markup
- **Slack** (`slacker`): Manage reminders, search messages, check activity

All skills use `uvx` for installation-free execution.

### 🎯 Team Collaboration
- Consistent entry format for shared understanding
- Progress tracking through "Next Steps" sections
- Knowledge connectivity via "Related" sections

## Directory Structure

```
shared-understanding/
├── README.md           # This file
├── CLAUDE.md          # Guidance for Claude Code
├── new_entry*         # Entry creation script
├── entries/           # Chronological documentation
│   ├── README.md      # Entry system documentation
│   └── YYYY/MM/DD/    # Date-organized entries
└── skills/            # External tool integrations
    ├── gcmd/          # Google Drive CLI
    ├── jirahhh/       # Jira CLI
    └── slacker/       # Slack CLI
```

## Usage Examples

### Investigation Workflow
1. Create entry: `./new_entry network-investigation "Network Connectivity Investigation"`
2. Document findings in structured sections
3. Import external data using skills
4. Cross-reference related entries
5. Track next steps for continuity

### External Data Import
```bash
# Export Google Doc for local analysis
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "GOOGLE_DRIVE_URL" -o /tmp/

# Create Jira issue from investigation
uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh create --project AAP --type Task --summary "Investigation Results"

# Set Slack reminder for follow-up
uvx --from "git+https://github.com/shanemcd/slacker" slacker reminder create "1 day" "Review investigation findings"
```

## Configuration

No central configuration required. The repository is self-contained with standardized templates.

External skills manage their own configuration:
- gcmd: OAuth credentials in `~/.config/gcmd/credentials.json`
- jirahhh: API tokens in `~/.config/jirahhh/config.yaml`
- slacker: Browser session credentials in `~/.config/slacker/credentials`

## Entry Template

Each entry follows a standardized structure:

```markdown
# Title

**Date:** YYYY-MM-DD
**Time:** HH:MM

## Overview
High-level summary

## Details
Comprehensive information

## Next Steps
Action items for continuity

## Related
Links to related entries or external resources
```

This framework promotes systematic knowledge building and shared understanding within teams before attempting solutions or for educational purposes.
