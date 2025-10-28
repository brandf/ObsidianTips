# Obsidian + Quartz Digital Garden Template

This template allows you to publish your Obsidian vault as a beautiful static website using [Quartz 4](https://quartz.jzhao.xyz/) and GitHub Pages.

## What This Template Provides

- ✅ **One-command setup** - Interactive configuration script
- ✅ **GitHub Actions workflow** - Automatic deployment on push
- ✅ **Pre-configured Quartz** - Optimized settings out of the box
- ✅ **Build & serve scripts** - Easy local development
- ✅ **Example vault structure** - Organized emoji folders (Life, People, Ideas, etc.)
- ✅ **Note templates** - Daily notes, person notes, and more
- ✅ **Master vault support** - Link multiple repo vaults as projects
- ✅ **Sensible defaults** - `.gitignore`, structure, and configs ready to go
- ✅ **Free hosting** - Deploy to GitHub Pages at no cost
- ✅ **Full Quartz features** - Search, graph view, backlinks, themes, and more

## Quick Start

### 1. Requirements

Make sure you have **Node.js >= 20** installed:
- Download from [nodejs.org](https://nodejs.org/) (get the LTS version)
- Or use a version manager like [nvm](https://github.com/nvm-sh/nvm) or [fnm](https://github.com/Schniz/fnm)

Check your version:
```bash
node --version  # Should be v20.0.0 or higher
```

### 2. Use This Template

Click "Use this template" button above to create your own repository.

> **⚠️ Note:** GitHub will automatically run the deployment workflow when you create the repo, but it will fail with "Ensure GitHub Pages has been enabled". This is expected - you need to enable GitHub Pages first (see step 7 below).

### 3. Enable GitHub Pages (Do This First!)

**Before cloning or making any changes**, enable GitHub Pages:

1. Go to your new repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Build and deployment", set Source to: **GitHub Actions**
4. Click **Save**

This prevents the initial workflow failure and ensures subsequent pushes will deploy automatically.

### 4. Clone and Setup

```bash
git clone https://github.com/brandf/ObsidianTips.git
cd ObsidianTips

# Run the interactive setup script
.\scripts\setup.ps1
```

The setup script will:
- Prompt for your site title, GitHub username, and repo name
- Optionally configure analytics
- Update all configuration files automatically
- Install dependencies (npm packages)

**Or** configure manually by editing `quartz.config.ts`:
- Change `pageTitle` to your site name
- Update `baseUrl` to `brandf.github.io/ObsidianTips`
- Customize fonts and colors in the `theme` section

### 4. Add Your Content

Add your Obsidian notes to the `obsidian/` folder:

- **Option 1: Copy files** - Copy notes from your existing vault into `obsidian/`
- **Option 2: Use as vault** - Open the `obsidian/` folder as a vault in Obsidian
- **Option 3: Symlink** (advanced) - Symlink your existing vault to `obsidian/`

Start by editing `obsidian/index.md` to customize your homepage!

### 5. Test Locally

```bash
npm run serve
```

Visit `http://localhost:8080` to preview your site.

### 6. Deploy

```bash
git add .
git commit -m "Configure my digital garden"
git push
```

### 7. Enable GitHub Pages

1. Go to your repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Build and deployment", set Source to: **GitHub Actions**

GitHub Actions will automatically build and deploy your site!

Visit `https://brandf.github.io/ObsidianTips/` in a few minutes to see it live.

## Local Development

### Build the site:
```bash
npm run build
```

The output will be in `./public/`

### Run development server:
```bash
npm run serve
```

Visit `http://localhost:8080` to preview your site locally.

## Requirements

- **Node.js >= 20** (preferably 22+)
- **npm >= 10.9.2**

Check your versions:
```bash
node --version  # Should be v20.0.0 or higher
npm --version   # Should be 10.9.2 or higher
```

## Customization

### Exclude Private Notes

In `quartz.config.ts`, add patterns to `ignorePatterns`:

```typescript
ignorePatterns: [
  "private",
  ".obsidian",
  "drafts",
],
```

### Change Theme Colors

Edit the `theme.colors` section in `quartz.config.ts`:

```typescript
colors: {
  lightMode: {
    light: "#faf8f8",
    dark: "#2b2b2b",
    secondary: "#284b63",
    // ... more colors
  },
  darkMode: {
    // ... dark mode colors
  },
}
```

### Change Fonts

Edit `theme.typography` in `quartz.config.ts`:

```typescript
typography: {
  header: "Schibsted Grotesk",  // Google Font name
  body: "Source Sans Pro",
  code: "IBM Plex Mono",
},
```

### Custom Homepage

Create or edit `obsidian/index.md` to customize your homepage.

### Add Analytics (Optional)

In `quartz.config.ts`:

```typescript
analytics: {
  provider: "plausible",
  host: "https://plausible.io"
}
```

## Project Structure

```
your-repo/
├── obsidian/              # Your Obsidian vault content
│   ├── index.md          # Homepage
│   └── ...               # Your notes
├── scripts/              # Build and serve scripts
│   ├── build-site.ps1   # Build script
│   └── serve-site.ps1   # Dev server script
├── .github/
│   └── workflows/
│       └── deploy.yml    # GitHub Actions deployment
├── quartz.config.ts      # Quartz configuration
├── package.json          # Node dependencies
└── .gitignore           # Git ignore rules
```

## Workflow

After initial setup:

1. ✍️ Write notes in the `obsidian/` folder
2. 💾 Commit and push to GitHub
3. 🤖 GitHub Actions automatically builds and deploys
4. 🌐 View at `https://brandf.github.io/ObsidianTips/`

Deployment usually takes 1-2 minutes.

## Troubleshooting

**Build fails with "requires Node >= 20"**
- Upgrade Node.js to version 20 or higher
- Run `npm install` again

**Links not working**
- Use Obsidian wikilinks: `[[Note Name]]`
- Check that linked notes exist
- Ensure they're not in ignored directories

**Images not showing**
- Use Obsidian embed syntax: `![[image.png]]`
- Verify images are in the `obsidian/` folder
- Check they're not in ignored folders

**Site not updating**
- Check GitHub Actions tab for build status
- Ensure you pushed to the `main` branch
- Wait 1-2 minutes for deployment

**Permission errors with symlinks (Windows)**
- Run PowerShell as Administrator
- Or enable Developer Mode in Windows Settings

## Advanced: Master Vault (Multi-Repo)

If you have multiple repositories with Obsidian vaults and want to link them all in one published site, use the `master-vault.ps1` script.

### Setup

1. Organize your repos in a parent folder:
```
GitHub/
├── ObsidianVault/        # This repo (the published site)
├── ProjectA/
│   └── obsidian/         # Project A's vault
├── ProjectB/
│   └── obsidian/         # Project B's vault
└── ProjectC/
    └── obsidian/         # Project C's vault
```

2. Add projects to the list:
```bash
.\scripts\master-vault.ps1 -Add ProjectA
.\scripts\master-vault.ps1 -Add ProjectB
```

3. Sync (creates symlinks in `obsidian/🚧 Projects/`):
```bash
.\scripts\master-vault.ps1 -Sync
```

### Usage

```bash
# List configured projects
.\scripts\master-vault.ps1 -List

# Add a project
.\scripts\master-vault.ps1 -Add <ProjectName>

# Remove a project
.\scripts\master-vault.ps1 -Remove <ProjectName>

# Sync projects (default if no flags)
.\scripts\master-vault.ps1 -Sync

# Don't prune orphaned symlinks
.\scripts\master-vault.ps1 -Sync -NoPrune

# Dry run (see what would happen)
.\scripts\master-vault.ps1 -Sync -DryRun
```

This creates symlinks like `obsidian/🚧 Projects/ProjectA` → `../ProjectA/obsidian`, making all project notes accessible in your published site.

**Note:** Add `obsidian/🚧 Projects/*` to `.gitignore` (already included) to avoid committing the symlinks.

## Using with an Existing Vault

If you have an existing Obsidian vault:

### Option 1: Copy Files
```bash
cp -r /path/to/your/vault/* obsidian/
```

### Option 2: Use as Your Vault
Open the `obsidian/` folder as a vault in Obsidian.

### Option 3: Symlink (Advanced)
```bash
# Windows (PowerShell as Admin)
New-Item -ItemType SymbolicLink -Path "obsidian" -Target "C:\path\to\your\vault"

# Mac/Linux
ln -s /path/to/your/vault obsidian
```

## Resources

- [Quartz Documentation](https://quartz.jzhao.xyz/)
- [Quartz GitHub](https://github.com/jackyzha0/quartz)
- [Example Sites](https://quartz.jzhao.xyz/showcase)
- [Obsidian Help](https://help.obsidian.md/)

## License

MIT License - Feel free to use this template for your own digital garden!

## Credits

- [Quartz](https://github.com/jackyzha0/quartz) by Jacky Zhao
- [Obsidian](https://obsidian.md/)
