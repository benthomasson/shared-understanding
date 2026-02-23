# How to create a Shared Understanding

A proven framework for collaborative intelligence that combines human insight with AI synthesis to build deeper understanding than either could achieve alone. Through structured documentation, systematic knowledge capture, and multi-platform integration, teams can discover breakthrough solutions and make better decisions faster.

## 📚 Key Resources

📋 **[Complete Framework Summary](docs/summary.md)** - Comprehensive overview with real-world validation and multi-cycle success stories

🚀 **[Getting Started Guide](docs/getting-started.md)** - Step-by-step setup instructions to implement in your organization

## ✨ What Makes This Different

**Collaborative Intelligence**: AI serves as an active stakeholder in knowledge building, not just a documentation tool
- Interactive validation catches errors and fills knowledge gaps
- Multi-platform synthesis reveals unknown relevant information
- Visual analysis includes diagrams and screenshots in understanding

**Proven Results**: Real project validation shows the framework can produce solutions that are:
- Less work to implement than expected
- Superior technical solutions
- Easier for customers to use

**Systematic Knowledge Discovery**: The framework consistently uncovers information unknown to meeting participants through integrated search across Jira, Google Drive, and Slack

## 🔄 Complete Workflow

1. **Pre-Meeting**: Import Jira issue context using skills integration
2. **Meeting**: Natural team discussion with AI transcript capture
3. **Post-Processing**: AI dialogue to validate understanding and correct errors
4. **Knowledge Discovery**: Search across organizational platforms for additional context
5. **Documentation**: Create structured entries with comprehensive synthesis
6. **Organizational Sharing**: Export to Google Docs for broader collaboration
7. **Iterative Refinement**: Multiple cycles compound understanding and reveal emergent solutions

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

## Repository Structure

```
shared-understanding/
├── README.md           # This file - framework overview
├── CLAUDE.md          # Guidance for Claude Code AI assistant
├── new_entry*         # Entry creation script
├── docs/              # Living documentation
│   ├── summary.md     # Complete framework summary
│   └── getting-started.md  # Setup and implementation guide
├── entries/           # Chronological documentation
│   ├── README.md      # Entry system documentation  
│   └── YYYY/MM/DD/    # Date-organized entries
└── skills/            # External tool integrations
    ├── gcmd/          # Google Drive CLI integration
    ├── jirahhh/       # Jira CLI integration
    └── slacker/       # Slack CLI integration
```

## Real-World Impact

**Multi-Cycle Success**: One project implementation achieved a breakthrough solution through multiple cycles of the framework that was less work to implement, technically superior, and easier for customers to use than any initially proposed approach.

**Key Success Factors**:
- **AI synthesis** across multiple information cycles
- **Slack's exceptional search** uncovering organizational knowledge  
- **Systematic discovery** of information unknown to meeting participants
- **Iterative refinement** revealing emergent solutions

## Technology Integration

### External Skills (Zero Installation)
All integrations use `uvx` for installation-free execution:

```bash
# Google Drive integration
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "DOC_URL" -o /tmp/

# Jira integration  
uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh search "keywords"

# Slack integration
uvx --from "git+https://github.com/shanemcd/slacker" slacker search "topic"
```

### Memory Persistence
- **Conversation Archival**: Use [`claude-projects`](https://github.com/benthomasson/claude-projects) to convert AI conversations to searchable markdown
- **Chronological Structure**: Helps AI overcome temporal confusion in attention mechanisms
- **Cross-Platform Synthesis**: Integrates Jira issues, meeting transcripts, Google Docs, and Slack conversations

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

## Why This Framework Works

**Overcomes Human Limitations**: Addresses short-term memory constraints and the tendency for familiarity to masquerade as understanding (Kahneman's System 1 vs System 2 thinking)

**Solves AI Constraints**: Provides external memory, temporal context, and structured input to overcome attention mechanism limitations and probabilistic drift

**Leverages Organizational Memory**: Slack search excellence combined with AI synthesis creates comprehensive knowledge discovery beyond manual capability

**Generates Emergent Solutions**: Multiple cycles compound understanding, leading to breakthrough insights not visible from initial perspectives

---

**Ready to start?** Check out the **[Getting Started Guide](docs/getting-started.md)** to implement this framework in your organization.
