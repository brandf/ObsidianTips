# AGENTS.md

This document is specifically for AI agents to understand the ObsidianTips project structure, conventions, and how to effectively help improve Obsidian notes.

## Project Overview

**Purpose:** This is a digital garden project that publishes Obsidian notes to the web using Quartz 4. The project serves as both:
1. A collection of tips and best practices for using Obsidian
2. A template/reference for publishing Obsidian vaults to GitHub Pages

**Tech Stack:**
- **Obsidian** - Markdown-based note-taking application
- **Quartz 4** - Static site generator for Obsidian vaults
- **GitHub Pages** - Static site hosting
- **Node.js >= 20** - Runtime environment
- **PowerShell** - Build and automation scripts (Windows-first)

**Live Site:** https://brandf.github.io/ObsidianTips/

## Repository Structure

```
c:\open\GitHub\ObsidianTips/
├── obsidian/                          # The Obsidian vault (main content)
│   ├── index.md                       # Homepage
│   ├── *.md                          # Individual notes
│   ├── *.png                         # Images and screenshots
│   ├── *.canvas                      # Canvas files (spatial organization)
│   └── 🚧 Projects/                  # Symlinked external projects (ignored by git)
├── scripts/                           # PowerShell automation scripts
│   ├── setup.ps1                     # Interactive site configuration
│   ├── build-site.ps1                # Build static site
│   ├── serve-site.ps1                # Local development server
│   ├── master-vault.ps1              # Multi-repo vault management
│   └── master-vault.txt              # List of linked projects
├── .github/workflows/deploy.yml       # GitHub Actions auto-deployment
├── quartz.config.ts                   # Quartz configuration
├── package.json                       # Node.js dependencies
└── README.md                          # User-facing documentation
```

## Key Concepts

### Obsidian Vault
The `obsidian/` folder is an Obsidian vault containing markdown files. Each `.md` file is a note that can:
- Link to other notes using wikilinks: `[[Note Name]]`
- Embed notes: `![[Note Name]]`
- Embed images: `![[image.png]]`
- Have YAML frontmatter for metadata
- Contain standard markdown, code blocks, tables, etc.

### Canvas First Workflow
The author uses **Canvas as the primary editor** for spatial organization:
- Each project should have a `.canvas` file at the root
- Canvas embeds markdown notes for content
- Markdown files remain independently useful
- Canvas provides an optional spatial view

### Master Vault Pattern
The project supports linking multiple repository vaults together:
- Each project has its own `obsidian/` folder
- `master-vault.ps1` creates symlinks to combine them
- Symlinks go into `obsidian/🚧 Projects/<ProjectName>`
- This allows one published site to aggregate multiple project vaults

### Publishing Flow
1. Notes are written in `obsidian/` folder
2. Quartz builds static site from markdown files
3. GitHub Actions auto-deploys to GitHub Pages on push
4. Site is live at `https://brandf.github.io/ObsidianTips/`

## File Patterns & Conventions

### Markdown Files
- **Location:** `obsidian/*.md`
- **Format:** Standard markdown with YAML frontmatter
- **Naming:** Human-readable with spaces (e.g., `How I Use Obsidian.md`)
- **Links:** Use Obsidian wikilinks `[[Page Name]]` not markdown links
- **Images:** Use Obsidian embed syntax `![[image.png]]`
- **Emojis:** Used extensively in headings and lists for visual organization

### Frontmatter
```yaml
---
title: Page Title
---
```

### Note Organization
Current notes are organized thematically:
- **Why Obsidian.md** - Philosophy and benefits
- **How I Use Obsidian.md** - Personal workflow (index/hub page)
- **Best Obsidian Plugins.md** - Plugin recommendations
- **Canvas First Workflow.md** - Spatial organization approach
- **Using AI with Obsidian.md** - AI integration patterns
- **Using Obsidian with GitHub.md** - Version control workflow
- **My Personal Vault.md** - Vault structure examples
- **One Vault to Rule Them All.md** - Master vault concept
- **Exporting to the Web.md** - Publishing workflow
- **How Obsidian Works.md** - Technical details
- **AboutObsidian.md** - General information

### Ignored Patterns
From `quartz.config.ts`:
```typescript
ignorePatterns: [
  "private",
  ".obsidian",
  "**/📄 Templates/**",
]
```

## How to Help Improve Notes

### Content Quality

**Expand and Enhance:**
- Turn outlines/bullet points into full paragraphs
- Add examples and use cases
- Improve clarity and flow
- Add missing context or explanations
- Expand on concepts that are too brief

**Structure Improvements:**
- Add table of contents for long notes
- Break up walls of text with headers
- Use lists, tables, and visual formatting
- Add "See Also" or related links sections
- Create better hierarchy with H2, H3 headings

**Consistency:**
- Maintain emoji usage patterns (already established)
- Use wikilinks `[[Link]]` not markdown links
- Keep frontmatter consistent
- Follow existing tone (helpful, practical, tutorial-like)

### Linking and Relationships

**Create Connections:**
- Add wikilinks between related notes
- Suggest backlinks where concepts overlap
- Create MOCs (Maps of Content) for topic areas
- Link to external resources where helpful

**Link Patterns:**
- Use descriptive link text: `[[Best Obsidian Plugins]]` ✅
- Not generic: `[[click here]]` ❌
- Embed related notes where appropriate

### Organization

**Folder Structure:**
Currently flat. Consider suggesting:
- Topic-based folders if needed
- But flat is OK for small vaults
- Don't over-organize early

**Index Pages:**
- `How I Use Obsidian.md` serves as main hub
- Could create more hub/index pages for subtopics
- Canvas files can also serve as visual indexes

### Technical Accuracy

**Verify:**
- Plugin names and links are correct
- Obsidian features are described accurately
- External links work
- Code examples are valid
- Quartz-specific features are properly documented

### AI-Specific Assistance

Since this vault is about Obsidian tips and includes AI integration:

**Meta Improvements:**
- The notes should exemplify best practices they describe
- `Using AI with Obsidian.md` should showcase good AI workflows
- Notes should demonstrate the principles they teach

**AI Use Cases to Implement:**
- Generate summaries of complex topics
- Create comparison tables (e.g., plugin features)
- Suggest tags based on content
- Find gaps in coverage
- Generate templates for new note types

## Common Tasks

### Adding New Notes

1. Create `.md` file in `obsidian/`
2. Add YAML frontmatter with title
3. Use wikilinks to related notes
4. Consider adding to hub pages like `How I Use Obsidian.md`
5. Add emojis for visual interest (match existing style)
6. Include images with `![[image.png]]` if helpful

### Editing Existing Notes

1. Read the full note first
2. Maintain existing voice and style
3. Add, don't remove (unless fixing errors)
4. Preserve all wikilinks
5. Keep emoji patterns consistent
6. Test that wikilinks work (target files exist)

### Adding Images

1. Place image files in `obsidian/` folder
2. Reference with `![[filename.png]]`
3. Use descriptive filenames
4. Common image types: screenshots, diagrams, icons

### Working with Canvas

1. Canvas files are JSON: `*.canvas`
2. They embed markdown notes for content
3. Don't edit canvas JSON directly unless necessary
4. Focus on the markdown files that canvas references

### Testing Changes Locally

```bash
# Build and serve locally
npm run serve

# Visit http://localhost:8080
# Check that:
# - Wikilinks work
# - Images display
# - Formatting looks correct
# - No broken links
```

## Configuration Files

### quartz.config.ts
- **Purpose:** Quartz static site generator configuration
- **Key settings:**
  - `pageTitle`: "Obsidian Tips"
  - `baseUrl`: "brandf.github.io/ObsidianTips"
  - `ignorePatterns`: What not to publish
  - `theme`: Colors, fonts, appearance
  - `plugins`: Content processing pipeline

**Don't modify unless:** User explicitly requests configuration changes

### package.json
- **Purpose:** Node.js project configuration
- **Key scripts:**
  - `npm run build` → `scripts/build-site.ps1`
  - `npm run serve` → `scripts/serve-site.ps1`

**Don't modify unless:** Adding new scripts or dependencies

## Workflow Scripts

### setup.ps1
Interactive configuration wizard for initial setup. Don't modify.

### build-site.ps1
Builds the Quartz static site. Review if build issues occur.

### serve-site.ps1
Runs local development server. Review if serving issues occur.

### master-vault.ps1
Manages symlinks for multi-repo vault pattern:
```powershell
# Add a project vault
.\scripts\master-vault.ps1 -Add ProjectName

# Sync all project symlinks
.\scripts\master-vault.ps1 -Sync

# List projects
.\scripts\master-vault.ps1 -List

# Remove a project
.\scripts\master-vault.ps1 -Remove ProjectName
```

**Important:** Projects are symlinked to `obsidian/🚧 Projects/` which is gitignored

## Best Practices for AI Agents

### DO:
- ✅ Read existing notes thoroughly before suggesting changes
- ✅ Maintain consistent style, tone, and formatting
- ✅ Use wikilinks `[[Page]]` for internal links
- ✅ Add emojis matching existing patterns
- ✅ Suggest concrete improvements with examples
- ✅ Create new notes when gaps are identified
- ✅ Link related concepts together
- ✅ Validate that linked notes exist
- ✅ Keep notes focused and practical
- ✅ Add frontmatter to new notes

### DON'T:
- ❌ Break existing wikilinks
- ❌ Remove content without good reason
- ❌ Use markdown links `[text](url)` for internal pages
- ❌ Over-complicate simple notes
- ❌ Add private/sensitive information
- ❌ Modify configuration files without explicit request
- ❌ Create deeply nested folder structures prematurely
- ❌ Remove emojis or visual formatting
- ❌ Change the established voice/tone
- ❌ Add notes that don't fit the Obsidian tips theme

### Content Quality Standards:
- **Clear:** Easy to understand for Obsidian users
- **Practical:** Actionable tips, not just theory
- **Example-rich:** Show, don't just tell
- **Well-linked:** Connected to related notes
- **Scannable:** Headers, lists, formatting
- **Accurate:** Technically correct information

## Common Improvement Patterns

### Pattern 1: Expand Stub Notes
If a note is too brief:
1. Add introduction paragraph
2. Expand bullet points into sections
3. Add examples and use cases
4. Include screenshots if helpful
5. Link to related concepts

### Pattern 2: Add Cross-References
When notes discuss related topics:
1. Add "See Also" section at bottom
2. Add inline wikilinks where concepts connect
3. Consider creating an MOC (Map of Content)
4. Update hub pages to include new connections

### Pattern 3: Create Missing Notes
When wikilinks point to non-existent notes:
1. Check if note should exist
2. Create with appropriate frontmatter
3. Add core content based on context
4. Link back to referring notes

### Pattern 4: Improve Structure
For long or dense notes:
1. Add table of contents
2. Use clearer heading hierarchy
3. Break into subsections
4. Add visual breaks (lists, quotes, etc.)
5. Consider splitting into multiple notes

### Pattern 5: Add Practical Examples
For conceptual notes:
1. Add "Example" sections
2. Include code blocks or commands
3. Show before/after comparisons
4. Add screenshots demonstrating concepts
5. Link to real-world use cases

## Questions to Ask When Reviewing

1. **Completeness:** Does this note fully cover the topic?
2. **Clarity:** Would an Obsidian user understand this?
3. **Links:** Are related notes linked?
4. **Examples:** Are there practical examples?
5. **Structure:** Is it easy to scan and navigate?
6. **Accuracy:** Is the information correct?
7. **Relevance:** Does it fit the "Obsidian Tips" theme?
8. **Style:** Does it match other notes' tone?

## Special Considerations

### Windows Environment
- File paths use backslashes: `c:\open\GitHub\ObsidianTips`
- Scripts are PowerShell (`.ps1`)
- Line endings are CRLF
- Case-insensitive filesystem

### Git Integration
- Notes are version controlled
- Changes are pushed to trigger deployment
- GitHub Actions handles build/deploy
- Symlinked projects are gitignored

### Publishing Constraints
- Only public notes are published
- Private notes go in folders matching `ignorePatterns`
- Images must be in the vault to publish
- Wikilinks must resolve to existing notes

## Getting Started as an Agent

When first helping with this project:

1. **Survey the vault:** Read `index.md` and main hub pages
2. **Understand structure:** Check existing note organization
3. **Note patterns:** Observe linking, formatting, emoji usage
4. **Identify gaps:** Find incomplete or stub notes
5. **Ask user:** What specific help do they need?

### Suggested First Tasks:
- Review notes for completeness
- Suggest missing cross-links
- Expand stub notes
- Create comparison tables
- Add examples to conceptual notes
- Generate summaries or MOCs
- Check for broken wikilinks
- Suggest new notes for gaps

## Technical Reference

### Quartz Features Available:
- ✅ Wikilinks with `[[brackets]]`
- ✅ Backlinks (automatic)
- ✅ Graph view (automatic)
- ✅ Search (automatic)
- ✅ Table of contents
- ✅ Syntax highlighting for code
- ✅ LaTeX math support
- ✅ Obsidian flavored markdown
- ✅ Popovers on link hover
- ✅ Dark/light themes

### Markdown Extensions:
- Standard markdown
- Obsidian wikilinks
- Obsidian embeds
- GitHub flavored markdown
- Code blocks with syntax highlighting
- Tables
- Footnotes
- Task lists

## Troubleshooting

### If wikilinks break:
- Verify target note exists
- Check filename exactly matches link
- Ensure target not in ignored patterns
- Use exact filename with spaces

### If images don't show:
- Verify image is in `obsidian/` folder
- Use `![[image.png]]` syntax
- Check filename exactly matches
- Ensure image not gitignored

### If builds fail:
- Check for invalid markdown
- Verify all wikilinks resolve
- Look for special characters in frontmatter
- Check Node.js version >= 20

## Summary

This project is a digital garden focused on Obsidian tips, published via Quartz to GitHub Pages. As an AI agent, your role is to help improve note quality, create connections, expand content, and maintain consistency while respecting established patterns and conventions. Focus on making notes more complete, practical, and well-linked while preserving the author's voice and organizational approach.
