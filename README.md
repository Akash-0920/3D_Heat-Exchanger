# Shell & Tube Heat Exchanger 3D Designer

Single-file web tool. Enter exchanger geometry and feed-in details, get a live 3D model, basic duty/velocity checks, STL export and a printable datasheet.

No build step, no server. Open `index.html` in a browser.

## Features
- **TEMA types:** BEM (fixed tubesheet), AES (split-ring floating head), AET (pull-through floating head), BEU (U-tube)
- **Tube passes:** 1, 2, 4, 6 with pass partition plates and pass-coloured tubes
- **Editable naming:** exchanger tag (e.g. E-101) and a name for each side (e.g. "CRUDE", "VGO"). Names appear in the panel, on the 3D nozzle labels and in the datasheet.
- **Feed-in blocks:** tube-side (red) and shell-side (orange): fluid, flow, inlet/outlet T, Cp, density
- **Geometry inputs:** shell ID, tube length, tube OD and wall, pitch, layout (triangular/square), bundle clearance, pass lane, baffle count and cut, nozzle IDs and orientation
- **Calculated:** tube count, heat transfer area, flow areas, baffle spacing, bundle OD, duty per side, imbalance, velocities, LMTD (counter-flow, F=1), required U
- **Export:** STL (zipped, mm, Z-up) and HTML datasheet

## Run locally
1. Download `index.html`.
2. Double-click to open. Internet is needed once to load three.js from a CDN.

For an offline or intranet install, download `three.min.js` (r128) and change the `<script src=...>` line in `index.html` to point to the local copy.

## Publish on GitHub Pages
1. Create a repository and upload `index.html` and `README.md`.
2. Go to **Settings > Pages**.
3. Under **Build and deployment**, choose **Deploy from a branch**, select `main` and `/ (root)`, then **Save**.
4. After about a minute the site is live at `https://<your-username>.github.io/<repo-name>/`.

Other free options: Netlify Drop (drag the file onto app.netlify.com/drop), Cloudflare Pages, any internal web server.

## How to use
1. Set **Exchanger tag** and **TEMA type**.
2. Fill the red and orange feed-in blocks. Rename each side in **Side name**.
3. Enter shell, tube and baffle geometry.
4. Drag to rotate, scroll or pinch to zoom. Use **Shell: transparent** to see the bundle.
5. Read results at the bottom of the panel. Use **Export STL** or **Datasheet** to save.

## Notes and limits
- Geometry and a basic duty check only. **Not a thermal or mechanical design.** Verify against TEMA and ASME, and use rating software for final design.
- LMTD assumes pure counter-flow (F=1). Duty uses constant Cp.
- STL is a surface model, not a solid shell.
- Display is capped at 3000 straight tubes or 250 U-tube pairs. Counts and area use the full number.
- Floating-head and U-tube types are forced to an even number of passes. BEU is modelled as 2 pass.
- Nozzles are not sized for velocity or pressure drop.

## Tech
Plain HTML, CSS and JavaScript with [three.js](https://threejs.org) r128 (CDN). No dependencies to install.

## Licence
MIT. Add a `LICENSE` file before publishing.
