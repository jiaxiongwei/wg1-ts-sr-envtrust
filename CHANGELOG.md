# Changelog

All notable changes to the TS.sr-envtrust source are recorded here.
Format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/).
Dates are ISO 8601 (YYYY-MM-DD).

## [Unreleased]

### Added

- Full reStructuredText source for Technical Specification TS.sr-envtrust,
  converted from the ITU-T-format Word contribution
  `FGTIDA-TS.sr-envtrust.docx` (background, gap analysis, A.1 justification,
  and a draft text of 9 clauses, 2 appendices and a bibliography; no tracked
  changes or comments).

### Changed

- **Structure.** The contribution's three parts were redistributed:
  the **Background** (1.1–1.5) moved into `index.rst` as front matter, its
  section numbers dropped because the front matter is not numbered; the
  **Gap analysis** became the final chapter; the **Suggestions** section (a
  single sentence proposing the work item) was dropped; the
  "Annex B: Proposed initial text" wrapper was dropped and its Summary and
  Keywords promoted into `index.rst`.
- **Clause numbering preserved.** The draft text already numbered its clauses
  1–9 with Conventions as clause 5, which is the final order, so no clause was
  renumbered and every in-text `Clause N` reference stays valid as written —
  unlike the Technical Report conversions, where inserting Conventions shifted
  the whole document.
- **Clause 9 split** into `09_main-procedures/index.rst` (9.1) plus one
  `_fragment.rst` per procedure, 9.2–9.9, included in order.
- **Front matter** carries the title, Abstract (from the cover), Background,
  Summary, History, Authors, Keywords, Foreword and Note. `conf.py` carries
  `project`, `release`, `author`, `copyright` and the four `cover_*` values; the
  History table is left empty pending approval records.
- **Numbering.** `numfig = False`; captions keep their document-wide numbers
  (`Figure 1–2`, `Table 1`) because the prose cites them by number.
- **Abbreviations** rendered as a two-column table (22 entries); the source
  table's blank header row was dropped and `:header-rows:` set to 0.
- **Definitions** in 3.1 rendered as a definition list, each entry keeping its
  source citation; 3.2 reads `None.` as in the source.
- **Bibliography** rendered as a definition list (3 entries).
- **Annex A** (A.1 justification) rendered as a `Field | Content` table, moved
  after the Bibliography. Base text recorded as `XXX`; the stray trailing
  placeholder in the Editor(s) cell was deleted.
- **Template example content removed**: the demonstration chapters and the
  OpenAPI sample (`src/doc/yaml/example.yaml`) with its `html_extra_path`
  entry. Archived under `local/archive/`, which is not tracked.
- **PDF cover** reads "Technical Specification" rather than "Recommendation".

### Fixed

- **Appendix II's JSON block** arrives as a four-space markdown indent, which
  reStructuredText reads as a block quote (20+ "Unexpected indentation"
  errors). Rendered as `.. code-block:: json`.
- **Fragment image paths.** A fragment lives one directory deeper than a
  chapter, so its figure needs `../../images/` rather than `../images/`.
- **Escaped bullets.** Word/pandoc emits `\-` for list items; normalised to
  `- ` so they render as a bullet list instead of literal text.
- **Foreword/Note over-capture.** The front-matter blocks were extracted from a
  sibling project whose `index.rst` has raw-LaTeX blocks between sections,
  which duplicated "Note"; extraction is now bounded and asserted.
- `exclude_patterns` extended to `**/_*.rst` so fragments are not built as
  standalone pages.
- Toctree entry for the split chapter points at
  `chapters/09_main-procedures/index`.
