# Patchplot

A single-file lighting plot planner for clubs and small venues. Drafting-style plan view with draggable fixtures, DMX patch data on every unit, and wire runs.

**Live:** https://nicholaspjm.github.io/patchplot/

## Features

- Fixture types: par, spot/beam, wash, beam bar, blinder, atomic, laser
- Per fixture: label, universe, address, channel footprint, Art-Net node, notes
- Patch conflicts flagged per node + universe (overlaps and >512 overflow)
- Wire tool: click fixtures one after another to chain cable runs, mark any wire wireless
- Multiple plans with duplicate, editable room size and dashed zones
- Patch list with per node/universe totals and one-click sequential auto-patch
- Exports: CSV patch sheet, print-style SVG plot, full project JSON (with import)

## Use

Open `index.html` in any browser, or use the live link. Everything is saved in your browser (localStorage). To hand a layout to someone, export the project JSON and they import it on their end.

Shortcuts: drag to move, arrows nudge 0.1 m (Shift 0.5), R rotates, Ctrl+D duplicates, Del deletes, Esc deselects or exits the wire tool.
