# Tactile Pixel Studio

Tactile Pixel Studio is a browser-based pixel-art editor built as a self-contained HTML application. It provides a layered sprite-editing workspace, frame-based animation tools, color and palette controls, import/export workflows, and a customizable interface inspired by desktop pixel-art editors.

## Features

### Pixel-art editing
- Pixel-precise canvas rendering with nearest-neighbour scaling.
- Canvas zooming, panning, centering, and a floating preview window with its own zoom/pan controls.
- Optional pixel grid, transparency checkerboard, selection overlays, guides, and cursor aids.
- Selection tools include rectangular marquee, elliptical marquee, and lasso.
- Selection operations include select all, deselect, invert, crop to selection, horizontal flip, and vertical flip.
- Undo and redo controls.
- Color replacement, including indexed-palette-aware color selection.

### Layers
- Multiple layers per frame.
- Rename, reorder, show/hide, and lock layers.
- Layer opacity controls.
- A timeline matrix for managing layer/frame cels and identifying populated cels.
- Multi-selection support for frames and layers in relevant operations.

### Animation
- Frame-based sprite animation with controls to add, duplicate, delete, and navigate frames.
- Playback controls, including play/pause, stop, loop, and onion skin.
- Adjustable animation timing/FPS and onion-skin opacity.
- A floating motion preview for inspecting the sprite while editing.

### Color and palettes
- Foreground and background color slots, with a swap control.
- Color wheel, native color picker, RGB/alpha controls, and hexadecimal color entry.
- Palette selection and palette swatches.
- RGB, indexed, and indexed-with-dithering color modes.
- Palette import and palette-related controls.

### Workspace and customization
- Desktop-editor-style layout with menu bar, document tabs, context bar, palette/color panel, canvas, vertical tool strip, timeline, and status bar.
- Multiple open projects represented by tabs.
- Resizable workspace panels and timeline.
- Themes include **Obsidian/Dark**, **Libre**, **Synthwave**, and **Bryce**.
- Customizable keyboard shortcuts and a searchable shortcut editor.
- Preferences for interface and editing behavior.
- Favorite folders for quick access to frequently used directories, where supported by the browser.

### Import and export

**Import paths visible in the source include:**
- Opening files through a file picker.
- Drag-and-drop.
- Pasting an image from the operating-system clipboard.
- Importing images and project data.
- OpenRaster (`.ora`) project import.
- Aseprite/LibreSprite binary sprite parsing (`.ase` / `.aseprite`) is implemented in the source.

**Export options include:**
- PNG, GIF, and WebP output.
- Export each frame as a separate image, combine frames into a sprite sheet, or export an animation (GIF/WebP).
- Choose all frames or selected frames, and choose visible, selected, or a specific layer.
- Scale pixel art up to 400% using nearest-neighbour resizing.
- Configure WebP quality and generated filenames.
- Save layered projects as OpenRaster (`.ora`).
- Aseprite-format (`.ase`) export code is also present.

Exact format compatibility and edge cases should be verified with representative files before relying on the editor in a production workflow.

## Getting started

1. Save `Tactile v6.7.html` to your computer.
2. Open the HTML file in a modern browser. A recent Chromium-based browser or Firefox is recommended; some compressed-file import paths rely on browser `DecompressionStream` support.
3. Use the entry dialog to create a new sprite, open/import a file, access preferences, or view the help guide.
4. Create a sprite and choose its canvas dimensions. The code clamps new project dimensions to a minimum of 4 and maximum of 256 pixels per side.
5. Draw on the canvas using the toolbar. Use the color panel to choose colors and the timeline to work with layers and frames.
6. Save the layered project as `.ora`, or use **Export** to create image files, a sprite sheet, or an animation.

The bootstrap code attempts to load autosaved projects first. If none are available, it creates a default `Sprite_1` project at 32 × 32 pixels.

## Main interface

| Area | Purpose |
|---|---|
| Menu bar | File, Select, Edit, Sprite, Layer, Frame, View, and Help commands |
| Document tabs | Switch between open projects; close tabs and create new projects |
| Context bar | Shows controls relevant to the current tool or editing context |
| Left panel | Palette, foreground/background colors, and color mixer |
| Center canvas | Main pixel-art editing area with zoom/pan and overlays |
| Right toolbar | Drawing, selection, and other editing tools |
| Bottom timeline | Frame headers and layer/cel matrix; animation controls |
| Floating preview | Separate view of the current sprite, with drag and zoom controls |
| Status bar | Canvas dimensions, current tool/color, frame, and zoom information |

## Keyboard and interaction notes

- **Space** is reserved for panning while held.
- **Alt** temporarily activates the eyedropper.
- **Enter** finishes polygon operations.
- **Esc** cancels an operation or closes the active dialog/menu where applicable.
- Other shortcuts can be viewed and customized through **Help → Field Guide & Shortcuts** or **Edit → Keyboard Shortcuts**, depending on the menu entry.

The shortcut editor supports recording combinations, adding or removing bindings, and searching commands. Consult the in-app guide for the current full shortcut list.

## Persistence and browser considerations

- The application includes an autosave engine for projects and a settings persistence path.
- Favorite-folder access and remembered file destinations depend on browser support and permission grants.
- Browser storage is not a substitute for an exported backup. Export important work regularly.
- Importing compressed `.ase`/`.aseprite` data and compressed OpenRaster entries requires compatible decompression support in the browser.
- This is a single HTML file; the supplied source does not identify a build system, package manager, or separate installation process.

## Known documentation caveats

This README describes features indicated by the supplied HTML source; it is not a full QA report. Before release, test:
- Opening and saving projects across supported browsers.
- Round-tripping layered `.ora` files and `.ase`/`.aseprite` files.
- Animation export timing, transparency, palette behavior, and frame ordering.
- Autosave recovery and unsaved-change prompts.
- Keyboard shortcut conflicts and behavior on different operating systems.
- Favorite-folder permissions and file-picker fallbacks.

## Technology

The supplied file contains the application markup, CSS, and JavaScript in one HTML document. It uses browser-native canvas and file APIs, CSS custom properties for themes, and browser capabilities such as `DecompressionStream` for supported compressed imports. No external package/build configuration is included in the provided HTML file.

## Project file

- `Tactile v6.7.html` — self-contained application.
