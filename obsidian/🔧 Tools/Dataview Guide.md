# Dataview Guide

Dataview is one of the most powerful plugins for Obsidian, transforming your vault into a queryable database. This guide covers everything you need to know to master Dataview queries.

**Related:** [[Best Obsidian Plugins]] | [[Daily Notes Workflow]] | [[Templates and Automation]] | [[Obsidian Glossary#Metadata]]

---

## What is Dataview?

Dataview treats your notes as a **database**, allowing you to query, filter, sort, and display information from across your vault. Think of it as SQL for your notes.

### Why Dataview is Powerful

- **Dynamic content** - queries update automatically as you add/modify notes
- **Multiple views** - lists, tables, tasks, and calendars
- **Advanced filtering** - query by folder, tag, metadata, links, and more
- **Aggregation** - count, sum, group, and analyze your data
- **No manual maintenance** - results update automatically

**Perfect for:**
- Project management (tracking tasks, deadlines, status)
- Content tracking (books read, articles, courses)
- Daily notes aggregation (habit tracking, journal analysis)
- Knowledge management (finding related notes, gap analysis)

---

## Installation

1. **Open Settings** → Community Plugins
2. **Disable Safe Mode** (if not already done)
3. **Browse** → Search for "Dataview"
4. **Install** the Dataview plugin by Michael Brenan
5. **Enable** the plugin

### Recommended Settings

Go to Settings → Dataview:

- ✅ **Enable JavaScript Queries** - for DataviewJS functionality
- ✅ **Enable Inline Queries** - for inline data display
- ✅ **Enable Inline JavaScript Queries** - for advanced inline features
- **Automatic Task Completion Tracking** - Optional, adds completion date to tasks
- **Data Refresh Interval** - Leave at default (2500ms) unless vault is very large

---

## Basic Dataview Concepts

### Treating Notes as Data

Every note in your vault is a **data object** with:
- **Implicit fields**: file name, path, size, creation date, modification date, tags, links
- **Explicit fields**: metadata you add via frontmatter or inline fields

### Frontmatter Metadata

Metadata in YAML frontmatter at the top of your note:

```yaml
---
title: My Project
status: in-progress
due: 2025-11-15
priority: high
tags: [project, work]
---
```

### Inline Fields

Metadata anywhere in your note using `field::value` syntax:

```markdown
Project:: Website Redesign
Status:: Active
Due:: 2025-11-15
Priority:: High
Assigned:: [[John Doe]]
```

**Inline field variations:**
- `field:: value` - standard syntax
- `(field:: value)` - hidden syntax (won't display in reading mode)
- `[field:: value]` - also hidden

### Implicit Fields (Always Available)

Every note automatically has these fields:

- `file.name` - file name without extension
- `file.path` - full file path
- `file.folder` - folder the file is in
- `file.link` - link to the file
- `file.size` - file size in bytes
- `file.ctime` - creation time
- `file.mtime` - last modified time
- `file.cday` - creation date (no time)
- `file.mday` - last modified date (no time)
- `file.tags` - array of all tags in the note
- `file.etags` - array of explicit tags (not from frontmatter)
- `file.inlinks` - array of links TO this file
- `file.outlinks` - array of links FROM this file
- `file.tasks` - all tasks in the file

---

## Query Types

Dataview supports four main query types, each optimized for different use cases.

### 1. LIST - Simple Lists

Displays notes as a simple list with optional additional values.

**Basic LIST syntax:**

````markdown
```dataview
LIST
FROM #project
```
````

**LIST with additional info:**

````markdown
```dataview
LIST status
FROM #project
WHERE status = "in-progress"
```
````

**LIST without links (just values):**

````markdown
```dataview
LIST WITHOUT ID file.name
FROM "Projects"
```
````

### 2. TABLE - Tabular Data

Displays data in columns and rows, perfect for dashboards.

**Basic TABLE syntax:**

````markdown
```dataview
TABLE status, due, priority
FROM #project
```
````

**TABLE with custom column names:**

````markdown
```dataview
TABLE status AS "Status", due AS "Deadline", priority AS "Priority Level"
FROM #project
```
````

**TABLE without file link column:**

````markdown
```dataview
TABLE WITHOUT ID file.name AS "Project", status, due
FROM #project
```
````

### 3. TASK - Querying Tasks

Displays tasks from across your vault.

**All incomplete tasks:**

````markdown
```dataview
TASK
WHERE !completed
```
````

**Tasks with specific tag:**

````markdown
```dataview
TASK
FROM #project
WHERE !completed
```
````

**Tasks due soon:**

````markdown
```dataview
TASK
WHERE !completed AND due <= date(today) + dur(7 days)
SORT due ASC
```
````

### 4. CALENDAR - Date-Based Views

Displays notes or tasks on a calendar based on a date field.

**Calendar of daily notes:**

````markdown
```dataview
CALENDAR file.cday
FROM "Daily Notes"
```
````

**Calendar of due dates:**

````markdown
```dataview
CALENDAR due
FROM #project
```
````

---

## Query Syntax

### FROM - Source Selection

Specifies where to search for notes.

**By folder:**
```dataview
FROM "Projects"
FROM "Projects/Active"
```

**By tag:**
```dataview
FROM #project
FROM #project AND #work
FROM #project OR #personal
```

**By outgoing link (notes that link TO a note):**
```dataview
FROM [[Project Index]]
```

**By incoming link (notes that link FROM a note):**
```dataview
FROM [[MOC]] AND #project
```

**Negation:**
```dataview
FROM #note AND -"Archive"
FROM #project AND -#completed
```

### WHERE - Filtering Criteria

Filters results based on conditions.

**Basic comparisons:**
```dataview
WHERE status = "active"
WHERE priority > 5
WHERE due < date(today)
WHERE rating >= 4
```

**Multiple conditions:**
```dataview
WHERE status = "active" AND priority = "high"
WHERE due < date(today) OR priority = "urgent"
```

**Checking for existence:**
```dataview
WHERE status
WHERE !completed
WHERE contains(file.tags, "#project")
```

**Date operations:**
```dataview
WHERE file.ctime >= date(today) - dur(7 days)
WHERE due <= date(today) + dur(1 week)
WHERE date(today) - file.mtime <= dur(30 days)
```

**String matching:**
```dataview
WHERE contains(file.name, "Meeting")
WHERE startswith(file.name, "2025")
WHERE endswith(file.path, "Archive")
```

**Array/list operations:**
```dataview
WHERE contains(tags, "important")
WHERE length(file.outlinks) > 10
```

### SORT - Ordering Results

Orders results by one or more fields.

**Basic sorting:**
```dataview
SORT file.name ASC
SORT due DESC
SORT priority DESC, due ASC
```

**Sort by multiple fields:**
```dataview
SORT status ASC, priority DESC, due ASC
```

**Common patterns:**
- `ASC` - ascending (A-Z, 0-9, oldest-newest)
- `DESC` - descending (Z-A, 9-0, newest-oldest)

### LIMIT - Limiting Results

Restricts the number of results returned.

```dataview
LIMIT 10
```

**Get top 5 by priority:**
```dataview
SORT priority DESC
LIMIT 5
```

### GROUP BY - Grouping Results

Groups results by a field value.

**Group tasks by status:**
````markdown
```dataview
TASK
GROUP BY status
```
````

**Group projects by folder:**
````markdown
```dataview
TABLE priority, status
FROM "Projects"
GROUP BY file.folder
```
````

---

## Inline Queries

Dataview supports inline queries for embedding single values in your text.

### Inline Query Syntax

**Display a single value:**
```markdown
`= this.status`
`= this.due`
```

**Display values from other notes:**
```markdown
`= [[My Project]].status`
`= [[My Project]].due`
```

**Simple calculations:**
```markdown
Tasks remaining: `= length(file.tasks)`
Days since created: `= date(today) - file.cday`
```

**List multiple values:**
```markdown
`= this.tags`
`= this.file.outlinks`
```

### DataviewJS Inline

For more complex inline queries:

**Count notes with tag:**
```markdown
`$= dv.pages("#project").length`
```

**Sum values:**
```markdown
Total budget: `$= dv.pages("#expense").sum(p => p.amount)`
```

**Get latest modified:**
```markdown
`$= dv.pages('"Daily Notes"').sort(p => p.file.mtime, 'desc')[0].file.link`
```

---

## Practical Examples

### Example 1: List All Notes with a Specific Tag

**Use case:** Show all project notes

````markdown
```dataview
LIST
FROM #project
SORT file.name ASC
```
````

### Example 2: Table of Project Notes with Status

**Use case:** Project dashboard

````markdown
```dataview
TABLE status AS "Status", due AS "Deadline", priority AS "Priority"
FROM #project
WHERE status != "completed"
SORT priority DESC, due ASC
```
````

### Example 3: All Incomplete Tasks

**Use case:** Today's task list

````markdown
```dataview
TASK
WHERE !completed
SORT due ASC
```
````

### Example 4: Tasks Due Today or Overdue

**Use case:** Urgent tasks widget

````markdown
```dataview
TASK
WHERE !completed AND due <= date(today)
SORT due ASC
```
````

### Example 5: Daily Notes from Last Week

**Use case:** Weekly review

````markdown
```dataview
LIST
FROM "Daily Notes"
WHERE file.cday >= date(today) - dur(7 days)
SORT file.cday DESC
```
````

### Example 6: Notes Linking to Current Note

**Use case:** See backlinks in a query

````markdown
```dataview
LIST
FROM [[]]
SORT file.name ASC
```
````

**Note:** Use the actual note name: `FROM [[Note Name]]`

### Example 7: Notes Modified in Last 30 Days

**Use case:** Recently edited notes

````markdown
```dataview
TABLE file.mday AS "Last Modified"
WHERE file.mtime >= date(today) - dur(30 days)
SORT file.mtime DESC
LIMIT 20
```
````

### Example 8: Books Read This Year

**Use case:** Reading tracker

**Book note example:**
```yaml
---
type: book
status: completed
finished: 2025-08-15
rating: 4
genre: fiction
---
```

**Query:**
````markdown
```dataview
TABLE finished AS "Date Finished", rating AS "⭐", genre AS "Genre"
FROM #book
WHERE status = "completed" AND finished >= date(2025-01-01)
SORT finished DESC
```
````

### Example 9: Meeting Notes with Attendees

**Use case:** Meeting log

**Meeting note template:**
```yaml
---
type: meeting
date: 2025-10-28
attendees: [Alice, Bob, Charlie]
project: Website Redesign
---
```

**Query:**
````markdown
```dataview
TABLE date AS "Date", attendees AS "Attendees", project AS "Project"
FROM #meeting
SORT date DESC
LIMIT 10
```
````

### Example 10: Task Completion by Project

**Use case:** Project progress tracking

````markdown
```dataview
TABLE
  length(file.tasks) AS "Total Tasks",
  length(filter(file.tasks, (t) => t.completed)) AS "Completed",
  round((length(filter(file.tasks, (t) => t.completed)) / length(file.tasks)) * 100) + "%" AS "Progress"
FROM #project
WHERE file.tasks
SORT file.name ASC
```
````

### Example 11: Daily Note Habit Tracker

**Use case:** Track habits across daily notes

**Daily note format:**
```yaml
---
exercise: true
meditation: false
reading: true
---
```

**Query:**
````markdown
```dataview
TABLE exercise AS "🏃", meditation AS "🧘", reading AS "📚"
FROM "Daily Notes"
WHERE file.cday >= date(today) - dur(14 days)
SORT file.cday DESC
```
````

### Example 12: Content Creation Dashboard

**Use case:** Track articles/videos by status

````markdown
```dataview
TABLE status AS "Status", topic AS "Topic", words AS "Words", published AS "Published"
FROM #content
WHERE type = "article"
SORT status ASC, published DESC
```
````

---

## Advanced DataviewJS Examples

For complex queries, DataviewJS provides JavaScript API access.

### Count Notes by Tag

````markdown
```dataviewjs
const tags = dv.pages().flatMap(p => p.file.tags);
const counts = {};
tags.forEach(tag => counts[tag] = (counts[tag] || 0) + 1);
dv.table(["Tag", "Count"],
  Object.entries(counts).sort((a, b) => b[1] - a[1])
);
```
````

### Create a Progress Bar

````markdown
```dataviewjs
const pages = dv.pages("#project");
const total = pages.length;
const completed = pages.where(p => p.status === "completed").length;
const percentage = Math.round((completed / total) * 100);

dv.paragraph(`**Progress:** ${completed}/${total} projects completed`);
dv.paragraph(`[${"█".repeat(percentage/2)}${"░".repeat(50-percentage/2)}] ${percentage}%`);
```
````

### Recent Activity Summary

````markdown
```dataviewjs
const recent = dv.pages()
  .where(p => p.file.mtime >= dv.date('today') - dv.duration('7 days'))
  .sort(p => p.file.mtime, 'desc')
  .limit(10);

dv.header(3, "Recently Modified");
dv.list(recent.map(p =>
  `${p.file.link} - ${p.file.mtime.toFormat('MMM dd')}`
));
```
````

### Notes Without Specific Metadata

````markdown
```dataviewjs
const withoutStatus = dv.pages("#project")
  .where(p => !p.status);

dv.header(3, "Projects Missing Status Field");
dv.list(withoutStatus.file.link);
```
````

---

## Common Use Cases by Vault Type

### Personal Knowledge Management (PKM)

**Most valuable queries:**
- Recent notes and modifications
- Notes without backlinks (orphans)
- Most linked notes (hubs)
- Notes by creation date
- Reading/learning progress tracking

### Project Management

**Most valuable queries:**
- Tasks by priority and due date
- Project status dashboard
- Overdue tasks
- Resource allocation tables
- Meeting notes with action items

### Academic/Research

**Most valuable queries:**
- Literature notes by topic/author
- Citations and references
- Paper reading status
- Research questions and gaps
- Course notes by semester

### Creative Writing

**Most valuable queries:**
- Character database
- Scene/chapter outlines
- Word count tracking
- Plot points and timelines
- Research notes by story element

### Journaling with [[Daily Notes Workflow]]

**Most valuable queries:**
- Mood/habit tracking over time
- Weekly review aggregation
- Gratitude/highlight collections
- Goal progress tracking
- Memory retrieval by date

---

## Performance Tips for Large Vaults

### 1. Be Specific with FROM Clause

❌ **Slow:**
```dataview
FROM ""
WHERE #project
```

✅ **Fast:**
```dataview
FROM "Projects" AND #project
```

### 2. Limit Query Scope

Use `LIMIT` to prevent processing thousands of results:

```dataview
LIMIT 50
```

### 3. Avoid Complex WHERE Clauses When Possible

❌ **Slow:**
```dataview
WHERE contains(file.name, "Project") AND file.size > 1000 AND length(file.outlinks) > 5
```

✅ **Better:**
```dataview
FROM "Projects"
WHERE length(file.outlinks) > 5
```

### 4. Use Frontmatter Over Inline Fields

Frontmatter is parsed once; inline fields are scanned continuously. For frequently queried fields, use frontmatter.

### 5. Disable Auto-Refresh for Complex Queries

For very complex queries that don't need real-time updates:

```dataviewjs
// Add manual refresh button
dv.paragraph("Last updated: " + new Date().toLocaleString());
// Your complex query here
```

### 6. Index Frequently Used Queries

Create MOC (Map of Content) notes with embedded queries rather than running the same query in multiple places.

### 7. Monitor Query Performance

If a query is slow, simplify it:
- Reduce the number of fields in TABLE queries
- Use LIST instead of TABLE when possible
- Break complex queries into smaller ones
- Cache results in dedicated notes for historical data

---

## Troubleshooting Common Issues

### Query Shows No Results

**Checklist:**
1. ✅ Is the Dataview plugin enabled?
2. ✅ Are you using the correct syntax (three backticks + `dataview`)?
3. ✅ Do any notes match your FROM/WHERE criteria?
4. ✅ Check field names for typos (case-sensitive!)
5. ✅ Test with a simpler query first

### Field Not Showing

**Common causes:**
- Inline field syntax incorrect (needs `::` not `:`)
- Frontmatter YAML not valid (check indentation)
- Field name has spaces (use quotes: `WHERE "field name" = "value"`)

### Date Comparisons Not Working

Make sure dates are in ISO format: `YYYY-MM-DD`

```yaml
due: 2025-10-28    ✅ Works
due: 10/28/2025    ❌ Won't work properly
```

### Query Shows "Dataview: ..." Error

The query has syntax errors. Check:
- Commas between TABLE columns
- Quotes around strings
- Valid field names
- Proper operators (=, !=, <, >, <=, >=)

---

## Quick Reference Card

### Query Structure Template

````markdown
```dataview
[QUERY_TYPE] [fields]
FROM [source]
WHERE [conditions]
SORT [field] [ASC|DESC]
LIMIT [number]
```
````

### Operators

- `=` equal
- `!=` not equal
- `>` greater than
- `<` less than
- `>=` greater than or equal
- `<=` less than or equal
- `AND` logical and
- `OR` logical or
- `!` logical not

### Functions

- `date(text)` - parse date
- `dur(text)` - parse duration
- `length(array)` - array length
- `contains(list, value)` - check if contains
- `filter(list, predicate)` - filter list
- `sum(list)` - sum numbers
- `round(number)` - round number

### Date/Time

- `date(today)` - today's date
- `date(now)` - current date and time
- `dur(1 day)` - duration of 1 day
- `dur(2 weeks)` - duration of 2 weeks
- Date arithmetic: `date(today) - dur(7 days)`

---

## Learning Path

1. **Start simple** - Begin with basic LIST queries by tag or folder
2. **Add WHERE clauses** - Filter by single conditions
3. **Create TABLE views** - Display multiple fields
4. **Use implicit fields** - Leverage file.*, tags, links automatically
5. **Add metadata** - Start with frontmatter in a few notes
6. **Complex queries** - Combine multiple WHERE conditions
7. **TASK queries** - Track todos across your vault
8. **DataviewJS** - For advanced customization needs

---

## Additional Resources

**Official Documentation:** [Dataview Docs](https://blacksmithgu.github.io/obsidian-dataview/)

**Related Guides:**
- [[Templates and Automation]] - Use Dataview in templates for dynamic content
- [[Daily Notes Workflow]] - Aggregate daily notes with Dataview
- [[Note-Taking Methodologies]] - Structure notes for better querying
- [[My Personal Vault]] - See real examples of Dataview in action
- [[Obsidian Glossary#Metadata]] - Understanding metadata types

---

## Example: Complete Project Dashboard

Here's a complete example combining multiple concepts:

````markdown
# 📊 Project Dashboard

## 🔥 Urgent Tasks
```dataview
TASK
WHERE !completed AND priority = "high" AND due <= date(today) + dur(3 days)
SORT due ASC
```

## 📋 Active Projects
```dataview
TABLE status AS "Status", due AS "Deadline", priority AS "Priority", progress AS "Progress"
FROM #project
WHERE status = "active" OR status = "in-progress"
SORT priority DESC, due ASC
```

## ✅ Recently Completed
```dataview
LIST completed AS "Completed On"
FROM #project
WHERE status = "completed" AND completed >= date(today) - dur(30 days)
SORT completed DESC
LIMIT 10
```

## 📅 Upcoming Deadlines
```dataview
CALENDAR due
FROM #project
WHERE due >= date(today)
```

## 📊 Project Stats
```dataviewjs
const projects = dv.pages("#project");
const total = projects.length;
const active = projects.where(p => p.status === "active").length;
const completed = projects.where(p => p.status === "completed").length;

dv.paragraph(`**Total Projects:** ${total} | **Active:** ${active} | **Completed:** ${completed}`);
```
````

---

**Master Dataview, and your Obsidian vault becomes a powerful, queryable knowledge base that grows more valuable with every note you add.**

**See also:** [[Best Obsidian Plugins]] | [[Getting Started with Obsidian]]
