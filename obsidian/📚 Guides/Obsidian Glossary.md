# Obsidian Glossary

A comprehensive reference of terms and concepts used in [[AboutObsidian|Obsidian]] and throughout this digital garden. Perfect for beginners or as a quick reference.

## Core Concepts

### Vault
A **vault** is a folder on your computer containing your markdown notes. See [[How Obsidian Works#The Vault|How Obsidian Works]] for details.

- Just a regular folder with `.md` files
- Contains a hidden `.obsidian/` folder for settings
- Can have any name and live anywhere on your system
- You can have multiple vaults for different purposes
- Example: `Documents/MyNotes/` is a vault if opened in Obsidian

**Related:** [[My Personal Vault|Personal vault patterns]], [[One Vault to Rule Them All|master vault]]

### Note
A **note** is a single markdown file (`.md`) in your vault.

- Contains text, links, images, etc.
- Can be edited in Obsidian or any text editor
- Stored as plain text with markdown formatting
- Named with the file name (e.g., `My Note.md`)
- Can be organized in folders or kept flat

**Related:** [[Getting Started with Obsidian#Step 4 Create Your First Note|Creating notes]]

### Markdown
**Markdown** is a lightweight markup language for formatting text using plain characters.

Common syntax:
- `# Heading` - Creates headings
- `**bold**` - Bold text
- `*italic*` - Italic text
- `[link](url)` - External links
- `![image](path)` - Images
- `- item` - Bullet lists

**Related:** [[Getting Started with Obsidian#Step 5 Learn Basic Markdown|Markdown basics]], [[How Obsidian Works|plain markdown files]]

## Linking & Connections

### Wikilink
A **wikilink** is Obsidian's internal linking format using double brackets: `[[Note Name]]`

- Links to other notes in your vault
- Creates bidirectional connections
- Can link to specific sections: `[[Note#Heading]]`
- Can use aliases: `[[Note|Display Text]]`
- Red/gray color indicates note doesn't exist yet

**Related:** [[How Obsidian Works - Details#Links|How links work]]

### Backlink
A **backlink** is an automatic reverse reference showing which notes link to the current note.

- Appears in right sidebar under "Backlinks"
- Updates automatically when links are created/removed
- Enables bidirectional navigation
- Core feature that makes Obsidian powerful
- No manual maintenance required

**Related:** [[How Obsidian Works - Details#Bidirectional Linking|Bidirectional linking]]

### Embed
An **embed** displays the content of another note or file inline using `![[Note]]`

- `![[Another Note]]` - Embeds entire note
- `![[Note#Section]]` - Embeds specific section
- `![[image.png]]` - Embeds image
- Content is live - edits appear everywhere it's embedded
- Used heavily in [[Canvas First Workflow|canvas]]

**Related:** [[How Obsidian Works - Details#Link Variations|Link variations]]

### MOC (Map of Content)
A **MOC** is an index note that links to related notes about a topic.

- Acts as a hub for a subject area
- Contains organized links to topic notes
- Helps navigate large vaults
- Can be hierarchical (MOCs linking to MOCs)
- Alternative to strict folder hierarchies

Example:
```markdown
# Web Development MOC

## Frontend
- [[HTML Basics]]
- [[CSS Layouts]]
- [[JavaScript]]

## Backend
- [[Node.js]]
- [[Databases]]
```

**Related:** [[Note-Taking Methodologies|Note-taking methodologies]]

## Visual Features

### Graph View
The **graph view** visualizes your vault as a network of connected notes.

- Each note is a node (dot)
- Each wikilink is an edge (line)
- Interactive - click nodes to open notes
- Can filter and customize appearance
- Reveals patterns and clusters

**Related:** [[How Obsidian Works - Details#Graph|Graph details]]

### Canvas
**Canvas** is an infinite spatial workspace for arranging notes, images, and text cards visually.

- `.canvas` files contain the layout
- Embeds actual markdown notes
- Supports arrows, grouping, colors
- Good for brainstorming and visual organization
- Layout only visible in Obsidian (not published)

**Related:** [[Canvas First Workflow|Canvas workflow]], [[How Obsidian Works - Details#Canvas|Canvas details]]

### Live Preview
**Live Preview** is an editing mode that shows markdown formatting as you type.

- Headings appear styled while editing
- Links are clickable in edit mode
- Images display inline
- Combines editing and reading views
- Can switch to Source mode to see raw markdown

**Related:** [[How Obsidian Works|Obsidian as markdown editor]]

### Source Mode
**Source mode** shows the raw markdown syntax of your note.

- See exactly what's stored in the file
- Edit markdown syntax directly
- Useful for complex formatting
- Switch back to Live Preview for visual editing
- Toggle with button in top-right

**Related:** [[How Obsidian Works|Plain markdown files]]

## Organization

### Folder
A **folder** is a directory containing notes within your vault.

- Organizes notes hierarchically
- Can be nested (folders within folders)
- Optional - flat structure is fine
- Visible in file explorer sidebar
- Standard filesystem folders

**Related:** [[Getting Started with Obsidian#Step 10 Organize Your Notes|Organization strategies]]

### Tag
A **tag** is a keyword marker added to notes using `#tagname`

- Cross-cutting categorization
- Can be nested: `#work/project`
- Searchable and filterable
- Appears in tag pane (right sidebar)
- Multiple tags per note

Example:
```markdown
#project #work #important
```

**Related:** [[Note-Taking Methodologies|Note organization methods]]

### Frontmatter (YAML)
**Frontmatter** is metadata at the top of a note enclosed in `---`

```markdown
---
title: My Note
tags: [work, important]
date: 2024-10-28
---
```

- Must be at very top of file
- Uses YAML syntax
- Contains note properties/metadata
- Can be queried with Dataview
- Used by themes and plugins

**Related:** [[Dataview Guide|Dataview queries]]

### Daily Note
A **daily note** is a note created for each day, typically named by date.

- Usually `YYYY-MM-DD.md` format
- Created automatically with Daily Notes plugin
- Used for journaling, logging, task tracking
- Creates chronological thread through vault
- Links back to other notes preserve timeline

**Related:** [[Daily Notes Workflow|Complete daily notes guide]]

### Template
A **template** is a reusable note structure that can be inserted into new notes.

- Stored in designated templates folder
- Can include dynamic dates: `{{date}}`
- Inserted via Templates plugin
- Good for daily notes, meeting notes, etc.
- Ensures consistency

**Related:** [[Daily Notes Workflow#Using Templates|Daily note templates]], [[Templates and Automation|Templates guide]]

## Technical Terms

### Plugin
A **plugin** is an extension that adds functionality to Obsidian.

**Core Plugins:**
- Built-in, shipped with Obsidian
- Can be enabled/disabled
- Examples: Daily notes, Templates, Quick switcher

**Community Plugins:**
- Created by third-party developers
- Must be installed from community list
- Thousands available
- Examples: Calendar, Dataview, Excalidraw

**Related:** [[How Obsidian Works - Details#Plugins|Plugin ecosystem]], [[Best Obsidian Plugins|Plugin recommendations]]

### Hotkey
A **hotkey** (or keyboard shortcut) triggers a command without using menus.

- Customizable in Settings → Hotkeys
- Common examples:
  - `Ctrl/Cmd + N` - New note
  - `Ctrl/Cmd + O` - Quick switcher
  - `Ctrl/Cmd + P` - Command palette
- Can assign to any command or plugin action

**Related:** [[Getting Started with Obsidian#Step 3 Understanding the Interface|Interface navigation]]

### Command Palette
The **command palette** is a searchable list of all available commands.

- Open with `Ctrl/Cmd + P`
- Fuzzy search for any action
- Shows hotkeys for commands
- Access any feature without remembering shortcuts
- Most powerful navigation tool

**Related:** [[Getting Started with Obsidian#Step 3 Understanding the Interface|Interface basics]]

### Quick Switcher
The **quick switcher** lets you jump to any note by typing part of its name.

- Open with `Ctrl/Cmd + O`
- Fuzzy search matches
- Press Enter to open note
- Fast navigation method
- Works across entire vault

**Related:** [[Getting Started with Obsidian#Step 3 Understanding the Interface|Navigation tools]]

### Metadata
**Metadata** is structured data about a note (title, tags, dates, custom fields).

- Can be in frontmatter (YAML)
- Or inline: `key:: value`
- Queryable with Dataview
- Used by plugins and themes
- Helps organize and filter notes

**Related:** [[Dataview Guide|Querying metadata]], [[Frontmatter (YAML)|Frontmatter]]

### Properties
**Properties** are the new name for frontmatter fields in Obsidian 1.4+.

- Same as frontmatter/YAML
- New UI for editing
- Type-aware (text, number, date, etc.)
- Can be added without editing YAML
- Backwards compatible with old frontmatter

**Related:** [[Frontmatter (YAML)|Frontmatter basics]]

## File Types

### .md File
Standard **markdown file** containing your note content.

- Plain text format
- Readable in any editor
- Contains markdown syntax
- What Obsidian edits
- Future-proof format

**Related:** [[How Obsidian Works|Obsidian and markdown]]

### .canvas File
A **canvas file** stores the layout of a canvas workspace.

- JSON format
- References embedded notes
- Stores positions, arrows, cards
- Not meant to be edited manually
- Requires Obsidian to view properly

**Related:** [[Canvas First Workflow|Canvas guide]], [[How Obsidian Works - Details#Canvas|Canvas details]]

### .obsidian Folder
The **.obsidian folder** contains vault settings and configuration.

- Hidden folder (starts with `.`)
- Contains workspace layouts, plugin settings
- Usually gitignored for personal settings
- Some files can be shared (graph.json, templates.json)
- Automatically created by Obsidian

**Related:** [[Using Obsidian with GitHub#Setting Up a Project Vault|Git configuration]]

## Workflows & Patterns

### Zettelkasten
**Zettelkasten** is a note-taking methodology emphasizing atomic notes and connections.

- Each note covers one concept
- Heavy linking between related notes
- Emergence over structure
- Numbers or IDs for notes
- "Slip-box" system from Niklas Luhmann

**Related:** [[Note-Taking Methodologies#Zettelkasten|Zettelkasten details]]

### PARA
**PARA** is an organizational system by Tiago Forte: Projects, Areas, Resources, Archives.

- **Projects** - Short-term efforts with goals
- **Areas** - Long-term responsibilities
- **Resources** - Topics of interest
- **Archives** - Inactive items
- Folder-based organization method

**Related:** [[Note-Taking Methodologies#PARA Method|PARA details]]

### Evergreen Notes
**Evergreen notes** are permanent, concept-based notes that evolve over time.

- Not time-based or project-based
- Refined and expanded continuously
- Densely connected to other notes
- Represent current best understanding
- Contrast with fleeting notes

**Related:** [[Note-Taking Methodologies#Evergreen Notes|Evergreen notes]]

### Second Brain
A **second brain** is a personal knowledge management system for storing and connecting ideas.

- Term from Tiago Forte
- External storage for thoughts and information
- Reduces cognitive load
- Enables better recall and creativity
- Obsidian is a popular second brain tool

**Related:** [[My Personal Vault|Personal vault]], [[Why Obsidian|Why build a second brain]]

### Digital Garden
A **digital garden** is a public collection of interconnected notes that grow over time.

- Emphasis on growth and evolution over polish
- Notes at different stages of development
- Networked rather than linear
- Shared publicly (often as a website)
- This site is a digital garden!

**Related:** [[Exporting to the Web|Publishing your garden]]

## Sync & Publishing

### Obsidian Sync
**Obsidian Sync** is the official paid service for syncing vaults across devices.

- End-to-end encrypted
- Works on all platforms
- Version history included
- Selective sync
- $10/month (as of 2024)

**Related:** [[Sync Strategies Compared|Sync comparison]]

### Obsidian Publish
**Obsidian Publish** is the official paid service for publishing vaults to the web.

- One-click publishing
- Custom domain support
- Automatic updates
- Navigation and search included
- $20/month (as of 2024)

**Related:** [[Exporting to the Web|Publishing alternatives]]

### Quartz
**Quartz** is a free, open-source tool for publishing Obsidian vaults as static websites.

- Converts markdown to HTML
- Preserves wikilinks and graph
- Deployable to GitHub Pages
- Fully customizable
- This site uses Quartz!

**Related:** [[Exporting to the Web|Quartz guide]]

### Local-First
**Local-first** means your data lives on your device, not in the cloud.

- Files stored locally
- Works offline always
- You control your data
- No vendor lock-in
- Core Obsidian philosophy

**Related:** [[Why Obsidian|Why local-first]], [[AboutObsidian|About Obsidian]]

## Common Abbreviations

- **PKM** - Personal Knowledge Management
- **MOC** - Map of Content
- **YAML** - Yet Another Markup Language (frontmatter format)
- **MD** - Markdown
- **API** - Application Programming Interface (for plugins)
- **CSS** - Cascading Style Sheets (for themes/styling)

## Learn More

For detailed explanations of these concepts in practice:

- [[Getting Started with Obsidian|Getting Started]] - Basic setup and first notes
- [[How Obsidian Works|How Obsidian Works]] - Core functionality overview
- [[How Obsidian Works - Details|Technical Details]] - Deep dives into features
- [[How I Use Obsidian|How I Use Obsidian]] - Real-world workflows
- [[Note-Taking Methodologies|Note-Taking Methodologies]] - Different organizational approaches
- [[Best Obsidian Plugins|Best Obsidian Plugins]] - Plugin ecosystem

---

**Not finding a term?** Check the specific guides or use the search function. This glossary covers the most common Obsidian terminology but isn't exhaustive.
