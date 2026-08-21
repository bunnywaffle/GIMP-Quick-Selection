# GIMP Quick Selection Tool Suite

An interactive, edge-aware **Quick Selection Brush Suite** for **GIMP 3** inspired by Adobe Photoshop and Affinity Photo's Quick Selection Tools.

Featuring **4 switchable segmentation algorithm engines** to deliver pixel-perfect accuracy across any image type, from fine hair and anime line-art to complex textured photos and solid silhouettes.

---

![GIMP Quick Selection Brush Screenshot](assets/screenshot.png)

---

## ⚙️ 4 Selectable Algorithm Engines

| Engine | Best For | How it Works |
| :--- | :--- | :--- |
| **🎯 Adaptive Wavefront** *(Photoshop Style)* | **Fine details, hair strands, line art, anime, crisp contours** | Direct pixel-level wavefront propagation with CIELAB $\Delta E$ and Sobel barrier gating. Evaluates exact sub-pixel boundaries without clustering artifacts. |
| **⚡ Lazy Snapping** *(Graph Cut + Superpixels)* | **Complex photos, textured surfaces, general objects** | SIGGRAPH Lazy Snapping energy minimization (Dinic Min-Cut) over SLIC super-regions with boundary prior smoothness. |
| **🌊 Geodesic Ridge** *(Gradient Distance)* | **Solid objects, strong silhouettes, high-contrast edges** | Geodesic gradient accumulation halting strictly at contrast boundary ridges without bleeding. |
| **🖌️ Adaptive Variance** *(Affinity Photo Style)* | **Smooth gradient shading, controlled touchups** | Local statistical Gaussian color distribution ($\mu \pm k\sigma$) sampled directly under the cursor footprint. |

> **Tip:** You can switch between algorithms on the fly during the same session! For instance, paint the main subject body using **Lazy Snapping** or **Geodesic Ridge**, then switch to **Adaptive Wavefront** to capture fine hair strands and tricky corners.

---

## ✨ Features

- **Multi-Algorithm Engine Selector**: Switch between 4 distinct segmentation engines instantly from the UI.
- **Photoshop / Affinity Photo Selection Workflow**:
  - **Add Mode (+)**: Paint over subjects to continuously accumulate selection.
  - **Subtract Mode (-)**: Paint over unwanted areas to carve away background spills.
  - **New / Replace Mode**: Reset and start a fresh selection.
- **🔍 Interactive Zoom & Pan Navigation**:
  - **Mouse Scroll Wheel**: Smooth zoom in/out (from 10% to 1000% magnification) anchored to the mouse cursor for pixel-precise selections.
  - **Middle-Click Drag / Right-Click Drag / Spacebar + Left-Click Drag**: Smooth pan across the canvas.
  - Toolbar quick zoom buttons: `[-]`, `[+]`, `[Fit]`, and `[100%]`.
- **Live Brush Ring Cursor**: Adaptive cursor ring dynamically tracks the exact brush radius and current zoom level.
- **Customizable Preview Overlays**:
  - 1-Click preset swatches: 🔵 **Cyan**, 🔴 **Red (Ruby Quick Mask)**, 🟢 **Green**, 🟡 **Amber / Yellow**, 🟣 **Magenta**.
  - Full **RGBA Color Picker** for any custom overlay color.
  - **Overlay Opacity Slider** (10% to 90%).
- **Snapping Tuning & Presets**:
  - **Snapping Reach**: Adjust how far the selection explores beyond the brush stroke (`Precise`, `Balanced`, `Broad`).
  - **Color Tolerance ($\Delta E$)**: Tune color boundary strictness.
  - **Edge Barrier Strictness**: Tune contrast barrier sensitivity.
- **High Performance & Instant Application**:
  - Real-time painting at **60+ FPS**.
  - **Instant selection application (<0.15s)** to native GIMP 3 buffers on full-resolution 4K and 8K images.
- **↩ Undo & Clear**: Multi-level undo stack for non-destructive editing.

---

## 📦 Installation

### Windows
1. Download or clone this repository.
2. Copy the `gradient-gated-select` folder into your GIMP 3 plug-ins directory:
   ```text
   %APPDATA%\GIMP\3.0\plug-ins\gradient-gated-select\
   ```
   *(or `%APPDATA%\GIMP\3.2\plug-ins\gradient-gated-select\` if using GIMP 3.2+)*
3. Restart GIMP.

### Linux
1. Copy the `gradient-gated-select` folder into:
   ```bash
   ~/.config/GIMP/3.0/plug-ins/gradient-gated-select/
   ```
2. Ensure the plugin file is executable:
   ```bash
   chmod +x ~/.config/GIMP/3.0/plug-ins/gradient-gated-select/gradient-gated-select.py
   ```
3. Restart GIMP.

### macOS
1. Copy the `gradient-gated-select` folder into:
   ```text
   ~/Library/Application Support/GIMP/3.0/plug-ins/gradient-gated-select/
   ```
2. Make it executable:
   ```bash
   chmod +x ~/Library/Application\ Support/GIMP/3.0/plug-ins/gradient-gated-select/gradient-gated-select.py
   ```
3. Restart GIMP.

---

## 🚀 How to Use

1. Open any image with an active layer in GIMP 3.
2. In the top menu, go to:
   **`Select` $\to$ `Quick Selection Brush (Edge-Aware)...`**
3. Select your preferred **Algorithm Engine** from the dropdown.
4. **Paint** over your subject with Left-Click Drag.
5. **Zoom / Pan**:
   - Use the **Mouse Scroll Wheel** to zoom in on fine details.
   - Hold **Middle-Click** or **Spacebar + Left-Click** to pan around.
6. Switch algorithm or adjust **Brush Size**, **Tolerance**, or **Reach** as needed.
7. Click **`[Apply Selection]`** to commit the selection back to GIMP.

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPLv3)** - see the [LICENSE](LICENSE) file for details.
