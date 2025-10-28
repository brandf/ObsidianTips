# How Obsidian Works

Think of [[AboutObsidian|Obsidian]] as a powerful front-end to markdown files. When you're editing notes, you're **editing standard markdown** that can be read in any text viewer or editor.

![[ObsidianSourceMode.png]]

## The Core Concept

[[AboutObsidian|Obsidian]] doesn't lock your data into a proprietary format. Every note is a plain `.md` (markdown) file stored on your computer. This is fundamental to [[Why Obsidian|why Obsidian works so well]] - you own your data completely.

While editing documents, the details of markdown syntax are hidden by default through Obsidian's beautiful editing interface. But you can always drop into "Source mode" to edit the raw markdown directly, seeing exactly what's being stored.

**This means:**
- Your notes work without Obsidian (use any editor)
- Easy to [[Using Obsidian with GitHub|version control with Git]]
- [[Using AI with Obsidian|AI agents can read and edit]] your notes
- [[Exporting to the Web|Simple to publish]] to the web
- Future-proof (plain text lasts forever)

## Key Features

[[AboutObsidian|Obsidian]] enhances these plain markdown files with four powerful features:

### 🔗 [[How Obsidian Works - Details#Links|Links]]

Create connections between your notes using wikilinks: `[[Note Name]]`. Every link automatically creates a backlink, showing you all the notes that reference the current one.

This builds a **bidirectional knowledge graph** - notes know about each other, forming a network of connected ideas. Learn more about [[How Obsidian Works - Details#Links|how links work]].

### 🕸️ [[How Obsidian Works - Details#Graph|Graph]]

Visualize the relationships between your notes through an interactive graph view. Each note is a node, each [[How Obsidian Works - Details#Links|wikilink]] is a connection.

The [[How Obsidian Works - Details#Graph|graph visualization]] helps you discover hidden patterns in your thinking and see how concepts cluster together.

### 🎨 [[How Obsidian Works - Details#Canvas|Canvas]]

An infinite spatial workspace to research, brainstorm, diagram, and lay out your ideas. [[Canvas First Workflow|Canvas]] embeds your actual markdown notes on a 2D plane where you can arrange them visually.

Unlike the [[How Obsidian Works - Details#Graph|graph view]] which shows link structure, [[How Obsidian Works - Details#Canvas|canvas]] lets you manually position notes to show relationships spatially. See the [[Canvas First Workflow|canvas-first approach]] for how to leverage this.

### 🧩 [[How Obsidian Works - Details#Plugins|Plugins]]

Build your ideal thinking space with [[Best Obsidian Plugins|thousands of community plugins]] and Obsidian's open API. Tailor the app to fit your personal workflow - from [[Best Obsidian Plugins#Calendar|calendar integration]] to [[Best Obsidian Plugins#Tasks|task management]] to AI assistance.

The [[How Obsidian Works - Details#Plugins|plugin ecosystem]] means Obsidian grows with your needs.

## The Vault

In Obsidian terminology, your collection of notes is called a "vault." A vault is simply:
- A folder on your computer
- Containing markdown (`.md`) files
- Optionally organized into subfolders
- Plus a hidden `.obsidian/` folder for settings

**Examples of Vault Patterns:**

**Single Personal Vault**
Keep all notes in [[My Personal Vault|one central vault]] for unified search and linking.

**Project-Specific Vaults**
Each [[Using Obsidian with GitHub|GitHub project has an obsidian folder]] that serves as its documentation vault.

**Master Vault**
Use the [[One Vault to Rule Them All|master vault pattern]] to symlink multiple project vaults into your personal vault, getting the best of both worlds.

## Markdown with Superpowers

[[AboutObsidian|Obsidian]] supports several markdown flavors:

**Standard Markdown**
```markdown
# Heading
**bold** and *italic*
- Lists
- And more

[external links](https://example.com)
![images](image.png)
```

**Obsidian Additions**
```markdown
[[Wikilinks]] to other notes
![[Embedded Notes]]
![[Images.png]] with simple syntax
#tags for categorization

[[Note#Section]] link to specific sections
[[Note|Custom Text]] for link aliases
```

**Extended Features**
- Callouts for highlighted content
- Tables (GitHub flavored)
- Task lists with `- [ ]`
- Footnotes
- LaTeX math equations
- Mermaid diagrams
- Code blocks with syntax highlighting

All of these work within plain markdown files that remain readable in any editor.

## Local-First Architecture

Unlike cloud-based note apps, [[AboutObsidian#1. Local-First & Private|Obsidian stores everything locally]]:

**Your Computer**
- All notes stored as files
- Fast access (no network latency)
- Works completely offline
- Complete privacy

**Optional Cloud Services**
- Obsidian Sync (paid) - Encrypted sync between devices
- Obsidian Publish (paid) - Publish notes to the web
- Or use your own solutions: [[Using Obsidian with GitHub|Git]], Dropbox, iCloud, etc.

The local-first approach means your notes are always accessible and you're never locked into a service.

## How Obsidian Compares

**vs. Notion/Confluence**
- ✅ You own the files (not in a database)
- ✅ Works offline always
- ✅ Faster (no server lag)
- ✅ More private
- ❌ Less real-time collaboration
- ❌ No built-in databases/views

**vs. Apple Notes/OneNote**
- ✅ Plain text files (future-proof)
- ✅ Powerful [[How Obsidian Works - Details#Links|linking]]
- ✅ Extensible with [[Best Obsidian Plugins|plugins]]
- ✅ Cross-platform
- ❌ Steeper learning curve
- ❌ No built-in cloud sync (but many options)

**vs. Plain Markdown Editors**
- ✅ [[How Obsidian Works - Details#Graph|Graph visualization]]
- ✅ Backlinks and [[How Obsidian Works - Details#Links|wikilinks]]
- ✅ [[Canvas First Workflow|Canvas]] for spatial organization
- ✅ [[Best Obsidian Plugins|Rich plugin ecosystem]]
- ✅ Beautiful editing interface
- Still just markdown underneath!

## The Philosophy

[[Why Obsidian|Obsidian's philosophy]] is built on three principles:

1. **Your thoughts are yours** - [[AboutObsidian#1. Local-First & Private|Local-first and private]]
2. **Your mind is unique** - [[How Obsidian Works - Details#Plugins|Customizable to your thinking]]
3. **Your knowledge should last** - [[Why Obsidian|Open file formats]] for longevity

Everything in Obsidian's design serves these principles. The result is a tool that enhances your thinking without ever locking you in.

## Getting Deeper

To understand specific features in detail:

- [[How Obsidian Works - Details#Links|Links]] - How wikilinks and backlinks work
- [[How Obsidian Works - Details#Graph|Graph]] - Visualizing your knowledge network
- [[How Obsidian Works - Details#Canvas|Canvas]] - Spatial organization
- [[How Obsidian Works - Details#Plugins|Plugins]] - Extending functionality

To see these concepts in practice:

- [[How I Use Obsidian]] - Complete workflow overview
- [[My Personal Vault]] - Personal knowledge management
- [[Using Obsidian with GitHub]] - Documentation workflows
- [[Canvas First Workflow]] - Spatial-first approach
- [[Using AI with Obsidian]] - AI-enhanced note-taking
- [[Exporting to the Web]] - Publishing your knowledge

[[AboutObsidian|Obsidian]] is fundamentally just a markdown editor - but it's a markdown editor that understands how ideas connect, how knowledge grows, and how thinking works. That's what makes it powerful.
