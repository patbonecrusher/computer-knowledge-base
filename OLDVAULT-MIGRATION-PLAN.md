---
creation date: 2025-11-30
tags:
  - documentation
  - migration
  - planning
---

# 📦 Old Vault Migration Plan

**Source**: `04-archive/oldvault/my-brain/`
**Total Files**: ~296 markdown files

## 📊 Content Analysis

### Current Distribution
- 🌳 **Genealogy**: 116 files (39%)
- 📝 **Today I Learned**: 78 files (26%)
- 🚧 **WIP (Work in Progress)**: 83 files (28%)
- 📚 **Notes**: 7 files (2%)
- 🏠 **Home**: 2 files (1%)
- 📄 **Root Level**: 7 files (2%)

---

## 🎯 Migration Strategy

### Phase 1: Genealogy Content (116 files)

**Destination**: `02-subjects/genealogy/`

#### Current Structure in Old Vault:
```
genealogy/
├── research/ (18 family research files)
├── famous relationships/ (20+ files on historical connections)
├── convents/ (1 file)
├── location/ (location-related research)
├── name variants/ (name variation documentation)
├── references/ (genealogy references)
└── attachments/ (genealogy images/documents)
```

#### Proposed New Organization:
```
02-subjects/genealogy/
├── genealogy.md (existing MOC - update)
├── families/
│   ├── levasseur.md
│   ├── lallier.md
│   ├── morel-seyer-laplante.md
│   ├── michaud-beauregard.md
│   ├── brunelle.md
│   ├── boissonnault.md
│   ├── gagne.md
│   ├── seyer-desmarais.md
│   └── ... (other family research)
├── historical/
│   ├── regiment-de-carignan.md
│   ├── filles-du-roi.md
│   ├── premiers-colons-quebec.md
│   ├── emigration-percheron.md
│   ├── louis-hebert.md
│   └── native-american-ancestors.md
├── institutions/
│   ├── sisters-of-presentation-mary.md
│   ├── les-soeurs-du-precieux-sang.md
│   └── convents.md
├── connections/
│   ├── paul-shaver-coworker.md
│   ├── philo-farnsworth.md
│   └── famous-relationships.md
├── resources/
│   ├── name-variants.md
│   └── location-references.md
└── _attachments/ (images, documents)
```

**Action Items**:
- ✅ Already have genealogy MOC
- 📝 Create family subdirectory structure
- 📝 Merge/consolidate research files
- 📝 Move attachments to `_attachments/`
- 📝 Update internal links

---

### Phase 2: Today I Learned Content (78 files)

**Destination**: `02-subjects/programming/til/` or integrate into existing tool docs

#### Current TIL Categories:
- Git (10 files)
- Shell (12 files)
- Linux (15 files)
- macOS (6 files)
- AWS (4 files)
- Web Dev (8 files)
- Python (3 files)
- Rust (3 files)
- NodeJS (2 files)
- MCU/Embedded (8 files)
- SSH/SSL (5 files)
- Other (2 files)

#### Proposed Organization Strategy:

**Option A: Create TIL Section (Recommended)**
```
02-subjects/programming/til/
├── til.md (MOC/index)
├── git/
│   ├── side-by-side-diff.md
│   ├── reset-submodules.md
│   ├── delete-all-tags.md
│   └── ...
├── shell/
│   ├── moving-process-to-tmux.md
│   ├── udp-packet-netcat.md
│   └── ...
├── linux/
│   ├── systemd/
│   ├── yocto/
│   ├── petalinux/
│   └── ...
├── cloud/
│   └── aws/
├── web-dev/
└── embedded/
```

**Option B: Integrate into Existing Docs**
- Add TIL snippets to existing tool documentation
- Git TILs → append to `02-subjects/tools-and-utilities/cli/git.md` as "Common Patterns" or "Advanced Tips"
- Shell TILs → append to relevant tool docs (tmux, bash, etc.)
- macOS TILs → `02-subjects/operating-systems/macos/tips-and-tricks.md`

**Recommendation**: Use **Option A** for now - keeps TILs discoverable and easy to reference. Can consolidate later if needed.

**Action Items**:
- 📝 Create TIL structure
- 📝 Review each TIL for relevance
- 📝 Update to new format (add frontmatter, tags)
- 📝 Fix internal links
- 🗑️ Archive outdated TILs (old versions, deprecated tools)

---

### Phase 3: WIP Content (83 files)

**Destination**: Mixed - depends on content type

#### WIP Categories:
- macOS setup (12 files)
- Norwegian learning (few files)
- Functional programming (10 files)
- Rust learning (5 files)
- Linux kernel dev (5 files)
- Raspberry Pi projects (5 files)
- Project structures (7 files)
- Import to clean (11 files)
- References to sort (various)
- Emulations (2 files)
- MDF 2024 (5 files)
- Home improvements (2 files)
- AI image enhancer (2 files)

#### Proposed Mapping:

**Active Learning Content**:
```
02-subjects/norwegian/
├── norwegian.md (existing MOC)
└── learning/ (new subdirectory)
    └── [Norwegian learning files from WIP]

02-subjects/programming/functional-programming/
└── learning/ (new subdirectory)
    └── [FP learning files from WIP]

02-subjects/programming/languages/rust/
└── learning/
    └── [Rust learning files from WIP]
```

**Project-Specific Content**:
```
03-projects/
├── macos-setup/
│   ├── README.md
│   └── [macOS setup files]
├── raspberry-pi/
│   └── [Pi project files]
├── linux-kernel-dev/
│   └── [Kernel dev files]
└── mdf-2024/
    └── [MDF files]
```

**Unsorted/Reference Content**:
```
00-inbox/
└── [Files from "import to clean" and "references to sort"]
```

**Personal/Miscellaneous**:
```
02-subjects/personal/
├── home-improvements/
└── trip-to-france.md

(Or keep in 04-archive if not actively used)
```

**Action Items**:
- 📝 Review each WIP folder
- ✅ Move active learning to subjects
- ✅ Move projects to `03-projects/`
- 📝 Move unsorted to `00-inbox/`
- 🤔 Decide on personal content location
- 🗑️ Archive test files and experiments

---

### Phase 4: Root Level Files (7 files)

#### Files to Migrate:
1. **Home.md** - Dashboard with dataviewjs
2. **Fleeting Notes.md** - Quick capture
3. **Quick Links.md** - Reference links
4. **To Investigate.md** - Investigation list
5. **mdf 2024.md** - Event/project notes
6. **root.md** - Navigation
7. **Screenshot metadata.md** - Can delete

#### Proposed Organization:

**Keep as Reference/Dashboard**:
```
00-INDEX.md (update to incorporate useful links from Quick Links)

00-inbox/
├── fleeting-notes.md (rename and clean up)
└── to-investigate.md (review and categorize)
```

**Project Specific**:
```
03-projects/mdf-2024/
└── mdf-2024.md
```

**Archive**:
- Home.md (old dashboard format, replaced by new index)
- root.md (replaced by 00-INDEX.md)
- Screenshot metadata (delete)

**Action Items**:
- 📝 Extract useful links from Quick Links → add to 00-INDEX.md
- 📝 Review Fleeting Notes → move relevant items to appropriate subjects
- 📝 Review To Investigate → create action items or research notes
- ✅ Move mdf-2024 to projects
- 🗑️ Archive/delete old dashboard files

---

### Phase 5: Notes & Home Content (9 files)

#### Notes/Engineering (7 files):
```
Likely embedded/engineering content - review and merge with:
02-subjects/embedded/
02-subjects/programming/
```

#### Home/Appliance (2 files):
```
Review content:
- If valuable → 02-subjects/personal/home/
- If outdated → 04-archive/
```

**Action Items**:
- 📝 Review engineering notes content
- 📝 Merge with existing subjects
- 🤔 Decide on home/appliance file disposition

---

## 🔄 Migration Process

### Preparation
1. ✅ Analyze old vault structure (DONE)
2. ✅ Create migration plan (DONE)
3. 📝 Backup current vault
4. 📝 Create new subdirectories

### Execution Order

**Week 1: Genealogy**
- Day 1-2: Create directory structure
- Day 3-4: Migrate family research files
- Day 5: Migrate historical content
- Day 6: Move attachments
- Day 7: Update MOC and fix links

**Week 2: TIL Content**
- Day 1: Create TIL structure
- Day 2-3: Migrate Git/Shell/Linux TILs
- Day 4: Migrate cloud/web-dev TILs
- Day 5: Migrate embedded TILs
- Day 6-7: Review, update format, fix links

**Week 3: WIP & Projects**
- Day 1-2: Sort WIP content by destination
- Day 3: Move learning content to subjects
- Day 4: Create project folders and move files
- Day 5: Move unsorted to inbox
- Day 6-7: Review and clean up

**Week 4: Cleanup**
- Day 1: Migrate root level files
- Day 2: Migrate notes/home content
- Day 3-4: Fix all broken links
- Day 5: Update MOCs and indexes
- Day 6: Final review and testing
- Day 7: Archive old vault

---

## 📋 Checklist Template

For each file migrated:
- [ ] Read and understand content
- [ ] Determine correct destination
- [ ] Add/update frontmatter (date, tags, description)
- [ ] Update content format if needed
- [ ] Fix internal links
- [ ] Add to relevant MOC
- [ ] Add related links
- [ ] Verify no duplicates
- [ ] Delete/archive source file

---

## 🚨 Special Considerations

### Duplicates
Some content may overlap with existing vault:
- Genealogy: Already have genealogy.md MOC
- Git/Shell: May overlap with tool documentation
- Norwegian: Already have norwegian.md

**Action**: Merge rather than duplicate. Keep most comprehensive version.

### Attachments
- Move all to `_attachments/` in root
- Update image links: `![[image.png]]` → `![](/_attachments/image.png)`
- Or keep in subdirectory: `02-subjects/genealogy/_attachments/`

### Outdated Content
- Review TILs for outdated information
- Archive old tool versions
- Delete test files and experiments

### Dataview Queries
- Home.md uses dataviewjs for recent files
- Consider recreating useful queries in new structure
- Or simply rely on Obsidian's built-in features

---

## 📊 Expected Outcomes

After migration:
- ✅ All content organized in new structure
- ✅ No more duplicate organizational systems
- ✅ TIL content easily discoverable
- ✅ Genealogy research well-organized
- ✅ Projects clearly separated
- ✅ Inbox for temporary/unsorted items
- ✅ Clean archive of old vault
- ✅ Updated MOCs with all content linked

---

## 🎬 Quick Start Commands

```bash
# Create TIL structure
mkdir -p "02-subjects/programming/til"/{git,shell,linux,cloud,web-dev,embedded}

# Create genealogy subdirs
mkdir -p "02-subjects/genealogy"/{families,historical,institutions,connections,resources}

# Create project directories
mkdir -p "03-projects"/{macos-setup,raspberry-pi,linux-kernel-dev,mdf-2024}

# Backup before migration
cp -r 04-archive/oldvault 04-archive/oldvault-backup-$(date +%Y%m%d)
```

---

## ❓ Questions to Answer

Before proceeding:
1. **TIL Organization**: Option A (dedicated section) or Option B (integrate into docs)?
2. **Personal Content**: Keep in vault or archive separately?
3. **Genealogy Attachments**: Root `_attachments/` or `02-subjects/genealogy/_attachments/`?
4. **WIP Content**: What's truly "work in progress" vs "should be archived"?
5. **Migration Speed**: All at once or gradual over 4 weeks?

---

**Back to:** [[00-INDEX|Main Index]]
