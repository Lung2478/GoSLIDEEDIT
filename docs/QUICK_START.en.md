# GoSLIDEEDIT Quick Start Manual (English)

**GoSLIDEEDIT** is a portable, single-executable, 100% offline presentation editor for Windows. It is purpose-built to eliminate the font reflow, broken charts, and missing animation issues that occur when exchanging `.pptx` files between **Microsoft PowerPoint** and **Google Slides**.

> **Built-In Interactive Practice Deck**: When you launch `GoSLIDEEDIT.exe`, it opens **`QuickStart_GoSLIDEEDIT.pptx` (an 11-slide interactive guide)** by default. Try clicking charts, dragging flowchart nodes, and testing controls directly on the canvas as you read this manual.

---

## Table of Contents

1. [Why GoSLIDEEDIT (Core Selling Points)](#1-why-goslideedit-core-selling-points)
2. [30-Second Launch & Workspace Map](#2-30-second-launch--workspace-map)
3. [5-Minute Quick Start: Build Your First Deck](#3-5-minute-quick-start-build-your-first-deck)
4. [Six Signature Features in Detail](#4-six-signature-features-in-detail)
5. [Cross-Platform Compatibility Diagnostics & Remake Assistant](#5-cross-platform-compatibility-diagnostics--remake-assistant)
6. [Keyboard Shortcuts & FAQ](#6-keyboard-shortcuts--faq)

---

## 1. Why GoSLIDEEDIT (Core Selling Points)

Presentations created in desktop PowerPoint often shift lines, distort chart labels, or lose single-vendor transitions when uploaded to Google Slides (and vice versa). **GoSLIDEEDIT** solves these problems by enforcing the strict intersection of both platforms:

| Common Pain Point | GoSLIDEEDIT Solution | Real-World Benefit |
| :--- | :--- | :--- |
| **Fonts reflow or overflow on another PC or cloud** | Enforces a **15 Safe Fonts Whitelist** + **Separate CJK & Latin Font Setup** with dual-track font binding | Mixed English/CJK text keeps exact line breaks across PowerPoint and Google Slides |
| **Charts break or become uneditable across platforms** | Compiles business charts (Bar, Line, Pie, Donut) into **standard grouped vector shapes** | Zero-pixel drift on both platforms while remaining directly editable |
| **External SmartArt or Excel charts break on import** | Captures an in-place **2x clean PNG visual snapshot** and offers a **Remake Assistant** | Nothing disappears; extract raw text/data into editable elements in one click |
| **Requires cloud login or heavy installation** | **Single portable `GoSLIDEEDIT.exe`**, 100% offline with zero network calls | Copy to any Windows PC and double-click `.pptx` files into one multi-tab window |

---

## 2. 30-Second Launch & Workspace Map

### Launching & Opening Files
* **Direct Launch**: Double-click `GoSLIDEEDIT.exe` with zero installation. It opens the 11-slide interactive `QuickStart_GoSLIDEEDIT.pptx` guide by default.
* **Single-Window Multi-Tab Opening**: Double-click `.pptx` files or open multiple decks from the File menu; they open cleanly as tabs inside the same window.

### Five-Zone Workspace Map

```text
+---------------------------------------------------------------------------------------+
| [1] Top Navbar & Formatting Toolbar                                                   |
| [SL] GoSLIDEEDIT | Sidebar | File | Undo/Redo | Layout | Theme | Insert | Fonts | Find | Auto Save | Present (F5) |
+------------------+------------------------------------------------+-------------------+
| Slides | Outline |  [Deck1.pptx]  [Deck2.pptx *]  [+]             | Inspector Header  |
+------------------+------------------------------------------------+-------------------+
| [2] Left Sidebar | [3] Center Interactive Canvas (16:9/16:10/4:3) | [4] Right Panel   |
|  - Slides Film   |                                                |  - No selection:  |
|    (Drag reorder)|    +--------------------------------------+    |    Ratio/BG/Trans |
|  - Outline View  |    |   Click, marquee-select, drag, and   |    |  - Single select: |
|    (Quick edit)  |    |   double-click to edit text here     |    |    Size/Style/Anim|
|                  |    +--------------------------------------+    |    Dual Font/Chart|
|                  |------------------------------------------------|  - Multi (>=2):   |
|                  |  Speaker Notes (Click bottom drawer to expand) |    6-Align/2-Distrib|
+------------------+------------------------------------------------+-------------------+
| [5] Status Bar: [Normal | Slide Sorter | Slideshow] [Compat Diagnostics] [Slide X/N] [25%-200% Fit] |
+---------------------------------------------------------------------------------------+
```

1. **Top Navbar & Formatting Toolbar**: Houses the File menu (New, Open, Save, Print, Export), Layout, Theme, element & chart insertion tools, Font selector & quick text controls (`A-` / `A+` / `B` / `I` / Text Color), Find & Replace (`Ctrl+F`), Auto Save capsule toggle, Light/Dark mode, `EN / 中` language toggle, and the primary **Present (`F5`)** button.
2. **Left Sidebar (`Ctrl+Shift+L`)**: Aligned flush with the document Tab Bar, switching between **Slides** (thumbnail strip) and **Outline** (fast text editing).
3. **Center Canvas & Speaker Notes**: Surrounded by neutral warm slate gray so slide colors are never visually distorted; toggle the bottom drawer anytime for speaker notes.
4. **Right Inspector Panel (`Ctrl+Shift+I`)**: Dynamically adapts to show Slide Setup & Transitions (no selection), Element Properties / Chart Data / Animations (single selection), or Multi-Selection Batch Alignment & Styling (2+ elements selected).
5. **Bottom Status Bar**: Switch between `Normal`, `Slide Sorter`, and `Slideshow` views on the left; inspect **Compatibility Diagnostics**, current slide count, and the **`25% - 200%` + `Fit` zoom controls** on the right.

---

## 3. 5-Minute Quick Start: Build Your First Deck

### Step 1: Create & Choose a Layout
1. Click **File -> New Blank Presentation** (or press `Ctrl+N`).
2. Click **Layout** on the top toolbar and pick from 7 standard layouts (`Title Slide`, `Title & Content`, `Section Header`, `Two Content`, `Title Only`, `Caption`, `Blank`). **Applying a layout preserves your existing text** on that slide.
3. Press **New Slide** or `Ctrl+M` to add another slide.

### Step 2: Insert & Edit Elements
* **Text Box**: Click **Text Box** on the toolbar, then **double-click** any text box, shape, or table cell to type. Press `Esc` to exit text editing.
* **Images**: Insert `.png`, `.jpg`, `.gif`, `.webp`, or `.svg`, or paste screenshots directly with `Ctrl+V`. (`.webp` and `.svg` images are automatically rasterized to high-resolution `.png` when saved to `.pptx` so both PowerPoint and Google Slides display them reliably.)
* **Shapes, Freeform Polygons, Connectors, Tables & Charts**: Insert directly from the top toolbar (selecting **Freeform Polygon** enters interactive crosshair drawing mode supporting both click-to-place vertices and hold-and-drag freehand drawing).

### Step 3: Navigate & Reorder Slides Smoothly
* **Fast Paging**: Scroll the **mouse wheel** over the main canvas or thumbnails, or press `Page Up` / `Page Down` (or Up/Down arrow keys when no element is selected) to flip slides.
* **Ghost-Free Drag Reordering**: In **Slides**, **Outline** (drag by the slide header bar), or **Slide Sorter** grid view, press and drag any slide card until the bright orange drop line appears, then release. The editor automatically focuses the moved slide and renumbers master page numbers (`Ctrl+Z` undoes in one step).

### Step 4: Two-Tier Right-Click Context Menu
Right-click any canvas element, blank canvas area, slide thumbnail, or document tab:
* Right-clicking a canvas element opens a **floating Mini Formatting Toolbar** on top (live CJK/Latin font, size, B/I/U, alignment, text color, and fill color without closing the menu) and a clean action menu below (Cut/Copy/Paste, Duplicate, Z-Order, Center on Slide).

### Step 5: Present, Save & Export
1. **Present**: Press `F5` (from slide 1) or `Shift+F5` (from current slide). Advance animations and slides with Left-Click, Space, Arrow keys, or Mouse Wheel; press `Esc` to exit.
2. **Save `.pptx`**: Press `Ctrl+S` to save as a standard cross-platform `.pptx` file, or toggle **Auto Save** on the top right.
3. **One-Way Exports**: Open **File -> Export One-Way Formats** to export multi-page `.pdf`, current-slide `.png` / `.jpg` / `.svg`, or plain-text `.txt` outline.

---

## 4. Six Signature Features in Detail

### Feature 1: 15 Safe Fonts & Separate CJK / Latin Font Setup
Need mixed-language slides where CJK characters use `Microsoft JhengHei` (or `DFKai-SB`) while English letters and numbers automatically use `Calibri` (or `Georgia`)?
* **15 Cross-Platform Safe Fonts**:
  * **Traditional Chinese (3)**: `Microsoft JhengHei`, `PMingLiU`, `DFKai-SB`.
  * **Western/Latin (12)**: Sans-serif `Calibri`, `Arial`, `Arial Black`, `Verdana`, `Tahoma`, `Trebuchet MS`, `Impact`; Serif `Georgia`, `Times New Roman`, `Cambria`, `Garamond`; Monospace `Courier New`.
* **Integrated Everywhere**: Independently set **CJK Font** and **Latin Font** (or pick from 4 Business Font Pair Presets) across the top **Fonts** menu (with "Apply Both / CJK Font / Latin Font" mode toggle), Right Inspector, Right-Click Mini Toolbar, and Slide Master Modal.
* **Local System Fonts Flexibility**: You can also preview and export PDF/images using any font installed on your Windows PC; when saving to `.pptx`, non-whitelisted fonts are automatically mapped to the nearest safe font so cross-platform formatting never breaks.

### Feature 2: Zero-Drift Business Charts, Freeform Polygons & 8-Anchor Magnetic Connectors
* **Grouped Vector Business Charts**: Create **Bar, Line, Pie, and Donut** charts. Charts compile down to standard grouped vector shapes and text boxes with embedded structured JSON, delivering **0-pixel drift** in PowerPoint and Google Slides while remaining fully editable in GoSLIDEEDIT's right Inspector.
* **Cross-Platform Freeform Polygon**: Launch from the top **Shape** menu, **Line / Arrow** menu, or right-clicking blank canvas. Supports both **click-by-click straight segments** and **hold-and-drag freehand strokes** (automatically smoothed into crisp vertices); click the start circle, double-click, or press `Enter` to auto-close into a filled polygon (`Backspace` undoes the last vertex, `Esc` cancels). Afterward, switch between **Closed Polygon / Open Polyline** or toggle **Edit Points** in the Inspector or right-click menu to drag vertices, click edge midpoints to insert vertices, or `Alt + Click` to delete vertices—100% natively editable in both PowerPoint (Freeform) and Google Slides (Polyline).
* **6 Straight & Curved Magnetic Connectors**: Insert straight or cubic-Bezier curved lines/arrows. Drag either endpoint handle within `18px` of any shape to snap onto its **8 anchor points** (`N, S, E, W, NW, NE, SW, SE`). Moving or resizing connected shapes automatically updates all attached connectors.

### Feature 3: Slide Master, External `.pptx` Master Import & 6 Theme Presets
* **6 Business Theme Palettes**: Open **Theme** on the top toolbar to switch between `Vibrant Tangerine`, `Executive Navy`, `Forest Emerald`, `Slate Minimal`, `Burgundy Gold`, and `Obsidian Dark` across **All Slides** or **Current Slide Only**.
* **Slide Master Setup**: Configure global title/body CJK & Latin fonts, sizes, colors, accent bars (top/bottom/left), corner brand logos, footers, and automatic page numbers (`1..N`).
* **Import Master from `.pptx`**: Import colors, fonts, accent bars, and corner logo directly from an existing company `.pptx` template in one click.

### Feature 4: Marquee Multi-Selection, Group Drag & 6-Align / 2-Distribute
* **Two Ways to Multi-Select**:
  1. **Left-Drag Marquee Box**: Press and drag from any blank canvas area or the outer gray surround—any non-master element touched by the selection box is selected (`Ctrl + drag` adds to selection).
  2. **`Ctrl + Left-Click`**: Toggle individual elements in/out of selection (`Ctrl+A` selects all non-master elements on the slide).
* **Group Drag & Precision Nudge**: Drag any selected element to move the whole group together with smart center guides and attached connector updates; use `Arrow keys` (`1px`) or `Shift + Arrow keys` (`10px`) for fine positioning.
* **Multi-Selection Inspector Panel**: When 2+ elements are selected, the right panel switches to batch controls: **6-way align** (Left, Center-H, Right, Top, Middle-V, Bottom), **2-way slide centering**, **horizontal/vertical equal distribution** (for 3+ elements), and batch fill/border/font/layer editing.

### Feature 5: Whole-Deck Find & Replace (`Ctrl+F` / `Ctrl+H`)
* Scans across **all slides** covering Text Boxes, Shapes, Table cells, Business Chart labels (title, categories, series), and Speaker Notes.
* Safely handles literal symbols like `$100` or `(Q1+Q2)`, preserves mixed inline text run formatting (`bold`, `italic`, `color`), protects Slide Master footers/page numbers, and supports single-step `Ctrl+Z` undo even after **Replace All**.

### Feature 6: Print & Export Watermark Modal (`Ctrl+P`)
Press `Ctrl+P` (or **File -> Print Presentation**) to open the two-column **Print & Watermark Setup** dialog with a live `1:1` slide preview:
* **Text or Image Watermarks**: Choose from 5 quick text presets (e.g., `CONFIDENTIAL`, `INTERNAL USE ONLY`, `DRAFT`) or upload an image / reuse your Slide Master Logo (with scale & grayscale options).
* **6 Layouts & Dual Layering**: Place at Center, Tiled 3x3 Staggered Grid, or any of the 4 Corners, with opacity (`5% - 80%`), rotation angle, and **Overlay (Above Content) / Underlay (Behind Content)** control.
* **Smart Print & Export Options**: Toggle **Skip First Slide (Cover)**, specify custom slide ranges (e.g., `1-3, 5`), optionally apply the same watermark to exported `PDF / PNG / JPG / SVG` files, and print in **Landscape (1 slide/page full-bleed)** or **Portrait (2 slides/page handout with subtle borders)**.
* **Zero `.pptx` Pollution**: Watermark settings remain strictly in session memory and never modify your `.pptx` file.

---

## 5. Cross-Platform Compatibility Diagnostics & Remake Assistant

Whenever you open an external `.pptx` file, GoSLIDEEDIT runs automatic cross-platform protection:

1. **Status Bar Compatibility Badge**:
   * `[PASS] PowerPoint & Google Slides 100% Compatible` confirms full two-platform safety.
   * If notices appear (mapped non-whitelist fonts, downgraded single-vendor transitions/animations, local non-whitelist fonts, or out-of-bounds elements), click the badge to inspect details, jump to the slide, or click **1-Click Auto-Fix**.
2. **Overwrite Protection**: When opening an external `.pptx` triggers automatic compatibility normalization, the tab is marked dirty and **Auto Save is paused** until you review and press `Ctrl+S`.
3. **Incompatible Snapshot & Remake Assistant**: External SmartArt, native Excel charts, or complex groups are captured in-place as clean **2x `.png` visual snapshots** with a dashed badge. Select the snapshot to open the **Remake Assistant** in the right Inspector—copy extracted text/data or spawn an editable Text Box, Table, or Business Chart beside it in one click.

---

## 6. Keyboard Shortcuts & FAQ

### Essential Keyboard Shortcuts

| Shortcut | Action |
| :--- | :--- |
| `Ctrl + N` / `Ctrl + O` | New Blank Presentation / Open `.pptx` File(s) |
| `Ctrl + S` / `Ctrl + Shift + S` | Save Presentation / Save As `.pptx` |
| `Ctrl + P` | Open Print & Watermark Setup (Print or Export PDF) |
| `Ctrl + W` / `Ctrl + Tab` | Close Current Tab / Switch to Next Tab |
| `Ctrl + M` / `Ctrl + D` | New Slide / Duplicate Slide or Selected Elements |
| `Ctrl + F` / `Ctrl + H` | Open Find / Find & Replace Bar |
| `Ctrl + A` | Select All Non-Master Elements on Current Slide |
| `Left-Drag Marquee` / `Ctrl + Click` | Drag-box multi-select on canvas or surround / Toggle element selection |
| `Ctrl + C` / `X` / `V` | Copy / Cut / Paste Selected Elements (or Clipboard Image) |
| `Arrow Keys` / `Shift + Arrow` | Nudge selected elements `1px` / `10px` (Up/Down switches slides when nothing is selected) |
| `Page Up` / `Page Down` / `Mouse Wheel` | Switch to Previous / Next Slide |
| `Ctrl + Wheel` / `Ctrl + +` / `-` / `0` | Zoom Canvas (`25% - 200%`) / Fit to Window |
| `Ctrl + Z` / `Ctrl + Y` | Undo / Redo |
| `F5` / `Shift + F5` | Start Slideshow from Beginning / From Current Slide |
| `Ctrl + 1` / `Ctrl + 2` | Switch between `Normal` and `Slide Sorter` View |
| `Ctrl + Shift + L` / `I` | Toggle Left Sidebar / Right Inspector Panel |
| `Enter` / `Backspace` / `Alt + Click` | Finish & close Freeform Polygon / Undo last vertex / Delete vertex in Edit Points mode |
| `Esc` | Step back / Close active dropdown, modal, text edit, selection, or slideshow |

### Frequently Asked Questions (FAQ)

* **Q1: Why are PowerPoint Morph, motion paths, or web fonts like Roboto/Aptos unavailable in menus?**
  * A: Those features belong exclusively to one vendor and break or reflow on the other platform. GoSLIDEEDIT intentionally locks its creation menus to the 15 safe fonts, 4 transitions, and 8 animations that work identically across both Microsoft PowerPoint and Google Slides.
* **Q2: What happens if I use a Windows local system font and then save as `.pptx`?**
  * A: Your local font renders accurately in the editor, F5 slideshow, and `.pdf`/`.png`/`.jpg`/`.svg` exports. When saving to `.pptx`, GoSLIDEEDIT automatically normalizes it to the closest safe font in the 15-font whitelist so colleagues and Google Slides never suffer broken layouts.
* **Q3: Are `.webp` and `.svg` images safe to insert?**
  * A: Yes. When packaging into `.pptx`, GoSLIDEEDIT automatically converts `.webp` and `.svg` images offline into high-resolution `.png` files so every PowerPoint and Google Slides version displays them cleanly.
* **Q4: How do I quickly exit any open menu, dialog, or playback mode?**
  * A: Press **`Esc`** anywhere in the app—it hierarchically exits text editing, closes open menus or modals, clears multi-selection, or returns from Slide Sorter / Slideshow to Normal editing.
