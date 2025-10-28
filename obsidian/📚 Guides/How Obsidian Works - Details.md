# How Obsidian Works - Details

Think of [[AboutObsidian|Obsidian]] as a sophisticated front-end to markdown files. When you're editing notes, you're **editing standard markdown** that can be read in any viewer. See [[How Obsidian Works|the main overview]] for the big picture.

![[ObsidianSourceMode.png]]

While editing documents, the details of markdown syntax are hidden by default through Obsidian's beautiful editing interface. But you can always drop into "Source mode" to edit the raw markdown directly, seeing exactly what's being stored.

This page dives into the specific features that make [[AboutObsidian|Obsidian]] powerful for knowledge management and note-taking.

## Links

Create connections between your notes using **wikilinks**. Link anything and everything — ideas, people, places, books, and beyond. Invent your own personal Wikipedia that grows with your thinking.

![[ObsidianLinks.png]]

### How Wikilinks Work

In [[How Obsidian Works|Obsidian]], you create links using double brackets:

```markdown
[[Target Note Name]]
```

This creates a link to another note in your vault. If the target note doesn't exist yet, the link appears in a different color - these "red links" show you what notes you might want to create.

### Bidirectional Linking

The key innovation is **automatic backlinks**. When you link from Note A to Note B, Obsidian automatically shows that connection in Note B's backlinks panel. You don't have to manually maintain connections - they're always up to date.

This bidirectional linking is fundamental to how [[My Personal Vault|personal vaults]] and [[Using Obsidian with GitHub|project documentation]] become knowledge graphs rather than just file collections.

### Link Variations

**Section Links:**
```markdown
[[Note#Heading]]  # Link to specific section
```

**Link Aliases:**
```markdown
[[Long Note Name|shorter text]]
```

**Embed Notes:**
```markdown
![[Another Note]]  # Embeds the entire note
![[Note#Section]]  # Embeds just a section
```

These linking patterns appear throughout [[Canvas First Workflow|canvas workflows]] and [[Using AI with Obsidian|AI-assisted]] knowledge management.

### Why Wikilinks Matter

**Low Friction**
Creating a link is instant - just type `[[` and start searching. This makes it easy to link liberally as you write.

**Discoverable Connections**
Backlinks show you where concepts are referenced across your vault, revealing connections you might have forgotten.

**Non-Hierarchical**
Ideas don't need to fit in one folder - they can link to anything, anywhere in your vault.

**Network Effects**
The more links you create, the more valuable your vault becomes. Each link is a path to related knowledge.

This linking philosophy connects to [[Why Obsidian|why Obsidian works]] and underlies the [[One Vault to Rule Them All|master vault pattern]].

## Graph

Visualize the relationships between your notes as an interactive network. Find hidden patterns in your thinking through a visually engaging graph that shows how your knowledge connects.

![[ObsidianGraph.png]]

### How the Graph Works

Every note in your vault appears as a **node** (dot) in the graph. Every [[#Links|wikilink]] between notes creates an **edge** (line) connecting them. The result is a visual map of your knowledge structure.

**Interactive Features:**
- **Zoom** in/out to see different levels of detail
- **Pan** around to explore different areas
- **Click** nodes to open that note
- **Hover** to see note titles
- **Filter** to show only specific notes or connections
- **Color code** by tags, folders, or properties

The graph reveals patterns you might not notice when just browsing individual notes.

### Types of Graph Views

**Global Graph**
Shows your entire vault at once. Great for:
- Understanding overall vault structure
- Finding isolated notes (no connections)
- Seeing which notes are most connected (hubs)
- Discovering unexpected clusters

**Local Graph**
Shows just the notes connected to the current note. Useful for:
- Understanding immediate context
- Finding related notes while writing
- Exploring a specific topic area
- Seeing how deep connection networks go

### What the Graph Tells You

**Highly Connected Notes (Hubs)**
Notes with many links are often:
- Core concepts or MOCs (Maps of Content)
- Index pages
- Frequently referenced ideas
- Good starting points for exploration

**Isolated Notes (Islands)**
Notes with no or few connections might need:
- Links to related concepts
- Integration into existing structure
- Or they're legitimately standalone

**Clusters**
Groups of tightly connected notes often represent:
- Topic areas (all your notes on a subject)
- Projects (notes about specific work)
- Time periods (if you use [[My Personal Vault#Daily Notes as the Foundation|daily notes]])

### Graph in Practice

**In Personal Vaults**
The [[My Personal Vault|personal vault]] graph shows how [[My Personal Vault#Daily Notes as the Foundation|daily notes]] connect to people, projects, and ideas over time.

**In Project Docs**
[[Using Obsidian with GitHub|Project documentation]] graphs reveal:
- System architecture (how components relate)
- Feature dependencies
- Knowledge gaps (missing connections)

**With Master Vault**
The [[One Vault to Rule Them All|master vault pattern]] creates a unified graph across all projects, showing cross-project connections.

### Graph vs Canvas

The [[#Graph|graph view]] and [[Canvas First Workflow|canvas]] serve different purposes:

**Graph (Automatic)**
- Shows actual link structure
- Generated automatically
- Good for discovery
- Can't be manually arranged

**Canvas (Manual)**
- You control the layout
- Shows spatial relationships
- Good for presentations
- Must be maintained

Use both! The graph reveals connections, [[Canvas First Workflow|canvas]] lets you organize them meaningfully.

## Canvas

An infinite spatial workspace to research, brainstorm, diagram, and lay out your ideas. [[Canvas First Workflow|Canvas]] is a limitless playground for visual thinking that embeds your actual markdown notes.

![[ObsidianCanvas.png]]

### What Canvas Provides

Unlike the auto-generated [[#Graph|graph]], canvas gives you manual control over layout:

**Infinite 2D Space**
Arrange notes, cards, images, and links across an unlimited workspace. Zoom out to see the big picture, zoom in to focus on details.

**Embed Real Notes**
Canvas doesn't create separate content - it embeds your actual `.md` files. Edit them right on the canvas or open them separately. They remain normal markdown files that work everywhere.

**Visual Organization**
Use spatial positioning, arrows, grouping, and color to show relationships that [[#Links|wikilinks]] alone can't express.

**Mixed Media**
Combine embedded notes, text cards, images, PDFs, and web links all in one visual workspace.

### Canvas vs Regular Notes

Canvas files (`.canvas`) are JSON that describes the layout. They don't replace markdown notes - they provide an optional visual view over them.

This means:
- Notes embedded in canvas can be opened normally
- Notes work in any markdown editor
- Canvas is just one way to view/organize
- [[Exporting to the Web|Publishing]] shows notes, not canvas layout

The [[Canvas First Workflow|canvas-first approach]] treats canvas as the primary entry point while keeping markdown as the content foundation.

### Common Canvas Uses

**Project Overview**
Create a [[Using Obsidian with GitHub|project canvas]] that spatially arranges architecture, roadmap, and implementation notes.

**Brain Dumps**
Capture ideas as text cards, arrange them spatially, then convert key cards to notes as they solidify.

**Meeting Prep**
Layout talking points, background notes, and data spatially for easy navigation during presentations.

**Learning/Research**
Collect sources and insights on a canvas, arrange by theme, draw connections, then synthesize understanding in a central note.

**System Design**
Visualize components and their relationships, with detailed notes embedded for each part.

See [[Canvas First Workflow|the full canvas workflow guide]] for detailed patterns and examples.

### Canvas in Different Contexts

**Personal Knowledge**
In [[My Personal Vault|personal vaults]], use canvas for year planning, weekly reviews, and learning projects.

**Team Documentation**
For [[Using Obsidian with GitHub|GitHub projects]], canvas provides visual onboarding, architecture diagrams, and feature planning boards.

**Publishing Limitation**
When [[Exporting to the Web|publishing with Quartz]], canvas layouts aren't preserved - they show as link lists. Keep canvas for private organization or include screenshots in published notes.

### Canvas Features

- **Text cards** for quick notes
- **Note embeds** for full markdown content
- **Image embeds** for diagrams and screenshots
- **Web cards** for external links
- **Arrows** to show relationships
- **Groups** to cluster related items
- **Colors** for visual coding
- **Labels** for sections
- **Zoom** for different perspectives

These features make canvas powerful for [[Using AI with Obsidian|AI-assisted]] brainstorming and organization.

## Plugins

Build your ideal thinking space. With [[Best Obsidian Plugins|thousands of community plugins]] and Obsidian's open API, it's easy to tailor the app to fit your personal workflow.

![[ObsidianPlugins.png]]

### Core vs Community

**Core Plugins (Built-in)**
Obsidian ships with optional features you can enable:
- Daily notes
- Templates
- Slash commands
- Quick switcher
- File recovery
- Sync (paid service)
- Publish (paid service)

**Community Plugins (Third-party)**
The [[Best Obsidian Plugins|community]] has created thousands of plugins for every imaginable use case - see [[Best Obsidian Plugins|the best plugins]] for recommendations.

### Why Plugins Matter

**Customization**
Make [[AboutObsidian|Obsidian]] match YOUR workflow, not the other way around. Need calendar integration? There's a [[Best Obsidian Plugins#Calendar|plugin]]. Want task management? Multiple [[Best Obsidian Plugins#Tasks|options]]. AI assistance? [[Using AI with Obsidian|Several plugins]] available.

**Extensibility**
The open API means the community continuously adds new capabilities. Features that other apps might never add, Obsidian has as plugins.

**No Vendor Lock-in**
Because notes are just [[How Obsidian Works|markdown files]], plugins enhance the experience without locking your data. If a plugin disappears, your notes remain fully functional.

### Popular Plugin Categories

**Enhanced Editing:**
- Advanced tables
- Better markdown syntax
- Vim/Emacs keybindings
- Advanced formatting

**Organization:**
- [[Best Obsidian Plugins#Calendar|Calendar]] for daily notes
- Kanban boards
- Dataview for queries
- Excalidraw for drawings

**Workflow:**
- [[Best Obsidian Plugins#Tasks|Task management]]
- Templates
- Quick capture
- Automation

**Integration:**
- Git version control (perfect for [[Using Obsidian with GitHub|GitHub workflows]])
- Import from other apps
- Export to various formats
- API connections

**AI & Advanced:**
- AI-powered writing and editing
- Smart connections
- Automated linking
- Content generation

See [[Best Obsidian Plugins|Best Obsidian Plugins]] for specific recommendations and how they integrate with different workflows.

### Plugin Philosophy

Plugins follow Obsidian's [[Why Obsidian|core philosophy]]:
- Work with markdown files (not against them)
- Enhance without lock-in
- Optional (use what you need)
- Community-driven
- Open source (mostly)

This makes the plugin ecosystem sustainable and user-focused rather than vendor-focused.

### Plugins in Practice

**Personal Vaults**
[[My Personal Vault|Personal vaults]] often use plugins for [[My Personal Vault#Daily Notes as the Foundation|daily notes]], calendar views, and task management.

**Project Documentation**
[[Using Obsidian with GitHub|Project vaults]] benefit from Git plugins, advanced canvas tools, and diagramming extensions.

**Publishing**
When [[Exporting to the Web|publishing with Quartz]], most plugin features don't transfer - but they enhance your local editing experience.

**AI Integration**
[[Using AI with Obsidian|AI-enhanced workflows]] leverage plugins for smart suggestions, automated linking, and content generation.

## Summary

These four features - [[#Links|wikilinks]], [[#Graph|graph]], [[#Canvas|canvas]], and [[#Plugins|plugins]] - transform [[How Obsidian Works|plain markdown files]] into a powerful thinking tool.

**Links** create the network structure.
**Graph** visualizes that structure.
**Canvas** lets you arrange it spatially.
**Plugins** customize everything to your needs.

Together, they enable workflows described in:
- [[How I Use Obsidian]] - Complete workflow overview
- [[My Personal Vault]] - Personal knowledge management
- [[Using Obsidian with GitHub]] - Project documentation
- [[Canvas First Workflow]] - Spatial organization
- [[Using AI with Obsidian]] - AI-enhanced note-taking
- [[One Vault to Rule Them All]] - Multi-project integration

All while keeping your notes as portable, future-proof [[Why Obsidian|markdown files]].
