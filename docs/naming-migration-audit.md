# Naming Convention Migration Audit

**Generated:** 2026-02-23  
**Task:** Audit codebase for "condo/condos" references  
**Goal:** Rename all references from "condos" to "strands"

---

## Executive Summary

This audit identifies all occurrences of "condo", "condos", "Condo", "Condos" (and compound forms like "ClawCondos") across the Helix Landing codebase. The findings are organized by file type with line numbers and context for each occurrence.

### Quick Statistics

| Category | Files Affected | Total Occurrences |
|----------|---------------|-------------------|
| HTML | 1 | 5 |
| Documentation (MD) | 5 | 24 |
| Images | 1 | 1 (filename) |
| **Total** | 7 | 30 |

### Migration Complexity

- **Simple renames:** UI text, headings, feature descriptions
- **External references:** Attribution link to ClawCondos (may stay as-is)
- **Image rename:** `condo-context.png` → `strand-context.png`
- **Documentation:** References to backend code (condos-handlers.js, condos.create, etc.)

---

## 1. HTML Files

### `index.html`

| Line | Type | Current Text | Suggested Change | Notes |
|------|------|--------------|------------------|-------|
| 337 | aria-labelledby | `screenshot-condo` | `screenshot-strand` | ID reference |
| 346 | img src | `images/condo-context.png` | `images/strand-context.png` | Image path |
| 348 | heading id | `id="screenshot-condo"` | `id="screenshot-strand"` | Element ID |
| 348 | heading text | `Condo Context` | `Strand Context` | UI text |
| 403 | heading text | `Condos (Projects)` | `Strands (Projects)` | Feature name |
| 612 | attribution | `ClawCondos` | **KEEP AS-IS** | External repo name (historical reference) |

#### Context for line 337-348 (Screenshots section):
```html
<article class="screenshot-card" aria-labelledby="screenshot-condo">
  <div class="screenshot-window">
    ...
    <img src="images/condo-context.png" alt="Helix project detail view...">
  </div>
  <h3 id="screenshot-condo">Condo Context</h3>
  <p>View project details with goals graph, workspace status, and activity timeline</p>
</article>
```

#### Context for line 403 (Features section):
```html
<article class="feature-card">
  <div class="feature-icon" aria-hidden="true">🏗️</div>
  <h3>Condos (Projects)</h3>
  <p>Project workspaces with isolated git repos, branches, and worktrees.</p>
</article>
```

#### Context for line 612 (Footer attribution):
```html
<small>Forked from <a href="https://github.com/acastellana/clawcondos">ClawCondos</a> by Albert Castellana</small>
```
> **Note:** This is an external reference to the original repository. Consider keeping as-is for proper attribution, or update to reflect the fork history.

---

## 2. Documentation Files

### `docs/IMAGE-ALT-TEXT-AUDIT.md`

| Line | Type | Current Text | Suggested Change |
|------|------|--------------|------------------|
| 15 | table cell | `condo-context.png` | `strand-context.png` |

#### Context:
```markdown
| `condo-context.png` | Screenshots gallery | "Helix project detail view displaying..." |
```

---

### `docs/HELIX-FRESH-INSTALL-REPORT.md`

This file contains **19 occurrences** referencing backend code and architecture.

| Line | Type | Current Text | Suggested Change | Notes |
|------|------|--------------|------------------|-------|
| 16 | table cell | `condos-handlers.js` | `strands-handlers.js` | Backend file reference |
| 28 | prose | `condos auto-create repos` | `strands auto-create repos` | Feature description |
| 38 | code example | `condos.create` | `strands.create` | RPC method |
| 42 | code example | `condo_create_goal` | `strand_create_goal` | Tool name |
| 43 | code example | `condo_add_task` | `strand_add_task` | Tool name |
| 44 | code example | `condo_spawn_task` | `strand_spawn_task` | Tool name |
| 50 | prose | `condo_create_goal, condo_spawn_task` | `strand_create_goal, strand_spawn_task` | Tool references |
| 60 | code example | `condo_create_goal` | `strand_create_goal` | Tool name |
| 61 | code example | `condo_spawn_task` | `strand_spawn_task` | Tool name |
| 85 | checklist | `CLAWCONDOS_WORKSPACES_DIR` | `HELIX_WORKSPACES_DIR` | Env var name |
| 126 | prose | `create condos, goals` | `create strands, goals` | Feature description |
| 138 | code example | `condos.create` | `strands.create` | RPC method |
| 143 | code example | `condo_create_goal` | `strand_create_goal` | Tool name |
| 148 | code example | `condo_spawn_task` | `strand_spawn_task` | Tool name |
| 171 | checklist | `creating condo without` | `creating strand without` | Feature description |
| 197 | prose | `on condo creation` | `on strand creation` | Feature description |

---

### `docs/ux-audit.md`

| Line | Type | Current Text | Suggested Change |
|------|------|--------------|------------------|
| 6 | file reference | `/images/condo-context.png` | `/images/strand-context.png` |

#### Context:
```markdown
**Reference Screenshots:** `/images/dashboard-overview.png`, `/images/condo-context.png`, `/images/agents-overview.png`
```

---

### `docs/PERFORMANCE-HINTS.md`

| Line | Type | Current Text | Suggested Change |
|------|------|--------------|------------------|
| 41 | table cell | `condo-context.png` | `strand-context.png` |

#### Context:
```markdown
| condo-context.png | Screenshots gallery | `lazy` |
```

---

### `docs/SEMANTIC-HTML-AUDIT.md`

| Line | Type | Current Text | Suggested Change |
|------|------|--------------|------------------|
| 145 | heading structure | `h3: Condo Context` | `h3: Strand Context` |
| 150 | heading structure | `h3: Condos (Projects)` | `h3: Strands (Projects)` |

#### Context:
```
│   ├── h3: Condo Context
│   ├── h3: Agents Overview
...
│   ├── h3: Condos (Projects)
```

---

## 3. Image Files

### `images/condo-context.png`

| Current Filename | Suggested Filename |
|-----------------|-------------------|
| `condo-context.png` | `strand-context.png` |

**Location:** `/images/condo-context.png`  
**Size:** 120,982 bytes  
**Referenced by:** 
- `index.html` (line 346)
- `docs/IMAGE-ALT-TEXT-AUDIT.md` (line 15)
- `docs/ux-audit.md` (line 6)
- `docs/PERFORMANCE-HINTS.md` (line 41)

---

## 4. Special Considerations

### External References (Do NOT Rename)

| Location | Reference | Reason |
|----------|-----------|--------|
| `index.html:612` | `ClawCondos` | Historical attribution to original project |
| `index.html:612` | `github.com/acastellana/clawcondos` | External URL to original repo |

### Backend References in Documentation

The file `docs/HELIX-FRESH-INSTALL-REPORT.md` references backend code that exists in the **Helix core repository**, not this landing page:
- `condos-handlers.js` - backend file
- `condos.create` - RPC method
- `condo_create_goal`, `condo_add_task`, `condo_spawn_task` - agent tools
- `CLAWCONDOS_WORKSPACES_DIR` - environment variable

These documentation references should be updated to match the actual backend naming after the backend migration is complete.

---

## 5. Migration Checklist

### Phase 1: Image Rename
- [ ] Rename `images/condo-context.png` → `images/strand-context.png`

### Phase 2: HTML Updates (`index.html`)
- [ ] Line 337: Update `aria-labelledby="screenshot-condo"` → `screenshot-strand`
- [ ] Line 346: Update image src `images/condo-context.png` → `images/strand-context.png`
- [ ] Line 348: Update `id="screenshot-condo"` → `id="screenshot-strand"`
- [ ] Line 348: Update heading text `Condo Context` → `Strand Context`
- [ ] Line 403: Update heading text `Condos (Projects)` → `Strands (Projects)`

### Phase 3: Documentation Updates
- [ ] `docs/IMAGE-ALT-TEXT-AUDIT.md` (1 occurrence)
- [ ] `docs/ux-audit.md` (1 occurrence)
- [ ] `docs/PERFORMANCE-HINTS.md` (1 occurrence)
- [ ] `docs/SEMANTIC-HTML-AUDIT.md` (2 occurrences)
- [ ] `docs/HELIX-FRESH-INSTALL-REPORT.md` (19 occurrences - see detailed list above)

### Phase 4: Verification
- [ ] Run visual regression tests
- [ ] Verify all image references resolve
- [ ] Check aria/accessibility attributes
- [ ] Validate no broken links

---

## 6. Search Commands Used

```bash
# Find all "condo" variations in source files
grep -rn -E "(condo|Condo|CONDO)" --include="*.js" --include="*.ts" \
  --include="*.css" --include="*.html" --include="*.md" . | grep -v node_modules

# Find files with "condo" in filename
find . -name "*condo*" -o -name "*Condo*" | grep -v node_modules
```

---

## Appendix: Files with NO Condo References

The following files were checked and contain **no** "condo" references:
- `package.json`
- `site.webmanifest`
- `robots.txt`
- `sitemap.xml`
- `css/styles.css`
- `tests/*` (all test files)
- `cross-browser-test.js`
- `playwright.config.ts`
- `playwright-crossbrowser.config.ts`
- `README.md`
