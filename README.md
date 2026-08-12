# Claude Skills Lab — Interface Orientation for Faculty

A self-paced, asynchronous skills lab that onboards faculty to the Claude.ai interface. It's a single, self-contained HTML page (`index.html`) designed to be published with GitHub Pages and embedded in a Canvas page via an `<iframe>`.

The lab orients faculty to *where things are* in Claude — the sidebar, memory, models, projects, artifacts, and more. It does **not** cover how to write prompts; that's a separate lab.

Each station follows a two-part split: an **Iorad "See it" clip** shows *where* something is on screen (no clicking required), and the text below explains *what it does and why*, with an optional prompt to try it in Claude.

## What's in the page

- **Stations 2–12** as collapsible cards, one concept each. Faculty can work through them in order on a first pass, or reopen any single station later as a reference.
- **A "See it" Iorad slot** on stations 2–10 for the visual "where" (you supply the embeds — see below).
- **A paste-in prompt** for stations 2–10 that faculty select, copy, and paste into Claude to learn each feature by using it directly.
- **A short reflection field** at every station ("note one thing you learned").
- **Print-to-PDF support** that force-expands every station — including reflection notes — so a saved PDF is complete and can serve as a completion artifact. (The video slots are hidden in the PDF, but each "Where to look" caption still prints.)

Station 1 (sign-in) is intentionally not included here; it's added directly on the Canvas page above the embed.

## Files

| File | Purpose |
|------|---------|
| `index.html` | The complete lab. All HTML, CSS, and JS are inline — no dependencies or build step. |
| `README.md` | This file. |

## Publish with GitHub Pages

1. Create a repository (e.g. `claude-faculty-lab`) and add `index.html` at the root.
2. In the repo, go to **Settings → Pages**.
3. Under **Build and deployment**, set **Source** to *Deploy from a branch*, choose your branch (e.g. `main`) and the `/ (root)` folder, then **Save**.
4. Wait a minute, then visit the published URL: `https://<your-username>.github.io/<repo-name>/`.

## Embed in Canvas

Add the sign-in content directly on the Canvas page, then embed the published lab below it. In the Canvas Rich Content Editor, switch to the HTML view (`</>`) and paste:

```html
<iframe
  src="https://<your-username>.github.io/<repo-name>/"
  title="Claude Skills Lab"
  width="100%"
  height="1200"
  style="border:0;">
</iframe>
```

Adjust `height` to fit your page. Faculty select and copy each prompt manually, then paste it into Claude. They can also open the published URL directly and use the **Save this lab as a PDF** button.

## Adding your Iorad clips

Stations 2–10 each have a placeholder waiting for an Iorad embed. To add one:

1. In Iorad, open the walk-through and choose **Share → Embed**, and copy the embed code (an `<iframe>`).
2. In `index.html`, search for the station you want, e.g. `IORAD EMBED — STATION 6`. Each is marked with a clear comment block.
3. Directly below that comment, replace this placeholder line:

   ```html
   <p class="seeit-ph">▶ Iorad walk-through goes here — paste this station's embed code.</p>
   ```

   with your Iorad embed code. Leave the surrounding `<div class="seeit-slot">` tags in place — the page styles the embed to fit automatically.

The station-to-topic map: **2** navigation sidebar · **3** memory & settings · **4** first chat · **5** the + menu · **6** models & effort · **7** voice mode · **8** projects · **9** artifacts · **10** search. Stations **11** (Claude Design) and **12** (Cowork) have no clip by design — they're conceptual heads-ups, not "find this on screen" tasks.

## Editing the content

Everything lives in `index.html`. Each station is a `<details class="station">` block containing the copy, an optional paste-in prompt, and a reflection field. To change wording or a prompt, edit that station's block. Styling is controlled by the CSS variables in the `:root` block near the top (colors, corner radius, shadow) — a good place to apply institutional branding later.

## Notes

- Styling is neutral and clean by default so it can be rebranded to NDMU without reworking the layout.
- The page has no external dependencies, works offline, and needs no build tools.
- Print behavior is handled by an `@media print` block plus a small `beforeprint`/`afterprint` script that opens all stations for export and restores their state afterward.
