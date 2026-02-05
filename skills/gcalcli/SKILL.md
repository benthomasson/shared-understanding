---
name: gcalcli
description: Google Calendar CLI for viewing agenda, adding events, and reminders
---

# Google Calendar CLI (gcalcli) Skill

Quick reference for using `gcalcli` to work with Google Calendar.

**Repository:** https://github.com/insanum/gcalcli

## Quick Start

Use `uvx` to run directly from the local repo:

```bash
# View today's agenda
uvx --from "/Users/ben/git/gcalcli" gcalcli agenda

# View agenda for specific date range
uvx --from "/Users/ben/git/gcalcli" gcalcli agenda "today" "tomorrow"

# View this week's calendar
uvx --from "/Users/ben/git/gcalcli" gcalcli calw

# View this month's calendar
uvx --from "/Users/ben/git/gcalcli" gcalcli calm

# List available calendars
uvx --from "/Users/ben/git/gcalcli" gcalcli list

# Quick add an event
uvx --from "/Users/ben/git/gcalcli" gcalcli quick "Meeting with Ben tomorrow at 3pm"

# Search for events
uvx --from "/Users/ben/git/gcalcli" gcalcli search "standup"
```

**Tip**: Add an alias to your shell for convenience:
```bash
alias gcalcli='uvx --from "/Users/ben/git/gcalcli" gcalcli'
```

## When to Use This Skill

Use this skill when:
- User asks about today's meetings or agenda
- User wants to see upcoming events
- User asks to add an event to their calendar
- User wants to search for calendar events
- User needs meeting context or preparation
- User asks about their schedule

## Common Commands

### View Agenda

```bash
# Today's agenda
uvx --from "/Users/ben/git/gcalcli" gcalcli agenda

# Agenda for specific range
uvx --from "/Users/ben/git/gcalcli" gcalcli agenda "today" "next week"

# Agenda with event details
uvx --from "/Users/ben/git/gcalcli" gcalcli agenda --detail-all

# Agenda without colors (for piping/parsing)
uvx --from "/Users/ben/git/gcalcli" gcalcli --nocolor agenda
```

### Calendar Views

```bash
# Week view
uvx --from "/Users/ben/git/gcalcli" gcalcli calw

# Month view
uvx --from "/Users/ben/git/gcalcli" gcalcli calm

# Multiple weeks
uvx --from "/Users/ben/git/gcalcli" gcalcli calw 3
```

### Search Events

```bash
# Search for events by text
uvx --from "/Users/ben/git/gcalcli" gcalcli search "standup"

# Search with date range
uvx --from "/Users/ben/git/gcalcli" gcalcli search --start "2026-01-01" "project review"
```

### Add Events

```bash
# Quick add (natural language)
uvx --from "/Users/ben/git/gcalcli" gcalcli quick "Lunch with team Friday at noon"

# Add with details
uvx --from "/Users/ben/git/gcalcli" gcalcli add \
    --title "Team Meeting" \
    --when "tomorrow 2pm" \
    --duration 60 \
    --description "Weekly sync"
```

### List Calendars

```bash
# Show all calendars
uvx --from "/Users/ben/git/gcalcli" gcalcli list
```

### Get Updates

```bash
# Events updated since a datetime
uvx --from "/Users/ben/git/gcalcli" gcalcli updates "2026-02-01"
```

## Workflow Examples

### Daily Meeting Prep

```bash
# Get today's meetings
uvx --from "/Users/ben/git/gcalcli" gcalcli --nocolor agenda "today" "tomorrow" --detail-all

# Output includes: time, title, location, description, attendees
```

### Find Conflicts

```bash
# Check for scheduling conflicts
uvx --from "/Users/ben/git/gcalcli" gcalcli conflicts "meeting"
```

### Meeting Reminders

```bash
# Set up reminder command (for cron)
uvx --from "/Users/ben/git/gcalcli" gcalcli remind
```

## Output Parsing

For scripts, use `--nocolor` and `--tsv` for parseable output:

```bash
uvx --from "/Users/ben/git/gcalcli" gcalcli --nocolor agenda --tsv
```

## Authentication

First-time setup requires OAuth:

1. Set up Google Cloud project with Calendar API enabled
2. Create OAuth credentials
3. Run init with client-id:

```bash
uvx --from "/Users/ben/git/gcalcli" gcalcli --client-id=YOUR_CLIENT_ID.apps.googleusercontent.com init
```

Token is cached at `~/.local/share/gcalcli/oauth`.

## Key Features

- **Agenda views**: Daily, weekly, monthly calendar views
- **Natural language**: Quick add events with natural language parsing
- **Search**: Find events by text across calendars
- **Multiple calendars**: Work with specific calendars by name
- **Reminders**: Execute commands when events are approaching
- **TSV output**: Machine-readable output for scripting

## Integration Ideas

- Daily cron job to create meeting prep entries
- tmux status line showing next event
- Pre-meeting context gathering combining gcalcli + gcmd (meeting notes)

---

*Last updated: 2026-02-05*
