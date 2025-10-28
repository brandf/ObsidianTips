# My Personal Vault

I maintain a personal vault that serves as my **second brain** - a centralized place for all my everyday note-taking, thinking, and knowledge management. Unlike project-specific vaults that live in [[Using Obsidian with GitHub|GitHub repositories]], this vault is where I capture personal thoughts, daily notes, ideas, and cross-project insights.

![[Personal Vault.png]]

## Why a Separate Personal Vault?

Having a dedicated personal vault alongside project-specific vaults gives you the best of both worlds:

**Personal Knowledge Hub**
Your personal vault becomes the home base for:
- Daily journaling and reflections
- Meeting notes and conversations
- Ideas and insights that span multiple projects
- Personal goals, habits, and planning
- Learning notes and resources
- People you work with and meet

**Project-Focused Vaults**
Meanwhile, each project gets its own [[Using Obsidian with GitHub|obsidian folder in its GitHub repo]] for:
- Technical documentation
- Project-specific notes and decisions
- Code references and architecture
- Team collaboration content

**Connecting Both Worlds**
Using the [[One Vault to Rule Them All|master vault pattern]], I symlink all my project vaults into my personal vault. This creates a unified knowledge graph where I can link personal insights to specific projects while keeping the project documentation version-controlled with the code.

## Vault Structure

My personal vault is organized around life areas rather than technical hierarchies:

```
PersonalVault/
├── 📅 Daily/           # Daily notes and journals
├── 👥 People/          # Notes about people I work with
├── 💡 Ideas/           # Random thoughts and insights
├── 📚 Learning/        # Study notes and resources
├── 🎯 Goals/           # Personal and professional goals
├── 🚧 Projects/        # Symlinks to GitHub project vaults
└── 📄 Templates/       # Note templates (excluded from web export)
```

This structure supports my [[Canvas First Workflow|canvas-first approach]] - each major area can have a canvas that spatially organizes the notes within it.

## Daily Notes as the Foundation

Daily notes are the backbone of my personal vault. Each morning, I create a new daily note using a template that includes:

**Sections:**
- 📋 **Plan** - What I want to accomplish today
- 🎯 **Focus** - Main priorities
- 📝 **Notes** - Capture thoughts throughout the day
- ✅ **Done** - What I actually completed
- 💭 **Reflections** - End-of-day thoughts

**Links Out:**
Daily notes heavily use [[How Obsidian Works - Details#Links|wikilinks]] to connect to:
- People I meet with (notes in `👥 People/`)
- Projects I work on (symlinked from `🚧 Projects/`)
- Ideas that emerge (`💡 Ideas/`)
- Goals I'm progressing toward (`🎯 Goals/`)

This creates a chronological thread through my vault - I can always see when I last thought about something by checking backlinks from my daily notes.

## People Notes

One of the most valuable patterns in my [[My Personal Vault|personal vault]] is maintaining notes for people:

**Why People Notes Matter**
- Remember context from previous conversations
- Track shared projects and interests
- Note important personal details
- Build better relationships through better memory

**What to Capture**
- How you know them (context)
- Current projects or focus areas
- Past conversations and meeting notes (linked from [[#Daily Notes as the Foundation|daily notes]])
- Follow-up items and action items
- Personal interests and background

These notes integrate naturally with [[How I Use Obsidian|daily workflows]] - during meetings, I link to the person's note from my daily note, and those backlinks create a conversation history.

## Ideas and Insights

The `💡 Ideas/` folder is where spontaneous thoughts go. Unlike structured project documentation or daily logs, this is a collection of:

- Random thoughts that might connect to something later
- "What if..." questions and explorations
- Insights that span multiple projects
- Future possibilities and experiments

Because these notes use [[How Obsidian Works - Details#Links|wikilinks]] extensively, ideas naturally find their home when connections emerge. The [[How Obsidian Works - Details#Graph|graph view]] often reveals surprising connections between ideas captured months apart.

## Integration with AI

My personal vault is perfect for [[Using AI with Obsidian|AI-assisted workflows]] because:

**Context-Rich**
The vault contains personal context that AI can reference when helping with tasks like:
- Summarizing weekly activities from daily notes
- Finding patterns across meeting notes
- Suggesting connections between ideas
- Drafting content based on my thinking patterns

**Privacy-First**
Because it's [[AboutObsidian#1. Local-First & Private|local-first]], I control exactly what context I share with AI tools. I can use local AI models for sensitive content or carefully curate what goes to cloud services.

**Markdown-Native**
Since everything is plain markdown, [[Using AI with Obsidian|AI agents]] can easily read, understand, and modify notes using standard file operations.

## Backup and Syncing

Since this vault contains personal knowledge, backup is critical:

**Version Control**
While I use [[Using Obsidian with GitHub|Git for project vaults]], my personal vault uses:
- **Obsidian Sync** (official paid service) - Simple, encrypted, works across devices
- **Or manual Git** - Free but requires more setup
- **Or cloud sync** (Dropbox, iCloud, etc.) - Simple but potential conflict issues

**Multi-Device Access**
The personal vault syncs across:
- Desktop computer (primary writing location)
- Laptop (for travel)
- Mobile phone (quick capture and review)

This ensures my second brain is always accessible, whether I'm at my desk or capturing an idea on the go.

## Publishing Selected Content

While most of my personal vault stays private, I occasionally want to [[Exporting to the Web|publish selected notes]]. The [[One Vault to Rule Them All|master vault pattern]] handles this elegantly:

**Keep Private Notes Private**
Personal vault stays on my computer with sensitive content.

**Publish Specific Projects**
Individual [[Using Obsidian with GitHub|GitHub project vaults]] can be published via [[Exporting to the Web|Quartz]] while the personal vault remains private.

**Selective Sharing**
If I want to publish personal notes, I can:
- Copy specific notes to a publishable vault
- Use ignore patterns to exclude private folders
- Create a separate "digital garden" vault for public content

## Why This Works

The personal vault pattern succeeds because it:

**Reduces Friction**
One place to capture everything means less time deciding where notes go.

**Creates Connections**
Personal insights naturally link to project work, creating a richer knowledge graph than either would have alone.

**Preserves Context**
Years of daily notes and accumulated knowledge become increasingly valuable over time. The [[How Obsidian Works - Details#Graph|graph grows]] and patterns emerge.

**Supports Multiple Workflows**
Works with [[Canvas First Workflow|canvas-first]], tag-based, folder-based, or link-based organization - choose what fits your thinking style.

**Scales Naturally**
Start simple with daily notes and a few folders. Add [[Best Obsidian Plugins|plugins]] and structure as needs emerge. The [[AboutObsidian|flexibility of Obsidian]] means the vault grows with you.

## Getting Started with Your Own

To create a similar personal vault:

1. **Create a new vault** - Pick a location outside your project folders
2. **Start with daily notes** - Just date and a few thoughts each day
3. **Add folders as needed** - Don't over-organize early
4. **Link liberally** - Use `[[wikilinks]]` whenever you reference anything
5. **Review the [[How Obsidian Works - Details#Graph|graph]]** - See what connections emerge
6. **Consider [[One Vault to Rule Them All|linking project vaults]]** - Unify your knowledge
7. **Explore [[Best Obsidian Plugins]]** - Enhance your workflow as needs arise

The key is to start simple and let the system grow organically. Your personal vault should feel like a natural extension of your thinking, not a complex system you have to maintain.

## Learn More

- [[Why Obsidian]] - The philosophy of local-first knowledge management
- [[How I Use Obsidian]] - Complete workflow overview
- [[One Vault to Rule Them All]] - Linking multiple vaults together
- [[Using Obsidian with GitHub]] - Managing project documentation
- [[Canvas First Workflow]] - Spatial organization approach
- [[Using AI with Obsidian]] - AI-enhanced note-taking
