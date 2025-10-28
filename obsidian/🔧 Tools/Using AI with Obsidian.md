# Using AI with Obsidian

Since vaults are just normal folders full of markdown files, AI Agents are really good at understanding, modifying, and creating/writing new notes. This makes Obsidian uniquely positioned to take advantage of modern AI assistants.

## Why AI + Obsidian Works So Well

The combination is powerful because:

- **Plain text format** - Markdown is easy for AI to read, understand, and modify
- **File-based structure** - AI agents can navigate your vault like a file system
- **Version control friendly** - Changes can be tracked with Git
- **No vendor lock-in** - Your notes work with any AI tool that can read files
- **Context awareness** - AI can understand relationships between notes through links
- **Batch operations** - AI can modify multiple notes at once consistently

## Common Use Cases

Here's what AI can help you do with your Obsidian vault:

### Content Creation & Enhancement
- 📝 **Expand outlines** into full notes
- ✍️ **Summarize** long meeting notes or articles
- 🎯 **Generate templates** for recurring note types
- 📋 **Create tables of contents** automatically
- 🔤 **Improve writing** - fix grammar, adjust tone, clarify ideas

### Organization & Structure
- 🔗 **Suggest links** between related notes
- 🏷️ **Generate tags** based on content
- 📁 **Reorganize notes** into better folder structures
- 🗂️ **Create MOCs** (Maps of Content) from groups of notes
- 🧹 **Clean up** inconsistent formatting across multiple notes

### Knowledge Work
- 💡 **Answer questions** about your vault's content
- 🔍 **Find connections** you didn't notice
- 📊 **Extract insights** from collected notes
- 🎓 **Generate study materials** from your notes
- 📚 **Create summaries** of entire topic areas

## AI Tools You Can Use

### CLI-Based AI Agents

These tools work directly with your vault folder through the command line:

![[CodexCLI.png]]

![[GeminiCLI.png]]

**Popular CLI tools:**
- **Claude CLI / Codex** - Navigate and modify notes with natural language
- **Aider** - AI pair programming tool that works great with markdown
- **Cursor** - AI code editor that treats your vault as a project
- **ChatGPT CLI** - Direct command-line access to GPT models

**Advantages:**
- Full file system access to your entire vault
- Can make batch changes across multiple files
- Works with version control (Git)
- Most powerful for complex operations

### Editor Integration

Use AI-enabled editors to work with your vault:

- **VS Code** with GitHub Copilot or Cursor extension
- **Cursor Editor** - Open your vault folder as a project
- **Any IDE** with AI plugins can work with markdown files

### Obsidian Plugins

Unfortunately I didn't find any Obsidian Plugins that did a good job.  Instead I use VS.Code opened to the same Vault folder.
## Getting Started

### Simple Example: Summarizing Notes

**Task:** "Create a summary of all my meeting notes from this week"

```bash
# Using Claude CLI
claude "Read all files in ./Meetings folder from this week and create a summary in ./Summaries/Weekly-Summary.md"
```

### Example: Creating Links

**Task:** "Find notes that should link to each other"

```bash
# Using an AI agent
cursor "Review all notes in ./Projects folder and suggest which notes should link to each other based on related topics"
```

### Example: Generating Content

**Task:** "Turn my quick bullet points into a full article"

Within Obsidian using Text Generator plugin:
1. Select your bullet points
2. Run command: "Generate Text from Selection"
3. Prompt: "Expand these points into a well-structured article"

## Best Practices

**🔐 Privacy Considerations**
- Use local AI models for sensitive/personal notes
- Review what you send to cloud-based AI services
- Consider using tools with privacy-focused modes

**🎯 Start Small**
- Begin with simple tasks like formatting or summarization
- Gradually move to more complex operations
- Always review AI-generated changes before committing

**💾 Use Version Control**
- Keep your vault in Git
- Commit before major AI operations
- Easy to revert if AI makes unwanted changes

**🔄 Iterate and Refine**
- AI might not get it perfect on first try
- Provide feedback and ask for adjustments
- Build up a collection of prompts that work well

**📖 Build Context**
- Give AI relevant context about your vault structure
- Explain your note-taking system
- Reference your templates and conventions

## Example Workflows

### Workflow 1: Weekly Review
1. AI summarizes all daily notes from the week
2. Extracts action items and key decisions
3. Creates a weekly summary note with links back to daily notes
4. Suggests follow-up notes to create

### Workflow 2: Research Organization
1. Drop multiple research articles/notes into a folder
2. AI reads all content and identifies themes
3. Creates a MOC (Map of Content) linking related ideas
4. Generates tags for each note
5. Suggests additional research questions

### Workflow 3: Content Creation
1. Brain dump ideas into a note as bullet points
2. AI expands bullets into structured sections
3. AI suggests internal links to existing notes
4. AI improves clarity and flow
5. You review and refine the final output

## The Future is Here

AI + Obsidian isn't just about automation - it's about **augmenting your thinking**. Your notes become a living knowledge base that you can have intelligent conversations with, helping you make connections, generate insights, and work more effectively.

The best part? You're always in control. Your notes remain plain markdown files that you own and can use with any tool, now or in the future.
