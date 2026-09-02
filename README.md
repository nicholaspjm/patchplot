# Patchplot

A single-file lighting plot planner for clubs and small venues. Drafting-style plan view with draggable fixtures, DMX patch data on every unit, and wire runs.

**Live:** https://nicholaspjm.github.io/patchplot/

## Features

- Light types: par, spot/beam, wash, beam bar, blinder, atomic, laser
- Gear types: speaker, sub, DJ decks, screen, projector, camera, hazer, Art-Net node, power drop, and installations (custom shape, size in metres, colour, note shown on the plot)
- Per fixture: label, universe, address, channel footprint, Art-Net node, notes
- Patch conflicts flagged per node + universe (overlaps and >512 overflow)
- Wire tool: click fixtures one after another to chain cable runs, mark any wire wireless
- Multiple plans with duplicate, editable room size and dashed zones
- Patch list with per node/universe totals and one-click sequential auto-patch
- Exports: CSV patch sheet, print-style SVG plot, full project JSON (with import)

## Use

Open `index.html` in any browser, or use the live link. Everything is saved in your browser (localStorage). To hand a layout to someone, export the project JSON and they import it on their end.

Shortcuts: drag to move, arrows nudge 0.1 m (Shift 0.5), R rotates, Ctrl+D duplicates, Del deletes, Esc deselects or exits the wire tool.
