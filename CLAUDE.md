# CLAUDE.md — Frontend Website Rules

## Always Do First
- **Invoke the `frontend-design` skill** before writing any frontend code, every session, no exceptions.

## Reference Images
- If a reference image is provided: match layout, spacing, typography, and color exactly. Swap in placeholder content (images via `https://placehold.co/`, generic copy). Do not improve or add to the design.
- If no reference image: design from scratch with high craft (see guardrails below).
- Screenshot your output, compare against reference, fix mismatches, re-screenshot. Do at least 2 comparison rounds. Stop only when no visible differences remain or user says so.

## Local Server
- **Always serve on localhost** — never screenshot a `file:///` URL.
- Start the dev server: `node serve.mjs` (serves the project root at `http://localhost:3000`)
- `serve.mjs` lives in the project root. Start it in the background before taking any screenshots.
- If the server is already running, do not start a second instance.

## Screenshot Workflow
- Puppeteer is installed at `C:/Users/nateh/AppData/Local/Temp/puppeteer-test/`. Chrome cache is at `C:/Users/nateh/.cache/puppeteer/`.
- **Always screenshot from localhost:** `node screenshot.mjs http://localhost:3000`
- Screenshots are saved automatically to `./temporary screenshots/screenshot-N.png` (auto-incremented, never overwritten).
- Optional label suffix: `node screenshot.mjs http://localhost:3000 label` → saves as `screenshot-N-label.png`
- `screenshot.mjs` lives in the project root. Use it as-is.
- After screenshotting, read the PNG from `temporary screenshots/` with the Read tool — Claude can see and analyze the image directly.
- When comparing, be specific: "heading is 32px but reference shows ~24px", "card gap is 16px but should be 24px"
- Check: spacing/padding, font size/weight/line-height, colors (exact hex), alignment, border-radius, shadows, image sizing

## Output Defaults
- Single `index.html` file, all styles inline, unless user says otherwise
- Tailwind CSS via CDN: `<script src="https://cdn.tailwindcss.com"></script>`
- Placeholder images: `https://placehold.co/WIDTHxHEIGHT`
- Mobile-first responsive

## Brand Assets
- Always check the `brand_assets/` folder before designing. It may contain logos, color guides, style guides, or images.
- If assets exist there, use them. Do not use placeholders where real assets are available.
- If a logo is present, use it. If a color palette is defined, use those exact values — do not invent brand colors.

## Anti-Generic Guardrails
- **Colors:** Never use default Tailwind palette (indigo-500, blue-600, etc.). Pick a custom brand color and derive from it.
- **Shadows:** Never use flat `shadow-md`. Use layered, color-tinted shadows with low opacity.
- **Typography:** Never use the same font for headings and body. Pair a display/serif with a clean sans. Apply tight tracking (`-0.03em`) on large headings, generous line-height (`1.7`) on body.
- **Gradients:** Layer multiple radial gradients. Add grain/texture via SVG noise filter for depth.
- **Animations:** Only animate `transform` and `opacity`. Never `transition-all`. Use spring-style easing.
- **Interactive states:** Every clickable element needs hover, focus-visible, and active states. No exceptions.
- **Images:** Add a gradient overlay (`bg-gradient-to-t from-black/60`) and a color treatment layer with `mix-blend-multiply`.
- **Spacing:** Use intentional, consistent spacing tokens — not random Tailwind steps.
- **Depth:** Surfaces should have a layering system (base → elevated → floating), not all sit at the same z-plane.

## Hard Rules
- Do not add sections, features, or content not in the reference
- Do not "improve" a reference design — match it
- Do not stop after one screenshot pass
- Do not use `transition-all`
- Do not use default Tailwind blue/indigo as primary color

---

## About Fabian (site owner — read before making content decisions)

**Who:** Fabian Prodan, 14, Romanian, currently in Botoșani area. Applying to Silverstone UTC (engineering school at the F1 circuit). Email: fabianprodan2011@gmail.com

**Situation:** May be moving to Northampton, UK (accepted at Weston Favell Academy and applied to Northampton Academy as options), but the move is not certain. Silverstone UTC is the main ambition — the portfolio is partly to support that application. Do not say he is "moving to England" as a done deal.

**The site:** `c:\Users\fabia\Documents\Bio\index.html` — single HTML file, all CSS/JS inline. Dark theme (`#0a0a0a`), chartreuse accent (`#7FFF00`), Space Mono + DM Sans. Hosted/to be hosted on GitHub Pages.

**Projects (current cards):**
- **DIY E-Ink Tablet** — In Development. Bespoke e-ink tablet to replace school textbooks. Waveshare 10.3" panel, IT8951 controller, RPi 4, Wacom EMR digitizer. Not built yet, not even in CAD. Competition targets: ONCS, RoSEF.
- **Sim Racing Rig** — Built. FFBeast direct drive wheelbase + hand-made steering wheel. Ground-up aluminium extrusion frame planned for a fixed, repeatable driving position.
- **Home NAS Server** — Decommissioned. 2008 AMD Phenom, TrueNAS SCALE, RAIDZ1, Syncthing, Tailscale, Homarr, Minecraft Forge. Retired — hardware too old, too little storage.
- **Electronics & Arduino** — Active. ODrive motor controllers (MKS ODrive Mini v1.0 repair), Pinecil V2 soldering, PT1000 sensor salvage, component-level repairs.
- **BeamNG Cinematic Edits** — Active. Video carousel (5 × edit-N.mp4 in videos/). Custom volume slider (no native input). Cinematic car edits posted to Instagram.
- **3D Printing & Fabrication** — Active. Bambu A1 + AMS Lite (FDM), Elegoo resin printer.

**Achievements:**
- Marea Aventură Digitală 2024 (first edition, November 2024) — 5th nationally out of 225 teams (675 participants), 1st in Județul Suceava. 5 points off 4th. Led the team's technical thinking.
- First Lego League school competition — 1st place, May 2026.
- First Lego League Camp — attended inaugural camp at school, summer 2024.
- Logiscool diplomas — digital, not publicly viewable (login required). Available on request.

**Brand — Chartreuse:**
- Personal creative brand. Three sub-teams: CRT (Chartreuse Racing Team), CTIT (Chartreuse IT), CDT (Chartreuse Design Team).
- Makes cinematic BeamNG.drive car edits posted to Instagram (@pillot2011_2111).
- Logo image: `images/chartreuse.png`. Berkeley Blue background (`#1e3566`) with outward glow.

**Contact:**
- Email: fabianprodan2011@gmail.com (links to Gmail compose, not mailto)
- Instagram: @pillot2011_2111
- GitHub: Pilot-572

**Image files needed in `images/`:**
- `myphoto.jpg` — karting photo (already added, landscape, aspect-ratio 4/3)
- `chartreuse.png` — Chartreuse logo (already added)
- `project-eink.jpg`, `project-simrig.jpg`, `project-nas.jpg`, `project-electronics.jpg`, `project-3dprint.jpg`

**Video files needed in `videos/`:** `edit-1.mp4` through `edit-5.mp4`

**Projects.txt** — Fabian writes raw project descriptions here (x.1 = card summary, x.2 = modal full description). Read it before writing any project copy.
