---
name: new_entry
description: Create chronologically organized documentation entries
---

# Entry Creation System - new_entry

Complete reference for the `new_entry` script that creates chronologically organized documentation entries in the shared understanding framework.

**Location**: `./new_entry` in repository root

## Quick Start

The `new_entry` script creates structured markdown entries with automatic date-based organization:

```bash
# Basic usage - creates entry with today's date
./new_entry investigation-findings

# With custom title
./new_entry refactoring-analysis "Refactoring Analysis"

# Open in editor after creation
./new_entry --edit meeting-notes "Meeting Notes"
```

## What is new_entry?

The `new_entry` script is a Python-based tool that:
- Creates chronologically organized documentation entries
- Automatically generates date-based directory structure (YYYY/MM/DD)
- Provides standardized markdown templates
- Integrates with the shared understanding framework
- Enables consistent knowledge capture across topics

## Command-Line Interface

### Basic Syntax

```bash
./new_entry <filename> [title] [options]
```

### Arguments

**Required:**
- `filename` - Name of the entry file (without .md extension, added automatically)

**Optional:**
- `title` - Custom title for the entry (defaults to formatted filename)

**Options:**
- `--edit`, `-e` - Open the created file in your default editor after creation

### Examples

```bash
# Minimal usage
./new_entry investigation
# Creates: entries/2026/02/05/investigation.md
# Title: "Investigation"

# With custom title
./new_entry ftl2-setup "FTL2 Package Setup"
# Creates: entries/2026/02/05/ftl2-setup.md
# Title: "FTL2 Package Setup"

# With .md extension (automatically handled)
./new_entry analysis.md "Analysis Results"
# Creates: entries/2026/02/05/analysis.md
# Title: "Analysis Results"

# Open in editor immediately
./new_entry --edit meeting-notes "Team Meeting Notes"
# Creates entry and opens in $EDITOR (or nano)
```

## Directory Structure

### Automatic Organization

Entries are organized by date in a hierarchical structure:

```
entries/
├── 2026/                    # Year
│   ├── 01/                  # Month (01-12)
│   │   ├── 30/              # Day (01-31)
│   │   │   ├── analysis.md
│   │   │   └── notes.md
│   │   └── 31/
│   │       └── summary.md
│   └── 02/
│       └── 05/
│           ├── investigation.md
│           └── refactoring-plan.md
└── README.md
```

### Benefits of Chronological Organization

1. **Temporal Context**: Clear timeline of understanding evolution
2. **Easy Navigation**: Find entries by date
3. **AI-Friendly**: Helps AI models track information recency
4. **Version History**: Git commits preserve entry evolution
5. **Cross-Topic Support**: Multiple topics can coexist with clear separation

## Entry Template

### Standard Template Structure

Each new entry is created with this template:

```markdown
# Title

**Date:** YYYY-MM-DD
**Time:** HH:MM

## Overview

## Details

## Next Steps

## Related

```

### Template Sections

**Header:**
- Title: Auto-generated from filename or custom title
- Date: Automatic timestamp (YYYY-MM-DD)
- Time: Automatic timestamp (HH:MM)

**Overview:**
- High-level summary of the entry
- 1-3 sentence description
- Purpose and context

**Details:**
- Comprehensive information
- Technical specifics
- Analysis and findings
- Code examples
- Command outputs

**Next Steps:**
- Action items
- Follow-up tasks
- Continuity tracking
- Future investigations

**Related:**
- Links to other entries
- External resource references
- Cross-references
- File paths and line numbers

## Usage Patterns

### Daily Workflow

```bash
# Morning: Create daily notes
./new_entry daily-standup "Daily Standup Notes"

# During work: Document findings
./new_entry bug-investigation "Authentication Bug Investigation"
./new_entry performance-analysis "API Performance Analysis"

# End of day: Capture learnings
./new_entry lessons-learned "Today's Lessons Learned"
```

### Project Workflow

```bash
# Initial analysis
./new_entry initial-analysis "Project Initial Analysis"

# Design documentation
./new_entry architecture-design "Architecture Design"

# Implementation tracking
./new_entry implementation-progress "Implementation Progress"

# Testing and validation
./new_entry test-results "Test Results and Coverage"
```

### Refactoring Workflow

```bash
# Analysis phase
./new_entry codebase-analysis "Codebase Analysis"

# Planning phase
./new_entry refactoring-plan "Refactoring Strategy"

# Implementation phase
./new_entry dataclass-migration "Dataclass Migration"

# Validation phase
./new_entry workflow-validation "Workflow Validation"
```

## File Naming Conventions

### Good Names

Use descriptive, hyphen-separated names:

```bash
./new_entry initial-codebase-analysis
./new_entry ftl2-package-setup
./new_entry workflow-validation
./new_entry meeting-notes-architecture
./new_entry bug-fix-authentication
./new_entry performance-optimization-results
```

### Name Characteristics

- **Descriptive**: Clearly indicate content
- **Lowercase**: Use lowercase letters
- **Hyphens**: Separate words with hyphens (not underscores or spaces)
- **Specific**: Include key topic identifiers
- **Concise**: Keep under 50 characters
- **No dates**: Date is in directory structure

### Avoid

```bash
# Too generic
./new_entry notes
./new_entry stuff

# Too long
./new_entry this-is-a-very-long-name-that-describes-everything-in-detail

# Poor formatting
./new_entry My_Entry
./new_entry "entry with spaces"
```

## Editor Integration

### Default Editor

The script uses your system's default editor:

```bash
# Uses $EDITOR environment variable
export EDITOR=vim
./new_entry --edit notes

# Falls back to nano if $EDITOR not set
./new_entry --edit notes  # Opens in nano
```

### Editor Configuration

```bash
# Set preferred editor in shell config (~/.bashrc, ~/.zshrc)
export EDITOR=vim          # Vim
export EDITOR=nvim         # Neovim
export EDITOR=code         # VS Code
export EDITOR="code -w"    # VS Code (wait for close)
export EDITOR=nano         # Nano (default fallback)
```

## Finding and Searching Entries

### Find by Date

```bash
# All entries from specific date
find entries/2026/02/05 -name "*.md"

# All entries from month
find entries/2026/02 -name "*.md" | sort

# All entries from year
find entries/2026 -name "*.md" | sort
```

### Search Content

```bash
# Search for keyword across all entries
grep -r "refactoring" entries/

# Search with context
grep -r -B 2 -A 2 "dataclass" entries/

# Search in specific date range
grep -r "performance" entries/2026/02/
```

### List Recent Entries

```bash
# Most recently modified entries
find entries -name "*.md" -type f -exec ls -lt {} + | head -10

# Entries from last 7 days
find entries -name "*.md" -type f -mtime -7

# Count entries by date
find entries -type d -depth 3 | sort | uniq -c
```

## Best Practices

### Entry Creation

1. **Create entries while information is fresh** - Don't delay documentation
2. **One topic per entry** - Separate concerns into different files
3. **Use descriptive filenames** - Future you will thank you
4. **Fill out all sections** - Even brief notes in each section help
5. **Cross-reference related entries** - Build knowledge graphs

### Content Guidelines

1. **Overview section**:
   - Write 1-3 sentences summarizing the entry
   - Make it scannable and informative
   - Include purpose and outcome

2. **Details section**:
   - Include code snippets with syntax highlighting
   - Add command outputs and examples
   - Document decisions and rationale
   - Include file paths and line numbers for code references

3. **Next Steps section**:
   - List actionable items
   - Prioritize tasks
   - Include enough context to resume work later
   - Mark completed items with ~~strikethrough~~ or ✓

4. **Related section**:
   - Link to related entries (relative paths)
   - Reference external resources (URLs)
   - Include file paths with line numbers (file.py:123)
   - List related Jira issues, Google Docs, Slack threads

### Cross-Referencing

```markdown
## Related

- entries/2026/02/05/initial-analysis.md - Initial codebase analysis
- /Users/ben/git/faster-than-light/module.py:168 - Core orchestration function
- https://github.com/org/repo/issues/123 - Related GitHub issue
- [Design Doc](https://docs.google.com/document/d/abc123)
```

## Integration with Shared Understanding

### Workflow Integration

The `new_entry` system integrates with the complete shared understanding workflow:

1. **Pre-Meeting**: Create entry for meeting notes
   ```bash
   ./new_entry meeting-ftl-refactor "FTL Refactoring Meeting"
   ```

2. **During Meeting**: Capture notes in entry

3. **Post-Meeting**: Document findings
   ```bash
   ./new_entry post-meeting-analysis "Post-Meeting Analysis"
   ```

4. **Information Gathering**: Use skills to gather context
   ```bash
   # Import Jira issue
   jirahhh view AAP-12345

   # Import Google Doc
   gcmd export "DOC_URL" -o /tmp/

   # Search Slack
   slacker search "topic"

   # Document findings
   ./new_entry information-gathering "Information Gathering Results"
   ```

5. **Synthesis**: Create comprehensive entry

### Multi-Topic Management

Use separate repositories for different topics:

```bash
# Topic 1: faster-than-light-refactor
cd /Users/ben/git/faster-than-light-refactor
./new_entry analysis "Refactoring Analysis"

# Topic 2: another-project
cd /Users/ben/git/another-project
./new_entry investigation "Feature Investigation"
```

Each repository maintains independent entry chronology.

## Technical Details

### Implementation

- **Language**: Python 3
- **Dependencies**: Standard library only (no external deps)
- **File**: `./new_entry` (executable Python script)
- **Template**: Embedded in script (lines 44-57)

### Date Handling

```python
from datetime import datetime

now = datetime.now()
year = now.strftime("%Y")     # 2026
month = now.strftime("%m")    # 02
day = now.strftime("%d")      # 05
```

### Path Construction

```python
from pathlib import Path

base_dir = Path(__file__).parent
entry_dir = base_dir / "entries" / year / month / day
entry_dir.mkdir(parents=True, exist_ok=True)
```

### Existing File Handling

If file exists:
- Prints warning message
- Opens in editor if `--edit` flag used
- Does not overwrite existing content

## Troubleshooting

### Script Not Executable

```bash
# Make script executable
chmod +x new_entry

# Verify
ls -la new_entry
# Should show: -rwxr-xr-x
```

### Editor Not Opening

```bash
# Check EDITOR variable
echo $EDITOR

# Set if not configured
export EDITOR=nano

# Or use specific editor
EDITOR=vim ./new_entry --edit notes
```

### Permission Denied

```bash
# Check directory permissions
ls -la entries/

# Fix if needed
chmod -R u+w entries/
```

### File Already Exists

If you see "File already exists", the entry for today already has that filename. Either:
1. Use a different filename
2. Edit the existing file
3. Use `--edit` to open existing file

## Examples

### Complete Workflow Example

```bash
# Day 1: Initial investigation
./new_entry initial-analysis "Initial Codebase Analysis"
# Fill in: codebase stats, architecture, patterns identified

# Day 2: Planning
./new_entry refactoring-plan "Refactoring Strategy"
# Fill in: approach, priorities, dataclass designs

# Day 3: Setup new package
./new_entry package-setup "FTL2 Package Setup"
# Fill in: structure, tooling, configuration

# Day 4: Validation
./new_entry workflow-validation "Workflow Validation"
# Fill in: test results, coverage, verification

# All entries preserved chronologically
find entries/2026/02 -name "*.md" | sort
# entries/2026/02/05/initial-analysis.md
# entries/2026/02/06/refactoring-plan.md
# entries/2026/02/07/package-setup.md
# entries/2026/02/08/workflow-validation.md
```

### Documentation Reference Example

```bash
# Create entry documenting an API
./new_entry api-design "REST API Design"

# Entry content references code
## Details

The API endpoint is implemented in `src/api/routes.py:45`:

\`\`\`python
@app.route('/api/v1/users', methods=['GET'])
def get_users():
    return jsonify(User.query.all())
\`\`\`

## Related

- src/api/routes.py:45 - User endpoint implementation
- src/models/user.py:12 - User model definition
- tests/test_api.py:78 - API endpoint tests
```

## Tips

1. **Create liberally**: Don't hesitate to create new entries
2. **Separate concerns**: One entry per distinct topic
3. **Cross-reference**: Link related entries in "Related" section
4. **Use git**: Commit entries to preserve history
5. **Search often**: Use grep to find past insights
6. **Review regularly**: Revisit entries to update understanding
7. **Include code references**: Use file:line format for traceability

## Related Skills

- **gcmd**: Import Google Docs content for entries
- **jirahhh**: Import Jira issue context for entries
- **slacker**: Import Slack discussions for entries

---

*The new_entry system is the foundation of the shared understanding framework, enabling systematic knowledge capture and temporal organization of collaborative intelligence.*
