# Portfolio site

Files: `index.html` (content), `style.css` (look; colours are at the top), `assets/` (CV, favicon, your media in `assets/media/`).

Preview locally: open `index.html` in a browser. YouTube embeds only play when the site is served, so for a full preview run
`python3 -m http.server` in this folder and open http://localhost:8000.

## Adding images and videos

Every grey striped box in `index.html` is a placeholder like this:

```html
<div class="media placeholder"><span>Video · Unitree B1 on hardware</span></div>
```

Replace that whole line with one of these:

**Image** (put the file in `assets/media/`, keep it under ~1 MB, .jpg or .webp)
```html
<img class="media" src="assets/media/b1.jpg" alt="Unitree B1 walking on hardware">
```

**YouTube video** (best for anything long; upload as Unlisted if you prefer). The ID is the part after `watch?v=` in the URL.
```html
<div class="media wide"><iframe src="https://www.youtube-nocookie.com/embed/VIDEO_ID" title="Unitree B1 deployment" allow="fullscreen; picture-in-picture" allowfullscreen loading="lazy"></iframe></div>
```

**Short looping clip** (a silent GIF-like loop, a few seconds, .mp4 under ~10 MB)
```html
<video class="media" src="assets/media/go2_trot.mp4" autoplay muted loop playsinline></video>
```

Shape of the box (default is 4:3, cropped to fill):
- `class="media portrait"` for upright phone photos (3:4)
- `class="media wide"` for YouTube videos (16:9)
- `class="media natural"` for diagrams and screenshots (whole image shown, nothing cropped)

**Gallery (extra photos under a project)**: paste this inside the project's `<div class="project-body">`, just above `<ul class="tags">`:
```html
<div class="gallery">
  <img src="assets/media/fpv_1.jpg" alt="Robot on the floating platform">
  <img src="assets/media/fpv_2.jpg" alt="Brush module">
  <img src="assets/media/fpv_3.jpg" alt="LiDAR edge detection">
</div>
```

**Logos** (Experience / Education): save e.g. `assets/media/vistec.png` and replace
`<div class="logo placeholder"><span>Logo</span></div>` with `<img class="logo" src="assets/media/vistec.png" alt="VISTEC">`.

**Profile photo**: save it as `assets/media/profile.jpg` (square crop works best) and replace
`<div class="avatar placeholder"><span>Photo</span></div>` with
`<img class="avatar" src="assets/media/profile.jpg" alt="Boonyaporn Preechasuth">`.

## Publishing on GitHub Pages (free)

Repository: https://github.com/bpbb/portfolio (must be public). Git is already set up in this folder with that remote.

1. When you are ready to publish, in this folder:
   ```bash
   git add .
   git commit -m "Portfolio site"
   git push -u origin main
   ```
2. On GitHub: repository → Settings → Pages → Source: "Deploy from a branch", branch `main`, folder `/ (root)`.
3. After a minute the site is live at https://bpbb.github.io/portfolio/

To update later: edit, then `git add . && git commit -m "Update" && git push`.

(If you later want the shorter address https://bpbb.github.io, rename the repository to `bpbb.github.io`.)

## Updating the CV

The CV link points to `assets/Boonyaporn_Preechasuth_CV.pdf`. When your CV changes, copy the new PDF over that file.
Note that it contains your phone number; remove it from the CV first if you do not want it public.
