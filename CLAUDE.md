# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Overview

This is a framework for building shared understanding of problems or topics within teams through structured documentation and external tool integration. The codebase facilitates knowledge capture, organization, and collaboration using a chronological entry system and modular skills for external services.

## Core Architecture

### Entry Management System
- Chronologically organized documentation using `entries/YYYY/MM/DD/` structure
- Automated entry creation via `./new_entry <filename> [title]` Python script
- Standardized markdown template with Overview, Details, Next Steps, and Related sections
- Cross-referencing support for linking related entries and external resources

### Skills System
- Modular integration documentation in `/.claude/skills/` directory
- Three main integrations: gcmd (Google Drive), jirahhh (Jira), slacker (Slack)
- Each skill uses `uvx` for installation-free execution of external CLI tools
- Skills are self-contained with comprehensive SKILL.md documentation

## Common Development Commands

### Entry Management
```bash
# Create new entry with automatic date structure
./new_entry investigation-findings "Investigation Findings"

# Create entry and open in editor
./new_entry --edit meeting-notes "Meeting Notes"

# Find entries by date
find entries/2026/01/30 -name "*.md"

# Search across all entries
grep -r "keyword" entries/

# List entries from current month
find entries/2026/01 -name "*.md" | sort
```

### External Tool Integration (Skills)
```bash
# Google Drive export (gcmd skill)
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "GOOGLE_DRIVE_URL" -o /tmp/

# Jira issue creation (jirahhh skill)
uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh create --env prod --project AAP --type Task --summary "Title" --description "Description"

# Slack reminder creation (slacker skill)
uvx --from "git+https://github.com/shanemcd/slacker" slacker reminder create "15 minutes" "Follow up on discussion"
```

## Development Workflow

1. **Documentation Creation**: Use `./new_entry` to maintain consistent chronological organization
2. **Topic Separation**: Create separate entries for different investigation areas
3. **External Data Import**: Leverage skills to import content from Google Drive, Jira, and Slack
4. **Cross-referencing**: Link related entries in "Related" sections for knowledge connectivity
5. **Progress Tracking**: Use "Next Steps" sections to maintain continuity across sessions

## Technology Stack

- **Core Language**: Python 3 (for new_entry script)
- **Documentation Format**: Markdown with standardized templates
- **External Tools**: CLI tools managed via uvx (no local installation required)
- **File Organization**: Date-based hierarchical structure
- **Dependencies**: None for core functionality

## Configuration Notes

- No central configuration files - the repository is self-contained
- External skills manage their own configuration:
  - gcmd: OAuth credentials in `~/.config/gcmd/credentials.json`
  - jirahhh: API tokens in `~/.config/jirahhh/config.yaml`
  - slacker: Browser session credentials in `~/.config/slacker/credentials`

## Entry Template Structure

When creating entries, follow the standardized template:
- **Date/Time**: Automatic timestamp
- **Overview**: High-level summary
- **Details**: Comprehensive information
- **Next Steps**: Action items for continuity
- **Related**: Links to related entries or external resources

## Skills Integration Patterns

- Use gcmd to export Google Docs as markdown for local analysis
- Use jirahhh with wiki markup for issue descriptions (configured in global CLAUDE.md)
- Use slacker for Slack workspace interaction and message management
- All skills support both stage and production environments where applicable