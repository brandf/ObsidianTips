# Vault Maintenance

Keeping your Obsidian vault healthy is essential for long-term productivity. Regular maintenance prevents accumulation of broken links, orphaned notes, and performance issues.

## Finding Broken Links

Obsidian's core **Backlinks** plugin helps identify broken links, but you need to enable it first.

### Using the Core Backlinks Plugin

1. **Settings** → **Core plugins** → Enable **Backlinks**
2. Open any note and check the **Backlinks** pane
3. Look for items marked as "Unlinked mentions"

### Manual Search Method

The most reliable way to find ALL broken links:

1. Open **Command Palette** (Ctrl/Cmd + P)
2. Search: "Search"
3. Enter search query: `[[]]` (finds empty links)
4. Or use regex search: `/\[\[.*?\]\]/`

### Common Causes of Broken Links

- Renamed notes without updating links
- Deleted notes still referenced elsewhere
- Case sensitivity issues (especially on Linux)
- Moved notes to different folders
- Special characters in filenames

**Fix Strategy**: Click the broken link → Create the note, or update the link to point to the correct note.

## Orphan Notes

Orphan notes have no incoming or outgoing links—they're isolated islands in your knowledge graph.

### Finding Orphans

**Option 1: Graph View**
1. Open **Graph view** (Ctrl/Cmd + G)
2. Isolated nodes (dots with no connections) are orphans
3. Click to open and add links

**Option 2: Dataview Plugin**
```dataview
TABLE file.ctime as Created
WHERE length(file.inlinks) = 0 AND length(file.outlinks) = 0
SORT file.ctime DESC
```

**Option 3: Community Plugins**
- **Strange New Worlds**: Specifically designed to find orphans
- **Linter**: Can flag orphans during lint operations

### What to Do with Orphans

**Don't automatically delete them!** Orphans aren't always bad:

- ✅ **Valid orphans**: Daily notes, templates, standalone reference documents
- ⚠️ **Review needed**: Old drafts, forgotten ideas, temporary notes
- ❌ **Delete candidates**: Truly obsolete or duplicate content

**Best practice**: Review orphans monthly, link valuable ones into your knowledge graph, archive or delete the rest.

## Cleaning Up Attachments

Attachments and images can accumulate quickly, eating storage and slowing sync.

### Find Unused Attachments

**Manual method:**
1. Check your attachment folder (usually `/attachments` or `/assets`)
2. Sort by date or size
3. Search vault for each filename to see if it's referenced

**Plugin method:**
- **Consistent Attachments and Links**: Renames and cleans up attachment files
- **Clear Unused Images**: Finds and deletes unreferenced images

### Cleanup Steps

```markdown
1. Backup first! (Always)
2. Use "Clear Unused Images" plugin to identify unused files
3. Review the list carefully (some files may be embedded in external links)
4. Delete or move to archive folder
5. Check vault still works correctly
```

### Prevention Strategy

- Set attachment folder location: **Settings** → **Files & Links** → **Default location for new attachments**
- Use descriptive filenames for images (easier to identify later)
- Delete attachments when deleting notes that use them
- Consider using external image hosting for large files

## Vault Health Checks

### Monthly Health Check Routine

**Week 1: Link Integrity**
- [ ] Search for broken links
- [ ] Review recently renamed notes
- [ ] Check graph view for unexpected disconnections

**Week 2: Content Review**
- [ ] Identify orphan notes
- [ ] Review notes with no recent modifications (3+ months)
- [ ] Archive or link orphans

**Week 3: File Management**
- [ ] Clean up unused attachments
- [ ] Check file sizes (find exceptionally large notes)
- [ ] Review folder structure

**Week 4: Performance**
- [ ] Monitor vault load time
- [ ] Check plugin performance
- [ ] Review and disable unused plugins

### Health Metrics to Monitor

```markdown
- Total note count: ___
- Average links per note: ___
- Orphan percentage: ___% (aim for <10%)
- Vault size: ___ MB
- Number of attachments: ___
- Plugin count: ___ (fewer is often better)
```

## Archiving Old Notes

Not everything needs to stay active in your vault. Archiving keeps your workspace clean while preserving content.

### When to Archive

- ✅ Completed project notes
- ✅ Outdated reference material
- ✅ Historical daily notes (older than 1 year)
- ✅ Superseded versions of notes
- ⚠️ Notes you haven't touched in 6+ months (review first)

### Archive Structure

Create an `Archive` folder with subfolders:

```
📁 Archive/
  📁 2024/
    📁 Projects/
    📁 Daily Notes/
    📁 Reference/
  📁 2023/
  📁 2022/
```

### Archive Process

1. Create archive folder structure
2. Move note to appropriate archive subfolder
3. Update any links pointing to archived note
4. Add `#archived` tag before moving (makes it findable)
5. Consider adding archive date: `archived: 2024-10-28`

**Pro tip**: Use a tag like `#archive-candidate` to mark notes for future archiving, then batch process monthly.

## Performance Optimization

Large vaults (5,000+ notes) can slow down. Here's how to keep things snappy.

### Common Performance Issues

**Symptom**: Slow startup
- **Cause**: Too many plugins, large images in startup note
- **Fix**: Disable unused plugins, move large images to attachments folder

**Symptom**: Laggy typing
- **Cause**: Real-time sync plugins, excessive Dataview queries on current note
- **Fix**: Adjust sync settings, optimize queries, reduce live preview complexity

**Symptom**: Slow search
- **Cause**: Vault size, too many excluded folders not properly indexed
- **Fix**: Use core search, exclude archive folders from search

### Optimization Checklist

```markdown
- [ ] Keep plugin count under 20 active plugins
- [ ] Disable plugins you don't use daily
- [ ] Use relative links instead of absolute paths
- [ ] Compress large images before adding
- [ ] Exclude archive folders from search indexing
- [ ] Split extremely large notes (>10,000 words)
- [ ] Use file explorer "Show inline title" sparingly
- [ ] Restart Obsidian weekly to clear cache
```

### Plugin Performance Tips

Some plugins are resource-intensive:
- **Dataview**: Great but can slow down with many queries—cache results
- **Calendar**: Minimal impact
- **Excalidraw**: Heavy with many drawings open
- **Kanban**: Light, well-optimized
- **Advanced Tables**: Negligible impact

**Check plugin performance**: Help → Toggle Developer Tools → Performance tab

## Backup Strategies

Your notes are valuable. Multiple backup strategies = peace of mind.

### The 3-2-1 Rule

- **3** copies of your data
- **2** different storage mediums
- **1** copy off-site

### Backup Methods

**Method 1: Git + GitHub/GitLab**
- ✅ Version control, free for private repos, accessible anywhere
- ⚠️ Learning curve, requires command line or plugin
- 📖 See: [[Using Obsidian with GitHub]]

**Method 2: Obsidian Sync**
- ✅ Automatic, version history, encrypted
- ⚠️ Paid service ($10/month)
- 📖 See: [[Sync Strategies Compared]]

**Method 3: Cloud Storage (Dropbox, OneDrive, iCloud)**
- ✅ Automatic sync across devices
- ⚠️ Sync conflicts possible, no version control
- 📖 See: [[Sync Strategies Compared]]

**Method 4: Manual Backup**
- ✅ Complete control, simple
- ⚠️ Easy to forget, no automation
- **How**: Copy entire vault folder to external drive monthly

**Method 5: Automated Local Backup**
```batch
REM Windows batch script - run weekly
xcopy "C:\MyVault" "D:\Backups\Vault_%date%" /E /I /Y
```

### Backup Testing

**Don't assume backups work!** Test your restore process:

1. Create test vault with sample notes
2. Perform backup
3. Delete test vault
4. Restore from backup
5. Verify all notes, attachments, and settings restored

Do this test **before** you need it.

## Reorganization Best Practices

Eventually, your vault structure may need a refresh.

### Signs You Need Reorganization

- Can't find notes quickly
- Folder structure doesn't match how you think
- Too many notes in root folder
- Folder nesting more than 3 levels deep
- Notes scattered without clear system

### Planning Your Reorganization

**Don't rush!** A bad reorganization is worse than no reorganization.

1. **Audit current structure**: What works? What doesn't?
2. **Define principles**: Organize by project? Topic? Date? [[Note-Taking Methodologies]] can help
3. **Test with subset**: Move 10-20 notes to new structure
4. **Live with it for a week**: Does it feel natural?
5. **Commit or revert**: Full reorganization or keep old structure

### Reorganization Process

```markdown
1. Backup entire vault first!
2. Create new folder structure (without moving notes yet)
3. Move notes in small batches (10-20 at a time)
4. Update links after each batch
5. Check for broken links
6. Repeat until complete
7. Archive old empty folders
```

### Minimize Link Breakage

- Use **Unique Note Names**: Makes linking easier regardless of location
- Enable **Settings** → **Files & Links** → **Automatically update internal links**
- Use **Wikilinks** over Markdown links (easier to update)
- Consider using **folder notes** to maintain structure references

### After Reorganization

- Review [[My Personal Vault]] to update your documentation
- Update any index notes or MOCs
- Check graph view for unexpected changes
- Monitor for broken links over next week
- Document your new system

## Maintenance Tools

### Essential Plugins for Maintenance

| Plugin | Purpose | Priority |
|--------|---------|----------|
| Consistent Attachments and Links | Rename/move with auto-link updates | High |
| Strange New Worlds | Find orphan notes | Medium |
| Linter | Enforce formatting standards | Medium |
| Clear Unused Images | Remove unreferenced images | Low |
| Janitor | Automated cleanup tasks | Low |

### Built-in Tools

- **Quick Switcher** (Ctrl/Cmd + O): Fast navigation
- **Search** (Ctrl/Cmd + Shift + F): Find anything
- **Command Palette** (Ctrl/Cmd + P): Access all commands
- **Graph View** (Ctrl/Cmd + G): Visualize connections

## Maintenance Schedule Template

Create a note called `Vault Maintenance Log` with this template:

```markdown
## 2024-10-28 Maintenance

### Checks Performed
- [ ] Broken links scan
- [ ] Orphan note review
- [ ] Attachment cleanup
- [ ] Plugin performance check

### Issues Found
- X broken links (fixed)
- X orphan notes (reviewed, archived Y)
- X MB unused attachments (deleted)

### Actions Taken
- [List what you did]

### Notes
- [Any observations or improvements for next time]

Next maintenance: 2024-11-28
```

## Key Takeaways

✅ Regular maintenance prevents problems before they escalate
✅ Broken links and orphans are normal—review and fix monthly
✅ Multiple backup methods provide redundancy
✅ Performance optimization matters more as vault grows
✅ Reorganize thoughtfully and infrequently

**Remember**: A well-maintained vault is a joy to use. Set aside 30 minutes monthly for these tasks—your future self will thank you.

---

**Related Guides**
- [[Using Obsidian with GitHub]] - Version control and backup
- [[Sync Strategies Compared]] - Sync and backup options
- [[My Personal Vault]] - Example vault structure and maintenance practices
