# Templates and Automation

Templates are the foundation of efficient note-taking in [[AboutObsidian|Obsidian]]. Instead of starting from scratch, templates give you consistent structure, automate repetitive content, and even execute dynamic logic. This guide covers everything from basic template setup to advanced automation patterns.

## Overview

**Why Use Templates:**
- **Consistency** - Same structure across similar notes
- **Speed** - Insert complex structures instantly
- **Automation** - Dynamic dates, prompts, calculations
- **Standardization** - Team-wide or personal conventions
- **Intelligence** - Conditional logic, file operations, API calls

**Two Approaches:**
1. **Core Templates Plugin** - Built-in, simple, good for basic needs
2. **Templater Plugin** - Community plugin, JavaScript-powered, advanced features

Most users start with Core Templates and graduate to Templater as needs grow. Both can coexist.

## Core Templates Plugin

The built-in Templates plugin handles basic template insertion with simple variable substitution.

### Basic Setup

**Enable Core Templates:**
1. Settings → Core plugins
2. Enable "Templates"
3. Settings → Templates → Configure settings

**Key Settings:**
- **Template folder location** - Where templates are stored (e.g., `📄 Templates/`)
- **Date format** - Default format for `{{date}}` variable
- **Time format** - Default format for `{{time}}` variable

**Folder Structure:**
```
📄 Templates/
├── Daily Note Template.md
├── Meeting Note.md
├── Project Note.md
├── Person Note.md
└── Quick Capture.md
```

Create this folder, then point Settings → Templates → Template folder location to it.

### Template Variables

Core Templates supports these variables:

**Date Variables:**
```markdown
{{date}} - Current date (uses format from settings)
{{date:YYYY-MM-DD}} - Custom format: 2024-10-28
{{date:dddd, MMMM D, YYYY}} - Monday, October 28, 2024
{{date:YYYY-MM-DD|+1 day}} - Tomorrow's date
{{date:YYYY-MM-DD|-1 week}} - Date one week ago
```

**Time Variables:**
```markdown
{{time}} - Current time (uses format from settings)
{{time:HH:mm}} - 14:30
{{time:h:mm A}} - 2:30 PM
```

**Title Variable:**
```markdown
{{title}} - Name of the current note
```

**Format Tokens:**
- `YYYY` - 4-digit year (2024)
- `MM` - 2-digit month (01-12)
- `DD` - 2-digit day (01-31)
- `dddd` - Full day name (Monday)
- `ddd` - Short day name (Mon)
- `MMMM` - Full month name (October)
- `MMM` - Short month name (Oct)
- `HH` - 24-hour format (00-23)
- `hh` - 12-hour format (01-12)
- `mm` - Minutes (00-59)
- `ss` - Seconds (00-59)
- `A` - AM/PM

### Using Templates

**Insert Template:**
1. Open note where you want template
2. Command palette (`Ctrl/Cmd + P`)
3. Type "Templates: Insert template"
4. Select template from list

**Set Hotkey:**
- Settings → Hotkeys
- Search "Templates: Insert template"
- Assign key (e.g., `Ctrl/Cmd + T`)

**Daily Notes Integration:**
- Settings → Daily notes
- Set "Template file location" to your daily note template
- New daily notes automatically use this template

### Example: Simple Daily Note

**Template file:** `📄 Templates/Daily Note Template.md`

```markdown
# {{date:dddd, MMMM D, YYYY}}

Created: {{date:YYYY-MM-DD}} at {{time:HH:mm}}

[[{{date:YYYY-MM-DD|-1 day}}|← Yesterday]] | [[{{date:YYYY-MM-DD|+1 day}}|Tomorrow →]]

## 🎯 Focus


## 📋 Tasks
- [ ]
- [ ]

## 📝 Notes


## 🔗 Links


## 💭 Reflection

```

**Result when inserted on Oct 28, 2024 at 2:30 PM:**

```markdown
# Monday, October 28, 2024

Created: 2024-10-28 at 14:30

[[2024-10-27|← Yesterday]] | [[2024-10-29|Tomorrow →]]

## 🎯 Focus
[cursor here]
```

### Limitations of Core Templates

- ❌ No conditional logic
- ❌ No user prompts
- ❌ No JavaScript execution
- ❌ No file operations
- ❌ Limited date math
- ❌ No dynamic content from other notes

For these features, use Templater.

## Templater Plugin (Advanced)

Templater is a community plugin that supercharges templates with JavaScript, dynamic content, user prompts, and extensive automation.

### Installation

1. Settings → Community plugins → Browse
2. Search "Templater"
3. Install and Enable
4. Settings → Templater → Configure

**Key Settings:**
- **Template folder location** - Same as Core Templates folder
- **Trigger Templater on new file creation** - Auto-apply templates
- **Enable System Commands** - Allow file operations (be careful!)
- **Folder Templates** - Auto-apply templates to specific folders

### Templater Syntax

Templater uses `<% %>` tags for code execution:

```markdown
<% JavaScript code %>          - Execute but don't output
<%= expression %>              - Execute and output result
<%* JavaScript code block %>   - Multi-line code block
```

**Example:**
```markdown
Current year: <%= tp.date.now("YYYY") %>
<% if (tp.file.title.includes("Project")) { %>
This is a project note!
<% } %>
```

### Templater Functions

**Date Functions:**
```markdown
<%= tp.date.now("YYYY-MM-DD") %>           - Current date
<%= tp.date.now("YYYY-MM-DD", 1) %>        - Tomorrow
<%= tp.date.now("YYYY-MM-DD", -7) %>       - 7 days ago
<%= tp.date.tomorrow("YYYY-MM-DD") %>      - Tomorrow
<%= tp.date.yesterday("YYYY-MM-DD") %>     - Yesterday
<%= tp.date.weekday("YYYY-MM-DD", 0) %>    - This Sunday (0 = Sunday)
<%= tp.date.weekday("YYYY-MM-DD", 1, 1) %> - Next Monday
```

**File Functions:**
```markdown
<%= tp.file.title %>                       - Current file name
<%= tp.file.path(true) %>                  - File path (relative)
<%= tp.file.folder(true) %>                - Parent folder
<%= tp.file.creation_date("YYYY-MM-DD") %> - File creation date
<%= tp.file.cursor() %>                    - Set cursor position
<%* await tp.file.rename("New Name") %>    - Rename file
<%* await tp.file.move("/path/to/file") %> - Move file
```

**Prompt Functions:**
```markdown
<%= tp.system.prompt("Question?") %>                    - Text input
<%= tp.system.suggester(["A","B","C"], [1,2,3]) %>     - Multiple choice
<%* tp.system.clipboard() %>                            - Clipboard content
```

**Web Functions:**
```markdown
<%* await tp.web.daily_quote() %>          - Random quote
```

**System Functions:**
```markdown
<%= tp.frontmatter.title %>                - Read frontmatter field
<%* tp.file.include("[[OtherNote]]") %>   - Include note content
```

### Template Examples

See [[Daily Notes Workflow]] for daily note patterns. Here are other essential templates:

#### Meeting Note Template

**Use Case:** Consistent structure for meeting notes with automatic date/time, attendees prompt, and automatic filing.

**Template:** `📄 Templates/Meeting Note.md`

```markdown
---
type: meeting
date: <%= tp.file.creation_date("YYYY-MM-DD") %>
time: <%= tp.date.now("HH:mm") %>
tags: [meeting]
---

# Meeting: <%= tp.system.prompt("Meeting topic?") %>

**Date:** <%= tp.date.now("dddd, MMMM D, YYYY") %> at <%= tp.date.now("HH:mm") %>
**Attendees:** <%* const attendees = await tp.system.prompt("Attendees (comma-separated)"); tR += attendees.split(",").map(name => `[[${name.trim()}]]`).join(", "); %>
**Project:** [[<%= tp.system.prompt("Related project?") %>]]

## 🎯 Objective


## 📋 Agenda
-

## 📝 Notes


## ✅ Action Items
- [ ]
- [ ]

## 📌 Decisions


## 🔗 Related
-

---
*Next Steps:*
```

**How to Use:**
1. Create new note
2. Insert template (or use hotkey)
3. Answer prompts: topic, attendees, project
4. Template fills in with date, creates links, sets structure
5. Cursor placed in Objective section

**Customization Ideas:**
- Add meeting type field (standup, planning, retrospective)
- Auto-generate file name based on date and topic
- Include previous meeting link automatically
- Add recurring meeting section
- Calculate meeting duration

#### Project Note Template

**Use Case:** Standard structure for project documentation with metadata, status tracking, and linked resources.

**Template:** `📄 Templates/Project Note.md`

```markdown
---
type: project
created: <%= tp.file.creation_date("YYYY-MM-DD") %>
status: <%* tR += await tp.system.suggester(["Planning", "Active", "On Hold", "Completed", "Cancelled"], ["planning", "active", "on-hold", "completed", "cancelled"]) %>
priority: <%* tR += await tp.system.suggester(["🔴 High", "🟡 Medium", "🟢 Low"], ["high", "medium", "low"]) %>
tags: [project]
---

# <%= tp.file.title %>

## 📊 Overview

**Status:** [[<%= tp.frontmatter.status %>]]
**Priority:** <%= tp.frontmatter.priority %>
**Start Date:** <%= tp.date.now("YYYY-MM-DD") %>
**Target Date:**
**Owner:** [[<%= tp.system.prompt("Project owner?") %>]]

## 🎯 Goals


## 📝 Description


## ✅ Tasks

### To Do
- [ ]

### In Progress
- [ ]

### Done
- [x] Project created <%= tp.date.now("YYYY-MM-DD") %>

## 🗓️ Timeline


## 👥 Stakeholders
- [[<%= tp.system.prompt("Key stakeholder?") %>]] -

## 📚 Resources
-

## 🔗 Related Projects
-

## 📊 Progress Log

### <%= tp.date.now("YYYY-MM-DD") %>
- Project initiated

---
*Last updated: <%= tp.date.now("YYYY-MM-DD") %>*
```

**How to Use:**
1. Create note with project name
2. Insert template
3. Select status and priority from dropdowns
4. Fill in owner and stakeholder
5. Template adds metadata and structure

**Customization Ideas:**
- Add budget tracking section
- Include risk register
- Auto-calculate days since start
- Add team members section with roles
- Include links to related documentation
- Add sprint/iteration tracking
- Calculate progress percentage

#### Person Note Template

**Use Case:** Contact/relationship notes for professional contacts, tracking interactions and context.

**Template:** `📄 Templates/Person Note.md`

```markdown
---
type: person
created: <%= tp.file.creation_date("YYYY-MM-DD") %>
tags: [people]
---

# <%= tp.file.title %>

## 👤 Basic Info

**Role:**
**Company/Organization:**
**Email:**
**LinkedIn:**
**Location:**

## 🤝 Relationship

**How we met:**
**Context:**
**Areas of collaboration:**

## 💼 Professional

**Expertise:**
-

**Current projects:**
-

**Interests:**
-

## 🗨️ Recent Interactions

### <%= tp.date.now("YYYY-MM-DD") %>
- First note created

## 📝 Notes


## 🔗 Related
- **Projects:**
- **Topics:**
- **Mutual connections:**

---
*Last interaction: <%= tp.date.now("YYYY-MM-DD") %>*
```

**How to Use:**
1. Create note with person's name
2. Insert template
3. Fill in known information
4. Update after each interaction

**Customization Ideas:**
- Add birthday field
- Track meeting frequency
- Link to meeting notes automatically
- Add communication preferences
- Include conversation topics
- Track action items per person
- Add photo or avatar

#### Decision Record Template

**Use Case:** Documenting important decisions for future reference (Architecture Decision Records pattern).

**Template:** `📄 Templates/Decision Record.md`

```markdown
---
type: decision
date: <%= tp.date.now("YYYY-MM-DD") %>
status: <%* tR += await tp.system.suggester(["Proposed", "Accepted", "Rejected", "Deprecated", "Superseded"], ["proposed", "accepted", "rejected", "deprecated", "superseded"]) %>
tags: [decision]
---

# Decision: <%= tp.system.prompt("Decision title?") %>

**Date:** <%= tp.date.now("YYYY-MM-DD") %>
**Status:** <%= tp.frontmatter.status %>
**Deciders:** <%* const deciders = await tp.system.prompt("Decision makers (comma-separated)"); tR += deciders.split(",").map(name => `[[${name.trim()}]]`).join(", "); %>
**Context:** [[<%= tp.system.prompt("Related project/context?") %>]]

## 📋 Context and Problem Statement

*What is the issue we're facing? What are we trying to solve?*


## 🎯 Decision Drivers

*What factors are important for this decision?*
-
-

## 🔍 Considered Options

1. **Option A:**
   - *Pros:*
   - *Cons:*

2. **Option B:**
   - *Pros:*
   - *Cons:*

3. **Option C:**
   - *Pros:*
   - *Cons:*

## ✅ Decision Outcome

**Chosen option:**

**Rationale:**


## 🔄 Consequences

**Positive:**
-

**Negative:**
-

**Neutral:**
-

## ⚠️ Risks and Mitigations

- **Risk:**
  - *Mitigation:*

## 📊 Implementation

**Action items:**
- [ ]
- [ ]

**Timeline:**

## 🔗 Related Decisions
-

## 📚 References
-

---
*Decision recorded: <%= tp.date.now("YYYY-MM-DD HH:mm") %>*
```

**How to Use:**
1. When making an important decision, create new note
2. Insert template
3. Answer prompts for title, deciders, context
4. Fill in options considered
5. Document chosen option and rationale
6. Track implementation

**Customization Ideas:**
- Add cost/impact assessment
- Include technical diagrams
- Link to discussion threads
- Add review date
- Include success metrics
- Reference similar past decisions

#### Quick Capture Template

**Use Case:** Fast capture of ideas/tasks with minimal friction, auto-tagged by date.

**Template:** `📄 Templates/Quick Capture.md`

```markdown
## <%= tp.date.now("HH:mm") %> - Quick Note

<%= tp.file.cursor() %>

---
*Captured: <%= tp.date.now("YYYY-MM-DD HH:mm") %>*
```

**How to Use:**
1. Add to end of today's daily note
2. Inserts timestamp and places cursor
3. Type thought and move on

**Best Practices:**
- Bind to hotkey for instant capture
- Use in [[Daily Notes Workflow|daily notes]]
- Review and process during evening routine

## Advanced Patterns

### Conditional Logic

Use JavaScript conditionals to adapt templates based on context:

```markdown
# <%= tp.file.title %>

<%* if (tp.file.folder(true).includes("Projects")) { %>
**Type:** Project Note
**Status:** Active
<%* } else if (tp.file.folder(true).includes("People")) { %>
**Type:** Contact
**Last contact:** <%= tp.date.now("YYYY-MM-DD") %>
<%* } else { %>
**Type:** General Note
<%* } %>

## Content

<%= tp.file.cursor() %>
```

**Use Cases:**
- Different sections based on folder
- Show/hide content based on day of week
- Adapt structure for work vs personal notes
- Conditional frontmatter based on note type

### User Input Prompts

Prompt for specific information to customize each note:

```markdown
<%*
const projectName = await tp.system.prompt("Project name?");
const client = await tp.system.prompt("Client name?");
const budget = await tp.system.prompt("Budget?");
const deadline = await tp.system.prompt("Deadline (YYYY-MM-DD)?");
%>

# <%= projectName %>

**Client:** [[<%= client %>]]
**Budget:** $<%= budget %>
**Deadline:** <%= deadline %>
**Days remaining:** <%*
const today = new Date();
const end = new Date(deadline);
const diff = Math.ceil((end - today) / (1000 * 60 * 60 * 24));
tR += diff;
%>

<%= tp.file.cursor() %>
```

**Multiple Choice Prompts:**

```markdown
<%*
const noteType = await tp.system.suggester(
  ["📝 Meeting", "📋 Task", "💡 Idea", "📚 Learning"],
  ["meeting", "task", "idea", "learning"]
);
%>

**Type:** <%= noteType %>

<%* if (noteType === "meeting") { %>
**Attendees:** <%= await tp.system.prompt("Attendees?") %>
**Duration:** <%= await tp.system.prompt("Duration?") %> minutes
<%* } else if (noteType === "task") { %>
**Priority:** <%= await tp.system.suggester(["High", "Medium", "Low"], ["high", "medium", "low"]) %>
**Due:** <%= await tp.system.prompt("Due date?") %>
<%* } else if (noteType === "idea") { %>
**Category:** <%= await tp.system.prompt("Category?") %>
<%* } else if (noteType === "learning") { %>
**Source:** <%= await tp.system.prompt("Source?") %>
**Topic:** <%= await tp.system.prompt("Topic?") %>
<%* } %>
```

### File Operations

Automatically organize files on creation:

**Auto-Rename Based on Content:**

```markdown
<%*
const meetingTopic = await tp.system.prompt("Meeting topic?");
const date = tp.date.now("YYYY-MM-DD");
const newName = `${date} - ${meetingTopic}`;
await tp.file.rename(newName);
%>

# <%= meetingTopic %>
```

**Auto-Move to Correct Folder:**

```markdown
<%*
const projectName = await tp.system.prompt("Project name?");
await tp.file.rename(projectName);
await tp.file.move(`Projects/${projectName}`);
%>

# <%= projectName %>
```

**Create Related Files:**

```markdown
<%*
const projectName = tp.file.title;
const files = ["Tasks", "Notes", "Resources"];

for (const file of files) {
  await tp.file.create_new(
    tp.file.find_tfile(`Templates/Project Sub-Template.md`),
    `${projectName}/${file}`
  );
}
%>

Project structure created for <%= projectName %>!
```

### Dynamic Content from Other Notes

Pull content from other notes:

```markdown
# Weekly Review - <%= tp.date.now("YYYY-[W]WW") %>

## This Week's Daily Notes

<%*
for (let i = 0; i < 7; i++) {
  const date = tp.date.now("YYYY-MM-DD", -i);
  const dayName = tp.date.now("dddd", -i);
  tR += `- [[${date}|${dayName}]]\n`;
}
%>

## Last Week's Review

<%*
const lastWeek = tp.date.now("YYYY-[W]WW", -7);
const lastWeekFile = `Weekly Reviews/${lastWeek}`;
tR += `![[${lastWeekFile}#Key Wins]]`;
%>
```

**Include Template Snippets:**

```markdown
# <%= tp.file.title %>

<%* await tp.file.include("[[Template Snippets/Standard Header]]") %>

## Content

<%= tp.file.cursor() %>

<%* await tp.file.include("[[Template Snippets/Standard Footer]]") %>
```

### Automation with Hotkeys

**Setup Hotkeys:**
1. Settings → Hotkeys
2. Search "Templater: Insert"
3. Assign to specific templates

**Recommended Hotkeys:**
- `Ctrl/Cmd + Shift + M` - Meeting note
- `Ctrl/Cmd + Shift + T` - Task/Todo
- `Ctrl/Cmd + Shift + C` - Quick capture
- `Ctrl/Cmd + Shift + P` - Project note

**Folder Templates (Auto-Apply):**

Settings → Templater → Folder Templates:
- `Projects/` → `Project Note.md`
- `People/` → `Person Note.md`
- `Meetings/` → `Meeting Note.md`

When you create a note in these folders, template auto-applies.

### Advanced JavaScript Patterns

**Calculate Values:**

```markdown
<%*
const startDate = await tp.system.prompt("Project start (YYYY-MM-DD)?");
const duration = parseInt(await tp.system.prompt("Duration (days)?"));
const start = new Date(startDate);
const end = new Date(start.getTime() + duration * 24 * 60 * 60 * 1000);
const endFormatted = tp.date.now("YYYY-MM-DD", 0, end);
%>

**Start:** <%= startDate %>
**End:** <%= endFormatted %>
**Duration:** <%= duration %> days
```

**Process Arrays:**

```markdown
<%*
const tags = await tp.system.prompt("Tags (comma-separated)?");
const tagArray = tags.split(",").map(t => t.trim());
%>

**Tags:** <%= tagArray.map(t => `#${t}`).join(" ") %>
```

**Complex Logic:**

```markdown
<%*
const dayOfWeek = tp.date.now("d"); // 0 = Sunday
const isWeekend = dayOfWeek === "0" || dayOfWeek === "6";
const timeOfDay = parseInt(tp.date.now("HH"));
const greeting = timeOfDay < 12 ? "Good morning" :
                 timeOfDay < 17 ? "Good afternoon" :
                 "Good evening";
%>

# <%= tp.date.now("dddd, MMMM D") %>

<%= greeting %>! <%= isWeekend ? "🎉 It's the weekend!" : "Let's make today productive." %>
```

## Template Organization and Management

### Folder Structure

**Organized Template Library:**

```
📄 Templates/
├── 📁 Core/
│   ├── Daily Note.md
│   ├── Weekly Review.md
│   └── Monthly Review.md
├── 📁 Work/
│   ├── Meeting Note.md
│   ├── Project Note.md
│   ├── Decision Record.md
│   └── Status Update.md
├── 📁 Personal/
│   ├── Journal Entry.md
│   ├── Person Note.md
│   └── Book Notes.md
├── 📁 Snippets/
│   ├── Standard Header.md
│   ├── Standard Footer.md
│   └── Task Section.md
└── 📁 Experimental/
    └── (test new templates here)
```

### Template Naming Convention

Use descriptive names:
- ✅ `Meeting Note - 1on1.md`
- ✅ `Project Note - Software.md`
- ✅ `Daily Note - Detailed.md`
- ❌ `template1.md`
- ❌ `temp.md`

Prefix for categories:
- `Core - `
- `Work - `
- `Personal - `

### Template Documentation

Create a template index note:

**`📄 Templates/Template Index.md`**

```markdown
# Template Index

Quick reference for all templates in this vault.

## Core Templates

### [[Daily Note Template]]
- **Use:** Every day
- **Hotkey:** Auto-applied
- **Location:** `Daily/`

### [[Weekly Review Template]]
- **Use:** End of week
- **Hotkey:** `Ctrl+Shift+W`
- **Location:** `Reviews/Weekly/`

## Work Templates

### [[Meeting Note Template]]
- **Use:** Any meeting
- **Hotkey:** `Ctrl+Shift+M`
- **Features:** Auto-prompts, attendee links, action items

### [[Project Note Template]]
- **Use:** New projects
- **Auto-applies:** In `Projects/` folder
- **Features:** Status tracking, timeline, stakeholders

### [[Decision Record Template]]
- **Use:** Important decisions
- **Features:** Options analysis, consequences tracking

## Personal Templates

### [[Person Note Template]]
- **Use:** Professional contacts
- **Auto-applies:** In `People/` folder
- **Features:** Contact info, interaction log

### [[Book Notes Template]]
- **Use:** Reading notes
- **Features:** Metadata, quotes, insights

## How to Use Templates

1. **Quick Insert:** `Ctrl/Cmd + T` → Select template
2. **Hotkey:** Assign frequently-used templates to hotkeys
3. **Auto-Apply:** Templates auto-insert in specific folders
4. **Daily Notes:** Daily template automatically applied

## Creating New Templates

1. Create in `📄 Templates/` folder
2. Use Core Templates syntax: `{{date}}`, `{{time}}`
3. Or Templater syntax: `<%= tp.date.now() %>`
4. Add to this index
5. Test before using regularly

## Template Best Practices

- Keep templates simple initially
- Add complexity as you identify patterns
- Use consistent naming conventions
- Document custom templates
- Review and prune unused templates quarterly
```

### Template Maintenance

**Regular Reviews:**
- **Monthly:** Check which templates you actually use
- **Quarterly:** Remove unused templates, update frequently-used ones
- **Yearly:** Major restructure if needed

**Version Control:**

If using [[Using Obsidian with GitHub|Git]], track template changes:

```bash
git add Templates/
git commit -m "Update meeting template with action items section"
```

**Template Changelog:**

Keep a note tracking major changes:

```markdown
# Template Changelog

## 2024-10-28
- Added Decision Record template
- Updated Meeting Note with attendee prompts
- Removed unused Book Review template

## 2024-09-15
- Restructured template folders
- Added Templater to all core templates
- Created template snippets for reusable sections
```

### Template Snippets (Reusable Sections)

Create reusable components:

**`📄 Templates/Snippets/Standard Header.md`**

```markdown
---
created: <%= tp.file.creation_date("YYYY-MM-DD") %>
modified: <%= tp.file.last_modified_date("YYYY-MM-DD") %>
tags: []
---
```

**`📄 Templates/Snippets/Task Section.md`**

```markdown
## ✅ Tasks

### To Do
- [ ]

### In Progress
- [ ]

### Done
- [x]
```

**`📄 Templates/Snippets/Related Links.md`**

```markdown
## 🔗 Related
-
```

**Use snippets with includes:**

```markdown
# <%= tp.file.title %>

<%* await tp.file.include("[[Snippets/Standard Header]]") %>

## Main Content

<%= tp.file.cursor() %>

<%* await tp.file.include("[[Snippets/Related Links]]") %>
```

### Sharing Templates

**Team Templates:**

If working with a team using [[Using Obsidian with GitHub|Git]]:

1. Store templates in `📄 Templates/` folder
2. Commit templates to repository
3. Everyone pulls to get latest templates
4. Document usage in `Template Index.md`

**Personal vs Team Templates:**

```
📄 Templates/
├── 📁 Shared/          ← Committed to Git
│   ├── Meeting Note.md
│   ├── Project Note.md
│   └── Decision Record.md
└── 📁 Personal/        ← .gitignore this folder
    ├── My Daily Note.md
    └── Private Journal.md
```

Add to `.gitignore`:
```
Templates/Personal/
```

## Best Practices

### Start Simple, Add Complexity

**Week 1:** Core Templates with basic date/time
```markdown
# {{date:YYYY-MM-DD}}

## Notes

```

**Month 1:** Add structure
```markdown
# {{date:dddd, MMMM D, YYYY}}

## Focus
## Tasks
## Notes
## Reflection
```

**Month 3:** Graduate to Templater
```markdown
# <%= tp.date.now("dddd, MMMM D, YYYY") %>

[[<%= tp.date.now("YYYY-MM-DD", -1) %>|← Yesterday]]

## Focus

<%= tp.file.cursor() %>
```

**Month 6:** Add advanced features
```markdown
<%*
const dayOfWeek = tp.date.now("dddd");
const isWeekday = !["Saturday", "Sunday"].includes(dayOfWeek);
%>

# <%= tp.date.now("dddd, MMMM D, YYYY") %>

<%* if (isWeekday) { %>
## 💼 Work
<% } else { %>
## 🎉 Weekend
<% } %>

<%= tp.file.cursor() %>
```

### Don't Over-Engineer

**❌ Too Complex:**
```markdown
<%*
const mood = await tp.system.suggester(["😊","😐","😢"], [1,2,3]);
const energy = await tp.system.suggester(["High","Medium","Low"], [3,2,1]);
const weather = await tp.system.prompt("Weather?");
const temperature = await tp.system.prompt("Temperature?");
const sleep = await tp.system.prompt("Hours of sleep?");
const exercise = await tp.system.prompt("Exercise minutes?");
const meals = await tp.system.prompt("List all meals:");
// ... 10 more prompts
%>
```

This is exhausting. You'll stop using it.

**✅ Right Amount:**
```markdown
# <%= tp.date.now("dddd, MMMM D, YYYY") %>

## 🎯 Focus

<%= tp.file.cursor() %>

## Notes

```

Add complexity only when you consistently want that information.

### Use Cursor Positioning

Place cursor where you'll start typing:

```markdown
# <%= tp.date.now("YYYY-MM-DD") %>

## Focus
<%= tp.file.cursor() %><% /* Cursor here, ready to type */ %>

## Tasks
- [ ]

## Notes
```

Without cursor positioning, it starts at top of file.

### Test Templates Before Full Deployment

1. Create in `📄 Templates/Experimental/`
2. Test for a week
3. Refine based on actual use
4. Move to main templates folder
5. Remove if not useful

### Version Templates

Track template evolution:

```markdown
# Meeting Note Template
<!-- Version 3.0 - Updated 2024-10-28 -->

<!--
Changelog:
- v3.0: Added decision section
- v2.0: Added auto-prompts for attendees
- v1.0: Initial version
-->
```

### Handle Template Errors Gracefully

**Check for empty inputs:**

```markdown
<%*
const projectName = await tp.system.prompt("Project name?");
if (!projectName || projectName.trim() === "") {
  tR += "Untitled Project";
} else {
  tR += projectName;
}
%>
```

**Provide defaults:**

```markdown
<%*
const priority = await tp.system.suggester(
  ["High", "Medium", "Low"],
  ["high", "medium", "low"]
);
%>

**Priority:** <%= priority || "medium" %>
```

## Integration with Workflows

### Daily Notes Workflow

See [[Daily Notes Workflow]] for complete guide. Templates are essential:

**Morning template:**
```markdown
# <%= tp.date.now("dddd, MMMM D, YYYY") %>

## 🌅 Morning Planning

**Yesterday:** [[<%= tp.date.now("YYYY-MM-DD", -1) %>]]

<%= tp.file.cursor() %>
```

**Evening addition:**
```markdown
## 🌙 Evening Reflection

**Completed:**
-

**Tomorrow:** [[<%= tp.date.now("YYYY-MM-DD", 1) %>]]
```

### Project Management

Link templates to [[My Personal Vault|vault structure]]:

**Project Index Auto-Update:**

When creating project note, append to project index:

```markdown
<%*
const projectName = tp.file.title;
const indexFile = "Projects/Index";
const newEntry = `\n- [[${projectName}]] - Created ${tp.date.now("YYYY-MM-DD")}`;

// Append to index (requires system commands enabled)
await tp.file.append(newEntry, indexFile);
%>
```

### Meeting Management

**Auto-link to daily note:**

```markdown
<%*
const todayNote = tp.date.now("YYYY-MM-DD");
const meetingTopic = await tp.system.prompt("Meeting topic?");
%>

# Meeting: <%= meetingTopic %>

*Also logged in [[<%= todayNote %>]]*

---

## Notes

<%= tp.file.cursor() %>
```

**Update daily note automatically:**

```markdown
<%*
const todayNote = tp.date.now("YYYY-MM-DD");
const meetingNote = tp.file.title;
const meetingTime = tp.date.now("HH:mm");
const entry = `\n## ${meetingTime} - Meeting\n- [[${meetingNote}]]\n`;

await tp.file.append(entry, `Daily/${todayNote}`);
%>
```

### Knowledge Management

**Book notes template:**

```markdown
---
type: book
title: <%= await tp.system.prompt("Book title?") %>
author: <%= await tp.system.prompt("Author?") %>
started: <%= tp.date.now("YYYY-MM-DD") %>
status: reading
tags: [book, reading]
---

# <%= tp.frontmatter.title %>

**Author:** <%= tp.frontmatter.author %>
**Started:** <%= tp.frontmatter.started %>

## 📚 Overview


## 💡 Key Ideas


## 📝 Notes by Chapter

### Chapter 1


## ✅ Action Items
- [ ]

## 🔗 Related
-
```

## Troubleshooting

### Template Doesn't Insert

**Check:**
1. Is Templates plugin enabled?
2. Is template folder path correct?
3. Is file actually in template folder?
4. Try restarting Obsidian

### Templater Code Doesn't Execute

**Check:**
1. Is Templater plugin enabled?
2. Did you use `<%= %>` or `<%* %>` tags?
3. Check console for JavaScript errors (Ctrl+Shift+I)
4. Test with simple template first

### Prompts Don't Appear

**Check:**
1. Did you use `await`?
   - ✅ `<%* await tp.system.prompt() %>`
   - ❌ `<%= tp.system.prompt() %>`
2. Is Templater syntax correct?

### File Operations Fail

**Check:**
1. Settings → Templater → Enable System Commands = ON
2. Check file path syntax
3. Ensure target folder exists
4. Test file operations on test notes first

### Date Format Issues

**Core Templates:**
```markdown
{{date:YYYY-MM-DD}}  ← Correct
{{date:yyyy-mm-dd}}  ← Wrong (case matters)
```

**Templater:**
```markdown
<%= tp.date.now("YYYY-MM-DD") %>  ← Correct
<%= tp.date.now("yyyy-mm-dd") %>  ← Wrong
```

Format tokens are case-sensitive. Use uppercase for most tokens.

### Variables Don't Substitute

**Core Templates needs:**
```markdown
{{date}}  ← Correct
{date}    ← Wrong (needs double braces)
```

**Templater needs:**
```markdown
<%= tp.date.now() %>  ← Correct
{{ tp.date.now() }}   ← Wrong (wrong syntax)
```

## Common Pitfalls

**❌ Creating Template Dependency:**
Don't make templates so complex that only you can use/maintain them.

**❌ Template Prompts Every Day:**
Daily note template shouldn't have 10 prompts. That's friction.

**❌ Not Testing Templates:**
Test new templates on dummy notes before using on real notes.

**❌ Hardcoded Values:**
Don't hardcode year or other values that change:
```markdown
❌ # 2024 Meeting
✅ # <%= tp.date.now("YYYY") %> Meeting
```

**❌ Ignoring User Experience:**
Template should make life easier, not add cognitive load.

**❌ Too Many Templates:**
Having 50 templates means you'll forget what each does. Keep it focused.

## Security Considerations

### Templater System Commands

Enabling System Commands allows file operations but also allows JavaScript execution:

**Be careful with:**
- Running external commands
- File deletion operations
- Templates from untrusted sources

**Best practice:**
- Only enable if you need file operations
- Review template code before using
- Keep templates in version control
- Don't share vault credentials

### External Templates

**Don't blindly copy templates from internet:**
- Review code first
- Understand what it does
- Test on disposable vault first
- Remove features you don't need

## Learn More

**Related Guides:**
- [[Getting Started with Obsidian]] - Obsidian basics
- [[Daily Notes Workflow]] - Daily note patterns and templates
- [[Best Obsidian Plugins]] - Templater and other automation plugins
- [[My Personal Vault]] - How templates fit into vault structure

**Template Resources:**
- Templater documentation: [silentvoid13.github.io/Templater](https://silentvoid13.github.io/Templater/)
- Template examples: Search community forums
- Obsidian help: [help.obsidian.md](https://help.obsidian.md)

**Next Steps:**
1. Enable Core Templates plugin
2. Create `📄 Templates/` folder
3. Create your first daily note template
4. Use it for a week
5. Install Templater when you need more power
6. Build your template library gradually

Templates are power tools for knowledge workers. Start simple, add complexity as you discover what you actually use, and never let templates become the goal instead of the means.

The best template is one you'll actually use every day.
