# Getting Started with Shared Understanding

This guide will help you set up your own shared understanding repository for your team or project.

## Quick Setup

### 1. Fork and Clone the Repository

```bash
# Fork this repository on GitHub, then clone your fork
git clone https://github.com/YOUR-USERNAME/shared-understanding.git
cd shared-understanding

# Set up your own remote
git remote rename origin upstream
git remote add origin https://github.com/YOUR-USERNAME/shared-understanding.git
```

### 2. Clear Example Content

Remove the existing entries while keeping the structure:

```bash
# Remove example entries but keep the directory structure
rm -rf entries/2026/
mkdir -p entries/

# Optional: Clear the example summary if you want to start fresh
# rm docs/summary.md
```

### 3. Initialize for Your Project

Update the README and docs for your specific use case:

```bash
# Edit README.md to reflect your project
# Update docs/summary.md with your topic
# Modify CLAUDE.md if needed for your specific context
```

### 4. Create Your First Entry

```bash
# Make the new_entry script executable
chmod +x new_entry

# Create your first entry
./new_entry project-kickoff "Project Kickoff Discussion"
```

## Setting Up External Integrations

### Prerequisites

Install `uvx` for running external tools without local installation:

```bash
# Install uvx (if not already installed)
curl -LsSf https://astral.sh/uv/install.sh | sh
```

### Configure Skills

#### 1. Jira Integration (jirahhh)

```bash
# Test the integration
uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh --help

# Set up configuration (follow the prompts)
uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh configure
```

#### 2. Google Drive Integration (gcmd)

```bash
# Test the integration
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd --help

# Set up OAuth credentials (follow the authentication flow)
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd auth
```

#### 3. Slack Integration (slacker)

```bash
# Test the integration
uvx --from "git+https://github.com/shanemcd/slacker" slacker --help

# Set up credentials (follow the setup instructions)
uvx --from "git+https://github.com/shanemcd/slacker" slacker configure
```

## Workflow Setup

### 1. Meeting Preparation

Before your first meeting:

1. Create a Jira issue for the topic you'll discuss
2. Import the issue context:
   ```bash
   # Example: Import a specific Jira issue
   uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh show PROJ-123
   ```

### 2. Post-Meeting Processing

After your meeting:

1. **Import meeting notes:**
   ```bash
   # Find and export Google Meet notes
   uvx --from "git+https://github.com/shanemcd/gcmd" gcmd list "meeting notes"
   uvx --from "git+https://github.com/shanemcd/gcmd" gcmd export "DOCUMENT_URL" -o /tmp/
   ```

2. **Gather additional context:**
   ```bash
   # Search for related Jira issues
   uvx --from "git+https://github.com/shanemcd/jirahhh" jirahhh search "relevant keywords"
   
   # Find related Slack conversations
   uvx --from "git+https://github.com/shanemcd/slacker" slacker search "topic keywords"
   ```

3. **Create structured entry:**
   ```bash
   ./new_entry meeting-analysis "Meeting Analysis and Next Steps"
   ```

### 3. Documentation Updates

Keep your living documents current:

```bash
# Update your project summary as understanding evolves
# Edit docs/summary.md with new insights
# Cross-reference entries in the "Related" sections
```

### 4. Share with Your Organization

Once you have a solid summary document:

1. **Import to Google Docs:**
   - Copy the contents of `docs/summary.md`
   - Create a new Google Doc
   - Use "Edit > Paste special > Paste from markdown" to import with proper formatting

2. **Enable collaboration:**
   - Share the Google Doc with relevant team members and stakeholders
   - Set appropriate permissions (view/comment/edit based on your needs)
   - Invite feedback and additional perspectives

3. **Maintain the feedback loop:**
   - Incorporate Google Doc comments and edits back into your markdown files
   - Update your local repository with new insights from broader collaboration
   - Create new entries for significant discoveries from organizational feedback

## Customization

### Adapting for Your Domain

1. **Update CLAUDE.md** with domain-specific context:
   - Replace software development examples with your field
   - Add relevant tools and workflows
   - Include domain-specific terminology

2. **Modify entry templates** in `new_entry` script:
   - Add sections relevant to your work
   - Change the template structure if needed
   - Include domain-specific metadata

3. **Customize skills integration:**
   - Add other external tools relevant to your domain
   - Create new skill definitions in the `skills/` directory
   - Document your specific integration patterns

### Team-Specific Setup

1. **Establish conventions:**
   - Entry naming patterns for your project
   - Cross-referencing standards
   - Review cycles for living documents

2. **Configure tools:**
   - Set up shared Jira projects
   - Establish Google Drive folder structure
   - Create relevant Slack channels

3. **Training:**
   - Share this repository with team members
   - Walk through the workflow together
   - Practice with a sample topic

## Best Practices

### Entry Creation
- Create entries while information is fresh in memory
- Use descriptive filenames that will make sense months later
- Always fill out the "Related" section to build knowledge graphs
- Include screenshots of diagrams and visual information

### Information Gathering
- Search broadly across all platforms (Jira, Google Drive, Slack)
- Validate AI understanding through dialogue
- Correct transcript errors early in the process
- Look for information unknown to meeting participants

### Documentation Maintenance
- Update `docs/summary.md` as understanding evolves
- Review and refine entries periodically
- Use git history to track how understanding changes over time
- Cross-reference related entries to build knowledge connectivity

### Organizational Sharing
- Import summary documents to Google Docs for broader collaboration
- Use "Paste from markdown" to preserve formatting and structure
- Enable commenting and editing to gather diverse perspectives
- Maintain feedback loops between Google Docs and your repository
- Create new entries based on organizational feedback and discoveries

### Collaborative Intelligence
- Treat AI as a collaborative partner, not just a tool
- Probe AI understanding through questions and dialogue
- Leverage AI's ability to synthesize across multiple information sources
- Use AI for visual analysis of diagrams and screenshots

## Troubleshooting

### Common Issues

**New entry script not executable:**
```bash
chmod +x new_entry
```

**External tools not working:**
```bash
# Ensure uvx is installed and in your PATH
uvx --version

# Test individual tools
uvx --from "git+https://github.com/shanemcd/gcmd" gcmd --help
```

**Missing directories:**
```bash
# Create the basic structure if missing
mkdir -p entries docs skills
```

### Getting Help

- Check the individual tool repositories for specific integration issues
- Review the `skills/` directory for tool-specific documentation
- Use the entry system to document your own troubleshooting discoveries

## Next Steps

Once you have your basic setup working:

1. **Run through a complete workflow** with a real topic
2. **Establish team conventions** for your specific use case
3. **Document your learnings** using the entry system
4. **Iterate and improve** based on what works for your team

The shared understanding framework will evolve as you use it - that's the point! Document your discoveries and improvements as you go.