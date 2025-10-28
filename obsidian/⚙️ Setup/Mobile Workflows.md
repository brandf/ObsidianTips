# Mobile Workflows

Mobile devices have become an essential part of the note-taking ecosystem, and Obsidian's mobile apps bring much of the desktop experience to your pocket. However, mobile comes with its own strengths, limitations, and optimal workflows. This guide covers practical strategies for making the most of Obsidian on mobile devices.

## Obsidian Mobile Overview

### Platform Differences

**iOS App**
- Available on iPhone and iPad
- Seamless integration with iOS share sheet
- Built-in support for iCloud sync
- Better file system integration
- Optimized for Apple Pencil on iPad
- Smooth gesture navigation
- Generally more stable plugin support

**Android App**
- Available on all Android devices
- Android share functionality
- More flexible file system access
- Greater freedom with sync options
- Works with various file managers
- Supports different keyboard layouts
- More customization options

### Core Capabilities

Both platforms support:
- Full markdown editing
- Bidirectional linking
- Graph view (though resource-intensive)
- Core plugins
- Many community plugins
- File management
- Themes and appearance customization
- Quick switcher and search
- Multiple vaults

## Quick Capture Workflows

The key to effective mobile use is optimizing for quick capture rather than extensive writing.

### Using Share Sheet (iOS)

The iOS share sheet is one of the most powerful quick capture tools:

**Setup:**
1. In Obsidian settings → Core plugins → enable "Quick Capture"
2. Configure your default capture note location
3. Optional: Create a capture template

**Capturing from anywhere:**
- Share text, links, or images to Obsidian
- Adds content directly to your capture note
- Include automatic timestamps if desired
- Process captured items later from desktop

**Best practices:**
- Set a dedicated "Inbox" note for captures
- Review and process captured items daily
- Use simple formatting that mobile handles well

### Share Functionality (Android)

Android's share functionality works similarly:
- Share to Obsidian from any app
- Appends to a designated capture note
- Can include URLs, text, and images
- Requires enabling Quick Capture plugin

### Quick Note Creation

**Mobile-optimized creation:**
- Use the "+" button or quick action
- Start with templates for consistency
- Keep initial structure simple
- Add metadata later from desktop

**Keyboard shortcuts (with external keyboard):**
- `Cmd/Ctrl + N` - New note
- `Cmd/Ctrl + O` - Open quick switcher
- `Cmd/Ctrl + E` - Toggle edit/preview

### Voice-to-Text Capture

Mobile excels at voice input:

**iOS dictation:**
- Tap microphone on keyboard
- Speak naturally with punctuation ("period", "comma")
- Works in any text field
- No special Obsidian configuration needed

**Android voice input:**
- Tap microphone on keyboard
- Use Gboard or other voice-enabled keyboards
- Similar punctuation commands
- Generally accurate for quick capture

**Best practices:**
- Review and clean up voice transcriptions later
- Use voice for quick thoughts, not polished writing
- Add proper formatting on desktop
- Consider creating "voice note" tag for later cleanup

### Templates on Mobile

Templates work on mobile but with limitations:

**What works:**
- Basic template insertion
- Core Templates plugin
- Simple variable substitution
- Date/time variables

**Limitations:**
- Complex Templater scripts may not work
- JavaScript-heavy templates can fail
- Some dynamic content may not render

**Mobile-optimized templates:**

```markdown
---
created: {{date:YYYY-MM-DD}}
tags: mobile-capture
---

# {{title}}

## Quick Notes


## Follow-up
- [ ] Process on desktop

```

**Template strategy:**
- Keep mobile templates simple
- Use basic variables only
- Create separate "mobile" versions of complex templates
- Test templates on mobile before relying on them

## Mobile-Optimized Vault Organization

Mobile devices demand simpler navigation structures.

### Simpler Folder Structures

**Desktop approach:**
```
Project/
  Meetings/
    2024/
      Q1/
        January/
```

**Mobile-friendly approach:**
```
Projects/
Meetings/
Archive/
Inbox/
```

**Principles:**
- Reduce nesting depth (2-3 levels max)
- Use wider, flatter structures
- Rely on tags and links instead of folders
- Keep frequently-accessed notes at top level

### MOCs as Navigation

Map of Contents (MOCs) are especially valuable on mobile:

**Example MOC for mobile:**

```markdown
# 📱 Mobile Hub

## Quick Access
- [[Daily Notes Workflow|Today's Note]]
- [[Inbox]] - Process captures
- [[Weekly Review]]

## Active Projects
- [[Project A Hub]]
- [[Project B Hub]]

## Reference
- [[Contacts MOC]]
- [[Resources MOC]]

## Templates
- [[Meeting Template]]
- [[Quick Note Template]]
```

**Benefits:**
- Single tap to main navigation
- No folder hunting
- Visual organization
- Easy to update

### Pinned Notes

Both iOS and Android support note pinning:

**Pin these types of notes:**
- Daily note template or today's note
- Main navigation MOC
- Inbox/capture note
- Current priority project
- Reading list

**Accessing pinned notes:**
- Show in file list at top
- Quick access from file explorer
- Available in quick switcher

## Sync Strategies for Mobile

Syncing is crucial for a seamless mobile experience. See [[Sync Strategies Compared]] for detailed comparison.

### Obsidian Sync (Easiest)

**Pros:**
- Works identically on iOS and Android
- End-to-end encrypted
- Version history included
- Handles conflicts automatically
- Syncs settings and plugins
- No file system setup needed

**Best for:**
- Users who want "it just works"
- Cross-platform users
- Those who value privacy
- Users syncing multiple vaults

**Setup:**
- Purchase Obsidian Sync subscription ($10/month)
- Enable in settings on all devices
- Connect to same vault
- Automatic syncing begins

### iCloud (iOS Only)

**Pros:**
- Free with Apple account
- Seamless iOS/macOS integration
- Uses native Files app
- Good for Apple ecosystem users

**Cons:**
- iOS/macOS only
- Can have sync conflicts
- Occasionally slow
- Doesn't sync settings/plugins
- Files need to finish syncing before editing

**Setup:**
1. On macOS, place vault in `~/Library/Mobile Documents/iCloud~md~obsidian/`
2. On iOS, vault appears automatically
3. Ensure "Optimize iPhone Storage" is off for reliability

### Alternatives for Android

**Syncthing (Free, Self-Hosted):**
- Peer-to-peer syncing
- No cloud storage needed
- Requires both devices online
- More technical setup
- Very reliable once configured

**Third-party cloud services:**
- **Dropbox**: Reliable but requires third-party file app
- **Google Drive**: Syncing can be inconsistent
- **OneDrive**: Similar to Google Drive
- **Sync.com**: E2E encrypted alternative

**Recommendation:**
For Android users serious about Obsidian, Obsidian Sync or Syncthing are most reliable.

## Mobile Plugins and Limitations

### Core Plugins That Work Well

**Fully functional:**
- File explorer
- Search
- Quick switcher
- Graph view (can be slow on large vaults)
- Backlinks
- Tags pane
- Page preview
- Templates
- Daily notes
- Random note

**Limited functionality:**
- Canvas (view only on many devices, limited editing)
- Audio recorder (device-dependent)

### Community Plugins on Mobile

**Works well on mobile:**
- Calendar plugin
- Kanban boards (with some lag on large boards)
- Dataview (simple queries)
- Templater (basic templates)
- Advanced Tables (basic functionality)

**Often problematic:**
- Plugins requiring desktop file system
- Plugins with complex UIs
- Resource-intensive plugins
- Plugins that modify many files at once

**Testing plugins:**
- Enable one at a time
- Test on mobile before relying on it
- Check plugin documentation for mobile support
- Be prepared to disable if it causes issues

### What Doesn't Work on Mobile

**Limitations to expect:**
- Complex Dataview queries can be slow
- Heavy graph view interactions
- Bulk file operations
- Advanced Templater scripts with JavaScript
- Some PDF annotation features
- Certain keyboard shortcuts
- Complex CSS snippets may not render
- Plugins requiring external programs

**Workaround strategy:**
- Do complex operations on desktop
- Use mobile for reading, capture, and simple edits
- Sync before attempting major changes
- Keep mobile use focused on strengths

## Mobile-Specific Tips

### Keyboard Shortcuts (External Keyboard)

If using iPad or Android tablet with keyboard:

**Essential shortcuts:**
- `Cmd/Ctrl + N` - New note
- `Cmd/Ctrl + O` - Quick switcher
- `Cmd/Ctrl + P` - Command palette
- `Cmd/Ctrl + E` - Toggle edit/reading mode
- `Cmd/Ctrl + F` - Find in note
- `Cmd/Ctrl + [/]` - Indent/unindent
- `Cmd/Ctrl + D` - Delete current line

**Link creation:**
- `Cmd/Ctrl + K` - Insert link
- `[[` then start typing - Create internal link

### Gesture Navigation

**iOS gestures:**
- Swipe from left edge - Navigate back
- Pull down - Access search
- Two-finger tap - Quick actions
- Pinch on graph view - Zoom
- Long press on link - Preview note

**Android gestures:**
- Swipe from left - Navigate back (if enabled)
- Pull down in file list - Refresh
- Long press - Context menu
- Device-specific gestures vary

### Viewing Modes

**Reading mode (Live Preview off):**
- Cleaner reading experience
- Better for reviewing notes
- Less risk of accidental edits
- Faster rendering on older devices

**Editing mode:**
- See markdown syntax
- Make quick changes
- Access full editing tools

**Live Preview mode:**
- Best of both worlds
- See rendered markdown while editing
- More resource-intensive

**Recommendation:**
- Default to reading mode on mobile
- Switch to editing only when needed
- Use Live Preview on newer devices

### Reading Workflows

Mobile excels at reading and reviewing:

**Effective reading setup:**
1. Use reading mode
2. Enable swipe navigation
3. Pin your reading list/MOC
4. Use backlinks to explore connections
5. Highlight passages (using markdown)
6. Add quick comments in brackets `[Note to self: review this]`

**Reading list workflow:**

```markdown
# 📚 Reading List

## Current
- [[Article Title 1]] - started 2024-10-15
- [[Book Notes - Title]] - in progress

## To Read
- [ ] [[Article Title 2]]
- [ ] [[Paper - Topic]]

## Completed
- [x] [[Article Title 3]] - completed 2024-10-10
```

## Cross-Device Workflows

The key to productivity is using each device for its strengths.

### Desktop for Deep Work

**Desktop excels at:**
- Long-form writing
- Heavy editing and restructuring
- Complex linking and organization
- Plugin management
- Bulk operations
- Canvas creation and editing
- Graph view exploration
- File system management
- Settings configuration

**Desktop tasks:**
- Weekly reviews
- Note refactoring
- Template creation
- Vault organization
- Processing inbox captures

### Mobile for Capture and Review

**Mobile excels at:**
- Quick capture anytime, anywhere
- Reading and reviewing notes
- Voice-to-text thoughts
- Sharing content from other apps
- Quick edits and additions
- Reference lookups
- Daily note creation
- On-the-go research review

**Mobile tasks:**
- Capturing ideas and tasks
- Morning/evening note reviews
- Reading while commuting
- Adding to daily notes
- Quick reference access
- Meeting notes (with template)

### Syncing Between Devices

**Best practices:**
- Let sync complete before editing same note
- Create "mobile-edited" tag if concerned about conflicts
- Use Obsidian Sync for most reliable experience
- Check sync status before making major changes
- Review conflict files if they appear

**Sync workflow:**
1. Make changes on one device
2. Wait for sync indicator to confirm upload
3. Open on other device
4. Confirm changes synced
5. Continue working

## Mobile Limitations and Workarounds

### Canvas on Mobile

**Current state:**
- Viewing works on most devices
- Editing is very limited
- Creating new canvases not recommended
- Performance issues on complex canvases
- Better on tablets than phones

**Workaround:**
- Create and edit canvases on desktop
- Use mobile for viewing only
- Use MOCs as mobile-friendly alternative
- Consider simpler visualization methods for mobile

### Plugin Limitations

**Common issues:**
- Plugins designed for desktop may not work
- Resource-intensive plugins slow performance
- Some plugins don't have mobile UI
- Settings may not sync properly

**Workarounds:**
- Test plugins on mobile before depending on them
- Disable problematic plugins on mobile only
- Use core functionality instead of plugins when possible
- Check plugin documentation for mobile support

### File Management

**Limitations:**
- Moving many files at once is cumbersome
- Renaming linked files requires careful sync
- Bulk operations are slow
- File system access varies by platform

**Workarounds:**
- Do bulk operations on desktop
- Use simple, flat folder structures
- Rely on links and tags more than folders
- Plan file organization from desktop

### Performance Considerations

**Large vaults on mobile:**
- Graph view can be very slow
- Search may take longer
- App startup slower with many plugins
- Sync takes longer

**Optimization tips:**
- Disable graph view if not needed
- Limit number of plugins on mobile
- Use search filters to narrow results
- Consider splitting into multiple vaults if very large
- Regularly archive old notes

## Final Tips for Mobile Success

1. **Keep it simple**: Mobile works best with straightforward workflows
2. **Embrace limitations**: Don't fight the platform, work with it
3. **Template everything**: Consistency matters more on mobile
4. **Use MOCs**: Better than folder navigation on small screens
5. **Quick capture only**: Save deep work for desktop
6. **Test regularly**: Ensure your workflow actually works on mobile
7. **Sync religiously**: Always ensure changes sync before switching devices
8. **Pin frequently**: Use pinned notes for quick access
9. **Reading mode**: Default to reading, edit when necessary
10. **Review workflow**: Use mobile for reading and desktop for writing

## Related Notes

- [[Daily Notes Workflow]] - Using daily notes on mobile
- [[Sync Strategies Compared]] - Detailed sync comparison
- [[Getting Started with Obsidian]] - Basic setup including mobile
- [[My Personal Vault]] - See mobile workflows in action
- [[Templates and Automation]] - Creating mobile-friendly templates

## Quick Reference

### When to Use Mobile
✅ Quick capture
✅ Reading notes
✅ Review workflows
✅ Light editing
✅ Reference lookup
✅ Daily notes

### When to Use Desktop
✅ Heavy writing
✅ Vault organization
✅ Plugin configuration
✅ Canvas creation
✅ Complex linking
✅ Bulk operations

---

*Remember: Mobile is a companion to your desktop workflow, not a replacement. Use each device for what it does best, and sync will keep everything connected.*
