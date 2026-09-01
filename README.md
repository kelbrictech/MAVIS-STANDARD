# MAVIS STANDARD

**M**ulti-page **A**rtboard **V**isual **I**nformation **S**ystem — A lightweight, grid-based page flow design tool.

Design page layouts fast. Export as PNG. Share visually. No complexity.

---

## What is MAVIS?

MAVIS STANDARD is a single-file, browser-based design tool for wireframing page flows and creating visual specifications. It's built for speed and simplicity—drag elements onto a grid, organize them across multiple pages, export as high-res PNG, and hand off to your team.

**No login required. Offline-complete. Online capabilities may enhance MAVIS, but core design work never depends on connectivity.**

---

## Features

### Core
- **Multi-page projects** — Create and manage multiple pages within one project
- **Grid-based canvas** — Precise alignment with customizable grid (6×12 portrait, 12×8 landscape)
- **Canvas elements** — Buttons, fields, toggles, icons, text labels, and images; place and move them on the grid
- **Reusable image library** — Create image placeholders once, reference them across pages
- **Z-ordering & layering** — Stack elements, bring to front/send to back

### Organization & Audit
- **Global instance tagging** — Every placed element gets a unique, immutable ID (`Button1-1`, `Hero2-3`, etc.)
- **Master instance registry** — Complete audit trail of all elements, creation timestamps, deletion records
- **Stamped deletions** — Deleted items marked with timestamp, never removed from history

### Export & Handoff
- **Page as PNG** — Export current page as high-resolution image (2x scale)
- **All pages grid** — Render all pages and export as a 2-column grid on one image
- **CSV export** — Two-table format:
  - **Master Instance Registry**: Full audit trail (active + deleted elements with timestamps)
  - **Page Layouts**: Current state with position, size, z-index per page
- **JSON export** — Export the current page state as structured JSON
- **Project persistence** — Auto-save to browser localStorage

### Per-Page Settings
- **Page name & metadata** — Name, zone, orientation (portrait/landscape)
- **Grid dimensions** — Custom width/height for layout
- **Background color** — Set canvas background per page

---

## Quick Start

### Open MAVIS
1. Download `index.html`
2. Open in any modern browser (Chrome, Firefox, Safari, Edge)
3. Start designing

### Create a Page
1. Enter **Project Name** in sidebar
2. Click **+ Create Page**
3. Set **Page Name**, **Orientation**, **Grid Size**, **Zone**
4. **Save Project**

### Add Elements
1. Select element type from **Elements** section (Button, Text, Field, etc.)
2. Set label, size (width/height in grid cells)
3. Click **+ Add Element**
4. Drag onto canvas to position

### Stack Elements (Z-Ordering)
1. Click element on canvas to select
2. In **Properties** panel, see **Layer (Z-Index)**
3. Click **↓ To Back** or **↑ To Front** to reorder
4. Bottom layers render first (images below, buttons on top)

### Use Image Placeholders
1. Go to **Image Library** section
2. Enter image name, click **+ Create**
3. Auto-generated ordinal: `Hero 1`, `Hero 2`, etc.
4. On any element, select the image in **Image Placeholder** dropdown
5. Multiple elements can reference the same image

### Export Your Work
- **🖼️ Page PNG**: Export current page as PNG
- **📐 All Pages**: Export all pages as grid on one PNG
- **⬇️ CSV**: Export audit trail + current state
- **💾 Save**: Auto-saves to browser (localStorage)

---

## File Structure

```
index.html              # Self-contained application; no network dependency at runtime
README.md               # This file
LICENSE                 # MIT License
.gitignore              # Git ignore rules
```

---

## Architecture

### Data Model

**Elements** (placed on canvas):
```javascript
{
  id: 1,                      // Internal ID
  instanceId: "Button1-1",    // Global unique instance tag
  type: "button",             // Element type
  label: "Button 1",          // Display name
  x: 2, y: 4,                 // Grid position
  width: 3, height: 1,        // Grid size
  zIndex: 3,                  // Layer order
  imageId: null,              // Reference to image library
  createdAt: "ISO-8601",      // Timestamp
  status: "active"            // "active" or "DELETED"
}
```

**Instance Registry** (immutable audit trail):
```javascript
{
  instanceId: "Button1-1",
  type: "button",
  baseName: "Button 1",
  createdAt: "2024-09-01T10:15:30Z",
  status: "active",           // "active" or "DELETED"
  deletedAt: null             // ISO-8601 or null
}
```

**Pages** (contains elements):
```javascript
{
  num: 1,
  name: "Landing",
  zone: "YELLOW",
  orientation: "portrait",    // "portrait" or "landscape"
  gridWidth: 6,
  gridHeight: 12,
  bgColor: "#ffffff",
  elements: [ /* array of elements */ ]
}
```

**Project** (saved to localStorage):
```javascript
{
  name: "My Project",
  pages: [ /* array of pages */ ],
  currentPageIndex: 0,
  instanceRegistry: [ /* audit trail */ ],
  nextInstanceId: 15,         // Next global ID to assign
  imageLibrary: [ /* array of images */ ],
  nextImageId: 3
}
```

### Global State
- `elements` — Current page's elements
- `pages` — All pages in project
- `instanceRegistry` — Master audit trail (never cleared)
- `imageLibrary` — Reusable image placeholders
- `nextInstanceId` — Global counter (increments forever, never resets)

---

## CSV Export Format

### Table 1: Master Instance Registry
Audit trail of every instance ever created:
```
Instance ID, Type, Base Name, Created At, Status, Deleted At
Hero1-1, Image, Hero 1, 2024-09-01T10:15:30Z, active, —
Button2-2, Button, Button 2, 2024-09-01T10:20:10Z, DELETED, 2024-09-01T14:32:15Z
```

### Table 2: Page Layouts
Current state of each page:
```
Page #, Page Name, Instance ID, Type, Label, Position (X;Y), Size (W×H), Z-Index
1, Landing, Hero1-1, Image, Hero 1, (0;0), 6×4, 2
1, Landing, Button2-1, Button, Button 2, (2;8), 3×1, 3
```

Use this for:
- **Developer handoff** — Every element ID is traceable and immutable
- **Version control** — Deleted items remain in audit trail with timestamps
- **Spec documentation** — Position, size, layer order all exported
- **Verification** — Easy to spot what changed between exports

---

## Element Types

| Type | Icon | Use |
|------|------|-----|
| **Button** | 🔘 | CTA, navigation, interaction |
| **Field** | 📝 | Input, form, text entry |
| **Toggle** | ⚪ | Switch, checkbox, option |
| **Icon** | ✨ | Icon, logo, accent |
| **Text** | 📄 | Copy, labels, notes |
| **Image** | 🖼️ | Image placeholder or local image |

---

## Keyboard & Touch Controls

- **Ctrl/Cmd + mouse wheel** — Zoom canvas
- **Two-finger pinch** — Zoom canvas on touch devices

MAVIS STANDARD does not depend on keyboard shortcuts for core operation.

---

## Browser Support

- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+

**Requirements:**
- Modern JavaScript (ES6+)
- Canvas API
- localStorage support

---

## Workflow Examples

### Example 1: Landing Page Flow
1. Create page "Hero"
2. Add image (Hero 1) at top, full width
3. Add button (CTA) below
4. Create page "Features"
5. Add 3 feature cards (reuse images if needed)
6. Export all pages as PNG grid
7. Share with team

### Example 2: Mobile Wireframe
1. Create page, set orientation to "portrait"
2. Add header area, navigation bar
3. Add content sections
4. Add footer
5. Export page PNG
6. Iterate, delete old versions (tracked in CSV)
7. Download final CSV with audit trail

### Example 3: Design Handoff
1. Build 5-page flow in MAVIS
2. Export all pages PNG for quick visual review
3. Export CSV for dev reference
4. Every element has traceable instance ID
5. Dev can match layout to spec by ID

---

## Limitations & Known Issues

- **No undo/redo** — Plan accordingly. Save frequently.
- **No multi-select** — Select and move one element at a time
- **No alignment tools** — Manual grid-based alignment
- **localStorage only** — Data persists per browser, not synced across devices
- **Local-first storage** — Project persistence is browser-local; CSV, JSON, HTML, and PNG exports are available for handoff

---

## Product Ladder

- **V1 STARTER** — Define the pages.
- **V2 STANDARD** — Visualize and design the system and page structure.
- **V3 ADVANCED** — Create actual visual page mockups without coding.

Future online capabilities may add convenience such as backup, sharing, or collaboration, but MAVIS follows one permanent rule: **online-enhanced, offline-complete**. Loss of connectivity must not disable core product functionality.

---

## Contributing

Found a bug? Have a feature idea? 

1. **Report issues** on GitHub Issues
2. **Submit PRs** with improvements
3. **Discuss** in Discussions tab

Code is single-file HTML for simplicity. Keep it that way.

---

## License

MIT License — Use freely, modify, distribute, commercial or personal.

See `LICENSE` file for details.

---

## FAQ

**Q: Is my data stored in the cloud?**  
A: No. Everything stays in your browser's localStorage. You control your data.

**Q: Can I use this offline?**  
A: Yes. Core functionality—including page design, local save/reopen, and PNG/CSV/JSON/HTML export—works without connectivity. Online capabilities may be added later as optional enhancements.

**Q: Can I import from Figma/Adobe XD?**  
A: Not yet. MAVIS is lightweight by design. Export from those tools as images, use image placeholders.

**Q: How do I backup my project?**  
A: Export CSV for the audit trail and JSON/HTML/PNG for portable handoff. Browser localStorage remains the working project store in STANDARD.

**Q: Can multiple people edit at once?**  
A: Not in STANDARD. Collaboration may be offered later as an optional online enhancement; offline core operation remains mandatory.

**Q: Why no undo/redo?**  
A: Keeps the tool lightweight. Save frequently. CSV audit trail helps you track changes.

**Q: Can I host this on my own server?**  
A: Yes. It's a single HTML file. Serve as-is.

---

## Support

- **Bugs/Issues**: GitHub Issues
- **Discussions**: GitHub Discussions
- **Documentation**: This README

---

## Credits

Built for speed. Designed for designers. Made simple.

**Version:** 2.0 STANDARD  
**Last Updated:** September 1, 2026  
**License:** MIT

---

**[Start Designing →](index.html)**

## Mobile-first offline hardening

MAVIS STANDARD is online-enhanced and offline-complete. The application shell is installable as a PWA and is cached locally by a service worker after first successful load. Core blueprint creation, editing, local persistence, and export features do not require a server connection.

Mobile behavior includes pointer-captured drag interactions, deferred local persistence on drag completion, canvas-owned touch gestures, 44 px minimum interaction targets, and collapsible mobile setup/properties sheets.
