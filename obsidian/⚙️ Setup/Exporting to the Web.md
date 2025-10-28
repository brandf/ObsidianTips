# Exporting to the Web

I use [Quartz 4](https://quartz.jzhao.xyz/) to export my Obsidian vault to a static website via GitHub Actions. Quartz is a static site generator designed specifically for digital gardens and knowledge bases.

## What is Quartz?

Quartz transforms your Obsidian vault into a beautiful website with:
- ✨ **Obsidian-native rendering** - Wikilinks, embeds, callouts, canvas files all work
- 🔍 **Full-text search** across all notes
- 📊 **Interactive graph view** of connections
- 🔗 **Automatic backlinks** on every page
- ⚡ **Fast static site** generation
- 📱 **Mobile-friendly** responsive design
- 🎨 **Customizable themes** - Fonts, colors, layouts

## Easy Setup with Template

The simplest way to get started is using my template repository that has everything pre-configured.

### Requirements

- **Node.js >= 20** (preferably 22+)
- **npm >= 10.9.2**

Check your versions:
```bash
node --version  # Should be v20.0.0 or higher
npm --version   # Should be 10.9.2 or higher
```

If you need to upgrade Node.js, download from [nodejs.org](https://nodejs.org/)

### Quick Start

**Step 1: Use the Template**

Go to the template repository and click "Use this template":
- [Obsidian Website Template Repository](https://github.com/brandf/ObsidianWebsiteTemplate)

> **⚠️ Note:** GitHub will run a workflow when you create the repo, but it will fail initially. This is expected - you need to enable GitHub Pages first.

**Step 2: Enable GitHub Pages (Do This First!)**

Before cloning:
1. Go to your new repository on GitHub
2. Click **Settings** → **Pages**
3. Under "Build and deployment", set Source to: **GitHub Actions**
4. Click **Save**

**Step 3: Clone and Configure**

```bash
git clone https://github.com/yourusername/your-repo-name.git
cd your-repo-name

# Run the interactive setup script
.\scripts\setup.ps1
```

The setup script will:
- Prompt for your site title, GitHub username, and repo name
- Optionally configure analytics
- Update all configuration files automatically
- Install dependencies

**Step 4: Add Your Content**

Add your Obsidian notes to the `obsidian/` folder:
- Copy notes from your existing vault
- Or use the `obsidian/` folder as your vault in Obsidian
- Edit `obsidian/index.md` to customize your homepage

**Step 5: Test Locally**

```bash
npm run serve
```

Visit `http://localhost:8080` to preview your site.

**Step 6: Deploy**

```bash
git add .
git commit -m "Add my content"
git push
```

GitHub Actions will automatically build and deploy your site!

Visit `https://yourusername.github.io/your-repo-name/` in a few minutes to see it live.

## What the Template Provides

The template includes:
- ✅ **Pre-configured Quartz** - Optimized settings ready to go
- ✅ **GitHub Actions workflow** - Automatic deployment on push
- ✅ **Build & serve scripts** - Easy local development
- ✅ **Interactive setup script** - One command configuration
- ✅ **Example vault structure** - Organized emoji folders (🌱 Life, 👥 People, 💡 Ideas, etc.)
- ✅ **Note templates** - Daily notes, person notes, and more
- ✅ **Master vault support** - Link multiple repo vaults as projects
- ✅ **Sensible defaults** - `.gitignore`, structure, configs all set up

## Project Structure

```
your-repo/
├── obsidian/              # Your Obsidian vault content
│   ├── index.md          # Homepage
│   ├── 🌱 Life/         # Example folders
│   ├── 👥 People/
│   ├── 💡 Ideas/
│   ├── 📄 Templates/    # Note templates (excluded from site)
│   └── ...
├── scripts/              # Build and utility scripts
│   ├── build-site.ps1   # Build script
│   ├── serve-site.ps1   # Dev server script
│   ├── setup.ps1        # Interactive setup
│   └── master-vault.ps1 # Multi-repo linking
├── .github/
│   └── workflows/
│       └── deploy.yml    # GitHub Actions deployment
├── quartz.config.ts      # Quartz configuration
├── package.json          # Node dependencies
└── .gitignore           # Git ignore rules
```

## Customization

### Exclude Content

Edit `quartz.config.ts` to exclude folders:

```typescript
ignorePatterns: [
  "private",
  ".obsidian",
  "📄 Templates/**",  # Templates won't show up on the site
  "drafts",
],
```

### Change Theme

Edit `quartz.config.ts` theme section:

```typescript
theme: {
  typography: {
    header: "Schibsted Grotesk",
    body: "Source Sans Pro",
    code: "IBM Plex Mono",
  },
  colors: {
    lightMode: {
      light: "#faf8f8",
      dark: "#2b2b2b",
      secondary: "#284b63",
      // ... more colors
    },
  },
}
```

### Custom Homepage

Edit `obsidian/index.md` to create a custom landing page with your own content, links, and structure.

### Add Analytics

In `quartz.config.ts`:

```typescript
analytics: {
  provider: "plausible",
  host: "https://plausible.io"
}
```

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
```

2. Add projects:
```bash
.\scripts\master-vault.ps1 -Add ProjectA
.\scripts\master-vault.ps1 -Add ProjectB
```

3. Sync (creates symlinks in `obsidian/🚧 Projects/`):
```bash
.\scripts\master-vault.ps1 -Sync
```

This makes all project notes accessible in your published site while keeping them in separate repositories.

## Canvas Support

Quartz has **limited** support for Obsidian Canvas files (`.canvas`):
- Canvas files are parsed and linked notes are included
- However, the visual canvas layout is **not rendered** on the web
- Instead, canvas files show as a list of linked notes
- Consider converting important canvas structures to regular notes for better web display

For best results, use canvas files for personal organization and create summary notes for publication.

## Publishing Workflow

After initial setup, your workflow is:

1. ✍️ Write notes in Obsidian
2. 💾 Commit and push to GitHub
3. 🤖 GitHub Actions automatically builds and deploys (1-2 minutes)
4. 🌐 View at `https://yourusername.github.io/your-repo-name/`

## Troubleshooting

**Build fails?**
- Check GitHub Actions logs for specific errors
- Ensure Node version is 20 or higher
- Try running `npm run serve` locally to debug

**Links broken?**
- Use Obsidian wikilinks: `[[Note Name]]`
- Links are case-sensitive!
- Check `ignorePatterns` isn't excluding linked notes

**Images not showing?**
- Use Obsidian embed syntax: `![[image.png]]`
- Images must be in the `obsidian/` folder
- Check image isn't in an ignored folder

**404 errors on GitHub Pages?**
- Verify baseUrl in `quartz.config.ts` matches your GitHub Pages URL
- Should be: `yourusername.github.io/repo-name` (no https://)

**Templates showing on site?**
- Add `"📄 Templates/**"` to `ignorePatterns` in `quartz.config.ts`
- Use glob patterns like `**` to exclude entire directories

## Manual Setup (Alternative)

If you prefer not to use the template, you can set up Quartz manually in your existing vault:

### 1. Install Quartz

```bash
npm init -y
npm install --save-dev git+https://github.com/jackyzha0/quartz.git
cd node_modules/@jackyzha0/quartz && npm install && cd ../../..
```

### 2. Organize Your Vault

Move your Obsidian content into an `obsidian/` subfolder within your repo. This keeps your notes separate from build scripts and configuration.

### 3. Configure Quartz

Create `quartz.config.ts` in your repo root (see template for full example).

### 4. Create Build Scripts

Create PowerShell scripts (see template repository) for building and serving locally.

### 5. Add GitHub Action

Create `.github/workflows/deploy.yml` (see template for full example).

### 6. Update package.json

Add scripts:
```json
"scripts": {
  "build": "pwsh -File scripts/build-site.ps1",
  "serve": "pwsh -File scripts/serve-site.ps1"
}
```

## Resources

- [Quartz Documentation](https://quartz.jzhao.xyz/)
- [Example Sites](https://quartz.jzhao.xyz/showcase)
- [Quartz Discord](https://discord.gg/cRFFHYye7t)
- [Template Repository](https://github.com/brandf/ObsidianWebsiteTemplate)

## Why This Setup?

This setup gives you:
- 🆓 **Free hosting** via GitHub Pages
- 🔒 **You own your data** - Plain markdown files in Git
- 🔄 **Version control** - Full history of all changes
- 🤖 **Automatic deployment** - Push and it's live
- 💻 **Local preview** - See changes before publishing
- 🔗 **Portable** - Not locked into any platform
- 🎨 **Customizable** - Full control over appearance and features
