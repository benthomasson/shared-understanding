# Entries Directory

This directory contains chronologically organized documentation entries for shared understanding and knowledge management.

## Directory Structure

```
entries/
├── YYYY/           # Year
│   ├── MM/         # Month (01-12)
│   │   ├── DD/     # Day (01-31)
│   │   │   ├── investigation-findings.md
│   │   │   ├── configuration-notes.md
│   │   │   └── troubleshooting-session.md
│   │   └── ...
│   └── ...
└── README.md       # This file
```

## Creating New Entries

Use the `new_entry` script in the repository root to create new entries with automatic date directory structure:

```bash
# Basic usage - creates file with today's date
./new_entry investigation-findings

# With custom title
./new_entry shared-understanding-analysis "Shared Understanding Analysis"

# File extension is automatic (.md)
./new_entry knowledge-capture
```

The script will:
1. Create the appropriate year/month/day directory structure
2. Generate a markdown file with a basic template
3. Open the file in your default editor (`$EDITOR` or nano)

## Entry Template

Each new entry starts with this template:

```markdown
# Title

**Date:** YYYY-MM-DD
**Time:** HH:MM

## Overview

## Details

## Next Steps

## Related

```

## Usage Tips

1. **Topic-focused entries** - Create separate files for different investigation topics
2. **Daily organization** - Multiple entries per day are encouraged for different topics
3. **Cross-referencing** - Use the "Related" section to link to other entries or external resources
4. **Progress tracking** - Use "Next Steps" to maintain continuity across sessions

## Finding Entries

```bash
# Find all entries from a specific date
find entries/2026/01/30 -name "*.md"

# Search for entries containing specific terms
grep -r "shared understanding" entries/

# List all entries from current month
find entries/2026/01 -name "*.md" | sort
```

## Examples

Good entry naming conventions:
- `shared-understanding-investigation.md` - Knowledge exploration
- `configuration-discovery.md` - Setup and config notes
- `team-knowledge-integration.md` - Team collaboration work
- `troubleshooting-session.md` - Problem-solving notes
- `meeting-notes-team-sync.md` - Meeting documentation