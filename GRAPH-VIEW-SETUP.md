---
creation date: 2025-11-29
tags:
  - guide
  - obsidian
  - graph-view
---

# Graph View Configuration Guide

This guide will help you configure Obsidian's graph view to display a clean, organized visualization of your knowledge base.

## Recommended Settings

### 1. Filters (Clean up the graph)

Go to **Settings → Graph View → Filters** and add these exclusions:

```
path:_attachments
path:04-archive
path:"trying new structure"
```

This will:
- Hide all media files from the graph
- Hide archived content
- Hide the old experimental structure

### 2. Groups (Color-code subjects)

Go to **Settings → Graph View → Groups** and create these groups:

| Group Name | Query | Color |
|------------|-------|-------|
| MOCs | `tag:#moc` | Orange/Red |
| Programming | `path:02-subjects/programming` | Blue |
| Frameworks | `path:02-subjects/frameworks` | Green |
| Databases | `path:02-subjects/databases` | Purple |
| Genealogy | `tag:#genealogy` | Pink |
| Norwegian | `tag:#norwegian` | Yellow |
| Tools | `path:02-subjects/tools` | Cyan |
| Inbox | `path:00-inbox` | Gray |

### 3. Display Settings

Recommended display settings:
- **Node Size**: Based on number of links
- **Link Distance**: Medium (50-70)
- **Repel Force**: Medium-High (70-85)
- **Link Thickness**: Based on number of links
- **Arrows**: On (shows directionality)

### 4. Forces

Adjust these for better visualization:
- **Center Force**: 0.3-0.5 (pulls nodes toward center)
- **Repel Force**: 70-85 (prevents overlap)
- **Link Force**: 1.0 (respects link distance)
- **Link Distance**: 50-70 (space between connected nodes)

## Expected Graph Structure

Your graph should now show:

1. **Central Hub**: `00-INDEX.md` at the center
2. **Subject Clusters**: Each subject MOC forms a cluster of related notes
3. **Cross-links**: Connections between subjects (e.g., Neo4j links both Databases and Genealogy)
4. **Clear Separation**: Distinct visual clusters for each subject area

## Using the Graph

### Local Graph
- Right-click any note → "Open local graph"
- Shows only connected notes
- Great for exploring a specific topic

### Search in Graph
- Use the search box to highlight specific notes
- Filter by tags (e.g., `tag:#genealogy`)

### Navigation
- Click nodes to open notes
- Drag nodes to rearrange
- Zoom and pan to explore

## Maintenance

To keep your graph clean:
1. **Always link to MOCs** - Every note should link to at least one MOC
2. **Use consistent tags** - Helps with grouping and filtering
3. **Avoid orphans** - Notes with no connections clutter the graph
4. **Archive old content** - Move completed work to `04-archive/`

## Troubleshooting

**Graph is cluttered:**
- Check filters are applied correctly
- Move attachments to `_attachments/`
- Archive old folders

**Notes not grouping:**
- Ensure proper tags in frontmatter
- Check MOC links exist
- Verify path filters

**Can't find notes:**
- Use search function
- Check if note is in archive
- Look at local graph of related notes

---

**Back to:** [[00-INDEX|Main Index]]
