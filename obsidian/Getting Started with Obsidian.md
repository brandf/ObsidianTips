# Getting Started with Obsidian

Welcome to [[AboutObsidian|Obsidian]]! This guide will walk you through everything you need to know to start building your knowledge base, from installation to creating your first connected notes.

[[AboutObsidian|Obsidian]] might seem overwhelming at first - there's a lot of power under the hood. But you can start simple and gradually adopt more advanced features as you need them. This guide focuses on the essentials to get you productive quickly.

## Step 1: Download and Install

**Get Obsidian:**
1. Visit [obsidian.md/download](https://obsidian.md/download)
2. Download for your operating system (Windows, Mac, Linux)
3. Install like any other application
4. Launch Obsidian

Obsidian is **free for personal use**. You don't need an account, credit card, or subscription to get started. See [[AboutObsidian#Free Forever|why it's free]] and how the business model works.

## Step 2: Create Your First Vault

When you first open Obsidian, you'll be prompted to create or open a vault.

**What's a Vault?**
A vault is just a folder on your computer containing markdown files. That's it. Nothing magical - just a regular folder that [[How Obsidian Works|Obsidian uses to organize your notes]].

**Creating a New Vault:**
1. Click **"Create new vault"**
2. Choose a name (e.g., "My Notes" or "Personal Knowledge")
3. Select a location on your computer
4. Click **Create**

**💡 Tips:**
- Pick a location you'll remember (Documents folder is common)
- Start with one vault - you can always [[One Vault to Rule Them All|create multiple vaults]] later
- The vault folder will contain all your notes as `.md` files
- You can open this folder in any file explorer and see your notes

**What Just Happened?**
Obsidian created a folder at your chosen location and added a hidden `.obsidian` subfolder for settings. That's all. Your notes will live here as [[How Obsidian Works|plain markdown files]].

## Step 3: Understanding the Interface

The Obsidian interface has several key areas:

**Left Sidebar (File Explorer)**
- Shows all your notes in a tree structure
- Create folders to organize (optional)
- Drag and drop to reorganize
- Click any note to open it

**Center Panel (Editor)**
- Where you write and read notes
- Switch between Reading and Editing modes
- Live Preview shows formatting as you type
- Source mode shows raw markdown

**Right Sidebar (Backlinks & More)**
- **Backlinks** - Shows notes that link to current note
- **Outline** - Table of contents for current note
- **Tags** - All tags used in your vault
- Collapse/expand with the icons

**Command Palette (Ctrl/Cmd + P)**
- Quick access to all features
- Search for any command
- Most powerful way to navigate Obsidian

**Quick Switcher (Ctrl/Cmd + O)**
- Quickly jump to any note
- Start typing to filter
- Press Enter to open

These basics will get you started. Don't worry about memorizing everything - you'll naturally learn the interface as you use it.

## Step 4: Create Your First Note

Let's create a note to get comfortable with the basics:

**Creating a Note:**
1. Click the **New note** icon (page with plus) in the left sidebar
2. Or use **Ctrl/Cmd + N**
3. Type a title at the top (e.g., "Welcome Note")
4. Start writing below the title

**Write Some Content:**
```markdown
# My First Note

This is my first note in Obsidian! I'm learning how to use markdown for note-taking.

## Things I Want to Learn
- How to link notes together
- Using tags
- Creating a daily journal

## Why I'm Using Obsidian
I want a note system that's private, portable, and powerful.
```

**💡 What You Just Did:**
- Created a markdown file named `Welcome Note.md` in your vault
- Used `#` for headings (one # = big heading, two ## = smaller, etc.)
- Created lists with `-`
- All stored as plain text you can read anywhere

## Step 5: Learn Basic Markdown

Obsidian uses markdown - a simple way to format text with plain characters. Here are the essentials:

**Headings**
```markdown
# Heading 1 (Largest)
## Heading 2
### Heading 3
#### Heading 4
```

**Formatting**
```markdown
**bold text**
*italic text*
***bold and italic***
~~strikethrough~~
==highlighted text==
```

**Lists**
```markdown
- Bullet point
- Another point
  - Indented point

1. Numbered list
2. Second item
3. Third item

- [ ] Checkbox (unchecked)
- [x] Checkbox (checked)
```

**Links and Images**
```markdown
[External link](https://example.com)
[[Internal link to another note]]
![[Embedded image.png]]
```

**Code**
```markdown
Inline `code` with backticks

```
Code block with triple backticks
Multiple lines of code
```
```

**Quotes**
```markdown
> This is a quote
> It can span multiple lines
```

Don't try to memorize all of this! Keep this note handy and refer back when you need formatting. [[How Obsidian Works|Obsidian's live preview]] will show you the results as you type.

## Step 6: Your First Wikilink

This is where Obsidian gets powerful - linking notes together.

**Creating a Wikilink:**
1. In your current note, type `[[`
2. Start typing a note name
3. If the note exists, it'll appear - press Enter to link
4. If it doesn't exist, type the name and press Enter anyway

Example:
```markdown
I'm learning about [[Markdown Basics]].

Today I read about [[Why Obsidian]] and it makes sense.

Need to explore [[Best Obsidian Plugins]] later.
```

**What Happens:**
- Links to existing notes appear in color
- Links to non-existent notes appear in different color (gray usually)
- Click any link to open that note
- If the note doesn't exist, clicking creates it
- Backlinks automatically appear in the target note

This is [[How Obsidian Works - Details#Links|bidirectional linking]] - the feature that makes Obsidian special. Every link you create is tracked both ways.

**💡 Best Practice:**
Link liberally! Don't overthink it. If you mention a concept, person, or project - make it a link. You can always create the note later.

## Step 7: Explore the Graph View

Click the **Graph view** icon in the left sidebar (looks like connected nodes).

**What You'll See:**
- Each note is a dot (node)
- Each [[How Obsidian Works - Details#Links|wikilink]] is a line (edge)
- Connected notes cluster together
- Isolated notes sit alone

**Try This:**
1. Create a few more notes
2. Add links between them
3. Watch the [[How Obsidian Works - Details#Graph|graph]] grow
4. Click nodes in the graph to open notes
5. Hover over nodes to see note titles

The graph helps you visualize your knowledge structure. As you add more notes and links, patterns will emerge showing how your ideas connect.

## Step 8: Add Some Plugins

[[How Obsidian Works - Details#Plugins|Plugins]] extend Obsidian's functionality. Let's enable a few essential ones:

**Core Plugins (Built-in):**
1. Open Settings (gear icon in bottom-left)
2. Click **Core plugins**
3. Enable these plugins:
   - **Daily notes** - Create a note for each day
   - **Templates** - Reusable note structures
   - **Quick switcher** - Already enabled, but check it
   - **Command palette** - Already enabled

**Community Plugins (Third-party):**
1. In Settings, click **Community plugins**
2. Click **Turn on community plugins**
3. Click **Browse**
4. Search and install:
   - **Calendar** - Visual calendar for daily notes
   - **Dataview** - Query your notes like a database (optional, more advanced)

See [[Best Obsidian Plugins|Best Obsidian Plugins]] for more recommendations once you're comfortable with the basics.

**⚠️ Start Simple:**
Don't install too many plugins at once. Use Obsidian for a week or two with just the core features. Add plugins as you discover specific needs.

## Step 9: Create a Daily Note

Daily notes are a great way to build a journaling habit and capture thoughts.

**Setup:**
1. Enable **Daily notes** core plugin (if not already)
2. In Settings → Daily notes:
   - Choose a folder (or leave blank for vault root)
   - Set date format (default is fine)
3. Click the **Open today's daily note** button (calendar icon)

**Your Daily Note:**
A new note appears with today's date (e.g., `2024-10-28.md`).

**What to Write:**
```markdown
# October 28, 2024

## Plan
- [ ] Review project documentation
- [ ] Create note about [[New Concept]]
- [ ] Weekly planning

## Notes
Started learning [[Getting Started with Obsidian]].

Met with [[Person Name]] about the project.

## Reflection
...
```

**Why Daily Notes Matter:**
- Regular capture habit
- Chronological record of thoughts
- Natural place to link to people, projects, ideas
- Backlinks create a timeline

Learn more in the [[Daily Notes Workflow|complete daily notes workflow guide]].

## Step 10: Organize Your Notes

As you create more notes, you'll want some organization. Obsidian gives you options:

**Option 1: Folders**
Create folders in the file explorer:
- Right-click in file explorer → New folder
- Drag notes into folders
- Use folders for broad categories

Example:
```
Vault/
├── Projects/
├── Areas/
├── Resources/
└── Archive/
```

**Option 2: Links (Recommended)**
Let links be your organization:
- Create an index note linking to related notes
- Use [[How Obsidian Works - Details#Links|wikilinks]] to navigate
- Let the [[How Obsidian Works - Details#Graph|graph view]] show structure

**Option 3: Tags**
Add tags to notes:
```markdown
#project #work #important
```
- Click any tag to see all notes with that tag
- Tags appear in the right sidebar
- Good for cross-cutting categories

**💡 Advice:**
Start simple with a flat structure (all notes in one folder). As patterns emerge, organize naturally. Don't over-organize early. See [[Note-Taking Methodologies|note-taking methodologies]] for popular approaches.

## Common Beginner Mistakes

Avoid these pitfalls as you get started:

**❌ Over-Organizing Too Early**
Don't spend hours creating the "perfect" folder structure before you have notes. Start writing. Structure emerges naturally.

**❌ Not Linking Enough**
Beginners often forget to add [[How Obsidian Works - Details#Links|wikilinks]]. The power of Obsidian is in connections. Link anything that might be related.

**❌ Installing Too Many Plugins**
Use vanilla Obsidian for a week. Learn the basics. Then add [[Best Obsidian Plugins|plugins]] as specific needs arise.

**❌ Treating It Like a Traditional App**
Obsidian isn't a structured database. It's more like a thinking space. Be messy. Experiment. Let it evolve.

**❌ Not Backing Up**
Your notes are [[AboutObsidian#1. Local-First & Private|local files]]. Set up backups:
- Use [[Using Obsidian with GitHub|Git for version control]]
- Enable cloud sync (iCloud, Dropbox, etc.)
- Or use Obsidian Sync (paid)

**❌ Expecting Perfection**
Your first notes will be rough. Your organization will change. That's normal. Just start writing and iterating.

**❌ Ignoring Daily Notes**
Even if you don't journal, [[Daily Notes Workflow|daily notes]] are valuable for capturing what you worked on each day and creating chronological backlinks.

## Next Steps

You now know enough to be productive with Obsidian! Here's what to explore next:

**Essential Reading:**
- [[Why Obsidian|Why Obsidian?]] - Understand the philosophy
- [[How Obsidian Works|How Obsidian Works]] - Deeper technical understanding
- [[How I Use Obsidian|How I Use Obsidian]] - See a complete workflow in action

**Level Up Your Workflow:**
- [[Daily Notes Workflow|Daily Notes Workflow]] - Build a sustainable journaling habit
- [[Best Obsidian Plugins|Best Obsidian Plugins]] - Enhance your setup
- [[Canvas First Workflow|Canvas First Workflow]] - Visual organization (once comfortable with basics)

**Explore Different Approaches:**
- [[My Personal Vault|My Personal Vault]] - Personal knowledge management patterns
- [[Note-Taking Methodologies|Note-Taking Methodologies]] - Zettelkasten, PARA, LYT, and more
- [[Using Obsidian with GitHub|Using Obsidian with GitHub]] - For developers and technical writing

**Advanced Topics:**
- [[One Vault to Rule Them All|Master Vault Pattern]] - Multi-vault workflows
- [[Using AI with Obsidian|Using AI with Obsidian]] - AI-enhanced note-taking
- [[Exporting to the Web|Exporting to the Web]] - Publishing your knowledge

## Practice Exercise

To solidify what you've learned, try this:

**Create a "Learning Obsidian" Project:**
1. Create a note: `Learning Obsidian`
2. Link to notes about specific topics you want to learn
3. Create those linked notes (even if just stubs)
4. Write a sentence or two in each
5. Check the [[How Obsidian Works - Details#Graph|graph view]] to see connections
6. Create a [[Daily Notes Workflow|daily note]] and link to your progress

Example structure:
```markdown
# Learning Obsidian

I'm learning [[AboutObsidian|Obsidian]] for personal knowledge management.

## Topics to Explore
- [[How Obsidian Works - Details#Links|Wikilinks and Backlinks]]
- [[How Obsidian Works - Details#Graph|Graph View]]
- [[Daily Notes Workflow|Daily Notes]]
- [[Best Obsidian Plugins|Essential Plugins]]
- [[Note-Taking Methodologies|Organization Methods]]

## Progress
- [[2024-10-28]] - Created first vault, learned basics
- [[2024-10-29]] - ...

## Resources
- [[Getting Started with Obsidian]] (this guide!)
- Official Obsidian docs
```

## Getting Help

**Official Resources:**
- [Obsidian Help](https://help.obsidian.md/) - Official documentation
- [Obsidian Forum](https://forum.obsidian.md/) - Community discussions
- [Obsidian Discord](https://discord.gg/obsidianmd) - Real-time chat

**Community:**
- r/ObsidianMD on Reddit - Active community
- YouTube tutorials - Tons of video guides
- This digital garden - You're here!

**Remember:**
- Everyone starts as a beginner
- Your vault will grow organically
- There's no "right way" - find what works for you
- The Obsidian community is friendly and helpful

## You're Ready!

You now have everything you need to start building your knowledge base in [[AboutObsidian|Obsidian]]:

✅ Vault created
✅ Basic markdown understood
✅ Wikilinks connecting notes
✅ Interface navigation
✅ Core plugins enabled
✅ Daily notes ready

The rest is practice. Start capturing notes, linking ideas, and building your personal knowledge graph. Return to this guide whenever you need a refresher.

Welcome to the world of [[Why Obsidian|local-first, future-proof knowledge management]]! 🌱
