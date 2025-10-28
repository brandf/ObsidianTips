# Note-Taking Methodologies

A comprehensive guide to popular note-taking methodologies and how to implement them in Obsidian. Each methodology offers a different approach to organizing knowledge, from atomic notes to numerical systems.

> **Related:** [[Getting Started with Obsidian]] | [[AboutObsidian]] | [[Obsidian Glossary]]

## Overview

Different note-taking methodologies suit different thinking styles and goals. This guide covers five major approaches you can implement in [[AboutObsidian|Obsidian]], leveraging its powerful [[How Obsidian Works - Details#Links|linking capabilities]].

---

## 1. Zettelkasten

The Zettelkasten method (German for "slip box") is a knowledge management system developed by sociologist Niklas Luhmann, who wrote over 70 books using this approach.

### Core Principles

- **Atomic Notes**: One idea per note, fully expressed
- **Permanent vs Fleeting Notes**: Distinguish between temporary thoughts and refined knowledge
- **Extensive Linking**: Connect ideas to create a web of knowledge
- **Index Notes**: Entry points to topics
- **Bottom-Up Structure**: Structure emerges from connections, not predetermined categories

### How to Implement in Obsidian

**1. Note Types:**

```markdown
<!-- Fleeting Note -->
# 📝 Meeting thoughts 2024-01-15
Quick ideas from today's discussion...
(Store in /Fleeting/ folder)

<!-- Literature Note -->
# 📚 Atomic Habits - Clear 2018
Notes from reading...
(Store in /Literature/ folder)

<!-- Permanent Note -->
# 202401151430 Habit formation requires environmental cues
Habits are triggered by environmental contexts...

#zettelkasten #permanent

**Related:** [[202401141200 Identity shapes behavior]]
[[202401101830 Small changes compound over time]]
```

**2. Unique Identifiers:**
- Use timestamp IDs: `202401151430` (YYYYMMDDHHmm)
- Or use Obsidian's unique note ID feature
- Keep titles descriptive of the single concept

**3. Linking Strategy:**
- Add 2-5 related notes at the bottom of each permanent note
- Create "Hub" notes (Structure Notes) as entry points
- Use [[How Obsidian Works - Details#Links|bidirectional links]] heavily

**4. Example Structure:**
```
Vault/
├── Fleeting/           # Temporary, unprocessed thoughts
├── Literature/         # Notes from sources
├── Permanent/          # Refined, atomic notes
└── Index/             # Hub notes for navigation
    ├── Index - Psychology.md
    ├── Index - Writing.md
    └── Index - Learning.md
```

**5. Workflow:**
1. Capture fleeting notes quickly
2. Process them within 24-48 hours
3. Extract concepts into permanent notes
4. Link to related permanent notes
5. Update index notes

### Pros

✅ Prevents information silos through heavy linking
✅ Facilitates unexpected connections and insights
✅ Notes remain relevant as your knowledge grows
✅ Encourages deep processing of information
✅ Scales infinitely without reorganization

### Cons

❌ Steeper learning curve
❌ Requires discipline to maintain
❌ Time-intensive processing of fleeting notes
❌ Can feel overwhelming initially
❌ Timestamp IDs aren't human-readable

### Best For

- **Researchers** building interconnected knowledge
- **Writers** developing ideas over time
- **Lifelong learners** building a personal knowledge base
- Anyone working on **long-term projects**
- People who enjoy **discovering connections**

---

## 2. PARA Method

Created by Tiago Forte, PARA (Projects, Areas, Resources, Archives) is a productivity-focused organization system that separates actionable information from reference material.

### Core Principles

- **Project**: Short-term efforts with a goal and deadline
- **Area**: Long-term responsibilities to maintain
- **Resource**: Topics of ongoing interest
- **Archive**: Inactive items from the other three

### How to Implement in Obsidian

**1. Folder Structure:**

```
Vault/
├── Projects/
│   ├── Website Redesign.md
│   ├── Book Draft.md
│   └── Client ABC Proposal.md
├── Areas/
│   ├── Health & Fitness.md
│   ├── Career Development.md
│   ├── Finances.md
│   └── Relationships.md
├── Resources/
│   ├── Marketing Strategies.md
│   ├── Writing Techniques.md
│   ├── Psychology Research.md
│   └── Productivity Tools.md
└── Archive/
    └── 2024/
        ├── Completed Website Project/
        └── Old Job Notes/
```

**2. Project Note Template:**

```markdown
# Project: [Name]

**Status:** Active
**Deadline:** 2024-03-15
**Area:** Career Development

## Goal
Complete X by Y date

## Next Actions
- [ ] Task 1
- [ ] Task 2
- [ ] Task 3

## Notes & Resources
- [[Resource link 1]]
- [[Resource link 2]]

## Archive Date
When completed or cancelled
```

**3. Area Note Template:**

```markdown
# Area: Health & Fitness

**Standard:** Maintain consistent exercise and healthy eating

## Current Projects
- [[Project - Run 5K Race]]

## Key Resources
- [[Nutrition Guidelines]]
- [[Workout Routines]]

## Regular Activities
- Weekly gym sessions
- Meal prep Sundays

## Review
Last reviewed: 2024-01-15
```

**4. Maintenance:**
- Weekly review: Update project statuses
- Monthly review: Move completed projects to Archive
- Quarterly review: Reassess Areas and Resources

### Pros

✅ Clear action-oriented structure
✅ Easy to find what you need
✅ Works well with GTD and productivity systems
✅ Simple to learn and implement
✅ Reduces decision fatigue

### Cons

❌ Can feel rigid for creative work
❌ Requires regular maintenance (reviews)
❌ Folder-heavy (less linking)
❌ May not suit pure knowledge work
❌ Distinction between Areas and Resources can blur

### Best For

- **Project managers** juggling multiple initiatives
- **Professionals** balancing work and life
- **Goal-oriented individuals**
- People who prefer **clear hierarchies**
- Those implementing **GTD** or similar productivity methods

---

## 3. LYT (Linking Your Thinking)

Developed by Nick Milo, LYT emphasizes flexibility through Maps of Content (MOCs) rather than rigid hierarchies. It combines structure with organic growth.

### Core Principles

- **Maps of Content (MOCs)**: Curated collections of related notes
- **Fluid Frameworks**: Adaptable structure that evolves
- **Home Note**: Central dashboard for navigation
- **Emergence**: Structure develops naturally from your notes
- **Progressive Summarization**: Ideas develop across multiple notes

### How to Implement in Obsidian

**1. Home Note:**

```markdown
# 🏠 Home

Welcome to [[My Personal Vault]]!

## 🗺️ Main Maps
- [[MOC - Productivity]]
- [[MOC - Writing]]
- [[MOC - Psychology]]
- [[MOC - Projects]]

## ⭐ Highlights
- [[Important concept 1]]
- [[Recent insight 2]]
- [[Active project 3]]

## 📅 Daily Notes
- [[2024-01-15]]

## 🔧 System
- [[Getting Started with Obsidian]]
- [[Note-Taking Methodologies]]
```

**2. Map of Content Template:**

```markdown
# MOC - Productivity

A map of my productivity notes and systems.

## 🎯 Core Concepts
- [[Deep Work]]
- [[Flow State]]
- [[Time Management]]
- [[Attention Management]]

## 🛠️ Systems & Methods
- [[GTD Overview]]
- [[Time Blocking]]
- [[PARA Method]]

## 📚 Related MOCs
- [[MOC - Learning]]
- [[MOC - Psychology]]

## 📝 Active Notes
*Recent additions to this topic*
- [[202401151200 Interruptions destroy flow]]
- [[202401141530 Energy management vs time management]]

---
**Related:** [[Home]]
```

**3. Typical Structure:**

```
Vault/
├── Home.md                    # Central hub
├── MOCs/                      # Maps of Content
│   ├── MOC - Productivity.md
│   ├── MOC - Writing.md
│   └── MOC - Learning.md
├── Notes/                     # All regular notes (flat or minimal folders)
│   ├── Deep Work.md
│   ├── Flow State.md
│   └── ...
├── Daily/                     # Daily notes
└── Atlas/                     # High-level overview maps
    └── Life Dashboard.md
```

**4. Creating MOCs:**
- Start writing notes naturally
- When you have 10-15 notes on a topic, create a MOC
- MOCs can link to other MOCs (hierarchical when needed)
- Update MOCs as you add related notes

### Pros

✅ Balances flexibility with structure
✅ Scales well as vault grows
✅ Multiple navigation paths (links + MOCs)
✅ Less rigid than folders
✅ Natural for non-linear thinking

### Cons

❌ MOCs require curation and maintenance
❌ Can be unclear when to create a MOC vs a regular note
❌ Less prescriptive (requires more thinking)
❌ Multiple MOCs can overlap
❌ Home note can become cluttered

### Best For

- **Creative thinkers** who need flexibility
- **Knowledge workers** building interconnected ideas
- People who dislike strict hierarchies
- Those who enjoy **curating collections**
- Users who want **multiple navigation options**

---

## 4. Evergreen Notes

Developed by Andy Matuschak, Evergreen Notes emphasize continuously refined, concept-oriented notes that develop over time. Similar to Zettelkasten but with emphasis on evolution.

### Core Principles

- **Concept-Oriented**: Notes are about ideas, not sources
- **Atomic**: One concept per note
- **Densely Linked**: Heavy cross-referencing
- **Continuously Refined**: Notes evolve with understanding
- **Written for Yourself**: Personal understanding, not documentation

### How to Implement in Obsidian

**1. Note Structure:**

```markdown
# Environmental cues trigger habits

Environmental design is more effective than willpower for behavior change. When we modify our physical environment to make desired behaviors obvious and undesired behaviors invisible, we reduce the need for conscious decision-making.

This works because habits are context-dependent. A habit is an association between a situation and a response. By controlling the situation, we control the automatic response.

## Connections
- [[Willpower is a limited resource]] - Why environmental design beats self-control
- [[Implementation intentions bridge goals and action]] - Specific cues are crucial
- [[Default options shape behavior]] - Environment creates defaults
- [[Context switching breaks habit loops]] - New environments enable new behaviors

## Questions & Development
- How long does it take for a new environmental cue to become automatic?
- What happens when environmental cues conflict?
- Can digital environments create the same effect?

## Sources
- [[📚 Atomic Habits - Clear 2018]]
- [[📚 Good Habits, Bad Habits - Wood 2019]]

---
*Created: 2024-01-10 | Updated: 2024-01-15*
```

**2. Key Practices:**

- **Revisit and refine**: Regularly update notes as understanding deepens
- **Merge related notes**: Combine similar concepts as they crystallize
- **Split growing notes**: Break apart notes that contain multiple concepts
- **Add connections**: Link to related concepts as they emerge

**3. Structure:**

```
Vault/
├── Evergreen/              # Main concept notes
├── Seedlings/              # Developing ideas (not yet evergreen)
├── References/             # Source material
└── Daily/                  # Capture and processing
```

**4. Workflow:**
1. Capture ideas in daily notes
2. Extract concepts to Seedlings
3. Develop and refine over weeks/months
4. Promote to Evergreen when mature
5. Continue updating as understanding grows

### Pros

✅ Notes improve over time
✅ Encourages deep thinking
✅ Creates genuinely useful knowledge base
✅ Reduces redundancy through merging
✅ Focus on understanding, not collection

### Cons

❌ Requires ongoing effort to maintain
❌ Can be perfectionist (notes never feel "done")
❌ Slower initial note-taking
❌ Difficult to know when a note is "evergreen"
❌ Time-intensive refinement process

### Best For

- **Researchers** building deep expertise
- **Writers** developing ideas into content
- **Academics** synthesizing knowledge
- People committed to **continuous learning**
- Those who value **quality over quantity**

---

## 5. Johnny Decimal System

A numerical classification system created by Johnny Noble that provides a logical, hierarchical structure using decimal notation for organization.

### Core Principles

- **10 Categories**: 10-19, 20-29, ..., 90-99
- **10 Areas per Category**: 11, 12, 13, ..., 19
- **Items within Areas**: 11.01, 11.02, 11.03
- **Nothing starts with zero**: Numbers 00-09 reserved
- **Rigid structure**: Forces thoughtful organization

### How to Implement in Obsidian

**1. Category Structure:**

```
Vault/
├── 10-19 Personal/
│   ├── 11 Health/
│   │   ├── 11.01 Fitness Routine.md
│   │   ├── 11.02 Nutrition Plan.md
│   │   └── 11.03 Medical Records.md
│   ├── 12 Finances/
│   │   ├── 12.01 Budget 2024.md
│   │   ├── 12.02 Investment Strategy.md
│   │   └── 12.03 Tax Documents.md
│   └── 13 Home/
├── 20-29 Work/
│   ├── 21 Projects/
│   │   ├── 21.01 Website Redesign.md
│   │   ├── 21.02 Product Launch.md
│   │   └── 21.03 Client Onboarding.md
│   ├── 22 Meetings/
│   └── 23 Documentation/
├── 30-39 Learning/
│   ├── 31 Courses/
│   ├── 32 Books/
│   └── 33 Research/
└── 40-49 Creative/
    ├── 41 Writing/
    ├── 42 Art Projects/
    └── 43 Music/
```

**2. Example Planning:**

```markdown
10-19 Personal Life
  11 Health & Fitness
  12 Finances
  13 Home Management
  14 Relationships
  15 Personal Development

20-29 Professional
  21 Active Projects
  22 Client Work
  23 Documentation
  24 Team Management
  25 Learning & Development

30-39 Knowledge Management
  31 Books & Reading
  32 Courses & Training
  33 Research Notes
  34 Reference Materials

40-49 Creative Work
  41 Writing Projects
  42 Art & Design
  43 Content Creation
```

**3. Index Note:**

```markdown
# Johnny Decimal Index

## 10-19 Personal
- **11 Health**: [[11.01 Fitness Routine]] | [[11.02 Nutrition Plan]]
- **12 Finances**: [[12.01 Budget 2024]] | [[12.02 Investment Strategy]]
- **13 Home**: [[13.01 Maintenance Schedule]] | [[13.02 Improvement Projects]]

## 20-29 Work
- **21 Projects**: [[21.01 Website Redesign]] | [[21.02 Product Launch]]
- **22 Meetings**: [[22.01 Weekly Team]] | [[22.02 One-on-Ones]]

## 30-39 Learning
- **31 Courses**: [[31.01 Python Course]] | [[31.02 Design Thinking]]
- **32 Books**: [[32.01 Atomic Habits Notes]] | [[32.02 Deep Work Notes]]

## Quick Find
Type the number to jump directly:
- 11.01 = Fitness
- 21.01 = Website Project
- 32.01 = Book Notes
```

**4. Naming Convention:**
- Include numbers in filenames: `11.01 Fitness Routine.md`
- Use Obsidian's search to jump by number
- Create aliases for natural language

### Pros

✅ Instantly know where everything belongs
✅ Maximum 100 categories prevents over-organization
✅ Numeric IDs are quick to reference
✅ Works well for file management
✅ Clear communication (tell someone "it's in 21.03")

### Cons

❌ Very rigid structure
❌ Difficult to change once established
❌ Doesn't leverage Obsidian's linking strengths
❌ Can feel artificial for knowledge work
❌ Requires planning categories upfront
❌ Poor for interconnected ideas

### Best For

- **Administrators** managing documents and files
- **Organized professionals** who like clear systems
- People managing **file-based workflows**
- Those who prefer **hierarchical thinking**
- Users coming from **traditional filing systems**

---

## How to Choose a Methodology

### Decision Framework

Ask yourself these questions:

**1. What's your primary goal?**
- **Build interconnected knowledge** → Zettelkasten or Evergreen Notes
- **Manage projects and tasks** → PARA
- **Flexible knowledge management** → LYT
- **Organize files and documents** → Johnny Decimal

**2. How do you think?**
- **Linear/Hierarchical** → PARA, Johnny Decimal
- **Networked/Associative** → Zettelkasten, LYT
- **Evolving/Iterative** → Evergreen Notes

**3. How much time can you invest?**
- **Low maintenance** → PARA, Johnny Decimal
- **Moderate maintenance** → LYT
- **High maintenance** → Zettelkasten, Evergreen Notes

**4. What's your use case?**
- **Research & Academia** → Zettelkasten, Evergreen Notes
- **Professional Work** → PARA, Johnny Decimal
- **Creative Projects** → LYT, Evergreen Notes
- **General Knowledge** → LYT, Zettelkasten

### Comparison Matrix

| Methodology | Complexity | Flexibility | Best for Links | Best for Folders | Maintenance |
|-------------|------------|-------------|----------------|------------------|-------------|
| Zettelkasten | High | High | ⭐⭐⭐⭐⭐ | ⭐⭐ | High |
| PARA | Low | Low | ⭐⭐ | ⭐⭐⭐⭐⭐ | Medium |
| LYT | Medium | High | ⭐⭐⭐⭐ | ⭐⭐⭐ | Medium |
| Evergreen | High | Medium | ⭐⭐⭐⭐⭐ | ⭐⭐ | High |
| Johnny Decimal | Medium | Low | ⭐ | ⭐⭐⭐⭐⭐ | Low |

### Hybrid Approaches

You don't have to choose just one! Many successful systems combine methods:

**Common Hybrids:**

**1. PARA + Zettelkasten**
```
Vault/
├── Projects/           # PARA for actionable work
├── Areas/
├── Resources/
│   └── Zettelkasten/  # Zettelkasten for knowledge
│       ├── Permanent/
│       └── Literature/
└── Archive/
```

**2. LYT + PARA**
```
Vault/
├── Home.md            # LYT home note
├── MOCs/              # Maps of Content
├── Projects/          # PARA for projects
├── Areas/             # PARA for areas
└── Notes/             # All notes with LYT linking
```

**3. Johnny Decimal + LYT**
```
Vault/
├── 10-19 Personal/    # Johnny Decimal structure
├── 20-29 Work/
├── 30-39 Knowledge/
│   └── MOCs/          # LYT maps within areas
└── Index.md           # LYT home note
```

### Starting Recommendations

**Beginner:** Start with **PARA** or **LYT**
- Clear structure, easier to understand
- Can evolve as you learn Obsidian
- Lower barrier to entry

**Intermediate:** Try **LYT** or begin **Zettelkasten**
- You understand linking and structure
- Ready for more flexible systems
- Can handle the maintenance

**Advanced:** Implement **Zettelkasten** or **Evergreen Notes**
- Committed to knowledge management
- Willing to invest time in processing
- Building long-term knowledge base

---

## Final Thoughts

The best methodology is the one you'll actually use. Start simple, experiment, and evolve your system over time. Many successful knowledge workers blend multiple approaches to suit their needs.

Remember:
- **Start small**: Don't reorganize everything at once
- **Iterate**: Your system will evolve
- **Stay consistent**: Regular maintenance beats perfect organization
- **Focus on use**: The goal is useful notes, not a perfect system

> **Learn More:** [[Getting Started with Obsidian]] | [[My Personal Vault]] | [[Obsidian Glossary]]

---

*Tags: #methodology #organization #pkm #knowledge-management*
