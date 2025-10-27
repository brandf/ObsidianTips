# Exporting to the Web

I use [Quartz 4](https://quartz.jzhao.xyz/) to export my Obsidian vault to a static website via GitHub Actions. Quartz is a static site generator designed specifically for digital gardens and knowledge bases.

## What is Quartz?

Quartz transforms your Obsidian vault into a beautiful website with:
- ✨ **Obsidian-native rendering** - Wikilinks, embeds, callouts all work
- 🔍 **Full-text search** across all notes
- 📊 **Interactive graph view** of connections
- 🔗 **Automatic backlinks** on every page
- ⚡ **Fast static site** generation
- 📱 **Mobile-friendly** responsive design

## Simple Setup (3 Steps)

### Step 1: Add Quartz to Your Vault

In your Obsidian vault directory (which is already a Git repo), run:

```bash
# Initialize NPM (if you haven't already)
npm init -y

# Install Quartz as a dependency
npx quartz create content

# This will:
# - Create necessary config files
# - Set up the Quartz content directory
# - Link your vault files
```

After running, you'll have:
- `quartz.config.ts` - Configuration file
- `quartz.layout.ts` - Layout customization
- `package.json` - With Quartz as a dependency

### Step 2: Configure Quartz

Edit `quartz.config.ts` in your vault root:

```typescript
import { QuartzConfig } from "./quartz/cfg"
import * as Plugin from "./quartz/plugins"

const config: QuartzConfig = {
  configuration: {
    pageTitle: "My Digital Garden",
    enableSPA: true,
    enablePopovers: true,
    analytics: null,
    baseUrl: "yourusername.github.io/your-vault-name",
    ignorePatterns: [
      "private",
      ".obsidian",
      "templates"
    ],
  },
  plugins: {
    transformers: [
      Plugin.FrontMatter(),
      Plugin.CreatedModifiedDate(),
      Plugin.SyntaxHighlighting(),
      Plugin.ObsidianFlavoredMarkdown(),
      Plugin.GitHubFlavoredMarkdown(),
      Plugin.TableOfContents(),
      Plugin.CrawlLinks(),
      Plugin.Description(),
      Plugin.Latex(),
    ],
    emitters: [
      Plugin.AliasRedirects(),
      Plugin.ComponentResources(),
      Plugin.ContentPage(),
      Plugin.FolderPage(),
      Plugin.TagPage(),
      Plugin.ContentIndex(),
      Plugin.Assets(),
      Plugin.Static(),
      Plugin.NotFoundPage(),
    ],
  },
}

export default config
```

**Key settings to change:**
- `pageTitle` - Your site name
- `baseUrl` - Your GitHub Pages URL
- `ignorePatterns` - Folders/files to exclude

### Step 3: Add GitHub Action

Create `.github/workflows/deploy.yml` in your vault:

```yaml
name: Deploy to GitHub Pages

on:
  push:
    branches: [ main ]  # or master, depending on your branch
  workflow_dispatch:

permissions:
  contents: read
  pages: write
  id-token: write

concurrency:
  group: pages
  cancel-in-progress: false

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v4
        with:
          fetch-depth: 0  # Needed for git info

      - name: Setup Node
        uses: actions/setup-node@v4
        with:
          node-version: 20

      - name: Install dependencies
        run: npm install

      - name: Build site
        run: npx quartz build

      - name: Upload artifact
        uses: actions/upload-pages-artifact@v3
        with:
          path: public

  deploy:
    needs: build
    runs-on: ubuntu-latest
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```

### Step 4: Enable GitHub Pages

1. Go to your vault's GitHub repository
2. **Settings** → **Pages**
3. Under "Build and deployment", set Source to: **GitHub Actions**

That's it! Push your changes and GitHub Actions will automatically build and deploy your site.

## Testing Locally

Preview your site before deploying:

```bash
npx quartz build --serve
```

Visit `http://localhost:8080` to see your site.

## Customization

### Exclude Private Content

In `quartz.config.ts`:

```typescript
ignorePatterns: [
  "private",
  "drafts",
  ".obsidian",
  "templates",
],
```

### Custom Homepage

Create an `index.md` in your vault root:

```markdown
---
title: Welcome to My Garden
---

# Welcome!

Explore my notes on:
- [[Topic 1]]
- [[Topic 2]]

Use the search or graph view to discover more!
```

### Custom Theme

Edit `quartz/styles/custom.scss`:

```scss
:root {
  --light: #faf8f8;
  --dark: #141021;
  --secondary: #284b63;
  --tertiary: #84a59d;
}
```

### Analytics (Optional)

In `quartz.config.ts`:

```typescript
analytics: {
  provider: "plausible",
  host: "https://plausible.io"
}
```

## Workflow

After initial setup, your publishing workflow is:

1. ✍️ Write notes in Obsidian
2. 💾 Commit and push to GitHub
3. 🤖 GitHub Actions automatically builds and deploys
4. 🌐 View at `https://yourusername.github.io/your-vault-name/`

Usually takes 1-2 minutes from push to live.

## Troubleshooting

**Build fails?**
- Check GitHub Actions logs for specific errors
- Ensure Node version is 18 or higher
- Try running `npx quartz build` locally to debug

**Links broken?**
- Use Obsidian wikilinks: `[[Note Name]]`
- Case-sensitive! Make sure linked files exist
- Check `ignorePatterns` isn't excluding linked notes

**Images not showing?**
- Use Obsidian embed syntax: `![[image.png]]`
- Images must be in your vault (not `.obsidian` folder)
- Check image isn't in an ignored folder

**Want to use a custom domain?**
- Add a `CNAME` file to your vault root with your domain
- Configure DNS per [GitHub's instructions](https://docs.github.com/en/pages/configuring-a-custom-domain-for-your-github-pages-site)

## Gitignore Recommendations

Add to your `.gitignore`:

```
# Quartz build artifacts
.quartz-cache/
public/
node_modules/

# Keep this
!quartz.config.ts
!quartz.layout.ts
!package.json
```

## Resources

- [Quartz Documentation](https://quartz.jzhao.xyz/)
- [Example Sites](https://quartz.jzhao.xyz/showcase)
- [Quartz Discord](https://discord.gg/cRFFHYye7t)
