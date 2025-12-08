---
creation date: 2025-12-05
tags: genealogy/book, project/planning
---

# Immigrant Ancestors Book - Structure Proposal

## Book Organization

### Chronological by Arrival + Mixed Detail Approach
- **Major immigrants**: Full chapters (8-15 pages)
- **Secondary immigrants**: Profiles (2-4 pages)
- **Historical context**: Dedicated chapters + woven into narratives + appendices

---

## Proposed Directory Structure

```
02-subjects/genealogy/book/
├── 00-book-index.md                    # Master outline and progress tracker
├── 01-front-matter/
│   ├── introduction.md                 # Your journey discovering these stories
│   ├── how-to-use-this-book.md        # Reader's guide
│   └── family-tree-overview.md        # Visual overview of immigrant lines
│
├── 02-historical-context/              # Dedicated context chapters
│   ├── 01-new-france-overview.md      # Setting the stage
│   ├── 02-carignan-salieres.md        # The Regiment
│   ├── 03-filles-du-roi.md            # King's Daughters
│   └── 04-colonial-life.md            # Daily life in New France
│
├── 03-immigrant-stories/               # The main content (chronological)
│   ├── _timeline-index.md             # Chronological list of all immigrants
│   │
│   ├── 1600s/
│   │   ├── 16XX-[name]-chapter.md     # Full chapter for major ancestor
│   │   ├── 16XX-[name]-profile.md     # Profile for secondary ancestor
│   │   └── 1665-louis-badaillac-chapter.md  # Example: Louis gets full chapter
│   │
│   ├── 1700s/
│   │   ├── 17XX-[name]-chapter.md
│   │   └── 17XX-[name]-profile.md
│   │
│   └── 1800s/
│       ├── 18XX-[name]-chapter.md
│       └── 18XX-[name]-profile.md
│
├── 04-appendices/
│   ├── A-ships-and-voyages.md         # All ship voyages compiled
│   ├── B-places-of-origin.md          # Maps and info about French regions
│   ├── C-timeline.md                  # Comprehensive timeline
│   ├── D-glossary.md                  # Terms, French words, historical context
│   └── E-sources-bibliography.md      # All sources and further reading
│
├── 05-back-matter/
│   ├── afterword.md                   # Reflections
│   └── acknowledgments.md             # Thanks
│
└── _templates/
    ├── template-full-chapter.md       # Template for major ancestors
    ├── template-profile.md            # Template for secondary ancestors
    └── template-context-chapter.md    # Template for historical chapters
```

---

## Chapter Templates

### Full Chapter Template (Major Immigrants)
```markdown
# [Name] - [Arrival Year]

## Opening Hook
[Engaging opening about their journey or a defining moment]

## Life in [Place of Origin]
- Historical context of their hometown/region
- What life was like when they lived there
- Why they might have left

## The Decision to Leave
- Historical push/pull factors
- Personal circumstances (if known)
- The recruitment/call to New France

## The Voyage
- Ship details (like Le Vieux Simeon)
- Voyage conditions
- Fellow travelers

## Arrival in New France
- First impressions
- Initial settlement location
- Early challenges

## Building a New Life
- Occupation/role
- Marriage and family
- Contributions to community
- Land/property
- Military service (if applicable)

## Legacy
- Children and where they settled
- How their line connects to you
- Their impact on Quebec/Canada

## Historical Context Sidebar
[Relevant historical events/context woven in]

## Research Notes
[Link to detailed research file]
[[../../families/louis-badaillac|Research Notes]]

## Sources
```

### Profile Template (Secondary Immigrants)
```markdown
# [Name] - [Arrival Year]

## Quick Facts
- **Born**: [date/location]
- **Arrived**: [date/ship/context]
- **Settled**: [location]
- **Occupation**: [role]
- **Married**: [spouse name]
- **Died**: [date/location]

## Their Story
[2-3 paragraphs telling their story, including voyage and life in Quebec]

## Connection to You
[How they fit in your family tree]

## Notable Details
- [Interesting facts]
- [Historical context]

## Research Notes
[[../../families/[name]|Full Research]]

## Sources
```

---

## Immigrant Ancestor Tracking File

Create a master tracking file to plan your book:

```markdown
# Immigrant Ancestors - Book Planning

## Immigrants by Arrival Date

### 1600-1649
| Name | Arrival | Origin | Type | Status | Link |
|------|---------|--------|------|--------|------|
| [Name] | 16XX | [Place] | Chapter | Draft | [[link]] |

### 1650-1699
| Name | Arrival | Origin | Type | Status | Link |
|------|---------|--------|------|--------|------|
| Louis Badaillac | 1665 | Périgueux, France | Chapter | Research Complete | [[1665-louis-badaillac-chapter]] |

### 1700-1749
[Continue...]

### 1750-1799
[Continue...]

### 1800-1849
[Continue...]

### 1850-1900
[Continue...]

## Decision Criteria: Chapter vs Profile

### Full Chapter (8-15 pages)
- Significant historical importance
- Rich documentation available
- Compelling personal story
- Major family line
- Direct ancestor (vs collateral)

### Profile (2-4 pages)
- Less documentation
- Collateral line
- Interesting but not central to narrative
- Want to include but not emphasize

## Writing Progress
- [ ] Identify all immigrant ancestors
- [ ] Classify each as Chapter or Profile
- [ ] Research completion checklist
- [ ] First draft status
- [ ] Editing status
```

---

## Workflow Recommendation

### 1. Create Master List
- List all immigrant ancestors
- Determine arrival dates
- Classify as Chapter or Profile
- Link to existing research notes

### 2. Link to Existing Research
Your existing files become your research notes:
- `families/louis-badaillac.md` → Source material
- `book/03-immigrant-stories/1600s/1665-louis-badaillac-chapter.md` → Book chapter

### 3. Write from Research
- Copy relevant info from research notes
- Transform into narrative prose
- Add historical context
- Weave in the "why it matters"
- Make it engaging and readable

### 4. Maintain Separation
- **Research notes** (families/) = Facts, sources, raw data
- **Book chapters** (book/) = Narrative, storytelling, context
- Link between them with `[[wikilinks]]`

---

## Example: Louis Badaillac

### Research File (Current)
`02-subjects/genealogy/families/louis-badaillac.md`
- Keep this as-is
- Raw facts, dates, sources
- Your research repository

### Book Chapter (New)
`02-subjects/genealogy/book/03-immigrant-stories/1600s/1665-louis-badaillac-chapter.md`
- Transform research into story
- Add historical narrative
- Include Périgueux context (Fronde, etc.)
- Tell the Carignan-Salières story
- Describe the voyage on Le Vieux Simeon
- Explain his life in New France
- Connect to his descendants (you!)

---

## Benefits of This Structure

### For Writing
- Clear organization by time period
- Easy to see what's done vs. needs work
- Templates ensure consistency
- Historical chapters can be written anytime

### For Research
- Research notes stay separate and detailed
- Book chapters reference research via links
- Can update research without disrupting book
- Easy to add new immigrants as you discover them

### For Publishing
- Chapters are modular - can rearrange if needed
- Export is straightforward
- Appendices compile reference info
- Front/back matter clearly separated

### For Readers
- Chronological flow shows settlement patterns
- Context chapters provide background
- Appendices offer deep dives
- Mixed detail levels keep pacing varied

---

## Next Steps

1. **Create the directory structure** above
2. **Copy templates** to `_templates/` folder
3. **Create master tracking file** listing all immigrant ancestors
4. **Start with Louis Badaillac** as your first chapter
5. **Write historical context chapters** (can work on these while researching)
6. **Build gradually** - this is a long-term project

---

## Tools & Tips

### Obsidian Features to Use
- **Dataview**: Create dynamic tables of immigrants, progress tracking
- **Templates**: Use core Templates plugin for consistent chapter structure
- **Graph view**: Visualize connections between book chapters and research
- **Tags**: `#book/chapter`, `#book/profile`, `#book/context`, `#book/draft`, `#book/complete`

### Writing Tips
- Write the stories you're most excited about first
- Don't aim for perfection on first draft
- Historical context chapters can be written independently
- Revisit and refine as you learn more

### Export Considerations
- Keep formatting simple and consistent
- Use markdown that exports well (to PDF, Word, etc.)
- Consider using Pandoc for final book compilation
- Images should go in `book/_attachments/`

---

## Estimated Scope

If you have:
- **10 major immigrants** × 12 pages = 120 pages
- **20 secondary immigrants** × 3 pages = 60 pages
- **4 historical chapters** × 15 pages = 60 pages
- **Appendices** = 30 pages
- **Front/back matter** = 10 pages

**Total: ~280 pages** - A substantial family history book!

---

Would you like me to create this structure and get you started with Louis Badaillac's chapter?
