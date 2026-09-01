# Quick Start Guide

Get up and running with MAVIS in 5 minutes.

---

## 1. Open MAVIS

Download or clone this repo, then open `index.html` in your browser.

**That's it.** No installation or build step. Core functionality works without an internet connection.

---

## 2. Create a Project

1. Enter a **Project Name** in the sidebar (e.g., "My App v1")
2. Click **💾 Save** to persist to browser storage

---

## 3. Create Your First Page

1. Click **+ Create Page** in the Pages section
2. Set:
   - **Page Name**: "Landing"
   - **Zone**: "YELLOW"
   - **Orientation**: "portrait"
3. Click **+ Create Page** again

---

## 4. Add Elements

1. In the **Elements** section, select an element type from the dropdown (e.g., "button")
2. Enter a **Label** (e.g., "Sign Up")
3. Set **Width** and **Height** in grid cells (e.g., 3×1 for a button)
4. Click **+ Add Element**

The element appears on your canvas. You can drag it to reposition.

Repeat to add more elements (buttons, text, fields, images, etc.)

---

## 5. Stack Elements (Z-Ordering)

1. Click an element on the canvas to select it
2. In the **Properties** panel (right), find **Layer (Z-Index)**
3. Click **↓ To Back** to move it behind other elements
4. Click **↑ To Front** to move it on top

**Typical order:**
- Background (bottom)
- Images
- Buttons, text, other elements (top)

---

## 6. Add Images to Library

1. In the **Image Library** section, enter an image name (e.g., "Hero")
2. Click **+ Create**
3. MAVIS auto-generates: "Hero 1", "Hero 2", etc.

Now any element can reference these images:
1. Select an element
2. In Properties, find **Image Placeholder**
3. Choose "Hero 1" from the dropdown

---

## 7. Export Your Work

### Export as PNG
- **🖼️ Page PNG**: Downloads current page as image
- **📐 All Pages**: Downloads all pages as a grid

### Export Data
- **⬇️ CSV**: Downloads audit trail + page layouts in two tables
- **⬇️ Export JSON**: Downloads the current page state
- **⬇️ Export HTML**: Downloads a simple handoff representation of the current page

---

## 8. Save & Close

1. Click **💾 Save** regularly
2. Close browser—your project persists in localStorage
3. Open again → your project is still there

---

## Tips

**✅ Do:**
- Save frequently
- Export PNG for design review
- Export CSV for developer handoff
- Create one page per screen/flow

**❌ Don't:**
- Forget to save before closing
- Clear browser data (deletes localStorage)
- Try to edit multiple elements at once (not yet supported)

---

## Next Steps

- Read the full [README.md](README.md) for detailed docs
- Explore the [CSV export format](README.md#csv-export-format) for dev handoff
- Check [Element Types](README.md#element-types) for what's available

---

## Stuck?

1. Try refreshing the page
2. Check **Project Name** is set
3. Ensure **💾 Save** was clicked
4. Open browser DevTools (F12) → Application → Storage → localStorage to see saved data

Happy designing! 🎨

---

## Offline Rule

MAVIS STANDARD is **online-enhanced, offline-complete**. Core creation, editing, local persistence, and export functions are designed to remain available in airplane mode.

## Mobile usage

On phones, use the ☰ button for project/setup controls and ⚙️ for element properties. The canvas keeps the majority of the screen. Dragging uses pointer capture and saves position only when the gesture ends. Pinch zoom remains available on the canvas.

For installed/offline use, open MAVIS once while online so the PWA application shell can be cached, then add/install MAVIS from your browser. After that successful cache, core functionality remains available in airplane mode.
