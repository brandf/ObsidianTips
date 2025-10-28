# One Vault to Rule Them All

![[Projects.png]]

The "master vault" pattern is a powerful way to unify multiple project-specific Obsidian vaults into a single, searchable knowledge base while keeping each project's documentation version-controlled with its code.

## The Problem

Many developers face a dilemma with [[AboutObsidian|Obsidian]] workflows:

**Option 1: One Big Vault**
Keep all notes in one vault for easy cross-linking and unified search.
- ✅ Easy to link between projects
- ✅ Unified graph view
- ✅ One search to find everything
- ❌ Project docs not versioned with code
- ❌ Can't easily collaborate on project docs
- ❌ Harder to share project-specific documentation

**Option 2: Separate Project Vaults**
Keep each project's [[Using Obsidian with GitHub|obsidian folder in its GitHub repo]].
- ✅ Documentation versioned with code
- ✅ Easy project-specific collaboration
- ✅ Can publish project docs independently
- ❌ No cross-project linking
- ❌ Have to open multiple vaults
- ❌ Can't see connections between projects

**The Master Vault Solution**
Using symlinks, we can have BOTH - project docs stay in their repos, but all appear in one master vault.

## How It Works

The master vault pattern uses symbolic links to bring external project vaults into your [[My Personal Vault|personal vault]]:

```
GitHub/
├── PersonalVault/              # Your master vault
│   ├── 📅 Daily/
│   ├── 👥 People/
│   ├── 💡 Ideas/
│   └── 🚧 Projects/           # Symlinks to project vaults
│       ├── ProjectA/          → ../../ProjectA/obsidian/
│       ├── ProjectB/          → ../../ProjectB/obsidian/
│       └── ProjectC/          → ../../ProjectC/obsidian/
├── ProjectA/
│   ├── src/
│   ├── obsidian/              # Project A's docs
│   └── README.md
├── ProjectB/
│   ├── src/
│   ├── obsidian/              # Project B's docs
│   └── README.md
└── ProjectC/
    ├── src/
    ├── obsidian/              # Project C's docs
    └── README.md
```

When you open `PersonalVault` in [[AboutObsidian|Obsidian]], all the project vaults appear as subfolders, but they're actually symlinks pointing to the real folders in each [[Using Obsidian with GitHub|GitHub repository]].

## Benefits

**Unified Knowledge Graph**
Link personal insights in your [[My Personal Vault|daily notes]] to specific project documentation. The [[How Obsidian Works - Details#Graph|graph view]] shows connections across all your work.

**Version Control Where It Matters**
Project documentation stays in Git with the code. When you edit project docs from your master vault, changes are made to the files in the project repo.

**One Search, All Projects**
Search once in your master vault to find information across all projects and your personal notes.

**Independent Publishing**
Each project can be [[Exporting to the Web|published independently via Quartz]] while your [[My Personal Vault|personal vault]] stays private.

**Context Integration**
Meeting notes about Project A (in your daily notes) can link directly to Project A's technical documentation. Six months later, backlinks show you exactly when you discussed specific features.

## Setup with PowerShell Script

I've created a PowerShell script that manages the symlinks automatically. It's included in the [[Exporting to the Web#What the Template Provides|template repository]].

### Prerequisites

**Windows:**
- PowerShell (built-in)
- Developer Mode enabled OR run PowerShell as Administrator
- All project repos in sibling folders

**Organization:**
```
GitHub/
├── PersonalVault/          # Your master vault (has the script)
├── ProjectA/               # Sibling project
│   └── obsidian/
├── ProjectB/               # Sibling project
│   └── obsidian/
└── ProjectC/               # Sibling project
    └── obsidian/
```

### Using the Script

**Add a Project:**
```powershell
cd PersonalVault
.\scripts\master-vault.ps1 -Add ProjectA
```

This adds `ProjectA` to the managed list and creates a symlink at `PersonalVault/obsidian/🚧 Projects/ProjectA` pointing to `../ProjectA/obsidian`.

**Add Multiple Projects:**
```powershell
.\scripts\master-vault.ps1 -Add ProjectA
.\scripts\master-vault.ps1 -Add ProjectB
.\scripts\master-vault.ps1 -Add ProjectC
```

**Sync All Projects:**
```powershell
.\scripts\master-vault.ps1 -Sync
```

This:
- Creates/updates symlinks for all projects in the list
- Removes orphaned symlinks (projects no longer in the list)
- Validates that target folders exist

**List Configured Projects:**
```powershell
.\scripts\master-vault.ps1 -List
```

**Remove a Project:**
```powershell
.\scripts\master-vault.ps1 -Remove ProjectB
```

This removes the symlink and removes the project from the managed list.

**Dry Run (Preview Changes):**
```powershell
.\scripts\master-vault.ps1 -Sync -DryRun
```

Shows what would happen without actually making changes.

### How the Script Works

The script maintains a simple text file (`scripts/master-vault.txt`) listing project names:

```
# My Projects
ProjectA
ProjectB
ProjectC
```

When you run `-Sync`, it:
1. Reads this list
2. Creates `obsidian/🚧 Projects/<ProjectName>` symlink → `../../<ProjectName>/obsidian`
3. Validates the target exists
4. Prunes any symlinks not in the list

The `🚧 Projects/` folder is gitignored, so symlinks don't get committed.

## Using the Master Vault

Once set up, using the master vault is seamless:

**Opening in Obsidian**
Just open your personal vault - all project vaults appear as subfolders.

**Editing Project Docs**
Edit files normally. Changes are saved to the actual project repo, ready to commit.

**Linking Across Vaults**
Create [[How Obsidian Works - Details#Links|wikilinks]] from personal notes to project docs:

```markdown
In my [[📅 Daily/2024-10-28|daily note]]:
Working on the authentication system for [[🚧 Projects/ProjectA/Auth Design]].
```

The backlinks on the project doc now show when you discussed it in daily notes!

**Searching Everything**
Obsidian's search works across all symlinked folders. One search finds results in personal notes and all projects.

**Graph View**
The [[How Obsidian Works - Details#Graph|graph view]] shows connections between:
- Personal notes and project docs
- Daily notes and project discussions
- Ideas that reference multiple projects
- Cross-project architectural patterns

## Publishing Considerations

When [[Exporting to the Web|publishing with Quartz]], you have options:

**Publish Personal Vault (Including Projects)**
If you publish your personal vault, the symlinked projects will be included. Use `ignorePatterns` in `quartz.config.ts` to exclude:

```typescript
ignorePatterns: [
  "🚧 Projects/**",  // Exclude all projects
  // Or selectively:
  "🚧 Projects/PrivateProject/**",  // Exclude specific projects
]
```

**Publish Individual Projects**
Each project can have its own [[Exporting to the Web#Quick Start|Quartz setup]] to publish just that project's docs independently.

**Hybrid Approach**
Keep your [[My Personal Vault|personal vault]] private, publish some projects independently. The master vault is just for your local Obsidian experience.

## Workflow Integration

The master vault pattern integrates beautifully with other workflows:

**Canvas First**
Create a [[Canvas First Workflow|canvas in your personal vault]] that embeds notes from multiple projects. Visually organize how different projects relate.

**AI Assistance**
When [[Using AI with Obsidian|using AI agents]], they can now access context from:
- Personal notes explaining your thinking
- Project documentation with technical details
- Daily notes showing project evolution
- Cross-project patterns and decisions

**Daily Notes**
Your [[My Personal Vault#Daily Notes as the Foundation|daily notes]] can reference work across all projects:

```markdown
# 2024-10-28

## ProjectA
- Fixed [[🚧 Projects/ProjectA/Authentication Bug]]
- Discussed approach with [[👥 People/Alice]]

## ProjectB
- Started [[🚧 Projects/ProjectB/API Redesign]]
- Need to apply patterns from [[🚧 Projects/ProjectA/API Architecture]]
```

## Troubleshooting

**Symlink Creation Fails (Windows)**

If you get "Administrator required" errors:
1. Enable Windows Developer Mode: Settings → Update & Security → For developers → Developer Mode
2. OR run PowerShell as Administrator

**Links Don't Work**

Make sure:
- Project folder names match exactly (case-sensitive on some systems)
- Target `obsidian/` folder exists in the project repo
- You've run `-Sync` to create the symlinks

**Symlinks Disappeared**

If symlinks vanish after `-Sync`:
- Check that projects are in `scripts/master-vault.txt`
- Verify projects are sibling folders to your vault
- Use `-DryRun` to see what the script would do

**Changes Not Reflected in Git**

Remember: Changes to symlinked files are made to the actual project repo. Commit from the project folder:

```bash
cd ../ProjectA
git status          # See your changes
git add obsidian/
git commit -m "Update docs"
git push
```

**Obsidian Performance**

If your master vault gets large:
- Exclude projects you're not actively working on
- Use [[Best Obsidian Plugins#Omnisearch|Omnisearch plugin]] for faster search
- Consider a smaller set of active projects in the master vault

## Alternative Approaches

If PowerShell scripts and symlinks aren't your style:

**Manual Symlinks**
Create symlinks manually:

```powershell
# Windows
New-Item -ItemType SymbolicLink -Path "PersonalVault\obsidian\🚧 Projects\ProjectA" -Target "..\ProjectA\obsidian"

# Mac/Linux
ln -s ../ProjectA/obsidian PersonalVault/obsidian/🚧Projects/ProjectA
```

**Obsidian Workspaces**
Open multiple vaults and switch between them. Less elegant but no symlinks needed.

**One Vault Only**
Accept the tradeoff - use one vault for everything and don't version-control notes with code.

**Separate Vaults Only**
Keep vaults separate and accept opening multiple vaults. Use tools that can search across folders.

## Why This Pattern Works

The master vault pattern succeeds because it:

**Respects Project Boundaries**
Each project's documentation stays with its code, making it easy for teams to collaborate using [[Using Obsidian with GitHub|standard Git workflows]].

**Enables Cross-Project Thinking**
Your [[My Personal Vault|personal insights]] and [[My Personal Vault#Daily Notes as the Foundation|daily notes]] can reference and link to any project, creating a unified view of your work.

**Scales With You**
Start with a few projects, add more as needed. Remove inactive projects. The symlink approach adapts to your current focus.

**Leverages Obsidian's Strengths**
The [[How Obsidian Works - Details#Links|linking]], [[How Obsidian Works - Details#Graph|graphing]], and search features work across all content without requiring any special configuration.

**Maintains Publishing Flexibility**
Each part of your knowledge base can be [[Exporting to the Web|published or kept private]] independently based on your needs.

## Getting Started

To implement the master vault pattern:

1. **Organize your repos** as siblings in a folder
2. **Ensure each project has** an `obsidian/` subfolder
3. **Create your [[My Personal Vault|personal vault]]** in the same parent folder
4. **Copy the `master-vault.ps1` script** from the template repo
5. **Add projects one by one** with `-Add ProjectName`
6. **Open your personal vault** in [[AboutObsidian|Obsidian]]
7. **Start linking** personal notes to project docs

The result is a unified knowledge base that respects project boundaries while enabling cross-project insights and connections.

## Learn More

- [[My Personal Vault]] - Setting up a personal knowledge hub
- [[Using Obsidian with GitHub]] - Versioning notes with code
- [[How I Use Obsidian]] - Complete workflow overview
- [[Exporting to the Web]] - Publishing your knowledge
- [[How Obsidian Works - Details#Links|How Links Work]] - Understanding wikilinks
- [[How Obsidian Works - Details#Graph|Graph View]] - Visualizing connections
