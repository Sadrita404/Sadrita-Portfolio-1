# 08 — Assets

All files that need to be replaced or created from scratch.

---

## 8.1 — Favicon set

**Location:** `public/icons/`

**Files to replace:**
```
favicon.svg                  ← Vector favicon (shown in browser tab)
favicon.ico                  ← Legacy fallback (IE, old Android)
favicon-48x48.png            ← 48×48 PNG
favicon-96x96.png            ← 96×96 PNG
apple-touch-icon.png         ← 180×180 PNG (iOS home screen)
web-app-manifest-192x192.png ← 192×192 PNG (Android PWA)
web-app-manifest-512x512.png ← 512×512 PNG (Android PWA splash)
```

### How to generate the full favicon set

**Step 1 — Create your icon design**
- Start with a 512×512 SVG or PNG of your logo/monogram
- Keep it simple — favicons are tiny, detail disappears
- Use a solid background or transparent background (SVG favicon supports both)

**Step 2 — Generate all sizes**

Option A (online, free):
1. Go to https://realfavicongenerator.net
2. Upload your 512×512 PNG
3. Configure colors and download the ZIP
4. Replace all files in `public/icons/`

Option B (online, simpler):
1. Go to https://favicon.io
2. Choose "From Image" or "From Text"
3. Download and extract to `public/icons/`

**Step 3 — Update `site.webmanifest`**

```json
{
  "name": "YOUR_FULL_NAME Portfolio",
  "short_name": "YOUR_SHORT_NAME",
  "icons": [
    {
      "src": "/icons/web-app-manifest-192x192.png",
      "sizes": "192x192",
      "type": "image/png",
      "purpose": "maskable"
    },
    {
      "src": "/icons/web-app-manifest-512x512.png",
      "sizes": "512x512",
      "type": "image/png",
      "purpose": "maskable"
    }
  ],
  "theme_color": "#160000",
  "background_color": "#160000",
  "display": "standalone"
}
```

Note: The `src` paths in `site.webmanifest` use `/icons/` prefix because
the manifest file lives at `public/icons/site.webmanifest` but the paths
are resolved from the site root.

---

## 8.2 — OG social share image

**Location:** `public/images/aw-creative-developer.png`
**Required size:** 1200 × 675 px (16:9)
**Current file:** Antoine's branded image showing his name and title

This image appears when the page is shared on Twitter, Slack, iMessage, etc.

### What to put in it

- Your name (large)
- Your title / role
- Your website URL (small, bottom)
- Optional: a photo of yourself or your work
- Optional: your logo or monogram

### How to create it

**Option A — Figma (recommended)**
1. Create a new frame: 1200 × 675
2. Add your name, title, URL
3. Style it to match your site's color palette (`#160000` background, off-white text)
4. Export as PNG
5. Save as `public/images/YOUR_OG_IMAGE.png` (you can rename it)
6. Update the filename in `src/pages/index.astro` og:image tags

**Option B — Canva**
1. Search for "Open Graph" or "Social Share" template
2. Customize with your info
3. Download as PNG (1200×675)

**Your OG image filename:** `___________________________`
(Update this in `src/pages/index.astro` lines 55, 59)

---

## 8.3 — QR Code

**Location:** `public/images/qr-code.svg`
**Current content:** Encodes `sadritaneogi@gmail.com`

The QR code appears in the top-right corner of the header on desktop. Visitors
can scan it to contact you directly.

### What to encode

Choose one:
- Your email: `mailto:YOUR_EMAIL`
- Your website URL: `https://YOUR_DOMAIN`
- Your LinkedIn: `https://linkedin.com/in/YOUR_HANDLE`
- Your contact page: `https://YOUR_DOMAIN/contact`

### How to generate

1. Go to https://qr.io or https://www.qr-code-generator.com
2. Select "SVG" as output format
3. Enter your chosen URL or email
4. Keep it simple — no colors or logos inside the QR (the site uses it as a small icon)
5. Download and replace `public/images/qr-code.svg`

**QR code encodes:** `___________________________`

---

## 8.4 — Frame images (14 photos)

**Location:** `src/assets/frames/`

See `docs/06-myway.md` for the complete list of what each frame should show
and the naming conventions.

**Checklist:**
- [ ] Frame 1 — replace `art-1987.jpg`
- [ ] Frame 2 — replace `art-dtyw.jpg`
- [ ] Frame 3 — replace `art-lines.jpg`
- [ ] Frame 4 — replace `first-fwa.jpg`
- [ ] Frame 5 — replace `roar.jpg`
- [ ] Frame 6 — replace `setup-2006.jpg`
- [ ] Frame 7 — replace `setup-2016.jpg`
- [ ] Frame 8 — replace `setup-2020.jpg`
- [ ] Frame 9 — replace `waaark.png`
- [ ] Frame 10 — replace `portfolio-2011.jpg`
- [ ] Frame 11 — replace `portfolio-2014.jpg`
- [ ] Frame 12 — replace `portfolio-2017.jpg`
- [ ] Frame 13 — replace `portfolio-2021.jpg`
- [ ] Frame 14 — replace `legos.jpg`

**Specs:**
- JPG or PNG
- Width: 800–1200px (frames display at 500px on desktop)
- Compress to < 200KB per image

---

## 8.5 — Work videos

**Location:** `src/assets/works/`

See `docs/05-work.md` for the complete list.

**Checklist:**
- [ ] Delete `Dummy.mp4`
- [ ] Delete `Pen-4.mp4` through `Pen-8.mp4`
- [ ] Add your CodePen videos: `Pen-1.mp4`, `Pen-2.mp4`, ...
- [ ] Add Project 1 videos: `KEY-1.mp4`, `KEY-2.mp4`, ...
- [ ] Add Project 2 videos
- [ ] Add Project 3 videos
- [ ] Add Project 4 videos
- [ ] Add Project 5 videos
- [ ] Add Project 6 videos

**Specs:**
- MP4, H.264 codec
- Resolution: 1280×720 minimum, 1920×1080 preferred
- Duration: 5–15 seconds (they loop)
- Compress with HandBrake or ffmpeg before adding

---

## 8.6 — Decorative assets (keep as-is or customize)

These assets are used for animations and decorations. They do not contain
personal information and can stay as-is.

| File                                         | Used in                                      | Notes            |
| -------------------------------------------- | -------------------------------------------- | ---------------- |
| `public/images/asset-smiley--main.svg`       | About section — smiley particles             | Keep or redesign |
| `public/images/asset-smiley--contrasted.svg` | About section — smiley (dark mode)           | Keep or redesign |
| `public/images/asset-star.svg`               | Hero, About, CTA — star decorations          | Keep or redesign |
| `public/images/asset-world.svg`              | (referenced in code, not used in visible UI) | Keep             |
| `public/images/sprite-vanish.png`            | My Way — vanish animation sprite             | Keep             |

---

## 8.7 — Summary table

| Asset         | Current file                   | Your file       | Size       |
| ------------- | ------------------------------ | --------------- | ---------- |
| Favicon SVG   | `favicon.svg`                  | Your logo SVG   | Any        |
| Favicon ICO   | `favicon.ico`                  | Generated       | 16–48px    |
| Favicon PNG   | `favicon-48x48.png`            | Generated       | 48×48      |
| Favicon PNG   | `favicon-96x96.png`            | Generated       | 96×96      |
| Apple Touch   | `apple-touch-icon.png`         | Generated       | 180×180    |
| PWA Icon      | `web-app-manifest-192x192.png` | Generated       | 192×192    |
| PWA Icon      | `web-app-manifest-512x512.png` | Generated       | 512×512    |
| OG Image      | `aw-creative-developer.png`    | Your design     | 1200×675   |
| QR Code       | `qr-code.svg`                  | Regenerated     | SVG        |
| Frame 1       | `art-1987.jpg`                 | Your photo      | < 200KB    |
| Frame 2       | `art-dtyw.jpg`                 | Your photo      | < 200KB    |
| Frame 3       | `art-lines.jpg`                | Your photo      | < 200KB    |
| Frame 4       | `first-fwa.jpg`                | Your photo      | < 200KB    |
| Frame 5       | `roar.jpg`                     | Your photo      | < 200KB    |
| Frame 6       | `setup-2006.jpg`               | Your photo      | < 200KB    |
| Frame 7       | `setup-2016.jpg`               | Your photo      | < 200KB    |
| Frame 8       | `setup-2020.jpg`               | Your photo      | < 200KB    |
| Frame 9       | `waaark.png`                   | Your photo      | < 200KB    |
| Frame 10      | `portfolio-2011.jpg`           | Your photo      | < 200KB    |
| Frame 11      | `portfolio-2014.jpg`           | Your photo      | < 200KB    |
| Frame 12      | `portfolio-2017.jpg`           | Your photo      | < 200KB    |
| Frame 13      | `portfolio-2021.jpg`           | Your photo      | < 200KB    |
| Frame 14      | `legos.jpg`                    | Your photo      | < 200KB    |
| Work Video 1+ | `Pen-*.mp4`                    | Your screen-cap | < 5MB each |
| Work Video 2+ | `Dummy.mp4`                    | Your screen-cap | < 5MB each |
