# Claude Skills Lab — Interface Orientation for Faculty

A self-paced, asynchronous skills lab that onboards faculty to the Claude.ai interface. It's a single, self-contained HTML page (`index.html`) designed to be published with GitHub Pages and embedded in a Canvas page via an `<iframe>`.

The lab orients faculty to *where things are* in Claude — the sidebar, memory, models, projects, artifacts, and more. It does **not** cover how to write prompts; that's a separate lab.

## What's in the page

- **Stations 2–12** as collapsible cards, one concept each. Faculty can work through them in order on a first pass, or reopen any single station later as a reference.
- **A paste-in prompt** for stations 2–10, each with a one-click Copy button, so faculty learn each feature by using Claude directly.
- **A short reflection field** at every station ("note one thing you learned").
- **Print-to-PDF support** that force-expands every station — including reflection notes — so a saved PDF is complete and can serve as a completion artifact.

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

Adjust `height` to fit your page. Faculty can also open the published URL directly and use the **Save this lab as a PDF** button.

## Editing the content

Everything lives in `index.html`. Each station is a `<details class="station">` block containing the copy, an optional paste-in prompt, and a reflection field. To change wording or a prompt, edit that station's block. Styling is controlled by the CSS variables in the `:root` block near the top (colors, corner radius, shadow) — a good place to apply institutional branding later.

## Notes

- Styling is neutral and clean by default so it can be rebranded to NDMU without reworking the layout.
- The page has no external dependencies, works offline, and needs no build tools.
- Print behavior is handled by an `@media print` block plus a small `beforeprint`/`afterprint` script that opens all stations for export and restores their state afterward.# Claude_onboarding_v2
