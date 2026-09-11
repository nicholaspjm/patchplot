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
- Auto-patch: assigns universes and addresses from your cable runs — everything on one cable shares a universe, nothing else does — with a live preview before you commit and one-click undo after
- Patch list with per node/universe totals
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

### Auto-patch

**auto-patch** (in the header, and in the patch list drawer) works out addresses for you. It packs each
fixture into a universe by its channel count, never lets one straddle a universe boundary, gives every
Art-Net node its own universe space, and skips anything with no channels (speakers, lasers left at 0,
power drops).

It works from the cable runs you have drawn with the wire tool. A DMX line carries exactly one universe, so
fixtures chained together are kept in the same one and addressed in cable order. By default nothing else
shares that universe: a fixture with no wire to anything gets a universe of its own. Art-Net nodes break a
chain, since each output off a node starts a fresh universe, and non-DMX gear in the middle of a run passes
the chain through.

The **node** on a fixture is always the node it gets patched to — auto-patch never moves a fixture to a
different one. Each node has its own universe numbering, so Node A U1 and Node B U1 are separate. A wire
drawn between fixtures on two different nodes cannot join them, so the run is cut at that boundary and the
preview says so.

- **Order** — group by fixture type, sort by label, or run across the room front to back
- **Scope** — *re-address everything*, or *fill unpatched only*, which leaves the existing patch alone and
  drops new fixtures into the gaps in it
- **Chans / universe** — 512 by default; lower it to leave headroom at the top of each universe
- **First universe / first address** — start somewhere other than U1 @ 001
- **Gap between fixtures** — leave spare channels between units for later expansion
- **Wire runs** — how cable runs map onto universes:
  - *One universe per run* (default) — nothing shares a universe without a wire between it
  - *Keep each run whole, but pack runs together* — runs stay intact but several share a universe, which
    uses far fewer universes
  - *Ignore wires* — pack purely by channel count
- **Keep each type in one universe** — starts a fresh universe rather than split a block of identical
  fixtures, when the whole block would fit in one (only applies when runs are packed together)

The preview shows what each universe will hold before you apply, and anything that cannot fit is named
rather than quietly pushed past 512 — including a wire run too long for one universe, which no DMX line
could carry either. After applying, the toast offers **undo**.

### Where your work is stored

Saved plots live in the browser's own storage on the device you are using, and nowhere else. The app makes no
network calls of its own — nothing is uploaded, no account is involved, and other people opening the same URL
get their own separate set of plots. Two consequences worth knowing:

- Clearing site data, or using a private window, loses them. Download the project JSON to keep a real backup.
- Storage is per origin, so plots saved on the live site do not show up when you open a local copy of
  `index.html`, and vice versa. Move one across with download + **open a .json file…**.

Shortcuts: drag to move, arrows nudge 0.1 m (Shift 0.5), R rotates, Ctrl+D duplicates, Del deletes,
Ctrl+S saves, Ctrl+O opens the saved list, Esc deselects or exits the wire tool.
