# Menaka — Academic Portfolio (Scroll-Cinema Edition)

A scroll-driven video-frame background layered behind glass-panel sections.

## Structure

```
index.html
style.css            → full design system (colors, type, spacing) + glass panels
script.js             → nav, reveal-on-scroll, contact form handling
scroll-cinema.js      → preloads frames-N/ folders and scrubs them based on scroll position
images/                → local SVG illustrations (hero + project thumbnails)
frames-1/              → frame001.jpg – frame100.jpg
frames-2/              → frame101.jpg – frame121.jpg
```

Frames are split 100-per-folder (frames-1, frames-2, …) so they're easy to
drag-and-drop into GitHub's web uploader, which caps out at 100 files per
upload. `scroll-cinema.js` reconstructs the right folder for any frame
number automatically.

## How the scroll-video background works

`scroll-cinema.js` preloads every JPEG across the `frames-N/` folders, then
on every scroll event computes `scrollTop / (documentHeight - viewportHeight)`
(0 → 1) and maps that directly to a frame index. There's no timer — the
frame only changes when you scroll, so scrolling up plays it backwards.
All frames preload up front (with a progress bar) so scrubbing never
flickers.

## Uploading to GitHub without git

1. Drag `index.html`, `style.css`, `script.js`, `scroll-cinema.js`, and
   `images/` into your repo and commit.
2. Create/open a `frames-1` folder in the repo, drag in the 100 files from
   your local `frames-1/`, commit.
3. Repeat for `frames-2`.

## Deploying

Static site — drop the whole folder into a GitHub repo with `index.html`
at the root and enable GitHub Pages (Settings → Pages → main branch,
`/ (root)`), or drag the folder into Netlify/Vercel. No build step
required.
