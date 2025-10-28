# Canvas First Workflow

I use [[How Obsidian Works - Details#Canvas|canvas]] as my primary editor to **organize information spatially**. This approach transforms how I think about and structure knowledge by giving me a visual, two-dimensional space to arrange ideas.

![[ObsidianCanvas.png]]

## What Is Canvas?

Canvas is [[AboutObsidian|Obsidian's]] infinite workspace feature that lets you arrange notes, images, web links, and text cards spatially. Think of it as a digital whiteboard that can embed your actual markdown notes.

**Key Capabilities:**
- Infinite 2D space to arrange content
- Embed markdown notes directly on the canvas
- Add text cards for quick notes
- Include images and PDFs
- Create connections with arrows
- Group related items visually
- Color code for organization
- Zoom in/out for different perspectives

The [[How Obsidian Works - Details#Canvas|canvas feature]] gives you spatial thinking combined with the power of [[How Obsidian Works - Details#Links|wikilinks]].

## Why Canvas First?

Traditional folder hierarchies force you to choose ONE organizational structure. But ideas don't naturally fit in trees - they form networks with multiple relationships.

**Folders:** Rigid hierarchy
```
Projects/
└── ProjectA/
    ├── Planning/
    ├── Design/
    └── Implementation/
```
Where does a note about a design decision during implementation go?

**Canvas:** Flexible spatial arrangement
On a canvas, that note can sit between Design and Implementation sections, with arrows showing how it relates to both. You get to see the relationships visually.

**Benefits of Canvas-First:**

**Spatial Memory**
Humans are great at remembering where things are spatially. "That API design note was in the upper right, near the architecture diagram."

**Multiple Perspectives**
Zoom out to see the big picture, zoom in to focus on details. Move seamlessly between forest and trees.

**Visual Relationships**
Use arrows, proximity, and grouping to show how ideas connect. The [[How Obsidian Works - Details#Graph|graph view]] shows link structure, but canvas shows spatial relationships.

**Rapid Reorganization**
Drag notes around to try different arrangements. Canvas makes it easy to experiment with organization without moving files.

**Mixed Media**
Combine embedded notes, images, sketches, and quick text cards all in one view.

## My Canvas Pattern

Each project has a canvas at the root:

```
MyProject/
├── Project.canvas      # Main visual overview
├── Architecture.md     # Embedded in canvas
├── Roadmap.md         # Embedded in canvas
├── API.md             # Embedded in canvas
└── ...
```

The `.canvas` file becomes the **primary entry point** for the project. When I open the project, I open the canvas and see everything at a glance.

### Canvas Embeds Markdown

This is the key pattern: **Canvas embeds markdown notes, not replaces them.**

Each embedded note is a real `.md` file that:
- Can be edited from the canvas
- Can be opened separately in Obsidian
- Contains [[How Obsidian Works - Details#Links|wikilinks]] to other notes
- Works in any markdown editor
- Can be [[Exporting to the Web|published to the web]]
- Appears in [[How Obsidian Works - Details#Graph|graph view]]

The canvas is an **optional visual view** over markdown files that remain independently useful.

## Creating a Canvas Structure

### Step 1: Start with Central Concepts

Create the main canvas and embed your core documents:

1. Create `ProjectName.canvas`
2. Drag in `index.md` as the central node
3. Arrange key notes around it spatially:
   - Architecture above
   - Roadmap to the right
   - Implementation notes below
   - Resources to the left

### Step 2: Add Context with Cards

Use text cards for:
- Section headers ("Architecture", "Planning", "Ideas")
- Quick notes that don't need a full file
- Questions or TODOs
- Visual labels and annotations

Text cards are perfect for ephemeral content, while embedded notes are for lasting knowledge.

### Step 3: Show Relationships

Use arrows to indicate:
- Dependencies (this requires that)
- Relationships (this relates to that)
- Flow (first this, then that)
- References (based on this idea)

Arrows make relationships explicit that [[How Obsidian Works - Details#Links|wikilinks]] alone might not convey.

### Step 4: Use Spatial Grouping

**By Time:** Left to right timeline
- Past decisions → Current work → Future plans

**By Layer:** Top to bottom architecture
- UI layer at top → Business logic → Database at bottom

**By Topic:** Clustered areas
- Authentication cluster in one area
- API design cluster in another
- Each with its own local organization

**By Status:**
- "In Progress" section at top
- "Backlog" at bottom
- "Done" off to the side

### Step 5: Color Code

Use colors to indicate:
- Priority (red = urgent, green = nice-to-have)
- Type (blue = technical, yellow = design, green = planning)
- Status (gray = done, bright = active, faded = backlog)
- Team (different colors for different people/teams)

Colors provide instant visual cues when scanning the canvas.

## Canvas Workflows

### Workflow 1: Project Planning

**Initial Brainstorm:**
1. Create new canvas
2. Add text cards for all ideas (rapid capture)
3. Arrange cards into clusters
4. Add arrows showing dependencies
5. Color code by priority

**Convert to Structure:**
1. Create markdown files for key cards
2. Replace cards with embedded notes
3. Refine arrangement
4. Add detail to individual notes

**Ongoing Management:**
1. Review canvas during weekly planning
2. Move completed items to "Done" area
3. Add new ideas as they arise
4. Adjust priorities visually

### Workflow 2: Learning/Research

**Collecting Information:**
1. Create canvas for topic
2. Drop in notes for each source/concept
3. Add images and diagrams
4. Create text cards for insights

**Finding Connections:**
1. Arrange notes by similarity
2. Draw arrows between related concepts
3. Add text cards for patterns you notice
4. Group into themes

**Synthesizing Understanding:**
1. Create new note: "My Understanding"
2. Embed it centrally on canvas
3. Draw arrows from sources
4. Use canvas as reference while writing

### Workflow 3: Meeting Prep

**Before Meeting:**
1. Create canvas for meeting
2. Embed relevant background notes
3. Add text cards for talking points
4. Arrange in discussion order
5. Include any images/data to share

**During Meeting:**
1. Open canvas in presentation mode
2. Navigate spatially through topics
3. Take notes in text cards
4. Link to [[My Personal Vault#People Notes|people notes]]

**After Meeting:**
1. Convert key text cards to notes
2. Link to [[My Personal Vault#Daily Notes as the Foundation|daily note]]
3. Archive canvas or keep for next meeting

### Workflow 4: Writing Long Documents

**Outlining:**
1. Create canvas for document
2. One text card per section/chapter
3. Arrange in rough order
4. Add cards for key points under each

**Drafting:**
1. Convert major sections to embedded notes
2. Write within the embedded notes
3. See full structure while writing
4. Easy to reorder sections

**Refining:**
1. Zoom out to see full structure
2. Identify gaps or redundancies
3. Move sections around
4. Add connections between chapters

## Canvas in Different Contexts

### Personal Vault

In my [[My Personal Vault|personal vault]], I use canvases for:
- **Year planning** - Goals, areas of focus, projects
- **Weekly review** - [[My Personal Vault#Daily Notes as the Foundation|Daily notes]] arranged chronologically
- **Project dashboard** - Links to all active [[One Vault to Rule Them All|project vaults]]
- **Learning topics** - Resources, notes, and connections for things I'm studying

### Project Documentation

For [[Using Obsidian with GitHub|GitHub projects]], canvases work well for:
- **System architecture** - Visual component layout
- **Feature planning** - User stories and technical tasks
- **Onboarding** - Guided tour for new team members
- **Decision records** - Chronological layout of major decisions

### Publishing Considerations

When [[Exporting to the Web|publishing to the web with Quartz]], be aware:

**Canvas Limitations:**
- Visual layout is NOT preserved on the web
- Published canvas shows as a list of links
- The spatial arrangement only exists in Obsidian

**Workarounds:**
1. **Screenshot approach** - Include canvas screenshot in a note
2. **Separate web note** - Create `index.md` that mirrors canvas structure
3. **Keep canvas private** - Add to `ignorePatterns` in `quartz.config.ts`
4. **Focus on notes** - Rely on [[How Obsidian Works - Details#Links|wikilinks]] for web navigation

I typically keep canvases for personal organization and create separate `index.md` files for web publication that capture the key structure.

## Canvas + AI

The [[Canvas First Workflow|canvas approach]] works wonderfully with [[Using AI with Obsidian|AI assistance]]:

**AI Can Help With:**
- Generating initial text cards from prompts
- Creating structure suggestions
- Finding related notes to embed
- Identifying missing connections
- Suggesting better spatial arrangements

**Limitations:**
- AI can't directly edit `.canvas` JSON (complex format)
- AI can edit the embedded markdown notes
- You handle spatial arrangement manually

**Best Practice:**
Use AI to create and improve the markdown notes, then arrange them on canvas yourself.

## Tips and Tricks

**Performance:**
- Keep canvases focused (< 50 items)
- Create sub-canvases for large topics
- Embed canvases within canvases for hierarchical structure

**Organization:**
- Name canvases clearly: `ProjectName Canvas.canvas`
- One main canvas per project
- Create topical canvases as needed

**Reusability:**
- Create canvas templates for common structures
- Use [[Best Obsidian Plugins#Advanced Canvas|Advanced Canvas plugin]] for extra features
- Share canvas patterns with team in [[Using Obsidian with GitHub|GitHub repos]]

**Maintenance:**
- Regular cleanup of completed/outdated items
- Archive old canvases but keep the embedded notes
- Use canvas as index, notes as permanent knowledge

## Why This Works

The canvas-first approach succeeds because:

**Leverages Spatial Thinking**
Our brains are wired for spatial memory. Seeing where information is located helps recall and understanding.

**Maintains Markdown Foundation**
Embedded notes are still normal [[How Obsidian Works|markdown files]]. The canvas is just a view, not a replacement.

**Flexible Organization**
No forced hierarchy. Arrange information however makes sense for your thinking.

**Combines Visual and Textual**
Get the benefits of visual organization without losing the power of text-based [[How Obsidian Works - Details#Links|wikilinks]] and search.

**Scales Appropriately**
Use canvases where spatial thinking helps, regular notes where it doesn't. Not every note needs a canvas.

**Works With Existing Tools**
Canvas files are JSON that version-controls well in [[Using Obsidian with GitHub|Git]], works with [[Using AI with Obsidian|AI tools]], and integrates with the [[How Obsidian Works - Details#Graph|graph view]].

## Getting Started

To adopt canvas-first workflow:

1. **Create first canvas** for an active project
2. **Drag in existing notes** to embed them
3. **Arrange spatially** - try different layouts
4. **Add arrows** to show key relationships
5. **Use text cards** for quick thoughts
6. **Color code** for visual clarity
7. **Review regularly** and adjust arrangement

Start with one canvas and see how it changes your thinking about the project. The spatial view often reveals insights and patterns you wouldn't notice in a linear list.

## Learn More

- [[How Obsidian Works - Details#Canvas|Canvas Details]] - Technical overview
- [[My Personal Vault]] - Using canvas in personal knowledge management
- [[Using Obsidian with GitHub]] - Canvas in project documentation
- [[How I Use Obsidian]] - Overall workflow integration
- [[Best Obsidian Plugins#Advanced Canvas|Advanced Canvas Plugin]] - Enhanced canvas features
- [[Using AI with Obsidian]] - AI-assisted note creation for canvas
