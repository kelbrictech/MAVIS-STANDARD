# Changelog

All notable changes to MAVIS STANDARD are documented here.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [2.0 STANDARD] — 2026-09-01

**First public release on GitHub.**

### Added
- **Multi-page project management** — Create, load, and switch between pages
- **Grid-based canvas** — Customizable grid (6×12 portrait, 12×8 landscape)
- **Canvas elements** — 6 element types (button, field, toggle, icon, text, image)
- **Z-ordering & layering** — Bring to front / send to back controls per element
- **Global instance tagging** — Every placed element gets unique, immutable instance ID
- **Master instance registry** — Complete audit trail with creation timestamps and deletion records
- **Stamped deletions** — Deleted elements marked with deletion timestamp, preserved in audit
- **Reusable image library** — Create image placeholders once, reference across pages and elements
- **Auto-ordinal naming** — Images and elements auto-numbered by type (Hero 1, Hero 2, Button 1, etc.)
- **PNG export** — Single page or all pages as grid
- **CSV export** — Two-table format: master registry + page layouts
- **Project persistence** — Auto-save to browser localStorage
- **Properties panel** — View and edit selected element properties
- **Dark theme UI** — Optimized for focus, readable dark sidebar with light canvas
- **Message notifications** — Real-time feedback for user actions
- **Project-level CSV download** — Full audit trail and layout specs

### Features
- **No installation required** — Single HTML file
- **No login required** — Working project data stays in browser-local storage
- **Offline-complete core** — PNG, CSV, JSON, and HTML export have no mandatory network dependency
- **Self-contained PNG rendering** — Removed the CDN runtime dependency

### Technical
- Responsive canvas with grid alignment
- Touch-friendly drag interactions
- Element positioning in grid cells (pixel-agnostic)
- Undo-less design (save frequently)
- localStorage-based persistence

---

## [Release Hardening] — 2026-09-01

### Changed
- Removed bundled SHALA sample project data from the public STANDARD build
- Removed the external html2canvas CDN runtime dependency
- PNG export now renders locally from MAVIS page data
- Project Save now synchronizes the current page before persistence
- Documentation reconciled with actual STANDARD behavior
- Established the product principle: **online-enhanced, offline-complete**

---

## V3 ADVANCED Direction

MAVIS V3 ADVANCED is defined by actual visual page mockup creation without coding. Supporting enhancements may include stronger layout controls and reusable components, but ADVANCED remains a design tool rather than an application code generator.

---

## Version Numbering

- **2.0 STANDARD** — Stable, public release
- **2.x** — Bug fixes and minor features
- **3.0 ADVANCED** — Visual page mockup creation without coding

---

## Known Issues

- No undo/redo (workaround: save frequently, export CSV)
- No multi-select (workaround: edit one element at a time)
- localStorage is per-browser (workaround: export CSV for backup)
- No import from other tools (workaround: manually recreate or screenshot)

---

## Migration Notes

### From Alpha/Beta
If you were using an earlier version of MAVIS:
1. Export your project as CSV
2. Manually recreate in v2 (layouts are lightweight)
3. Instance IDs will be fresh (expected)

v2 data format is stable going forward.

---

## Support

- **Bugs**: [Report on GitHub Issues](../../issues)
- **Ideas**: [Discuss on GitHub Discussions](../../discussions)
- **Docs**: See [README.md](README.md)

---

## License

MIT — Free to use, modify, distribute.

## Mobile-first hardening

- Added PWA manifest and service-worker application-shell caching.
- Added local 192 px and 512 px install icons.
- Converted element movement from mouse-only dragging to primary Pointer Events with pointer capture.
- Drag rendering now updates visual position during movement and persists only when the gesture finishes.
- Preserved deliberate two-touch pinch zoom on the canvas.
- Added mobile setup and properties bottom sheets.
- Enforced larger mobile interaction targets and canvas-specific touch ownership.
- Kept browser-level accessibility zoom available outside the canvas rather than globally disabling touch behavior.
