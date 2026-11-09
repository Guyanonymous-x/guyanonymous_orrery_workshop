# Guyanonymous' Orrery Explorer — V2 changelog (release)

Released 7 Nov 2026. This is the finished V2, identical to "backup 11 (stage 2 part B - binary stars)" in the
"V2 - Work in progress" folder. The full step-by-step history (backups 01–11) follows.

## V2 in short
- Renamed from "Orrery Workshop" (V1) to "Guyanonymous' Orrery Explorer". V1 saved systems and files still load.
- Region of space: boxes up to 100 × 100 × 100 light-years filled with realistic numbers of stars, white dwarfs, brown dwarfs,
  neutron stars, black holes, rogue planets, gas clouds, interstellar objects and binary stars, from published surveys.
- 2D and rotatable 3D region maps; populate every star's planets; filters, statistics, planet table export.
- Save/load regions (browser + region files), plus everything V1 could save and export.
- Editing everywhere with "Keep it plausible" fix-ups and a Keep / Undo review of every change.
- Night sky charts (north and south) from any planet or moon.
- Live simulated 3D view of planets with moons, and of the whole system, with time controls.
- Full two-star (binary) systems.
- Plain-English comments throughout the V2 code.

---

## Stage 1 — Region of space (started 7 Nov 2026)

### Backup 01 — region code added, not yet tested
- App renamed from "Orrery Workshop" to "Guyanonymous' Orrery Explorer" (title, header, export file comments).
  Saved-data keys and file format names stay the same so V1 libraries and files still load.
- New "Region of space" workspace beside the existing "Solar system" one (switch at the top).
- Region box: width, depth and height each 1–100 light-years.
- Realistic counts from published space densities near the Sun:
  - about 3,600 stars, brown dwarfs and white dwarfs within 20 parsecs (Kirkpatrick et al. 2024),
  - stars : brown dwarfs about 4 : 1 (same paper),
  - white dwarfs 4.47 per 1,000 cubic parsecs (Gaia 20-pc sample).
- Each count is a random (Poisson) draw around the expected number; you can type your own count instead (0–10,000 per type).
- Star mass range is yours to set (0.08–150 solar masses); masses inside it follow the measured mass function.
- Objects: main-sequence stars, white dwarfs, brown dwarfs, each with its own data and description.
- 2D map (top, front, side) and rotatable 3D map, zoom, pan, labels, height lines, legend, click to select.
- Stars open as full planetary systems built from their own seed (same result every time); opened systems are saved in full.
- Region kept in the browser automatically, plus "Save region file" / Import (includes any opened systems).

### Backup 02 — stage 1 tested
- Fixed: the drawing loop could stop when switching workspaces (the hidden solar-system size strip tried to draw with zero height). Both maps now draw only when visible, and an error can no longer stop drawing.
- Counts table no longer wraps awkwardly; "Your count" shows "auto" when empty.
- Volume shown as a plain number (1,000,000 cubic light-years).
- Height lines fade when there are many objects so the 3D view doesn't turn hazy.
- Singular/plural wording fixed ("1 star", "1 object").
- Tested in a browser: realistic counts (a full 100-ly box gave about 2,400 stars, 125 white dwarfs, 600 brown dwarfs; about 3 in 4 stars are red dwarfs),
  2D and 3D maps, clicking dots, opening a star (same planets every time), save and re-import of a region file with its opened systems,
  reload keeps everything, a 5-ly box, out-of-range sizes are refused, and all V1 exports still work.

### Backup 03 — map fix (open this one)
- Reported: 2D and 3D maps showed nothing. Cause: backup 01 had the drawing-loop bug (fixed in backup 02),
  so backup 01 always shows blank maps. Use backup 03 or later.
- Extra safety: each map re-measures itself if it was hidden when last sized.
- If the region map ever fails to draw, it now shows the error message on the map instead of staying blank.
- Retested at 100%, 125% and 150% display scale, and starting straight into the region view after a reload.

### Backup 04 — Populate all systems
- New "Populate all systems" button (region settings): builds the planets of every star in the region from each star's own seed.
  A full 100-ly box (about 2,400 stars) takes under a second here.
- Only a short summary per star is stored in the browser (planets, rocky, giant, rocky planets in the habitable zone, moons,
  dwarf planets, belts, comets). Full systems are rebuilt identically whenever needed; systems you opened and edited are used as saved.
- Map and list filter (under the map): all objects, stars with planets, rocky planet in habitable zone, stars with giant planets, stars without planets.
- Region overview now has a "Planetary systems" statistics section; each star shows its planet summary; the list shows planet counts and "HZ".
- "Save region file" now opens a save window with three choices:
  - Region file (as before),
  - Region + all systems (every planetary system written out in full; about 6 MB for a full box),
  - Planet table (.csv): one row per planet and dwarf planet, with host-star position.
- Importing a "Region + all systems" file does not flood the Solar system list: only systems you had opened are added.
- Large files show a shortened preview; Save file and Copy always use the whole file.
- Regenerating a region clears its population (new stars need Populate again).

### Backup 05 — editing with Keep / Undo, "Keep it plausible", region links
- "Keep it plausible" switch at the top (remembered). When on, finishing an edit (Enter or leaving the box) fixes anything
  impossible by adjusting the *other* values; the value you typed is kept. Warnings are left as warnings.
  - Star: too old for its mass → age lowered to 85% of its lifetime; age edited beyond lifetime → mass lowered; limits 0.08–150 M☉, age ≤ 13.8 billion years.
    Impossible radius/luminosity overrides are cleared.
  - Planet: mass outside its type → type changes (or, if you changed the type, the mass changes); over 13 Jupiters capped;
    orbit inside the star or its tidal break-up zone moved out (or eccentricity lowered if that's what you edited);
    spin faster than break-up slowed; impossible radius override cleared (or mass changed if you edited the radius);
    neighbours too close or crossing moved to 7 mutual Hill radii, cascading outward (inward if you moved the outer planet).
  - Belt: edges kept in order and outside the rock-vaporising zone. Comet: kept out of the star.
  - Moon: kept outside its planet's break-up zone and inside half its Hill sphere; can't outweigh its planet.
  - White dwarf: 0.2–1.43 M☉, age raised (or mass raised) so its original star could have died. Brown dwarf: 13–78 Jupiter masses.
  - Region positions kept inside the box.
- Every edit (both views) shows an "Unsaved changes" panel listing each change, plus what was adjusted and why, with Keep and Undo.
  Moving to another object, system or view keeps pending changes (a short message says so).
- Region objects are now editable: name, mass, age, metallicity (stars), and x/y/z position.
  Editing a star that has planets saves its system in full first, then nudges the planets to suit the new star.
- Edits made in the Solar system view to a star from a region are copied back to the region.
- Switching to the region view brings in the system you were looking at: a region star is selected;
  a hand-made system is added at its distance and sky position (or the box centre if that's outside the box) and selected. No duplicates.
- After "Populate all", a star's button says "Open this system".

### Backup 06 — night sky from a planet
- New "Night sky from here (north & south)" button on every planet and dwarf planet.
- Opens a window with two round sky charts: northern and southern celestial hemispheres (pole in the centre, equator at the edge).
- Stars and white dwarfs from the planet's region, placed by their real direction from this system, sized by how bright they
  look from there (apparent magnitude from their physics and distance) and coloured by temperature. Brown dwarfs are too faint
  in visible light and are left out.
- Each system has its own fixed random tilt in space (from its id); the planet's inclination and axial tilt are applied on top.
  Right ascension 0h is where the planet's equator crosses its orbit plane (like Earth's equinox).
- Brightness slider: magnitude 1 to 15 (naked eye, binoculars, small and large telescopes).
- Names of the 12 brightest visible stars per chart; click any star for name, type, distance, magnitude and coordinates.
- Poles and grid: pole marks, 30° and 60° circles, hour lines and labels; names the nearest naked-eye "pole star" north and south.
- Decorative backdrop (switchable, labelled as not real): a Milky Way band along one fixed plane per region plus scattered faint dots.
- If the system isn't in a region yet, the window says so and shows only the backdrop.
- Note added when the star sits well off the box centre, since one side of its sky will look fuller.

### Backup 07 — code comments
- Added plain-English comments to all V2 code so a person can follow it:
  - about 110 one-line `//` comments, one above each V2 function or setting, saying what it does and why;
  - `<!-- -->` comments marking the V2 page sections (view switch, plausible switch, region view, changes panel, sky window);
  - `/* */` comment marking where the V2 styles begin;
  - comments on the few places V2 hooks into the original V1 code.
- No behaviour changes; all tests re-run and passed.
- From here on, new code gets comments as it is written.

### Backup 08 — night sky from moons
- Every moon card now has a "Night sky" button (next to Remove), so the sky view is available from every planet, dwarf planet and moon.
- A moon's sky uses its planet's poles: regular moons orbit in their planet's equator plane and are tidally locked with almost
  no tilt. Star positions are the same as from the planet (the distance between them is tiny compared with light-years).
- Window title names the moon and its planet.
- Comments added for the new code.

### Backup 09 — simulated view in the Inspector
- Live 3D view at the top of the Inspector (Solar system view):
  - Planet or dwarf planet selected: the body spins at its real rotation period (tidally locked ones once per orbit,
    retrograde ones backwards), lit from its star; the lit side moves round once per orbit. Moons orbit around its equator
    at their real periods; rings drawn in the equator plane. Axis and equator shown (switchable), axis hidden behind the planet.
  - Star selected: the star spins and every planet, dwarf planet and comet moves along its real 3D orbit
    (inclination, node, periapsis, eccentricity); belts drawn as moving debris; comet tails grow near the star.
- Controls: Pause/Play, Reverse, speed slider (real time, 1 minute/s, 1 hour/s, 6 hours/s, 1 day/s, 1 week/s, 30 days/s,
  1 year/s, 10 years/s), Real time button, Readable / True scale switch, Axis switch, drag to turn the camera, scroll to zoom.
  Starts at 6 hours/s for a planet and 30 days/s for the star.
- Readable scale: planet large, moon distances squeezed logarithmically, moons enlarged. True scale: real sizes and spacing.
- Surface looks are an artist's impression chosen by type and temperature (marked as such under the view):
  gas giants banded, ice giants blue, sub-Neptunes hazy teal; rocky worlds icy (<200 K), oceans/land/ice caps (temperate),
  dry rock (>330 K) or glowing lava cracks (>700 K); dwarf planets grey and cratered; stars mottled with darker edges.
- Star spin period is an estimate (the app stores none): about 25 days for the Sun, slowing with age (∝ √age),
  slower for smaller stars; stars above 1.3 M☉ spin at about 150 km/s at the equator. Labelled as an estimate.
- Runs at 60 frames per second in testing. All earlier tests re-run and passed. Comments added for all new code.

### Backup 10 — speeds halved; stage 2 part A: new object types
- Simulated view now starts at 3 hours/s for planets and 15 days/s for the star (both speeds added to the slider).
- New region object types, each on the map, in the list, in the Inspector (data + description) and editable with Keep / Undo:
  - Neutron stars (~2.5 per full 100-ly box; McKee et al. 2015): mass, 12 km radius, density, gravity, escape speed,
    spin period slowing with age, magnetic field, rough cooling temperature, gravitational redshift; "active pulsar" if younger
    than 50 million years (my working figure for the pulsar phase).
  - Black holes (~0.4 per box; McKee et al. 2015, ~8 M☉ each): event horizon, photon sphere, innermost stable orbit (with spin),
    tidal stretch, Hawking temperature, evaporation time. Many boxes have none.
  - Rogue planets (~21 per star, ~50,000 per full box; Sumi et al. 2023 mass function). Rebuilt from the seed rather than saved;
    only your edits are saved. A slider chooses which appear (default heavier than 10 Earth masses, ~2,000 shown); all are counted.
    Internal-heat temperatures are rough estimates.
  - Warm gas clouds (~31 per box; 15 within 15 pc per Redfield & Linsky 2008): 4–20 ly across (my choice of size range),
    5,300–9,900 K, 0.05–0.3 hydrogen atoms/cm³, drifting 10–30 km/s; drawn as soft glows at their real size.
  - Interstellar asteroids & comets: estimated total shown (≈0.1 per cubic AU, ~2.5×10¹⁹ per full box; range 0.004–0.24),
    plus 25 clickable examples (50–1,000 m, ~26 km/s, half icy, half rocky — example ranges are my choice).
- Counts table, census and summary include the new kinds; each has an "auto" or typed count.
- Existing regions keep their stars exactly; the new kinds are added from a separate random stream the first time they're opened.
- Plausibility rules for new kinds: neutron star 1.1–2.3 M☉; black hole ≥ 3 M☉, spin ≤ 0.998; rogue planet 0.01 Earth masses to
  13 Jupiter masses; cloud temperature 3,000–12,000 K, radius ≥ 0.5 ly (my lower limit); interstellar object speed ≤ 550 km/s
  (Galaxy escape speed), size ≥ 1 m.
- Object list shows at most 3,000 rows at once (with a note) to stay quick.
- Night sky ignores the new kinds (far too faint in visible light) and says so.
- Region settings pane slightly wider so the counts table fits.

### Backup 11 — stage 2 part B: binary stars and the two-star solar view
- Regions: new regions pair stars realistically — ~27% of red dwarfs, ~46% of Sun-like stars, ~55% at 1.5–5 M☉,
  65% at 5–16 M☉ (my in-between value), ~75% above (Winters 2019; Raghavan 2010; Duchêne & Kraus 2013; Sana & Evans 2010).
  Separations log-normal (peak ~45 AU, spread 1.5 dex; red dwarfs ~20 AU, 1.16 dex); mass ratio flat 0.1–1;
  eccentricity 0 below 0.1 AU, up to 0.2 below 1 AU, up to 0.6 beyond (my approximation).
  Companions are taken from the region's own stars (nearest suitable mass), so star totals and the mass mix stay realistic.
  Companions that would be brown dwarfs are left out (star stays single).
- Older regions are not changed automatically: a "Pair up binary stars" button (with confirm) appears for them.
  Stars you opened or made by hand are never paired.
- Region map/list show a pair as one point with combined brightness ("K7V + M3V pair"); census counts both stars and the number in pairs.
- Region Inspector shows companion, separation, period and stable planet zones; companion mass, separation and eccentricity are editable.
- Solar system view (full two-star support):
  - Companion listed in the Catalogue (selectable, editable: name, mass, separation, eccentricity, inclination, node, periapsis,
    mean anomaly) with description and derived values; "Add companion star" / "Remove companion star" buttons (Keep/Undo apply).
  - Orbit map: companion's dashed orbit and moving star; red "unstable zone"; circumbinary planets orbit the pair's balance point.
  - Physics: planets circling both stars use the pair's combined mass and light; others get the primary plus the companion's light.
    Planets in the unstable zone (Holman & Wiegert 1999) are flagged impossible.
  - Opening a region binary moves any generated planets out of the unstable zone (spacing kept).
  - Simulated view (star) shows both stars spinning, the companion orbiting, circumbinary planets following the balance point.
  - Night sky from a planet shows its own companion as a very bright star; other pairs shine as one combined point.
  - Exports: Celestia .stc writes a barycentre with both stars orbiting it; exoplanet CSV gains sy_snum (number of stars).
- Plausibility rules: companion ≥ 0.08 M☉ and never heavier than the primary; stars kept from touching; eccentricity ≤ 0.95;
  bodies moved out of the unstable zone (inward if they fit, otherwise outward), alternating with the spacing rule until both hold.
- All earlier tests re-run and passed. Comments added for all new code.
