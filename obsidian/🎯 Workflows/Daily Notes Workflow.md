# Daily Notes Workflow

Daily notes are one of the most powerful features in [[AboutObsidian|Obsidian]] - a simple practice that creates a chronological backbone for your entire [[My Personal Vault|personal vault]]. This guide covers everything from basic setup to advanced patterns.

## What Are Daily Notes?

A daily note is simply a note created for each day, typically named with the date (e.g., `2024-10-28.md`). Instead of trying to figure out where each thought belongs, you capture it in today's note and [[How Obsidian Works - Details#Links|link]] to relevant concepts, people, and projects.

**Why Daily Notes Work:**
- **Low friction** - One place for everything each day
- **Chronological record** - Natural timeline of your thinking
- **Automatic backlinks** - Every link creates a date-stamped reference
- **Habit building** - Regular capture becomes second nature
- **Context preservation** - See what you were thinking about when

## Basic Setup

**Enable Daily Notes Plugin:**
1. Open Settings (gear icon)
2. Go to Core plugins
3. Enable "Daily notes"
4. Configure in Settings → Daily notes

**Key Settings:**
- **New file location** - Folder for daily notes (e.g., `Daily/` or leave blank for root)
- **Date format** - How files are named (default `YYYY-MM-DD` is good)
- **Template file location** - Path to your template (covered below)

**Create Today's Note:**
- Click calendar icon in left sidebar (using [[Best Obsidian Plugins#Calendar|Calendar plugin]])
- Or use command palette: "Open today's daily note"
- Keyboard shortcut (can customize)

That's it! You now have daily notes enabled. But the real power comes from how you use them.

## Daily Note Structure

A good daily note template provides structure without being restrictive. Here's a proven pattern:

```markdown
# {{date:dddd, MMMM D, YYYY}}

## 🎯 Focus
<!-- What's most important today? -->

## 📋 Tasks
- [ ]
- [ ]
- [ ]

## 📝 Notes
<!-- Capture thoughts, meetings, ideas throughout the day -->

## 🔗 Links
<!-- Quick links to people, projects, topics you worked on -->

## 💭 Reflection
<!-- End of day: What happened? What did you learn? -->
```

**Customize sections** based on your needs:
- Work log style: Projects → Tasks → Notes
- Journal style: Morning pages → Log → Evening reflection
- GTD style: Inbox → Process → Review
- Simple style: Just a heading and freeform notes

The key is consistency - use the same structure daily so it becomes habitual.

## Using Templates

Create reusable templates with the core Templates plugin (see [[Templates and Automation|Templates and Automation]] for advanced patterns).

**Create a Template:**
1. Create folder: `📄 Templates/`
2. Create file: `📄 Templates/Daily Note Template.md`
3. Add your structure (see above)
4. In Settings → Daily notes → Template file location: `📄 Templates/Daily Note Template.md`

**Template Variables:**
```markdown
# {{date:dddd, MMMM D, YYYY}}
<!-- Shows: Monday, October 28, 2024 -->

Created: {{date:YYYY-MM-DD}} at {{time}}

[[{{date:YYYY-MM-DD|-1 day}}|← Yesterday]] | [[{{date:YYYY-MM-DD|+1 day}}|Tomorrow →]]
```

Now every new daily note starts with your template automatically.

## Linking Strategies

The magic of daily notes comes from [[How Obsidian Works - Details#Links|linking]] liberally to the rest of your vault:

**Link to People:**
```markdown
## Meetings
- 10am: Standup with [[Alice]], [[Bob]]
- 2pm: 1:1 with [[Charlie]] about [[Project X]]
```

Now Alice's note shows backlinks to every daily note mentioning her - an automatic meeting history!

**Link to Projects:**
```markdown
## Work
Working on [[ProjectA/Authentication]] today. Made progress on [[ProjectA/API Design]].
Need to review [[ProjectB/Deployment]] tomorrow.
```

Project notes now have a chronological thread showing when you worked on them.

**Link to Concepts:**
```markdown
## Learning
Read about [[Zettelkasten]] methodology. Interesting connection to [[Graph Theory]].
Should explore how this relates to [[My Personal Vault]].
```

Concept notes accumulate references over time, showing how your understanding evolved.

**Link to Ideas:**
```markdown
## 💡 Ideas
- What if we combined [[Canvas First Workflow]] with [[Using AI with Obsidian]]?
- Need to write note about [[Idea: Automated Link Suggestions]]
```

Ideas captured in daily notes can be extracted into full notes later.

## Daily Note Workflows

### Morning Planning Workflow

**Start your day:**
1. Open today's daily note (click calendar icon)
2. Review yesterday's note (click backlink)
3. Check incomplete tasks from yesterday
4. Set 1-3 focus areas for today
5. Brain dump anything on your mind

**Template:**
```markdown
## 🌅 Morning

**Yesterday's Progress:**
![[2024-10-27#Tasks]]

**Today's Focus:**
1. [[Project]] - Ship feature X
2. [[Learning]] - Finish reading [[Book Name]]
3. [[Personal]] - Exercise

**On My Mind:**
- Concerned about [[Issue]]
- Excited about [[Opportunity]]
```

### Throughout-the-Day Capture

Keep your daily note open in a pinned tab. Capture continuously:

**Meeting Notes:**
```markdown
## 10:30 - Meeting with [[Person]]
- Discussed [[Topic]]
- Action: [ ] Follow up on [[Task]]
- Decision: Going with approach B (see [[Decision Record]])
```

**Random Thoughts:**
```markdown
## 14:00 - Thoughts
Realized that [[Concept A]] connects to [[Concept B]]. This could solve [[Problem]].
Need to explore this more.
```

**Work Log:**
```markdown
## 15:30 - Work
Fixed [[Bug #123]] in [[ProjectA]].
Approach: Used [[Pattern]] instead of previous solution.
Commit: abc123
```

### Evening Review Workflow

**End your day:**
1. Scan through today's note
2. Complete the reflection section
3. Move important items to permanent notes
4. Mark tasks as done or forward to tomorrow
5. Set intention for tomorrow

**Template:**
```markdown
## 🌙 Evening Reflection

**What Got Done:**
- ✅ Completed [[Task 1]]
- ✅ Made progress on [[Project]]
- ⏭️ Tomorrow: [[Task 2]]

**What I Learned:**
- [[Insight about X]]
- [[New approach for Y]]

**Grateful For:**
-
-

**Tomorrow's Focus:**
[[2024-10-29]] - Start with [[Priority Task]]
```

## Advanced Patterns

### Weekly Review Note

Link to your daily notes for weekly review:

```markdown
# Week of October 21, 2024

## Daily Notes
- [[2024-10-21]] Monday
- [[2024-10-22]] Tuesday
- [[2024-10-23]] Wednesday
- [[2024-10-24]] Thursday
- [[2024-10-25]] Friday

## Themes This Week
- Lots of work on [[ProjectA]]
- Met with [[Person]] 3 times - [[Issue]] is progressing
- Learning about [[New Technology]]

## Next Week Focus
-
```

### Project Daily Log

Embed daily note sections into project notes:

```markdown
# ProjectA

## Recent Activity
![[2024-10-28#ProjectA]]
![[2024-10-27#ProjectA]]
![[2024-10-26#ProjectA]]
```

If you use consistent headings in daily notes, you can pull project-specific content automatically.

### People Interaction Log

In [[My Personal Vault#People Notes|people notes]], show interaction history:

```markdown
# Alice Smith

## Role
Product Manager at Company

## Recent Interactions
![[2024-10-28#Alice]]
![[2024-10-25#Alice]]
![[2024-10-22#Alice]]
```

Every mention in daily notes creates an automatic timeline.

### Time Blocking

Use daily notes for time blocking:

```markdown
## ⏰ Schedule

- 09:00-10:00 | Deep work on [[ProjectA]]
- 10:00-10:30 | Meeting with [[Team]]
- 10:30-12:00 | [[ProjectB]] - Feature development
- 12:00-13:00 | Lunch & [[Learning/Reading]]
- 13:00-15:00 | [[ProjectC]] - Bug fixing
- 15:00-16:00 | Email & admin
- 16:00-17:00 | [[ProjectA]] - Documentation
```

Combine with [[Best Obsidian Plugins#Calendar|Calendar plugin]] for visual time blocking.

### Daily Metrics

Track habits and metrics:

```markdown
## 📊 Tracking

**Health:**
- Exercise: ✅ 30 min run
- Sleep: 7.5 hours
- Water: 8 glasses

**Productivity:**
- Deep work blocks: 3
- Meetings: 4
- Interruptions: 2

**Mood:** 😊 7/10
```

Use [[Dataview Guide|Dataview]] to aggregate metrics across days.

## Integration with Other Systems

### Canvas Integration

Create a [[Canvas First Workflow|canvas]] showing your week:

1. Create `Week-2024-W43.canvas`
2. Embed daily notes: `[[2024-10-21]]`, `[[2024-10-22]]`, etc.
3. Arrange spatially by day
4. Add text cards for weekly themes
5. Draw arrows showing project progression

### Git Integration

If using [[Using Obsidian with GitHub|Git]], daily notes create a natural commit cadence:

```bash
git add Daily/2024-10-28.md
git commit -m "Daily note: Oct 28 - Work on ProjectA"
git push
```

Your daily notes become a commit history of your thinking.

### AI Integration

Use [[Using AI with Obsidian|AI assistance]] with daily notes:

**Prompts:**
- "Summarize the key themes from this week's daily notes"
- "What projects did I mention most this month?"
- "Find all mentions of [Person] in my daily notes"
- "Generate a weekly review from daily notes Oct 21-27"

AI excels at finding patterns across chronological notes.

## Common Pitfalls

**❌ Too Much Structure**
Don't create a template so detailed you avoid using it. Start simple, add structure as needed.

**❌ Not Linking Enough**
The power is in [[How Obsidian Works - Details#Links|links to other notes]]. Link people, projects, concepts liberally.

**❌ Perfectionism**
Daily notes are meant to be messy capture. Don't worry about perfect formatting or complete sentences.

**❌ No Review**
Capturing is good, but reviewing periodically is what makes it valuable. Weekly reviews help extract insights.

**❌ Forgetting to Create Note**
Some days you'll forget. That's fine. Don't let guilt stop you from starting again tomorrow.

**❌ Using for Tasks Only**
Daily notes are more than task lists. Capture thoughts, learnings, and connections too.

## Plugins That Enhance Daily Notes

From [[Best Obsidian Plugins|Best Obsidian Plugins]]:

- **Calendar** - Visual calendar interface, see at a glance which days have notes
- **Periodic Notes** - Adds weekly, monthly, quarterly notes alongside daily
- **Templater** - Advanced template features with dynamic date handling
- **Dataview** - Query and aggregate data from daily notes
- **Tasks** - Advanced task management across daily notes

## Getting Started

**Week 1: Build the Habit**
- Create a simple template (heading + freeform notes)
- Open daily note every morning
- Write just 3 sentences minimum
- Don't worry about linking yet

**Week 2: Add Links**
- Start linking to people: `[[Name]]`
- Link to projects you work on
- Link to concepts you think about
- Check backlinks - see the connections forming

**Week 3: Add Structure**
- Add sections that help you (tasks, meetings, notes)
- Create a template that matches your needs
- Start morning/evening routines

**Week 4: Review & Refine**
- Do your first weekly review
- Look at backlinks on project/people notes
- Adjust template based on what you actually use
- Notice patterns in your work/thinking

**Month 2+: Advanced Patterns**
- Explore [[Best Obsidian Plugins#Calendar|Calendar plugin]]
- Use [[Dataview Guide|Dataview]] for queries
- Create weekly/monthly review notes
- Integrate with [[Canvas First Workflow|canvas]]

## Why This Works

Daily notes succeed because they:

**Lower Friction**
One place for everything eliminates "where should this go?" paralysis.

**Build Momentum**
Small daily captures compound into a rich knowledge base over weeks and months.

**Create Context**
Backlinks show when you thought about something, preserving chronological context.

**Support Multiple Workflows**
Works for journaling, task management, meeting notes, or all three.

**Scale Naturally**
Start simple, add complexity as needed. The system grows with you.

**Leverage Obsidian's Strengths**
Uses [[How Obsidian Works - Details#Links|bidirectional linking]] and [[How Obsidian Works - Details#Graph|graph view]] to create a timeline through your vault.

The result is a [[My Personal Vault#Daily Notes as the Foundation|chronological foundation]] that makes your entire vault more valuable over time.

## Learn More

- [[Getting Started with Obsidian|Getting Started]] - Basic Obsidian setup
- [[Templates and Automation|Templates and Automation]] - Advanced template patterns
- [[My Personal Vault|My Personal Vault]] - How daily notes fit into personal knowledge management
- [[Best Obsidian Plugins|Best Obsidian Plugins]] - Calendar, Periodic Notes, and more
- [[Dataview Guide|Dataview Guide]] - Query your daily notes
- [[How I Use Obsidian|How I Use Obsidian]] - Daily notes in a complete workflow
