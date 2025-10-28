# Migrating to Obsidian

Switching note-taking systems is daunting, but Obsidian's plain-text markdown format makes it one of the most migration-friendly options. This guide covers practical strategies for moving from popular platforms.

## General Migration Principles

### Before You Start

**Critical questions to answer:**

1. **Why are you migrating?** (Clarity prevents regret mid-migration)
2. **What must come with you?** (Active notes vs. archives)
3. **Can you tolerate a hybrid approach?** (Keep old system read-only)
4. **How much time can you dedicate?** (Full vs. gradual migration)

### The Three Migration Strategies

**1. Cold Turkey (Full Migration)**
- Export everything, convert all at once, switch completely
- ✅ Clean break, forces commitment
- ⚠️ High upfront time investment, disruptive

**2. Gradual Migration (Recommended)**
- Move active notes first, old system becomes read-only archive
- ✅ Less disruptive, test Obsidian with real work
- ⚠️ Maintaining two systems temporarily

**3. Fresh Start**
- Start new notes in Obsidian, reference old system as needed
- ✅ Minimal migration effort, cleanest vault
- ⚠️ Knowledge fragmentation

**Most people find gradual migration the sweet spot.**

### What to Expect

**Reality check:**
- 🔴 Not everything will convert perfectly
- 🔴 Some formatting will break
- 🔴 Proprietary features won't transfer (databases, embeds, etc.)
- 🟢 Plain text and images convert well
- 🟢 Link structure often translates
- 🟢 Markdown content is usually clean

**Plan for 20-30% post-migration cleanup time.**

## From Notion

Notion is one of the most common migration sources, but its proprietary features make this challenging.

### Export Process

1. **Workspace Settings** → **Settings & Members**
2. **Export all workspace content**
3. Choose **Markdown & CSV** format
4. **Export** → Downloads ZIP file
5. Extract ZIP to temporary folder

### What Exports Well

✅ Basic text and headings
✅ Simple tables (as CSV or markdown)
✅ Images and attachments
✅ Links between pages
✅ Code blocks

### What Doesn't Export Well

❌ Databases (export as CSV, lose functionality)
❌ Inline databases (export as simple tables)
❌ Callouts (convert to `>` blockquotes)
❌ Toggle lists (become flat lists)
❌ Embedded content (links only)
❌ Comments and discussions
❌ Page relationships and properties

### Conversion Steps

**1. Initial Import**
```markdown
1. Extract Notion export ZIP
2. Copy all .md files to new Obsidian vault
3. Copy images to attachments folder
4. Open vault in Obsidian
```

**2. Fix File Structure**
- Notion exports with spaces in filenames (works fine, but optional to change)
- Notion creates UUID subfolders (flatten if desired)
- Move images to dedicated attachment folder

**3. Fix Notion-Specific Formatting**

**Callouts**: Notion exports callouts as plain blockquotes
```markdown
Notion export:
> 💡 This is a callout

Convert to Obsidian callout:
> [!info]
> This is a callout
```

**Toggle lists**: Become regular headings, manually convert if needed

**Databases**: CSV exports need manual conversion
- Simple lists → Bullet points
- Tables → Markdown tables or Dataview
- Linked databases → Create manual links or use Dataview

**4. Link Cleanup**

Notion exports links with URL encoding:
```markdown
Bad: [[Page%20With%20Spaces]]
Good: [[Page With Spaces]]
```

**Fix with Find & Replace:**
- Find: `%20`
- Replace: ` ` (space)

### Structure Adaptation

**Notion's hierarchy:**
```
Workspace → Pages → Sub-pages → Blocks
```

**Obsidian's approach:**
```
Vault → Folders → Notes → Links
```

**Migration strategy:**
1. Top-level pages → Folders or MOC notes
2. Sub-pages → Individual notes in folders
3. Databases → Tags + Dataview queries or manual indexes

### Post-Migration Notion Workflow

**Option 1**: Keep Notion read-only for reference
**Option 2**: Export databases as CSV, import to Dataview

**For databases**, consider:
- Simple task lists → Obsidian Tasks plugin
- Content databases → Dataview with frontmatter
- Reference tables → Markdown tables with links

### Notion Migration Timeline

- **Day 1**: Export and initial import (2-4 hours)
- **Day 2-3**: Folder structure and file organization (3-5 hours)
- **Week 1**: Fix formatting and links (5-10 hours)
- **Week 2+**: Gradually clean up remaining issues as you use notes

## From Evernote

Evernote's export is more straightforward than Notion's, but has its own challenges.

### Export Process

1. **File** → **Export Notes** (desktop app)
2. Select all notebooks or specific notebooks
3. Export format: **ENEX** (Evernote's XML format)
4. Save .enex files

### Converting ENEX to Markdown

**Option 1: Yarle (Recommended)**
```bash
npm install -g yarle
yarle --enex "path/to/export.enex" --output "path/to/obsidian/vault"
```

**Option 2: Obsidian Importer Plugin**
- Install **Obsidian Importer** community plugin
- Import ENEX files directly
- Handles attachments and basic formatting

**Option 3: Manual (not recommended for bulk)**

### Tag Migration

Evernote tags → Obsidian tags (mostly direct translation)

```markdown
Evernote: work, project-alpha, important

Obsidian note frontmatter:
---
tags: [work, project-alpha, important]
---

Or inline: #work #project-alpha #important
```

**Decision point**: Frontmatter vs. inline tags vs. both?
- Frontmatter: Cleaner reading, better for Dataview
- Inline: More contextual, easier to add/remove
- Both: Most flexible, some redundancy

### What Converts Well

✅ Note text and formatting
✅ Tags
✅ Images and attachments (with Yarle)
✅ Note titles
✅ Notebooks → Can become folders

### What Doesn't Convert Well

❌ Note links (Evernote uses internal IDs)
❌ Web clipper metadata
❌ Reminders (convert to tasks manually)
❌ Notebooks as organization (you need to create folder structure)
❌ Saved searches (recreate in Obsidian)

### Post-Migration Cleanup

1. **Review folder structure**: Notebooks export flat, organize by topic/project
2. **Recreate note links**: Evernote links break—find references and manually link
3. **Convert reminders**: Use Tasks plugin or Dataview
4. **Handle web clippings**: Decide to keep, summarize, or delete

### Evernote Migration Timeline

- **Day 1**: Export and convert (1-3 hours)
- **Day 2**: Import and initial organization (2-4 hours)
- **Week 1**: Tag review and folder structure (3-5 hours)
- **Ongoing**: Fix links as you encounter them

## From Roam Research

Roam users often find Obsidian familiar due to shared linking philosophy.

### Export Process

1. Click **⋯** (three dots menu)
2. **Export All**
3. Choose **JSON** format
4. Download JSON file

### Converting JSON to Markdown

**Option 1: Roam-to-Obsidian Converter**
- Install **Markdown Importer** community plugin
- Supports Roam JSON import
- Handles block references with some limitations

**Option 2: Custom scripts**
- GitHub: `roam-to-git` or similar converters
- More control but requires technical knowledge

### Block Reference Conversion

This is the biggest challenge. Roam's block references don't directly translate.

**Roam block reference:**
```
((block-id-abc123))
```

**Obsidian options:**
1. **Embed blocks**: Use block IDs `![[note#^block-id]]`
2. **Regular links**: Convert to full note links
3. **Copy content**: For short blocks, just duplicate content

**Realistic approach**: Convert most block references to regular note links, manually handle critical block embeds.

### Daily Notes

Roam's daily notes are central; Obsidian has similar functionality.

**Migration:**
1. Enable Core **Daily Notes** plugin
2. Set date format to match Roam (often `YYYY-MM-DD`)
3. Move Roam daily notes to daily notes folder
4. Update templates

### Bidirectional Links

Both Roam and Obsidian support bidirectional links—this transfers well!

```markdown
Roam: [[Note Name]]
Obsidian: [[Note Name]]
```

Direct translation, no changes needed.

### What Converts Well

✅ Page links (wikilinks)
✅ Daily notes
✅ Tags
✅ Basic markdown formatting
✅ Code blocks
✅ Images

### What Doesn't Convert Well

❌ Block references (require manual handling)
❌ Block embeds (need reconstruction)
❌ Queries (Roam queries ≠ Dataview, must rewrite)
❌ Page attributes (convert to frontmatter)
❌ Namespaced pages (flatten or create folder structure)

### Roam Migration Timeline

- **Day 1**: Export and convert (1-2 hours)
- **Day 2**: Import and structure review (2-3 hours)
- **Week 1**: Block reference fixes, daily notes setup (3-5 hours)
- **Week 2+**: Query rewrites and ongoing adjustments

## From Apple Notes

Apple Notes is convenient but limited in export options.

### Export Process

**Challenge**: Apple Notes has no native bulk export to markdown.

**Option 1: Exporter App (Mac only)**
- Use third-party tool like **Exporter** or **CloudPull**
- Select notes and export to plain text or HTML
- Convert HTML to markdown manually or with Pandoc

**Option 2: Manual Copy-Paste**
- Open note in Apple Notes
- Copy content (Cmd+A, Cmd+C)
- Paste into Obsidian note
- Repeat for each note (tedious for large libraries)

**Option 3: Script-Based (Technical)**
```bash
# Using osascript to access Apple Notes database
# Search GitHub for "apple-notes-exporter" scripts
```

### Export Limitations

❌ No official bulk export
❌ Images embedded in proprietary format
❌ Attachments difficult to extract
❌ No link preservation
❌ Limited formatting in export

### Workarounds

**For images:**
1. Right-click image in Apple Notes
2. **Copy** or **Save Image**
3. Paste/save to Obsidian attachments folder
4. Link manually in markdown: `![[image.png]]`

**For tables:**
- Apple Notes tables export as plain text
- Reformat as markdown tables manually

### Realistic Approach

Given limitations, consider:
- **Gradual migration**: Only migrate active/important notes
- **Leave archive**: Keep Apple Notes as read-only reference
- **Fresh start**: Use migration as opportunity to review and rebuild

### Apple Notes Migration Timeline

- **Per note**: 2-5 minutes depending on complexity
- **100 notes**: 5-10 hours (with images/formatting)
- **Recommendation**: Migrate selectively, not exhaustively

## From OneNote

OneNote's organizational model differs significantly from Obsidian's flat structure.

### Export Process

**Challenge**: OneNote has no direct markdown export.

**Option 1: OneNote Batch Exporter Plugin**
1. Download community tool (search GitHub)
2. Export sections/notebooks to HTML or DOCX
3. Convert to markdown with Pandoc

**Option 2: Manual Export**
1. **File** → **Export** in OneNote
2. Export as **PDF** or **Word Document**
3. Convert with Pandoc:
```bash
pandoc input.docx -t markdown -o output.md
```

**Option 3: Copy-Paste with Markdown Formatting**
- Use **Obsidian Web Clipper** to paste formatted text
- Preserves basic formatting

### What Doesn't Transfer

❌ Section organization (no equivalent)
❌ Embedded files (extract manually)
❌ Ink/drawing annotations (export as images)
❌ Audio/video recordings (save separately)
❌ Page templates (recreate in Obsidian)
❌ Tags (OneNote tags ≠ Obsidian tags)

### Structure Adaptation

**OneNote hierarchy:**
```
Notebook → Section Group → Section → Page → Subpage
```

**Obsidian equivalent:**
```
Vault → Folder → Folder → Note → Heading/Link
```

**Migration strategy:**
1. Notebook → Vault folder
2. Section → Note or subfolder
3. Page → Note
4. Subpage → Linked note or heading in parent

### OneNote Migration Timeline

- **Day 1-2**: Export notebooks (varies widely)
- **Week 1**: Convert to markdown (5-15 hours)
- **Week 2**: Restructure and link notes (10-20 hours)
- **Reality**: OneNote migration is time-intensive

## Post-Migration Cleanup

Regardless of source system, expect cleanup work.

### Broken Links Audit

**Week 1 post-migration:**
1. Search for `[[]]` (empty links)
2. Use **Graph View** to find disconnected clusters
3. Fix or remove broken references

### Formatting Fixes

**Common issues:**
- Extra blank lines
- Inconsistent heading levels
- Code blocks without language tags
- Stray HTML from conversion
- Incorrect list formatting

**Tools to help:**
- **Linter** plugin: Auto-format according to rules
- Find & Replace: Batch fix patterns
- **Markdown Format Importer**: Normalize from various sources

### Link Consolidation

You may have duplicate concepts from old system:
```markdown
[[Project Alpha]]
[[project-alpha]]
[[Project_Alpha]]
```

**Fix:**
1. Choose canonical name: `[[Project Alpha]]`
2. Search for variations
3. Replace with canonical version
4. Delete duplicate notes

### Frontmatter Standardization

Converted notes may have inconsistent metadata:

```markdown
Before:
---
title: Some Note
date: 2024-01-15
category: work
---

Standardize to:
---
title: Some Note
created: 2024-01-15
tags: [work]
---
```

Use Find & Replace or Linter to normalize.

## Gradual vs Full Migration

### Full Migration

**When to choose:**
- Small library (<500 notes)
- Dissatisfied with current system
- Can afford 1-2 weeks of setup time
- Want clean break

**Process:**
1. Export everything
2. Convert in bulk
3. Import to Obsidian
4. Cleanup phase (2-3 weeks)
5. Close old system

### Gradual Migration

**When to choose:**
- Large library (>1000 notes)
- Can't afford disruption
- Uncertain about Obsidian
- Want to test workflow first

**Process:**
1. Set up Obsidian with templates/plugins
2. Start all NEW notes in Obsidian
3. Migrate frequently-used notes from old system
4. Leave archive in old system (read-only)
5. Migrate more over 3-6 months as needed

**Benefits:** Less pressure, learn Obsidian while migrating, only migrate what matters.

## What to Keep vs What to Leave Behind

### Migration is a Filter

Use this opportunity to curate your knowledge base.

**Questions to ask each note:**
- Have I referenced this in the last year?
- Is this still accurate/relevant?
- Does this spark ideas or just clutter?
- Would I be upset if I lost this?

### Categories to Consider

**✅ Definitely migrate:**
- Active project notes
- Reference material you use regularly
- Core knowledge base
- Ongoing learning notes
- Templates and processes

**⚠️ Evaluate carefully:**
- Completed project notes (archive vs migrate?)
- Old meeting notes (summarize instead?)
- Duplicated web content (link instead?)
- Rough drafts (clean up first?)

**❌ Consider leaving behind:**
- Truly outdated content
- Notes you can't even remember creating
- Duplicates of published content
- Temporary/scratch notes
- Personal notes you've outgrown

### The 80/20 Rule

**Reality**: 80% of your value comes from 20% of your notes.

**Strategy**: Migrate the vital 20% with care, leave the rest as searchable archive in old system.

## Migration Checklist

### Pre-Migration
- [ ] Understand why you're migrating
- [ ] Choose migration strategy (full/gradual/fresh)
- [ ] Backup existing notes (always!)
- [ ] Set up Obsidian vault structure
- [ ] Install essential plugins
- [ ] Create templates for common note types

### During Migration
- [ ] Export from source system
- [ ] Convert to markdown
- [ ] Import to Obsidian
- [ ] Verify attachments transferred
- [ ] Initial link audit
- [ ] Test search and navigation

### Post-Migration
- [ ] Fix broken links (ongoing)
- [ ] Standardize formatting
- [ ] Add frontmatter where needed
- [ ] Reorganize folder structure if needed
- [ ] Set up templates and workflows
- [ ] Document your system
- [ ] Test backup/sync solution

### Week 2-4
- [ ] Review orphan notes
- [ ] Connect isolated clusters
- [ ] Refine folder structure
- [ ] Optimize plugins
- [ ] Final link cleanup

## Common Migration Mistakes

### 1. Trying to Migrate Everything

**Mistake**: Treating old system as sacred archive.
**Better**: Migrate what's valuable, leave the rest accessible but separate.

### 2. Not Testing First

**Mistake**: Migrating 5,000 notes before understanding Obsidian.
**Better**: Migrate 50 notes, use for a week, then proceed.

### 3. Ignoring Cleanup

**Mistake**: Import everything, never fix formatting/links.
**Better**: Schedule cleanup time, tackle systematically.

### 4. Over-Organizing Immediately

**Mistake**: Spending weeks creating perfect folder structure.
**Better**: Simple structure first, refine as usage patterns emerge.

### 5. Forgetting Backups

**Mistake**: Deleting old system immediately after migration.
**Better**: Keep old system read-only for 3-6 months minimum.

## Key Takeaways

✅ Perfect migration is impossible—aim for "good enough"
✅ Gradual migration often works better than full migration
✅ Use migration as opportunity to curate and improve notes
✅ Keep old system as read-only backup for months
✅ Accept some manual cleanup work is inevitable
✅ Test with small subset before bulk migration

**Remember**: The goal isn't to perfectly replicate your old system in Obsidian—it's to build a better knowledge management workflow. Don't let migration paralysis stop you from starting.

---

**Related Guides**
- [[Getting Started with Obsidian]] - Set up your vault properly before migrating
- [[Note-Taking Methodologies]] - Rethink your approach while migrating
- [[Vault Maintenance]] - Keep your migrated vault healthy long-term
