# Patchplot

A single-file lighting plot planner for clubs and small venues. Drafting-style plan view with draggable fixtures, DMX patch data on every unit, and wire runs.

**Live:** https://nicholaspjm.github.io/patchplot/

## Features

- Light types: par, spot/beam, wash, beam bar, blinder, atomic, laser
- Gear types: speaker, sub, DJ decks, screen, projector, camera, hazer, Art-Net node, power drop, and installations (custom shape, size in metres, colour, note shown on the plot)
- Per fixture: label, universe, address, channel footprint, Art-Net node, notes
- Patch conflicts flagged per node + universe (overlaps and >512 overflow)
- Wire tool: click fixtures one after another to chain cable runs, mark any wire wireless
- Named plot files: new, open, rename, save as a copy, delete — all kept in the browser, with autosave
- Multiple plans per file, with duplicate, editable room size and dashed zones
- Patch list with per node/universe totals and one-click sequential auto-patch
- Exports: CSV patch sheet, print-style SVG plot, full project JSON (with import)

## Use

Open `index.html` in any browser, or use the live link.

Work is organised into named **plots**, each holding one or more plans. The **file** menu covers the lot:

- **new blank plot** — an empty room, nothing patched
- **open saved plot…** — the list of everything saved in this browser, with rename, copy, download and delete on each
- **rename this plot… / save as a copy…**
- **open a .json file… / paste project json…** — both land as a new saved plot, leaving the rest alone
- **download project json** — the whole plot as a file, to back up or hand to someone else

Every change autosaves to the browser a moment after you stop, and the button at the top right shows whether
the current state is on disk.

### Where your work is stored

Saved plots live in the browser's own storage on the device you are using, and nowhere else. The app makes no
network calls of its own — nothing is uploaded, no account is involved, and other people opening the same URL
get their own separate set of plots. Two consequences worth knowing:

- Clearing site data, or using a private window, loses them. Download the project JSON to keep a real backup.
- Storage is per origin, so plots saved on the live site do not show up when you open a local copy of
  `index.html`, and vice versa. Move one across with download + **open a .json file…**.

Shortcuts: drag to move, arrows nudge 0.1 m (Shift 0.5), R rotates, Ctrl+D duplicates, Del deletes,
Ctrl+S saves, Ctrl+O opens the saved list, Esc deselects or exits the wire tool.
