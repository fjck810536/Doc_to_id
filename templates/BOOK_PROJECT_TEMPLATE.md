# Google Drive Book Project Template

建立新書時，以此結構初始化：

```
<BOOK_PROJECT>/
├── 00_PROJECT/
│   ├── PROJECT.json
│   ├── CURRENT_STATE.md
│   ├── NEXT_ACTION.md
│   ├── CHANGELOG.md
│   └── LAST_GOOD_BUILD.json
├── 01_MANUSCRIPT/
│   ├── SOURCE/
│   └── PUBLICATION_SOURCE/
├── 02_EDITORIAL/
│   ├── EDITORIAL_DIAGNOSIS.md
│   ├── BOOK_PROPOSAL.md
│   ├── BOOK_STRUCTURE.json
│   ├── CHICAGO_POLICY.md
│   └── HOUSE_STYLE.md
├── 03_DESIGN/
│   ├── DESIGN_PROFILE.json
│   ├── reference/
│   └── special_layouts/
├── 04_ASSETS/
│   ├── images/
│   ├── captions/
│   └── ASSET_MANIFEST.json
├── 05_QA/
│   ├── regression/
│   ├── full/
│   └── visual/
├── 06_BUILDS/
│   ├── working/
│   └── releases/
└── 99_ARCHIVE/
```

## PROJECT.json 最小範例

```json
{
  "schema_version": "1.0",
  "project_id": "book-example",
  "title": "書名",
  "publication_source": "01_MANUSCRIPT/PUBLICATION_SOURCE/book.docx",
  "structure": "02_EDITORIAL/BOOK_STRUCTURE.json",
  "design_profile": "03_DESIGN/DESIGN_PROFILE.json",
  "current_state": "00_PROJECT/CURRENT_STATE.md",
  "next_action": "00_PROJECT/NEXT_ACTION.md",
  "production_target": {
    "application": "Adobe InDesign",
    "version": "17.3.0.61",
    "scripting_runtime": "ExtendScript JSX"
  },
  "stage": "editorial",
  "last_good_build": null
}
```
