# Sync Strategies Compared

Choosing the right sync strategy for your Obsidian vaults is crucial for maintaining seamless access across devices while preserving data integrity. This guide provides an objective comparison of the most popular sync methods, their trade-offs, and practical setup instructions.

## Quick Comparison Table

| Sync Method | Cost | Platforms | Setup Complexity | Sync Speed | Conflict Handling | Version History | Mobile Support | Encryption |
|-------------|------|-----------|------------------|------------|-------------------|-----------------|----------------|------------|
| **Obsidian Sync** | $8/month or $96/year | All | Low | Excellent | Automatic merge | Full (1 year) | Native | End-to-end |
| **Git/GitHub** | Free (or $4/month Pro) | All | High | Moderate | Manual merge | Full (unlimited) | Requires apps | In transit |
| **iCloud** | Free (5GB) or $0.99-$9.99/month | Apple only | Low | Good | Last-write-wins | Limited | Excellent | Yes |
| **Dropbox** | Free (2GB) or $11.99+/month | All | Low | Good | Conflict copies | 30-180 days | Good | Yes |
| **OneDrive** | Free (5GB) or $1.99+/month | All | Low | Moderate | Conflict copies | 30 days | Good | Yes |
| **Syncthing** | Free | All | Moderate-High | Good | Conflict copies | Optional (Staggered File Versioning) | Requires setup | Optional |

## Detailed Comparison

### 1. Obsidian Sync (Official Paid Service)

**Overview:** Obsidian's official sync service, purpose-built for the app with deep integration and features specifically designed for note-taking workflows.

#### Features
- **End-to-end encryption** (E2EE) with zero-knowledge architecture
- **Selective sync** - choose which folders/files to sync per device
- **Version history** - access any note version from the past year
- **Deleted file recovery** - restore deleted notes up to 1 year
- **Third-party plugin sync** - sync settings across devices
- **Live collaboration** (coming soon)
- **Priority support** from Obsidian team

#### Pricing
- **Monthly:** $8/month per user
- **Annual:** $96/year per user (same as monthly, no discount)
- **Vault limit:** Up to 10 vaults with 10GB shared storage
- **Add-on:** Commercial use license ($50/year per user)

#### Pros
- ✅ **Easiest setup** - works out of the box, no technical knowledge required
- ✅ **Best mobile experience** - native integration with iOS/Android apps
- ✅ **Intelligent conflict resolution** - automatic merging when possible
- ✅ **No file system conflicts** - doesn't rely on OS file syncing
- ✅ **Selective sync** - save space on mobile by excluding large attachments
- ✅ **Fastest sync** - optimized specifically for Obsidian's data structure
- ✅ **Supports the developers** - funds continued development

#### Cons
- ❌ **Recurring cost** - most expensive option over time
- ❌ **Storage limits** - 10GB shared across all vaults
- ❌ **No local backup control** - relies on Obsidian's infrastructure
- ❌ **Lock-in** - only works with Obsidian (can't easily switch apps)
- ❌ **No self-hosting** - must trust Obsidian's servers (though encrypted)

#### Best For
- Users who want hassle-free sync across multiple devices
- Those who value time over cost
- Mobile-heavy workflows
- Users managing sensitive information (E2EE)
- Supporting Obsidian's development

#### Setup Instructions

1. **Subscribe to Obsidian Sync:**
   - Open Obsidian Settings → Account
   - Create an Obsidian account if you don't have one
   - Go to the Obsidian website and purchase a subscription
   - Return to Settings → Account and sign in

2. **Enable sync on primary device:**
   - Settings → Core plugins → Enable "Sync"
   - Settings → Sync → Create new remote vault or connect to existing
   - Choose sync settings (what to sync: settings, themes, plugins, etc.)
   - Configure excluded folders if needed

3. **Connect other devices:**
   - Install Obsidian on the new device
   - Settings → Account → Sign in
   - Enable Sync plugin
   - Settings → Sync → Connect to remote vault
   - Choose selective sync options if needed
   - Wait for initial sync to complete

4. **Best practices:**
   - Enable "Sync settings" to maintain consistent configuration
   - Use excluded folders for device-specific content
   - Check sync status regularly (bottom-right icon)

---

### 2. Git/GitHub

**Overview:** Version control system originally designed for code, adapted for note management. Provides unparalleled version history and collaboration features. See also: [[Using Obsidian with GitHub]]

#### Features
- **Complete version history** - every change tracked forever
- **Branching and merging** - experiment without affecting main vault
- **Collaboration features** - pull requests, issues, discussions
- **Free unlimited private repos** (GitHub)
- **Works offline** - commit locally, push when connected
- **Platform independent** - works with any text files
- **Open source tools** - no vendor lock-in

#### Pricing
- **GitHub Free:** Unlimited private repos, 500MB storage per repo
- **GitHub Pro:** $4/month - 2GB LFS storage, advanced tools
- **GitHub Team:** $4/user/month - team features
- **Self-hosted:** Free (GitLab, Gitea, or your own server)

#### Pros
- ✅ **Best version control** - complete history with branching
- ✅ **True backup** - distributed copies on every device
- ✅ **Free for most users** - especially with small vaults
- ✅ **Collaboration ready** - great for shared knowledge bases
- ✅ **No file size limits** - with Git LFS for large files
- ✅ **Learning opportunity** - transferable skill for developers
- ✅ **Automation potential** - CI/CD, scripts, hooks

#### Cons
- ❌ **Steep learning curve** - Git terminology and concepts
- ❌ **Manual sync required** - must commit/push/pull explicitly
- ❌ **Merge conflicts** - requires manual resolution
- ❌ **Mobile complexity** - requires third-party apps (Working Copy, MGit)
- ❌ **Binary file handling** - images/PDFs need Git LFS
- ❌ **Slow with large files** - not optimized for attachments
- ❌ **Risk of data loss** - if not used correctly (force pushes, etc.)

#### Best For
- Developers or technically inclined users
- Users who need complete version history
- Collaborative vaults with multiple contributors
- Users already comfortable with Git
- Those who want free, open-source solution

#### Setup Instructions

**Initial Setup (Windows):**

1. **Install Git:**
   ```powershell
   # Download from https://git-scm.com/download/win
   # Or use winget
   winget install Git.Git
   ```

2. **Configure Git:**
   ```bash
   git config --global user.name "Your Name"
   git config --global user.email "your.email@example.com"
   ```

3. **Initialize repository in vault:**
   ```bash
   cd "C:\path\to\your\vault"
   git init
   ```

4. **Create .gitignore file:**
   ```plaintext
   # Obsidian workspace and cache
   .obsidian/workspace.json
   .obsidian/workspace-mobile.json
   .obsidian/cache
   .trash/

   # System files
   .DS_Store
   Thumbs.db
   desktop.ini

   # Optional: exclude large attachments
   # *.pdf
   # *.mp4
   ```

5. **Make initial commit:**
   ```bash
   git add .
   git commit -m "Initial commit"
   ```

6. **Create GitHub repository:**
   - Go to https://github.com/new
   - Create new private repository
   - Don't initialize with README

7. **Connect local to GitHub:**
   ```bash
   git remote add origin https://github.com/yourusername/your-vault.git
   git branch -M main
   git push -u origin main
   ```

**Daily Workflow:**

```bash
# Pull latest changes (before working)
git pull

# After making changes
git add .
git commit -m "Description of changes"
git push

# Or use a helper script
```

**Automation with Obsidian Git Plugin:**

1. Install "Obsidian Git" community plugin
2. Settings → Obsidian Git:
   - Enable "Automatic" backups every X minutes
   - Set "Auto commit message" template
   - Enable "Pull on startup"
   - Configure "Push on backup"

**Mobile Setup (iOS - Working Copy):**

1. Install "Working Copy" app ($19.99 one-time)
2. Clone your repository
3. Open Obsidian mobile
4. Create vault from folder → select Working Copy repository
5. Use Working Copy to commit/push/pull changes

**Mobile Setup (Android - MGit):**

1. Install "MGit" (free) from Play Store
2. Clone repository to accessible location
3. Open Obsidian mobile
4. Create vault from folder → select MGit repository
5. Use MGit to manage Git operations

---

### 3. iCloud

**Overview:** Apple's native cloud storage service, deeply integrated into macOS and iOS. Automatic and transparent sync for Apple users.

#### Features
- **Automatic sync** - no manual intervention
- **Native integration** - built into OS
- **Fast sync** on Apple devices
- **Files app integration** - easy file management
- **iCloud.com web access** - view files from any browser
- **Family sharing** - share storage with family members

#### Pricing
- **Free:** 5GB total (shared with photos, backups, etc.)
- **50GB:** $0.99/month
- **200GB:** $2.99/month
- **2TB:** $9.99/month
- **Higher tiers:** Up to 12TB available

#### Pros
- ✅ **Zero setup** - works immediately on Apple devices
- ✅ **Best iOS/macOS integration** - feels native
- ✅ **Fast on Apple devices** - optimized sync
- ✅ **Family sharing** - share storage costs
- ✅ **Works with Obsidian mobile** - seamless experience
- ✅ **Optimized storage** - can keep older files in cloud only

#### Cons
- ❌ **Apple ecosystem only** - no Windows/Linux/Android
- ❌ **Limited free storage** - 5GB shared with everything
- ❌ **Conflict issues** - last-write-wins, creates conflict copies
- ❌ **Sync delays** - can be slow or stuck occasionally
- ❌ **File system dependency** - sync issues affect vault
- ❌ **No true version history** - only conflict copies
- ❌ **Cannot exclude .obsidian folder** - syncs everything

#### Best For
- Apple-only users (Mac + iPhone/iPad)
- Users who want automatic, transparent sync
- Non-technical users
- Those already using iCloud storage

#### Setup Instructions

**macOS:**

1. **Enable iCloud Drive:**
   - System Settings → Apple ID → iCloud
   - Enable "iCloud Drive"
   - Ensure "Desktop & Documents Folders" is enabled

2. **Move vault to iCloud:**
   - Move existing vault to `~/Library/Mobile Documents/iCloud~md~obsidian/Documents/`
   - Or create new vault in that location
   - Alternatively, use any folder in `~/Library/Mobile Documents/com~apple~CloudDocs/`

3. **Verify sync:**
   - Check Files app on iOS to see if vault appears
   - Wait for initial sync (may take time for large vaults)

**iOS/iPadOS:**

1. **Ensure iCloud Drive is enabled:**
   - Settings → [Your Name] → iCloud → iCloud Drive (on)

2. **Open Obsidian:**
   - Tap "Create new vault" or "Open folder as vault"
   - Choose location in iCloud Drive
   - Vault will automatically sync with macOS

**Troubleshooting iCloud sync:**
- If sync is stuck: Turn iCloud Drive off and on
- Check available iCloud storage
- Ensure all devices signed into same Apple ID
- Try "Keep All Files Downloaded" for vault folder

---

### 4. Dropbox

**Overview:** Long-established cloud storage service with excellent cross-platform support. Popular in professional settings.

#### Features
- **Selective sync** - choose what to sync per device
- **File version history** (30 days standard, 180 days with Plus)
- **Conflict resolution** - creates numbered conflict copies
- **Shared folders** - collaborate with others
- **Paper integration** - Dropbox Paper for collaborative notes
- **Smart Sync** - keep files in cloud only

#### Pricing
- **Free:** 2GB storage
- **Plus:** $11.99/month - 2TB storage, 180-day history
- **Family:** $19.99/month - 2TB shared, up to 6 users
- **Professional:** $19.99/month - 3TB, advanced features

#### Pros
- ✅ **Excellent cross-platform** - Windows, Mac, Linux, iOS, Android
- ✅ **Mature and stable** - well-established service
- ✅ **Good conflict handling** - clear conflict copies
- ✅ **Selective sync** - save local storage
- ✅ **Version history** - recover old versions
- ✅ **Large file support** - handles attachments well
- ✅ **Business features** - team folders, admin controls

#### Cons
- ❌ **Limited free storage** - only 2GB
- ❌ **Expensive paid tiers** - $12+/month
- ❌ **Performance issues** - can be slow with many small files
- ❌ **Sync conflicts common** - with multiple devices
- ❌ **Mobile app limitations** - offline access requires manual pinning
- ❌ **Resource intensive** - desktop app uses significant RAM/CPU
- ❌ **.obsidian sync issues** - settings may conflict between devices

#### Best For
- Users needing cross-platform sync (Windows + Android, etc.)
- Teams collaborating on shared vaults
- Users already using Dropbox for other files
- Those who need reliable version history

#### Setup Instructions

1. **Install Dropbox:**
   - Download from https://www.dropbox.com/install
   - Sign in or create account
   - Complete initial setup

2. **Create or move vault:**
   ```
   # Windows
   C:\Users\YourName\Dropbox\ObsidianVault

   # Mac
   ~/Dropbox/ObsidianVault
   ```

3. **Configure Obsidian:**
   - Create new vault in Dropbox folder
   - Or move existing vault to Dropbox

4. **Setup other devices:**
   - Install Dropbox on each device
   - Wait for initial sync to complete
   - Open Obsidian and point to synced vault

5. **Mobile setup:**
   - Install Dropbox app
   - Install Obsidian mobile
   - Open folder as vault → Browse → Dropbox
   - Select your vault folder

6. **Best practices:**
   - Don't open vault on multiple devices simultaneously
   - Wait for sync to complete before switching devices
   - Use selective sync to exclude large files on mobile
   - Check for conflict copies regularly in `.obsidian` folder

---

### 5. OneDrive

**Overview:** Microsoft's cloud storage solution, tightly integrated with Windows and Office 365. Default choice for many Windows users.

#### Features
- **Windows integration** - built into Windows 10/11
- **Office 365 bundle** - included with Microsoft 365
- **Files On-Demand** - cloud-only file storage
- **Version history** - 30 days (or 180 with Microsoft 365)
- **Personal Vault** - encrypted folder with extra security
- **Sharing and collaboration** - via links or Office apps

#### Pricing
- **Free:** 5GB storage
- **Microsoft 365 Basic:** $1.99/month - 100GB
- **Microsoft 365 Personal:** $6.99/month - 1TB + Office apps
- **Microsoft 365 Family:** $9.99/month - Up to 6TB (1TB per person) + Office apps

#### Pros
- ✅ **Windows integration** - automatic on Windows 10/11
- ✅ **Generous with Microsoft 365** - 1TB included
- ✅ **Files On-Demand** - save local disk space
- ✅ **Good value** - if already using Office 365
- ✅ **Personal Vault** - extra security for sensitive notes
- ✅ **Cross-platform** - Windows, Mac, iOS, Android, web

#### Cons
- ❌ **Sync reliability issues** - known problems with many small files
- ❌ **Slow sync** - especially with large vaults
- ❌ **Frequent conflicts** - particularly in .obsidian folder
- ❌ **Files On-Demand issues** - can cause Obsidian errors
- ❌ **Limited control** - less granular than Dropbox
- ❌ **Not ideal for Obsidian** - community reports frequent issues
- ❌ **Path length limits** - Windows 260-character limit

#### Best For
- Windows-primary users
- Microsoft 365 subscribers (already have storage)
- Users with simple, single-device workflows
- Small vaults with infrequent changes

#### Setup Instructions

1. **Enable OneDrive (Windows):**
   - Usually pre-installed on Windows 10/11
   - Sign in with Microsoft account
   - Complete OneDrive setup wizard

2. **Configure Files On-Demand:**
   - Right-click OneDrive icon in system tray
   - Settings → Files On-Demand → Disable
   - **Important:** Keep vault files "Always keep on this device"

3. **Create vault:**
   ```
   # Windows
   C:\Users\YourName\OneDrive\ObsidianVault
   ```

4. **Disable Files On-Demand for vault:**
   - Right-click vault folder
   - "Always keep on this device"
   - This prevents sync issues

5. **Mobile setup:**
   - Install OneDrive app
   - Install Obsidian mobile
   - Open folder as vault → OneDrive → Your vault

6. **Critical settings to prevent issues:**
   - Disable Files On-Demand for entire vault
   - Exclude vault from antivirus real-time scanning (performance)
   - Don't use Personal Vault for Obsidian (access issues)
   - Close vault on one device before opening on another

**Troubleshooting OneDrive issues:**
- If seeing "file in use" errors: Close Obsidian, pause OneDrive sync, restart
- If conflicts frequent: Only use one device at a time
- Consider excluding `.obsidian/workspace.json` from sync
- Some users report better success with OneDrive + Git for version control

---

### 6. Syncthing

**Overview:** Free, open-source, peer-to-peer file synchronization. Your devices sync directly with each other without cloud servers.

#### Features
- **Peer-to-peer** - no central server required
- **Free and open-source** - no ongoing costs
- **Private** - data never touches third-party servers
- **Cross-platform** - Windows, Mac, Linux, Android
- **Versioning** - optional file history
- **Selective sync** - ignore patterns
- **Encryption** - transfer encryption (TLS)

#### Pricing
- **Free forever** - open-source (GPL license)
- No storage limits (only limited by your devices)

#### Pros
- ✅ **Completely free** - no subscription, no costs
- ✅ **True privacy** - no third party has your data
- ✅ **No storage limits** - only limited by device space
- ✅ **Fast local sync** - direct device-to-device
- ✅ **Open source** - auditable, community-driven
- ✅ **Versioning options** - keep old file versions
- ✅ **Works offline** - syncs when devices reconnect

#### Cons
- ❌ **Complex setup** - requires configuration on each device
- ❌ **No iOS support** - only Android for mobile (major limitation)
- ❌ **Requires running device** - at least one device must be always-on for sync
- ❌ **Manual conflict resolution** - creates conflict copies
- ❌ **No web interface** - must have device access
- ❌ **Technical knowledge required** - not beginner-friendly
- ❌ **Port forwarding may be needed** - for optimal sync

#### Best For
- Privacy-conscious users
- Those with always-on devices (home server, NAS)
- Users who want no recurring costs
- Android users (iOS is problematic)
- Technical users comfortable with configuration

#### Setup Instructions

**Windows Setup:**

1. **Download and install:**
   - Download from https://syncthing.net/downloads/
   - Run installer
   - Syncthing will start automatically
   - Access web UI at http://localhost:8384

2. **Configure first device:**
   - Web UI will open automatically
   - Note your Device ID (long alphanumeric string)
   - Actions → Settings → General → Set device name
   - Settings → GUI → Set username/password for web UI

3. **Add folder to sync:**
   - Click "Add Folder"
   - Folder Path: Path to your Obsidian vault
   - Folder Label: Give it a name (e.g., "ObsidianVault")
   - File Versioning: Enable "Staggered File Versioning" (recommended)
   - Ignore Patterns: Add patterns if needed
   ```
   .obsidian/workspace.json
   .obsidian/workspace-mobile.json
   ```
   - Save

4. **Set up second device:**
   - Install Syncthing on second device
   - Access web UI on second device
   - On Device 1: Actions → Show ID → copy Device ID
   - On Device 2: Add Remote Device → paste Device ID
   - Share the folder with Device 2
   - On Device 2: Accept the shared folder
   - Choose location for vault on Device 2

**Android Setup:**

1. **Install app:**
   - Install "Syncthing" from Google Play Store
   - Grant necessary permissions (storage access)

2. **Add device:**
   - On Android: Menu → Show device ID
   - On PC: Add Remote Device → scan QR code or paste ID
   - Accept connection on Android

3. **Receive folder:**
   - PC will offer to share folder
   - Accept on Android
   - Choose storage location (internal/SD card)
   - Wait for initial sync

4. **Obsidian mobile:**
   - Open Obsidian
   - Open folder as vault
   - Navigate to Syncthing folder location

**Advanced Configuration:**

- **Run as service (Windows):**
  - Syncthing can run as Windows service for always-on sync
  - Use SyncTrayzor for easier Windows management

- **Versioning options:**
  - Staggered: Keeps versions based on age (recommended)
  - Simple: Keeps all versions in `.stversions` folder
  - External: Custom versioning script

- **Discovery servers:**
  - Global discovery: Find devices via internet
  - Local discovery: Find devices on same network
  - Both can be disabled for maximum privacy

**Troubleshooting:**
- If devices won't connect: Check firewall settings
- Slow sync: Enable "Relay" servers in Settings
- Conflicts: Check `.stversions` folder for old versions

---

## Multiple Vault Sync Strategies

Different vaults may have different sync needs. Here's how to think about multi-vault setups:

### Strategy 1: Same Sync Method for All Vaults
**Use when:** All vaults have similar requirements

Example: All vaults on Obsidian Sync (can have up to 10 vaults)

### Strategy 2: Different Sync per Vault Purpose
**Use when:** Vaults have different security/access needs

Example:
- **Personal vault** → iCloud (Apple devices only)
- **Work vault** → OneDrive (company provided)
- **Shared knowledge base** → GitHub (collaboration)
- **Private journal** → Local only (no sync)

### Strategy 3: Hybrid Approach
**Use when:** Optimizing for different features

Example:
- Primary sync: Obsidian Sync (for speed and mobile)
- Backup: Git/GitHub (for version history)
- Archive: External drive (for old content)

### Implementation Tips

**Keep .obsidian folders separate:**
Different devices may need different settings (workspace layouts, plugins). Consider excluding:
```
.obsidian/workspace.json
.obsidian/workspace-mobile.json
```

**Mobile vs Desktop separation:**
- Mobile: Light vault with selective sync (notes only)
- Desktop: Full vault with all attachments
- Use Obsidian Sync's selective sync or symbolic links

**Vault structure for mixed sync:**
```
📁 Main Vault/
  📁 Notes/ (synced everywhere)
  📁 Attachments/ (desktop only)
  📁 Archive/ (selective sync)
  📁 Templates/ (synced)
  📁 .obsidian/ (partially synced)
```

See also: [[One Vault to Rule Them All]] for centralization strategies and [[My Personal Vault]] for practical examples.

---

## Mobile Considerations

Mobile sync presents unique challenges. Here's what to consider for each method:

### Storage Limitations
Mobile devices have limited storage. Consider:

- **Obsidian Sync:** Selective sync lets you exclude large attachment folders
- **Git/GitHub:** Clone only recent history (`--depth 1`) or use sparse checkout
- **iCloud/Dropbox/OneDrive:** Use "download on demand" features (with caution)
- **Syncthing:** Select specific folders to sync per device

### Battery & Data Usage

**High battery/data consumption:**
- OneDrive (continuous background sync)
- Dropbox (can be configured)
- iCloud (less control)

**More efficient:**
- Obsidian Sync (optimized protocol)
- Git (manual sync only when needed)
- Syncthing (configurable sync intervals)

**Best practices:**
- Sync only on WiFi (disable cellular data for sync apps)
- Schedule syncs during charging
- Use selective sync to reduce data transfer

### Mobile App Requirements

| Method | iOS | Android |
|--------|-----|---------|
| **Obsidian Sync** | Native | Native |
| **Git/GitHub** | Working Copy ($19.99) | MGit (free) or Termux (free) |
| **iCloud** | Native | Not available |
| **Dropbox** | Native | Native |
| **OneDrive** | Native | Native |
| **Syncthing** | Not available | Native (free) |

### Offline Access

All methods provide offline access once files are downloaded, but:

- **Obsidian Sync:** Selective sync means some files may not be local
- **Cloud services:** "On-demand" files must be downloaded before offline access
- **Git:** Full clone gives complete offline access
- **Syncthing:** All synced files are always local

### Best Mobile Sync Strategy

**For iOS users:**
1. **Best overall:** Obsidian Sync or iCloud (seamless)
2. **Best free:** iCloud (if in Apple ecosystem)
3. **Best with version control:** Git + Working Copy

**For Android users:**
1. **Best overall:** Obsidian Sync
2. **Best free:** Syncthing (requires setup)
3. **Best with version control:** Git + MGit

**Cross-platform (iOS + Android in household):**
1. **Best paid:** Obsidian Sync
2. **Best free:** Git/GitHub or Dropbox

See [[Mobile Workflows]] for detailed mobile-specific strategies and workflows.

---

## Conflict Resolution

Conflicts occur when the same file is modified on multiple devices before syncing. Here's how each method handles them:

### Obsidian Sync
**Behavior:** Intelligent automatic merging
- Attempts to merge changes automatically
- If automatic merge fails, creates conflict copy
- Shows notification of conflicts
- Conflict files: `filename.sync-conflict-TIMESTAMP.md`

**Resolution:**
1. Open both versions
2. Manually merge content
3. Delete conflict file
4. Original file continues syncing

**Prevention:**
- Obsidian Sync is best at avoiding conflicts
- Let sync complete before switching devices
- Check sync status icon before closing app

### Git/GitHub
**Behavior:** Manual merge required
- Prevents automatic overwrites
- Shows merge conflict markers in file
- Requires explicit conflict resolution

**Conflict markers:**
```markdown
Your current content from HEAD
Changes from other branch or device
```

**Resolution:**
1. Edit file to remove markers and merge content
2. Stage resolved file: `git add filename.md`
3. Complete merge: `git commit`
4. Push: `git push`

**Prevention:**
- Always `git pull` before starting work
- Use Obsidian Git plugin for automatic pulls
- Commit and push frequently
- Use branches for experimental work

### Cloud Services (iCloud, Dropbox, OneDrive)
**Behavior:** Creates duplicate conflict files
- Last-write-wins for original file
- Creates numbered copy with conflict notation
- No automatic merging

**Conflict file names:**
- **iCloud:** `filename 2.md`
- **Dropbox:** `filename (conflicted copy 2024-10-28).md`
- **OneDrive:** `filename-LAPTOP-2.md`

**Resolution:**
1. Open both versions side-by-side
2. Copy desired content from conflict file
3. Paste into main file
4. Delete conflict file
5. Let sync complete

**Common conflict locations:**
- `.obsidian/workspace.json` (very frequent)
- `.obsidian/plugins/` settings
- Recently edited notes

**Prevention:**
- Close Obsidian on one device before opening on another
- Wait for sync to complete (check cloud app status)
- Exclude workspace files from sync if possible
- Use one device at a time

### Syncthing
**Behavior:** Similar to cloud services
- Creates `.sync-conflict-TIMESTAMP` copies
- Original file keeps last-write content
- Notifies of conflicts in web UI

**Resolution:**
1. Check Syncthing web UI for conflict notifications
2. Find conflict files (search for `.sync-conflict`)
3. Manually merge content
4. Delete conflict copies
5. Can check `.stversions` folder for history

**Prevention:**
- Enable versioning (keeps file history)
- Use same workflow as cloud services
- Monitor Syncthing web UI for sync status

### Best Practices for All Methods

1. **Device discipline:**
   - Finish work on one device before switching
   - Wait for sync indicator to show completion
   - Don't force-quit apps during sync

2. **Exclude problematic files:**
   ```
   .obsidian/workspace.json
   .obsidian/workspace-mobile.json
   ```

3. **Regular conflict checks:**
   - Search vault for "conflict" weekly
   - Set up automated search/alert if possible
   - Address conflicts immediately

4. **Backup before merging:**
   - Keep conflict files until sure merge is correct
   - Have secondary backup (see next section)

5. **Use device-specific files:**
   - Separate daily notes per device
   - Device-specific dashboards
   - Different workspace layouts per device type

---

## What Happens When Syncs Fail

Sync failures are inevitable. Here's what to expect and how to recover:

### Common Failure Scenarios

#### 1. Network Interruption During Sync
**Symptoms:**
- Partial file updates
- Missing content
- Corrupted files (rare)

**Recovery:**
- **Obsidian Sync:** Usually auto-recovers when connection restored
- **Git:** Check status with `git status`, may need to reset
- **Cloud services:** Usually resume automatically, check for conflicts
- **Syncthing:** Resumes automatically, check web UI for errors

#### 2. Storage Quota Exceeded
**Symptoms:**
- Sync stops
- New files not uploading
- Error notifications

**Recovery:**
- Delete unnecessary files
- Upgrade storage plan
- Move large attachments elsewhere
- Use selective sync

**Warning signs to watch:**
- Cloud service shows storage nearly full
- Sync slower than usual
- Random sync failures

#### 3. File System Permissions
**Symptoms:**
- "Access denied" errors
- Files locked
- Can't save changes

**Recovery:**
- Close Obsidian completely
- Check file/folder permissions
- Restart sync service
- Reboot device if needed

#### 4. Sync Service Outage
**Symptoms:**
- Can't connect to sync
- Error messages from service
- Works locally but won't sync

**Recovery:**
- Check service status page:
  - Obsidian: https://status.obsidian.md
  - GitHub: https://www.githubstatus.com
  - Dropbox: https://status.dropbox.com
  - Others: Search "[service] status"
- Work locally
- Wait for service restoration
- Check for backlog once restored

#### 5. Corrupted Cache/Database
**Symptoms:**
- Constant sync errors
- Files resyncing repeatedly
- Settings not saving

**Recovery by method:**

**Obsidian Sync:**
```
1. Settings → Sync → Disconnect from remote vault
2. Close Obsidian
3. Delete .obsidian/sync-* files
4. Reopen Obsidian
5. Reconnect to remote vault
```

**Git:**
```bash
# Check repository health
git fsck

# If corrupted, re-clone
cd ..
mv old-vault old-vault-backup
git clone [repository-url] old-vault
# Copy .obsidian settings from backup if needed
```

**Cloud services:**
- Unlink device from service
- Clear cache (varies by service)
- Relink device
- Force re-download

**Syncthing:**
- Stop Syncthing
- Delete database: `.config/syncthing/index-v0.14.0.db`
- Restart Syncthing
- Allow re-indexing

### Data Loss Prevention

**Layer 1: Primary Sync**
Your chosen sync method (e.g., Obsidian Sync, Git, etc.)

**Layer 2: Secondary Backup**
Additional backup method:
- Git (if primary is cloud service)
- External hard drive (scheduled backups)
- NAS device (automated rsync)
- Cloud backup service (Backblaze, etc.)

**Layer 3: Export/Archive**
Periodic exports:
- ZIP entire vault monthly
- PDF exports of critical notes
- Git tags for major milestones

**Backup automation examples:**

**Windows Task Scheduler + Robocopy:**
```powershell
# Create scheduled task to backup vault
robocopy "C:\Users\YourName\ObsidianVault" "D:\Backups\ObsidianVault" /MIR /R:3 /W:10
```

**macOS Automator + Time Machine:**
- Include vault in Time Machine backups
- Create Automator script for additional backup
- Store on external drive

**Linux cron + rsync:**
```bash
# Add to crontab: daily backup at 2 AM
0 2 * * * rsync -av ~/ObsidianVault ~/Backups/ObsidianVault-$(date +\%Y\%m\%d)
```

### Recovery Checklist

When sync fails catastrophically:

1. **Don't panic - Stop making changes**
   - Close Obsidian on all devices
   - Don't delete anything yet

2. **Assess the situation**
   - Which device has most recent content?
   - Are any devices in good state?
   - Can you access backup?

3. **Locate latest good copy**
   - Check each device
   - Check secondary backups
   - Check version history if available

4. **Create safety copy**
   - Copy entire vault folder to safe location
   - Don't rely on sync services for this

5. **Attempt recovery**
   - Start with least destructive method
   - Document what you try
   - Keep safety copies

6. **Rebuild if necessary**
   - Use latest good copy as base
   - Manually recover missing content from other sources
   - Re-establish sync from clean state

7. **Post-recovery**
   - Verify all critical content present
   - Test sync on single device first
   - Gradually add other devices
   - Review backup strategy

### Testing Your Sync & Backup

Don't wait for disaster! Test regularly:

**Monthly tests:**
1. Create test note on Device A
2. Verify it appears on Device B
3. Modify on Device B
4. Verify changes on Device A
5. Test conflict resolution (edit same note on both devices while offline)

**Quarterly tests:**
1. Restore vault from backup to new location
2. Verify all files present
3. Verify Obsidian opens correctly
4. Check attachments and links work

**Annual tests:**
1. Full disaster recovery drill
2. Pretend primary device lost
3. Recover vault on new device from backup
4. Document any issues found
5. Update recovery procedures

---

## Recommendations by Use Case

### Solo User, Single Device
**Recommendation:** No sync needed, but backup essential
- **Best option:** Local vault + Git for version history
- **Alternative:** Local vault + periodic manual backup
- **Why:** No sync complexity, full offline access

### Solo User, 2-3 Devices, Non-Technical
**Recommendation:** Obsidian Sync or iCloud (if Apple-only)
- **Best option:** Obsidian Sync ($8/month)
- **Alternative:** iCloud (free for small vaults)
- **Why:** Hassle-free, automatic, reliable mobile support

### Solo User, 2-3 Devices, Technical
**Recommendation:** Git/GitHub with automation
- **Best option:** Git + Obsidian Git plugin
- **Alternative:** Syncthing (privacy-focused)
- **Why:** Free, complete version control, learning opportunity

### Team Collaboration (2-10 People)
**Recommendation:** Git/GitHub
- **Best option:** Git + GitHub (private repo)
- **Alternative:** Obsidian Sync + Publish (for public sharing)
- **Why:** Collaboration features, branching, pull requests, issue tracking

### Large Team/Organization (10+ People)
**Recommendation:** Git with hosted solution
- **Best option:** GitHub Enterprise or GitLab
- **Alternative:** Confluence, Notion, or proper wiki (Obsidian may not scale)
- **Why:** Better access control, audit logs, integrations

### Privacy-Critical / Sensitive Data
**Recommendation:** Self-hosted or E2EE solution
- **Best option:** Obsidian Sync (E2EE) or Syncthing
- **Alternative:** Self-hosted Git server
- **Why:** Zero-knowledge encryption or no third-party access

### Budget-Conscious
**Recommendation:** Free solutions
- **Best option:** Git/GitHub (free tier)
- **Alternative:** Syncthing or existing cloud storage (iCloud/OneDrive free tier)
- **Why:** No ongoing costs

### Mobile-Primary Workflow
**Recommendation:** Obsidian Sync or iCloud
- **Best option:** Obsidian Sync
- **Alternative:** iCloud (iOS) or Dropbox (cross-platform)
- **Why:** Best mobile app integration and selective sync

### Large Vaults (10GB+)
**Recommendation:** Cloud storage or Syncthing
- **Best option:** Cloud storage with good plan (Microsoft 365, Google Drive)
- **Alternative:** Syncthing (unlimited storage)
- **Avoid:** Git (not designed for large binary files), Obsidian Sync (10GB limit)

### Academic Research / Citations
**Recommendation:** Git for version control
- **Best option:** Git + Obsidian Git plugin + Zotero
- **Alternative:** Obsidian Sync with manual exports for archival
- **Why:** Complete history, attribution, proper academic versioning

---

## Making Your Decision

### Decision Framework

Ask yourself these questions:

1. **How many devices?**
   - One: Local + backup
   - 2-3: Any sync method works
   - 4+: Obsidian Sync or cloud storage

2. **What platforms?**
   - All Apple: iCloud
   - Mixed: Obsidian Sync, Git, Dropbox, or OneDrive
   - Android + iOS: Not iCloud

3. **Technical comfort level?**
   - Low: Obsidian Sync or iCloud
   - Medium: Dropbox or OneDrive
   - High: Git or Syncthing

4. **Budget?**
   - $0: Git, Syncthing, or free cloud tier
   - $1-5/month: Microsoft 365, iCloud upgrade
   - $8+/month: Obsidian Sync, Dropbox Plus

5. **Privacy concerns?**
   - High: Obsidian Sync (E2EE), Syncthing, or self-hosted Git
   - Medium: Any cloud service
   - Low: Any method works

6. **Version history importance?**
   - Critical: Git
   - Important: Obsidian Sync or Dropbox Plus
   - Nice to have: Any cloud service

7. **Mobile usage?**
   - Heavy: Obsidian Sync or iCloud
   - Moderate: Dropbox or OneDrive
   - Light: Git or Syncthing

### Quick Decision Chart

```
START HERE
    |
    ├─ Need collaboration? ──YES──> Git/GitHub
    |
    ├─ NO ──> Apple only? ──YES──> iCloud (free) or Obsidian Sync
    |
    ├─ NO ──> Want free? ──YES──> Git (technical) or Syncthing
    |
    ├─ NO ──> Want easiest? ──YES──> Obsidian Sync
    |
    └─ NO ──> Already pay Microsoft 365? ──YES──> OneDrive

                                      NO ──> Obsidian Sync or Dropbox
```

### Hybrid Strategy (Advanced)

Consider combining methods:

**Primary + Backup:**
- Obsidian Sync (primary) + Git (backup/version control)
- iCloud (primary) + Git (version control)
- Dropbox (primary) + Local external drive (backup)

**Device-Specific:**
- Desktop: Git workflow
- Mobile: Obsidian Sync
- Sync subset of notes to mobile, full vault on desktop

**Time-Based:**
- Daily: Fast sync (Obsidian Sync, cloud)
- Weekly: Comprehensive backup (Git commit)
- Monthly: Archive backup (ZIP + external drive)

---

## Conclusion

There's no universally "best" sync method—the right choice depends on your specific needs, technical comfort level, and workflow.

**TL;DR Recommendations:**
- **Easiest:** Obsidian Sync ($8/month)
- **Best free:** Git/GitHub (if technical) or Syncthing (if privacy-focused)
- **Best for Apple users:** iCloud (built-in) or Obsidian Sync
- **Best for teams:** Git/GitHub
- **Best for mobile:** Obsidian Sync
- **Best for privacy:** Obsidian Sync (E2EE) or Syncthing (P2P)

**Key Takeaway:** Whatever method you choose, implement a backup strategy. No sync method is perfect, and data loss is preventable with proper backups.

Start with one method, test it thoroughly, and don't be afraid to switch if it's not working for your needs. Many users successfully transition between sync methods as their workflows evolve.

---

## Related Resources

- [[Using Obsidian with GitHub]] - Detailed Git workflows for Obsidian
- [[Mobile Workflows]] - Mobile-specific tips and strategies
- [[My Personal Vault]] - Real-world vault organization example
- [[One Vault to Rule Them All]] - Single vs. multiple vault strategies

## External Resources

- [Obsidian Sync Documentation](https://help.obsidian.md/Obsidian+Sync/)
- [Obsidian Git Plugin](https://github.com/denolehov/obsidian-git)
- [Git Documentation](https://git-scm.com/doc)
- [Syncthing Documentation](https://docs.syncthing.net/)
- [Obsidian Community Forum - Sync Discussion](https://forum.obsidian.md/tag/sync)

---

*Last updated: October 2024*

*Note: Pricing and features subject to change. Check official sources for current information.*
