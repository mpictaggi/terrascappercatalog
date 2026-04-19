# 🌿 Terra Scaper — Plant Care Brochure Library

A complete browser-based system for creating, managing, and printing professional plant care brochures for aquatic, terrarium, vivarium, houseplant, and exotic plants. No server, no build step, no dependencies to install — everything runs directly in the browser from a single folder.

---

## 📁 What's Included

| File | Purpose |
|------|---------|
| `TerrascaperCatalog.html` | Main library hub — browse, search, and filter all plants |
| `MasterTerrascaperBrochureGenerator.html` | Create and edit plant care brochures |
| `TerrascaperBrochure-[plant].html` | Individual plant brochures (16 included) |

---

## 🚀 Getting Started

1. **Download or clone this repository**
2. **Keep all files in the same folder** — the catalog links to brochures by filename
3. **Open `TerrascaperCatalog.html`** in your browser — this is your home base
4. Everything works from there — no internet connection required after the page loads

> **Note:** Files must be served over HTTP for full functionality. Double-clicking in some browsers may restrict localStorage. Use a local server (see [Running Locally](#running-locally)) or deploy to a host like Netlify.

---

## 🌱 The Catalog

The catalog (`TerrascaperCatalog.html`) is your plant library hub.

**Features:**
- Search by plant name, scientific name, SKU, or tagline
- Filter by plant type — Aquatic, Terrarium, Vivarium, Houseplant, Exotic
- Sort by name, SKU, or price
- Upload a cover photo to each card — saved permanently in your browser
- **Open Brochure** — opens the individual plant brochure
- **⬇ PDF** — opens the brochure and automatically exports a print-ready PDF with photos included

**Adding new brochures:**

Any new brochure dropped into the folder will appear in the catalog automatically after being opened once. The brochure registers itself in the browser's `localStorage` on first open — no manual catalog updates needed.

---

## ✏️ The Generator

The generator (`MasterTerrascaperBrochureGenerator.html`) lets you create and edit plant care brochures.

**Features:**
- Full plant data entry — name, care parameters, identification, propagation, warnings, tags
- 5 plant type palettes — Aquatic, Terrarium, Vivarium, Houseplant, Exotic
- 3 photo slots — cover photo, close-up, leaf detail (all persist in browser storage)
- Leaf number badge — numbered collector badge on the front cover
- Live A4 preview — two-spread layout matching the printed output exactly
- **💾 Save** — saves to the plant library, syncs to the catalog, and downloads an updated copy of the brochure HTML with your edits baked in
- **⬇ PDF** — exports a print-ready A4 landscape PDF with all photos included
- **🖨 Print** — browser print with correct A4 page setup

**Editing an existing brochure:**

Open the brochure file directly, make your changes, and click **💾 Save**. The browser will download an updated copy of the file with your edits baked in — replace the old file in your folder with the download.

---

## 📐 Brochure Layout

Each brochure is designed for **A4 paper, landscape, half-fold**.

```
Sheet 1 (outside) — print first
┌──────────────┬──────────────────────┐
│  Front Cover │  Back Cover + margin │
│   138mm      │   159mm              │
└──────────────┴──────────────────────┘

Sheet 2 (inside) — flip and print second
┌──────────────────────┬──────────────┐
│  Care & Husbandry    │ Identification│
│  + 23mm margin       │   138mm      │
│   159mm              │              │
└──────────────────────┴──────────────┘
```

**Printing instructions:**
1. Print Sheet 1 — Landscape · A4 · No Scaling · Background graphics on
2. Flip, feed back through, print Sheet 2
3. Fold at **138mm** from left — front cover faces out
4. Bind or staple through the left spine

---

## 📱 Accessing on Mobile

**Netlify Drop (easiest):**
1. Go to [netlify.com/drop](https://netlify.com/drop)
2. Drag your folder onto the page
3. Get an instant URL — open on any device

**Local network (same WiFi):**
```bash
cd /path/to/TerrascaperLibrary
python3 -m http.server 8080
```
Then open `http://YOUR-COMPUTER-IP:8080/TerrascaperCatalog.html` on your phone.

---

## 🏷️ Plant Types & Colour Codes

| Type | Colour | SKU Prefix |
|------|--------|------------|
| 🐠 Aquatic | Steel Blue `#4a7b9d` | `TS-AQ-` |
| 🌿 Terrarium | Chocolate `#d56f3e` | `TS-TR-` |
| 🦎 Vivarium | Hunter Green `#386641` | `TS-VV-` |
| 🪴 Houseplant | Sage `#a7cab1` | `TS-HP-` |
| 🌺 Exotic | Plum `#593f62` | `TS-EX-` |

---

## 🗂️ localStorage Keys

All data is stored in the browser's `localStorage` under these keys:

| Key | Contents |
|-----|----------|
| `ts_plant_library_v1` | Generator plant library |
| `ts_catalog_library_v1` | Catalog registry (shared between generator and catalog) |
| `ts_catalog_photos_v1` | All plant photos, keyed by SKU |
| `ts_brochure_edits_v1` | Saved brochure edits, keyed by SKU |
| `ts_auto_pdf_trigger` | Temporary flag for auto PDF export from catalog |

> localStorage is **per browser** — data does not sync between devices automatically. To move data, use the **⬆ Export** and **⬇ Import** buttons in the generator.

---

## 🖨️ Adding a New Plant

**Option A — Use the generator:**
1. Open `MasterTerrascaperBrochureGenerator.html`
2. Click **+ New** and fill in the plant details
3. Click **💾 Save** — the browser downloads a new brochure HTML file
4. Move the downloaded file into your library folder
5. Open it once — it registers itself in the catalog automatically

**Option B — Duplicate an existing brochure:**
Open any existing brochure HTML file, edit the `DEFAULT_PLANT` object near the top of the `<script type="text/babel">` block, save the file with a new name, and drop it in the folder.

---

## 🛠️ Technical Notes

- Built with **React 18** + **Babel Standalone** — no build step required
- **Fonts** loaded from Google Fonts: Playfair Display, Josefin Sans, Source Sans 3
- **PDF export** via html2canvas + jsPDF (loaded from cdnjs CDN)
- **QR codes** generated via api.qrserver.com
- Requires an internet connection on first load to fetch CDN assets; subsequent loads may work offline if the browser has cached them
- All photos are stored as base64 data URLs in localStorage — large photos may approach the ~5MB localStorage limit

---

## 📄 Included Plants

| Plant | Type | SKU |
|-------|------|-----|
| Anubias Panda Marble | Aquatic | TS-AQ-0058 |
| Baby Tears | Vivarium | TS-VV-0122 |
| Bean Fern | Vivarium | TS-VV-0094 |
| Buce 'Skeleton King' | Aquatic | TS-AQ-0065 |
| Butterfly Begonia | Vivarium | TS-VV-0115 |
| Pothos 'Cebu Blue' | Vivarium | TS-VV-0101 |
| Friendship Plant | Terrarium | TS-TR-0133 |
| Ludwigia Repens | Aquatic | TS-AQ-0071 |
| Neoregelia 'Fireball' | Vivarium | TS-VV-0088 |
| Philodendron Micans | Terrarium | TS-TR-0117 |
| Neo 'Chiquita Linda' | Vivarium | TS-VV-0138 |
| Neo 'Tiger Cub' | Vivarium | TS-VV-0131 |
| Philodendron El Choco Red | Terrarium | TS-TR-0124 |
| Watermelon Begonia | Vivarium | TS-VV-0108 |

---

## 🌐 www.terrascaper.com
