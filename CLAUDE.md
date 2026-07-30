# Drinking Buddies Zine website

Static site (plain HTML/CSS/JS, no build step) for Ahli Switzler's zine, Drinking Buddies. Deployed via GitHub Pages from the `main` branch of `github.com/Ahli-Switzler/DrinkingBuddiesWebsite`.

**Live site:** https://ahli-switzler.github.io/DrinkingBuddiesWebsite/

## Structure

- `index.html` — homepage: pixel-art lantern scene (3-floor bar diorama), circulation stats, nav chips (Get Involved / Play the Game / About the Author / Events / Keep the Lights On), Get Involved / About the Author / Events modals, red party button easter egg.
- `reader.html` — page-flip reader for zine issues, driven by `?issue=N`.
- `issues/issue-N/page-NN.jpg` — web-sized JPEGs extracted from source PDFs via `pdftoppm` (poppler). The original PDFs are print-resolution and far too large for git; only rendered pages are committed.
- `table-popup.html` — QR-code landing page for the July 28 Table pop-up event.
- `events/<event-slug>/index.html` — recap pages for past events (e.g. `events/daiq-off/`, `events/potions-and-paws/`), each with its own photo gallery pulled from the user's Desktop event folders.

## Conventions that matter

- **Never use em dashes (—) or en dashes (–) anywhere** — the user has explicitly flagged this multiple times as reading as AI-generated. Use periods, commas, or colons instead. Also avoid other AI-cliche phrasing (generic marketing-brochure voice, "seamless," "elevate," etc.) — the user is a writer and wants her own voice preserved, not paraphrased.
- **When incorporating the user's own writing** (from PDFs, menus, past copy), keep it close to verbatim. Don't rewrite/condense it into a different voice — she's called this out before as feeling "co-written" in a way she didn't want.
- **Every standalone event page gets its own one-off visual identity** matching that specific event's real promo material (flyer, menu, photos), not the main site's pixel/retro theme. Check the user's Desktop for an event folder with real assets (photos, flyers, cocktail cards) before designing. Past examples: Daiq Off used a forest-green vintage menu look; Potions & Paws used a spooky Halloween look matching its actual poster; the Table pop-up used a warm/brush-script look. The main `index.html` pixel theme is the exception, not the default, for anything event-specific.
- **`body { min-height: 100vh; }` is required on every page.** Without it, on pages with enough content to overflow one viewport, body's box collapses to exactly one viewport tall while content renders past it uncontained, breaking backgrounds, borders, and decorative absolutely-positioned elements partway down the page. Also set `align-items: flex-start` (not the flex default `stretch`) on any `body { display: flex }` used for centering.
- **Large media never goes directly into the repo.** PDFs, raw event photos/videos, etc. get processed first (`sips` for image resize/compress, `pdftoppm` for PDF pages) down to reasonable web sizes before committing. Always check file sizes before adding.
- **Fact-check event stats against real sources before publishing.** This user corrects numbers often (e.g. mini bar count, Instagram share counts, nonprofit name, bar lineups). Prefer real screenshots/photos/checks over stated round numbers when both are available, and flag discrepancies rather than silently picking one.
- **This project is entirely separate from the user's other GitHub repo**, a Drinking Buddies video game (different repo, different codebase). Never touch that repo from here; only link to its deployed URL when asked.
- Google Fonts are loaded via normal `<link>` tags (not embedded base64) on the event pages since this is a real deployed site, not a CSP-restricted Artifact. `index.html`/`reader.html` do embed Press Start 2P as base64 for historical reasons; either approach is fine going forward.

## Useful local commands

Serve the site locally for a quick check:
```bash
python3 -m http.server 8935 --directory /Users/ahli/drinking-buddies-map
```
