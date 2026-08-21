# 🖌️ GIMP Quick Selection Brush Suite (Edge-Aware)

[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue.svg)](https://www.gnu.org/licenses/gpl-3.0)
[![GIMP Version](https://img.shields.io/badge/GIMP-3.0%20%2F%203.2%2B-orange.svg)](https://www.gimp.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows%20%7C%20Linux%20%7C%20macOS-brightgreen.svg)](#installation)

An interactive, edge-aware **Quick Selection Brush Suite** for **GIMP 3.0+** bringing the intuitive, natural object selection experience of Photoshop and Affinity Photo directly into GIMP.

Featuring **Multi-Modal Graph Cut optimization**, interactive **Zoom & Pan navigation**, customizable preview overlays, and **instant selection application (<0.15s)** with **zero lag**.

---

![GIMP Quick Selection Brush UI](assets/screenshot.png)

---

## ✨ Features

- **4 High-Performance Segmentation Engines**: Switch between Multi-Modal Graph Cut, Adaptive Wavefront Flood, Geodesic Ridges, and Variance Gating.
- **⚡ Zero Lag (60 FPS Interactive Painting)**: Superpixel-accelerated Dinic Max-Flow Min-Cut solves optimal boundaries in <0.002s with zero UI stutter.
- **🎨 Multi-Cluster K-Means Color Modeling**: Automatically captures multiple highlights, shadows, and color textures under your brush stroke.
- **🔍 Viewport Navigation**: Smooth mouse-wheel zooming (10% to 1000%) and middle-click/space-drag panning to inspect fine details.
- **🎨 Custom Selection Overlays**: Choose from vibrant preset swatches (Cyan, Red, Green, Amber, Magenta), pick custom colors, and adjust overlay opacity in real-time.
- **🎛️ Collapsible Advanced Controls**: Fine-tune background cutoff strictness, graph smoothness priors, and contrast sensitivity via an expandable panel.
- **⚡ Instant Apply (<0.15s)**: High-speed precomputed row assembly applies 4K/8K selections into GIMP's selection buffer with zero UI lag or freezing.
- **↩ Full Undo & History**: Easily step backward through previous brush strokes.

---

## ⚙️ The 4 Algorithm Engines

| Engine | Ideal For | How It Works |
| :--- | :--- | :--- |
| **⚡ Lazy Snapping** *(Default)* | Complex photos, multi-colored objects & textures | Multi-Cluster **K-Means Graph Cut** across fine SLIC super-regions. Automatically captures complex textures with 0 lag. |
| **🎯 Adaptive Wavefront** | Hair strands, line art, silhouettes, sharp contours | **Photoshop-style** core-seeded floodfill gated by CIELAB $\Delta E$ color coherence and Sobel gradient barrier walls. |
| **🌊 Geodesic Ridge** | High-contrast objects, solid silhouettes | **Fast Marching** gradient distance transform that traverses smooth surfaces freely and halts at sharp contrast ridges. |
| **🖌️ Adaptive Variance** | Smooth shading, gradients, controlled touchups | **Affinity Photo style** local Gaussian color distribution ($\mu \pm k\sigma$) sampled under the brush footprint. |

---

## 🚀 Installation

### Option 1: Quick Install via Git Clone (Recommended)

Open your terminal or command prompt, navigate to your GIMP 3 plug-ins folder, and clone the repository directly:

#### 🪟 Windows (PowerShell / Command Prompt):
```powershell
cd "$env:APPDATA\GIMP\3.0\plug-ins"
git clone https://github.com/bunnywaffle/GIMP-Quick-Selection.git
```
*(If using GIMP 3.2, replace `3.0` with `3.2`)*

#### 🐧 Linux:
```bash
cd ~/.config/GIMP/3.0/plug-ins/
git clone https://github.com/bunnywaffle/GIMP-Quick-Selection.git
chmod +x GIMP-Quick-Selection/*.py
```

#### 🍏 macOS:
```bash
cd ~/Library/Application\ Support/GIMP/3.0/plug-ins/
git clone https://github.com/bunnywaffle/GIMP-Quick-Selection.git
chmod +x GIMP-Quick-Selection/*.py
```

---

### Option 2: Manual Download

1. Click **Code $\to$ Download ZIP** on GitHub and extract the archive.
2. Move the extracted `GIMP-Quick-Selection` folder into your GIMP 3 `plug-ins/` directory:
   - **Windows**: `C:\Users\<YourUsername>\AppData\Roaming\GIMP\3.0\plug-ins\`
   - **Linux**: `~/.config/GIMP/3.0/plug-ins/`
   - **macOS**: `~/Library/Application Support/GIMP/3.0/plug-ins/`
3. *(Linux/macOS only)* Make the scripts executable:
   ```bash
   chmod +x GIMP-Quick-Selection/*.py
   ```
4. Restart GIMP.

---

## 🎮 How to Use

1. Open an image in GIMP with an active layer.
2. In the top menu, go to:
   **`Select` $\to$ `Quick Selection Brush (Edge-Aware)...`**
3. **Paint over the subject** you want to select:
   - **Add Mode (`+`)**: Drag the brush over your subject. The selection automatically expands to the edges.
   - **Subtract Mode (`-`)**: Paint over any unwanted areas to erase them from the selection.
   - **New / Replace**: Clears the previous mask and starts a fresh selection.
4. **Zoom & Pan**:
   - **Mouse Scroll**: Zoom in / out centered at your cursor.
   - **Middle-Click Drag** or **Space + Left-Click Drag**: Pan across the image.
   - **Fit / 100% Buttons**: Quickly reset viewport view.
5. Click **Apply Selection** to commit the marching ants selection mask to your GIMP image.

---

## ⌨️ Shortcuts & Controls

| Action | Shortcut / Control |
| :--- | :--- |
| **Paint / Select** | `Left Click + Drag` |
| **Zoom In / Out** | `Mouse Wheel Up / Down` |
| **Pan Canvas** | `Middle Click Drag` or `Spacebar + Left Click Drag` |
| **Undo Stroke** | Click `↩ Undo` or press button |
| **Clear Selection** | Click `Clear` |
| **Commit Selection** | Click `Apply Selection` (or press `Enter`) |
| **Cancel Dialog** | Click `Cancel` (or press `Escape`) |

---

## 🔧 Advanced Fine-Tuning

Click the **`🔧 Advanced Parameters & Fine Tuning`** toggle in the right sidebar to access precision adjustments:

- **Hard Background Cutoff ($\Delta E$)**: Sets the strictness threshold at which diverging colors are permanently excluded from the foreground.
- **Graph Cut Smoothness Prior ($\lambda$)**: Controls silhouette edge tension. Higher values ensure cleaner silhouettes and eliminate speckling in textured areas.
- **Boundary Contrast Sensitivity ($\sigma$)**: Controls how sharp a contrast difference must be to form a boundary cut.

---

## 📄 License

This project is licensed under the **GNU General Public License v3.0 (GPL-3.0)** — see the [LICENSE](LICENSE) file for details.

---

## 🤝 Contributing & Feedback

Contributions, feature suggestions, and bug reports are welcome! Feel free to open an issue or submit a Pull Request on [GitHub](https://github.com/bunnywaffle/GIMP-Quick-Selection).
