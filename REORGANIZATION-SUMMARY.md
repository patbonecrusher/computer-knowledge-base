---
creation date: 2025-11-29
tags:
  - guide
  - migration
---

# Vault Reorganization Summary

**Date**: 2025-11-29
**Status**: Complete ✅

## What Changed

Your vault has been reorganized from a traditional folder-based structure to a brain-like, link-based system with Maps of Content (MOCs).

### New Structure

```
/
├── 00-INDEX.md                    # Main entry point
├── 00-inbox/                      # Unsorted new items
├── 01-sources/                    # Where info comes from
├── 02-subjects/                   # What the info is about
│   ├── programming/
│   ├── frameworks/
│   ├── databases/
│   ├── genealogy/
│   ├── norwegian/
│   ├── tools-and-utilities/
│   ├── web-development/
│   ├── engineering-concepts/
│   └── hardware/
├── 03-projects/                   # Active work (empty, ready for use)
├── 04-archive/                    # Old folder structure
├── _attachments/                  # All media files
├── GRAPH-VIEW-SETUP.md           # Graph configuration guide
└── REORGANIZATION-SUMMARY.md     # This file
```

## Migration Details

### Content Migrated

**From `sandbox/` (13 files)**
- Programming references → `02-subjects/programming/`
- Tool references → `02-subjects/tools-and-utilities/`
- Investigation list → `00-inbox/`

**From `software/` (7 files)**
- Framework docs → `02-subjects/frameworks/`
- Web tools → `02-subjects/tools-and-utilities/`

**From `engineering/` (8 files)**
- Concepts → `02-subjects/programming/`
- Learning notes → `02-subjects/databases/`, `02-subjects/tools-and-utilities/`
- Tools → `02-subjects/tools-and-utilities/`

**From `hobby/` (3 files)**
- Norwegian → `02-subjects/norwegian/`
- Miscellaneous → `00-inbox/`, `01-sources/`

**From `references/` (2 files)**
- Cool websites → `01-sources/`
- Fonts → `02-subjects/tools-and-utilities/`

**Attachments Consolidated**
- All images/media from scattered attachment folders → `_attachments/`

## Key Improvements

### 1. Maps of Content (MOCs) Created
- `00-INDEX.md` - Main vault entry point
- `02-subjects/programming/programming.md`
- `02-subjects/frameworks/frameworks.md`
- `02-subjects/databases/databases.md`
- `02-subjects/genealogy/genealogy.md`
- `02-subjects/norwegian/norwegian.md`
- `02-subjects/tools-and-utilities/tools-and-utilities.md`
- `00-inbox/00-inbox.md`
- `01-sources/01-sources.md`

### 2. Cross-Linking Implemented
- Neo4j links to both Databases and Genealogy MOCs
- All MOCs link back to main index
- Related topics linked across subjects

### 3. Frontmatter Standardized
Example:
```yaml
---
creation date: 2025-11-29
tags:
  - relevant
  - tags
subject: subject-name
source: source-name
---
```

### 4. Graph View Optimized
- Attachments isolated in `_attachments/`
- Old structure archived
- Configuration guide created

## Next Steps

### 1. Configure Your Graph View
Follow `GRAPH-VIEW-SETUP.md` to:
- Filter out attachments and archive
- Color-code subject areas
- Optimize display settings

### 2. Start Using the New Structure

**For new notes:**
1. Create in appropriate `02-subjects/` folder
2. Add frontmatter with tags and links
3. Link to relevant MOC
4. Add to inbox if unsorted

**For genealogy work:**
- Main hub: `02-subjects/genealogy/genealogy.md`
- Neo4j reference: `02-subjects/databases/neo4j.md`
- Add family tree notes and link to the genealogy MOC

**For Norwegian learning:**
- Main hub: `02-subjects/norwegian/norwegian.md`
- Vocabulary: `02-subjects/norwegian/words-and-phrases.md`

### 3. Clean Up (Optional)

Once you've verified the migration:
1. Review `04-archive/` to ensure all content migrated
2. Delete the archive folder if satisfied
3. Review `00-inbox/` and categorize pending items

### 4. Maintain the System

**Daily:**
- Quick captures → `00-inbox/`
- Process inbox regularly

**Weekly:**
- Review inbox items
- Update MOCs with new notes
- Add cross-links as you discover connections

**Monthly:**
- Archive completed projects to `04-archive/`
- Review graph view for orphaned notes

## Benefits You'll See

1. **Better Graph View**
   - Clear subject clusters
   - MOCs as central hubs
   - Visual connections between related topics

2. **Easier Navigation**
   - Start at `00-INDEX.md`
   - Jump to subject MOCs
   - Follow links to specific notes

3. **Flexible Organization**
   - Notes can belong to multiple subjects via tags
   - Cross-linking breaks folder barriers
   - Genealogy spans databases, tools, and research seamlessly

4. **Scalable System**
   - Add new subjects easily
   - No deep folder nesting
   - Tags and links grow with your knowledge

## Questions?

- **Where did my files go?** Check the migration mapping above
- **Can't find something?** Search in Obsidian or check `04-archive/`
- **Graph still messy?** Follow `GRAPH-VIEW-SETUP.md`
- **How to add notes?** Create in `02-subjects/`, link to MOC

---

**Happy linking!** 🧠🗺️
