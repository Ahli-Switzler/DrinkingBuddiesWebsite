# Drinking Buddies Zine: Website

A blog-style archive site for Drinking Buddies Zine, replacing the old Squarespace carousel with a retro pixel-art homepage: a glowing lantern-shaped zine stand with a 3-floor bar diorama (rooftop lounge, dance floor, ground-floor bar and kitchen prep area), modeled after the physical lantern zine stand. Clicking the sign opens the issue archive.

## Status

- `index.html`: homepage (pixel-art scene, circulation stats, link row, Get Involved modal, click-through to the issue archive). Plain HTML/CSS/JS, no build step.
- `reader.html`: simple page-flip reader for each issue.
- `issues/issue-N/`: web-sized JPEG pages extracted from the source PDFs (the originals are print-resolution and too large for the repo, so only the rendered pages are committed).

## Running locally

Just open `index.html` in a browser, or serve the folder:

```bash
python3 -m http.server 8000
```
