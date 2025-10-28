# Using Obsidian with GitHub

[[AboutObsidian|Obsidian]] is fundamentally just a sophisticated front-end for plain markdown files. This makes it a perfect companion for GitHub - your notes can be version-controlled, collaborated on, and integrated with your code projects using standard Git workflows.

## The Obsidian + Git Pattern

I use a convention where each GitHub project has an `obsidian/` folder at the root that can be opened as an Obsidian vault:

```
YourProject/
├── src/              # Your code
├── tests/
├── obsidian/         # Project documentation as Obsidian vault
│   ├── index.md
│   ├── Architecture.md
│   ├── API.md
│   └── ...
├── README.md
└── package.json
```

This pattern means:
- **Documentation lives with code** - Changes to docs can be reviewed alongside code changes
- **Version controlled together** - Docs and code stay in sync as the project evolves
- **Obsidian enhanced** - Get the benefits of [[How Obsidian Works - Details#Links|wikilinks]], [[How Obsidian Works - Details#Graph|graph view]], and backlinks for your project docs
- **Plain markdown fallback** - Even without Obsidian, docs are readable on GitHub

## Why This Works

**Git Is Made for Text Files**
Since [[How Obsidian Works|Obsidian notes are just markdown]], they work perfectly with Git:
- Easy to diff changes
- Merge conflicts are readable
- Full history of documentation evolution
- Branch documentation alongside code branches

**Team Collaboration**
Team members can:
- Edit docs in Obsidian (with all its features)
- Or edit in any text editor or directly on GitHub
- Review documentation changes in pull requests
- Discuss changes using GitHub's comment system

**Documentation That Stays Fresh**
When docs live with the code:
- You update them when you update code
- Code reviews catch outdated documentation
- Documentation versions match code versions
- No separate docs repo to keep in sync

**Local-First, Team-Accessible**
Get the benefits of [[AboutObsidian#1. Local-First & Private|local-first]] editing while enabling team collaboration through Git.

## Setting Up a Project Vault

**1. Create the Folder**
```bash
cd your-project
mkdir obsidian
```

**2. Add Initial Content**
Create `obsidian/index.md` as your project homepage:

```markdown
---
title: ProjectName Documentation
---

# ProjectName

Welcome to the project documentation!

## Getting Started
- [[Setup Guide]]
- [[Architecture]]
- [[API Reference]]

## Development
- [[Contributing]]
- [[Testing]]
- [[Deployment]]
```

**3. Configure .gitignore**
Add to your project's `.gitignore`:

```
# Obsidian workspace files (user-specific)
obsidian/.obsidian/workspace*
obsidian/.obsidian/hotkeys.json
obsidian/.obsidian/appearance.json

# Keep these (team-shared settings)
!obsidian/.obsidian/graph.json
!obsidian/.obsidian/templates.json
```

This keeps personal workspace settings out of Git while preserving shared configuration like graph settings and templates.

**4. Open in Obsidian**
- Launch [[AboutObsidian|Obsidian]]
- Open the `obsidian/` folder as a vault
- Start writing and linking docs

## Workflow Patterns

### Pattern 1: Documentation-Driven Development

Write documentation first using [[How Obsidian Works - Details#Links|wikilinks]] for concepts that don't exist yet:

```markdown
# Authentication System

The [[User Service]] will handle authentication using [[JWT Tokens]].
See [[Security Considerations]] for threat model.
```

Those red links (non-existent notes) become your development roadmap. Create the notes as you implement features, and the [[How Obsidian Works - Details#Graph|graph view]] shows your progress.

### Pattern 2: Code and Docs in Same PR

When working on a feature:
1. Create a feature branch
2. Implement the code
3. Write/update docs in `obsidian/`
4. Commit both together
5. Pull request reviews both code and docs

Example commit:
```bash
git add src/auth.js obsidian/Authentication.md
git commit -m "Add JWT authentication with docs"
```

### Pattern 3: Link to Code from Docs

Reference code files from documentation:

```markdown
# API Implementation

The main API router is in `src/api/routes.js`.

Key endpoints:
- `/auth` - See [[Authentication]]
- `/users` - See [[User Management]]

For the database schema, check [[Database Design]].
```

The documentation becomes a guide through the codebase, with [[How Obsidian Works - Details#Links|wikilinks]] connecting concepts and file references connecting to actual code.

### Pattern 4: Meeting Notes with Context

Use your [[My Personal Vault|personal vault]] for meeting notes, but link to project docs:

```markdown
# Meeting 2024-10-28

Discussed the [[🚧 Projects/MyProject/API Redesign]] with the team.

Decisions:
- Go with REST over GraphQL (see [[🚧 Projects/MyProject/API Architecture]])
- Target Q1 launch (see [[🚧 Projects/MyProject/Roadmap]])

Action items:
- [ ] Update [[🚧 Projects/MyProject/API Documentation]]
- [ ] Review [[🚧 Projects/MyProject/Security Model]]
```

This requires the [[One Vault to Rule Them All|master vault pattern]] to link personal notes to project docs.

## Publishing Project Docs

You can [[Exporting to the Web|publish your project docs]] to make them accessible to a wider audience:

**Option 1: Quartz on GitHub Pages**
Add a [[Exporting to the Web#Quick Start|Quartz setup]] to your project repo. The documentation at `yourname.github.io/yourproject/` updates automatically with each push.

**Option 2: Obsidian Publish**
Use Obsidian's official paid service to publish directly from the Obsidian app.

**Option 3: Copy to GitHub Wiki**
Convert the markdown files to GitHub wiki format. Less elegant but keeps everything on GitHub.

**Option 4: Generate Static Docs**
Use tools like Docusaurus, MkDocs, or VuePress that can consume your markdown files.

The beauty of using plain markdown is that you're not locked into any particular publishing solution.

## Team Collaboration Best Practices

**Establish Conventions**
Document in your `obsidian/index.md`:
- How to structure new notes
- Naming conventions for files
- When to use folders vs tags
- How to link to code files

**Use Templates**
Create note templates in `obsidian/📄 Templates/`:
- Feature documentation template
- API endpoint template
- Decision record template
- Bug investigation template

Share these via Git so the whole team uses consistent structure.

**Review Documentation in PRs**
Treat documentation changes like code:
- Check for broken [[How Obsidian Works - Details#Links|wikilinks]]
- Verify accuracy
- Suggest improvements
- Ensure clarity

**Sync Graph Settings**
Keep `.obsidian/graph.json` in version control so everyone sees the same [[How Obsidian Works - Details#Graph|graph layout]] and filters.

**Link Liberally**
The more [[How Obsidian Works - Details#Links|wikilinks]] between docs, the easier it is to navigate the knowledge base. Don't worry about over-linking.

## Integrating with AI

Project vaults work excellently with [[Using AI with Obsidian|AI assistance]]:

**Documentation Generation**
Ask AI to:
- Generate API documentation from code
- Create architectural diagrams
- Write getting-started guides
- Expand outline notes into full documentation

**Documentation Review**
AI can:
- Find broken links
- Identify outdated information
- Suggest missing documentation
- Improve clarity and consistency

**Cross-Referencing**
AI excels at:
- Adding [[How Obsidian Works - Details#Links|wikilinks]] between related docs
- Finding relevant notes for cross-reference
- Creating Maps of Content (MOCs)
- Building comprehensive indexes

Since the [[Using AI with Obsidian|obsidian folder is just markdown]], AI agents can read and edit project docs using standard file operations.

## Multi-Project Management

When you have multiple projects with `obsidian/` folders:

**Personal Vault Integration**
Use the [[One Vault to Rule Them All|master vault pattern]] to:
- Link all projects into your [[My Personal Vault|personal vault]]
- Search across all project docs at once
- See connections between projects in the [[How Obsidian Works - Details#Graph|graph]]
- Keep personal notes separate but accessible

**Project-Specific Vaults**
Each project gets its own isolated documentation, perfect for:
- Team collaboration (via Git)
- Project-specific [[Exporting to the Web|publishing]]
- Clean separation of concerns
- Focused context when working on one project

**Unified Knowledge Graph**
With the [[One Vault to Rule Them All|master vault]], your [[My Personal Vault#Daily Notes as the Foundation|daily notes]] can reference any project, creating a chronological thread through all your work.

## Troubleshooting

**Merge Conflicts in Docs**

Treat them like code:
```bash
# See the conflict
git status

# Edit the file to resolve
# Markdown conflicts are readable!

# Mark as resolved
git add obsidian/ConflictedFile.md
git commit
```

**Workspace Settings Conflicts**

If team members commit their personal workspace files:
```bash
# Add to .gitignore
echo "obsidian/.obsidian/workspace*" >> .gitignore

# Remove from Git but keep local
git rm --cached obsidian/.obsidian/workspace.json
git commit -m "Remove personal workspace from repo"
```

**Large Binary Files**

Avoid committing large images directly. Options:
- Use Git LFS for large images
- Link to external image hosting
- Compress images before committing
- Keep images in a separate `assets/` folder

**Symlinks Not Working**

If using the [[One Vault to Rule Them All|master vault pattern]] on Windows:
- Enable Developer Mode, OR
- Run commands as Administrator

## Advanced: Canvas for Architecture

The [[Canvas First Workflow|Canvas feature]] works great for project architecture:

Create `obsidian/Architecture.canvas` that visually shows:
- System components (as cards)
- Embedded notes for each component
- Arrows showing relationships
- Color-coding for different layers

This gives you a visual overview while keeping detailed docs in linked markdown files. The canvas itself is JSON, so it version-controls well with Git.

## Why It Works

This pattern succeeds because it:

**Meets Teams Where They Are**
Team members can use [[AboutObsidian|Obsidian]], VS Code, GitHub web editor, or any text editor. Everyone can contribute.

**Scales From Solo to Team**
Start with just yourself, add team members gradually. The pattern works at any scale.

**Preserves Git Workflows**
Branches, PRs, code review, CI/CD - all standard Git practices work with documentation.

**Enables Rich Features**
While keeping compatibility with plain markdown, you get [[How Obsidian Works - Details#Links|bidirectional links]], [[How Obsidian Works - Details#Graph|graph visualization]], and powerful search when using [[AboutObsidian|Obsidian]].

**Future-Proof**
Your docs are portable markdown. If Obsidian disappears tomorrow, your documentation is still perfectly readable and useful.

## Getting Started Checklist

To adopt this pattern:

- [ ] Create `obsidian/` folder in your project root
- [ ] Add `obsidian/index.md` as documentation homepage
- [ ] Configure `.gitignore` to exclude personal settings
- [ ] Create a few initial docs with [[How Obsidian Works - Details#Links|wikilinks]]
- [ ] Open in [[AboutObsidian|Obsidian]] and start writing
- [ ] Commit docs alongside code changes
- [ ] Consider [[One Vault to Rule Them All|master vault]] for multi-project setup
- [ ] Explore [[Exporting to the Web|publishing options]]
- [ ] Share conventions with your team

The result is documentation that lives with your code, stays in sync, and gives you the power of Obsidian's knowledge management features.

## Learn More

- [[One Vault to Rule Them All]] - Unifying multiple project vaults
- [[My Personal Vault]] - Personal knowledge management
- [[Exporting to the Web]] - Publishing project docs
- [[How Obsidian Works]] - Understanding the fundamentals
- [[Canvas First Workflow]] - Visual organization
- [[Using AI with Obsidian]] - AI-enhanced documentation
- [[Best Obsidian Plugins]] - Enhance your workflow
