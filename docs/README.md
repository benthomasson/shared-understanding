# Documentation

This directory contains documentation artifacts for the shared understanding framework.

## Files

| File | Purpose |
|------|---------|
| `summary.md` | Comprehensive framework overview |
| `getting-started.md` | Setup and onboarding guide |
| `presentation.md` | Speaker script for 15-minute presentation |
| `slides.md` | Slide deck in markdown format |
| `slides.pptx` | Generated PowerPoint presentation |
| `podcast.md` | 20-25 minute podcast script |
| `diagrams.md` | Mermaid workflow diagrams |
| `people.md` | Template for tracking topic participants |

## Creating Presentations

### Workflow

1. **Generate markdown slides** - Have Claude create `slides.md` from content
2. **Edit slides** - Review and refine the markdown
3. **Convert to PowerPoint** - Run pandoc:
   ```bash
   pandoc slides.md -o slides.pptx
   ```
4. **Import to Google Slides** - Upload the .pptx file
5. **Beautify per slide** - Use `Slide > Beautify this slide` (no prompt)

### Tips

- Keep content per slide minimal to avoid pandoc splitting across slides
- Put trailing text after tables into table rows to keep them together
- Use `:::notes` blocks for speaker notes
- Beautify without a prompt produces cleaner results than with a prompt

## Creating Podcasts

Have Claude generate a conversational interview script in `podcast.md`:

- Define host and guest personas
- Structure into timed segments (intro, problem, solution, results, outro)
- Include natural dialogue with back-and-forth
- Add production notes for timing and key messaging

## Creating Diagrams

Use Claude to generate Mermaid diagrams in `diagrams.md`:

- Workflow diagrams (flowchart)
- Data flow diagrams
- Sequence diagrams
- Architecture diagrams

Mermaid renders in GitHub, VS Code, and many markdown viewers.

## Tracking Participants

Use `people.md` as a template to track who is working on a shared understanding topic:

- Core participants (humans and AI)
- Roles and contributions
- Contact information
