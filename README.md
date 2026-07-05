# Terrain Sculptor
 
A browser-based heightmap sculpting tool. Paint elevation data on a 2D canvas and inspect the result in real time as a rendered 3D mesh. Implemented as a single self-contained HTML file (HTML/CSS/JS + Three.js), with no build step and no external tooling required to run or deploy.
 
## Overview
 
Terrain Sculptor couples a 2D raster paint surface with a live 3D viewport. Every brush stroke on the heightmap canvas immediately updates the corresponding vertex displacement in the Three.js scene, giving direct visual feedback on slope, elevation range, and terrain continuity before exporting.
 
## Architecture
 
- **Single-file deployment** — all markup, styling, and logic live in one `.html` file. No bundler, package manager, or server-side component. Deployable as a static asset (e.g. via GitHub Pages) by uploading the file as-is.
- **2D paint layer** — a `<canvas>`-based editor where pixel intensity encodes elevation. Supports adjustable brush size and paints directly into the underlying heightmap data array.
- **3D preview layer** — a Three.js scene that reads the heightmap array and displaces a plane geometry's vertices accordingly, rendered with orbit controls for inspection from arbitrary angles.
- **Aspect ratio handling** — the heightmap grid and 3D mesh dimensions are kept in sync, so painted proportions are preserved between the 2D and 3D representations rather than being stretched to fit a canvas.
## Height Range Configuration
 
Elevation values are not hardcoded to a fixed range. A configurable `minHeightValue` and `minHeightValue` parameters shifts the bounds of the height scale, allowing the full paintable range (min → max) to be tuned per-project rather than assuming terrain always starts at zero.
 
## Export Formats

**Long-format coordinate export (XLSX and JSON)** — a tabular, coordinate-based export where each row represents a single grid cell as `(x, y, height)`. This format is intended for workflows that consume terrain data as discrete coordinate/height triples rather than as an image, e.g. CNC/plotting pipelines, physical model fabrication, or spreadsheet-driven post-processing.

Currently working on **Raster heightmap export** — the painted 2D data will be exported as a standard heightmap image/array, suitable for downstream terrain-generation pipelines.

## Running Locally
 
No installation required,  just open the file **index.html** directly in your browser, or

## [RUN IT FROM HERE](https://orangetungsten.github.io/Terrain-Sculptor/index.html)
 