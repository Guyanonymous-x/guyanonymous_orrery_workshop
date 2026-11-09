# Guyanonymous' Orrery Explorer — V3 changelog (release)

Released 9 Nov 2026. Identical to "backup 04 (part 4 - close-ups, save images)" in the "V3 - Work in progress" folder.
The step-by-step history (backups 01–04) follows.

## V3 in short
- Triple and quadruple star systems, with stable planet zones at every level.
- Night sky shows the system's own planets, moons and companion stars; Celestia export handles multiple stars properly;
  the planet table includes rogue planets.
- Earth Similarity Index for every planet, a region "most Earth-like planets" ranking and filter.
- Travel planner between any two objects (real spacecraft, fractions of light speed with time aboard, or your own speed).
- Star motion over ±100,000 years with a time slider; the map, distances, travel planner and night sky all follow the clock.
- Live close-ups of every region object (stars, white and brown dwarfs, neutron stars and pulsars, black holes, clouds,
  interstellar objects, rogue planets).
- Save the region map and the night-sky charts as pictures.

---

V3 builds on the released V2 (!Releases\V2). Planned parts:
1. Fix V2 limits (triple/quadruple stars, planets and moons in the night sky, better multi-star Celestia export, rogue planets in the planet table)
2. Habitability ranking (Earth Similarity Index) + travel planner
3. Star motion over time (±100,000 years)
4. Close-ups of region objects + save images

## Part 1 — backup 01 (7 Nov 2026)
- Triple and quadruple stars (hierarchical: close pair A–B, then C circling the pair, then D circling all three).
  - Rates: Raghavan et al. (2010) — 56% single, 33% binary, 8% triple, 3% higher-order for Sun-like stars, i.e. ~18% of multiple
    systems are triples and ~7% quadruples. Applied to every star mass (my simplification).
  - Outer orbits must satisfy the Mardling & Aarseth (2001) stability rule; outer companions wider than 100,000 AU are not made
    (the Galaxy's tides pull such stars apart). Extra stars are taken from the region's own single stars, so totals stay realistic.
  - Every level gets its own stable planet zone (Holman & Wiegert 1999): around A alone, around A+B, around A+B+C, around all four.
    Some tight triples have no stable room around the inner pair at all; planets are then placed around one star or around everyone.
  - Solar system view: outer companions in the Catalogue, editable (name, mass, separation, eccentricity, angles), "Add outer
    companion (C/D)" and "Remove" buttons, red unstable zones for each gap, orbits drawn around the right balance point; Keep/Undo.
  - Region view: "G2V + M3V + M5V triple" labels, combined brightness, census counts pairs/triples/quadruples, outer companions'
    mass and separation editable. Older regions get an "Add triple & quadruple stars" button (with confirm) instead of changing silently.
  - Plausibility: outer companions ≥ 0.08 M☉, lighter than A, eccentricity ≤ 0.95, orbit widened to the stability limit (+10%).
- Night sky now shows this system's own planets, dwarf planets, comets, companion stars and moons (planets and moons ringed;
  switchable). Positions are at the simulated view's time; brightness is reflected starlight (Lambert phase, geometric albedo ≈
  the planet's albedo). From a moon, its planet hangs in the sky; a planet's moons sit along its equator.
  Example (Sun-like system): companion at 50 AU ≈ magnitude −13, a large moon ≈ −11, inner planets ≈ −2 to −5 (like Venus).
- Celestia: multiple stars written as nested barycentres ("X AB" inside "X ABC" …). Planets that circle several stars now get an
  OrbitBarycenter line pointing at the right barycentre (needs Celestia 1.6 or later).
- Planet table (.csv) now also lists every rogue planet (no host star; their own positions in the host columns). Full box ≈ 8 MB.
- Tested: 443 multiple systems from a fresh region opened without any impossible results; all earlier tests pass. Comments added.

## Part 2 — backup 02 (9 Nov 2026)
- Earth Similarity Index (Schulze-Makuch et al. 2011) for every planet: radius (weight 0.57), density (1.07), escape velocity (0.70),
  temperature (5.58); 1 = identical to Earth. Shown in each planet's derived values with interior and surface parts.
  - No greenhouse model exists in the app, so temperature is compared as equilibrium temperature against Earth's 255 K
    (equivalent to assuming Earth-like greenhouse warming — my choice). Checks: Earth 1.00, Mars 0.72 (published 0.70),
    Mercury 0.54 (0.60). Venus scores 0.90 instead of 0.44 because its runaway greenhouse isn't modelled; this is stated in the app.
  - Populate all systems now records each star's most Earth-like planet. Region overview lists the 15 most Earth-like planets
    (click to go to the star) and how many score 0.8 or more. New map filter: "Planet with Earth Similarity ≥ 0.8".
  - Regions populated before this version show a hint to press "Rebuild all systems" to score them.
- Travel planner in every region object's Inspector: pick any destination (300 nearest listed, any name can be typed).
  Times at New Horizons (16 km/s), Voyager 1 (17 km/s), Parker Solar Probe's fastest pass (192 km/s), 1%, 10%, 50% and 99% of
  light speed, plus your own speed in km/s or % of light speed. Shows time aboard the ship at high speed (special relativity).
  Cruise speed the whole way (no acceleration), as stated in the app.
- All earlier tests pass. Comments added.

## Part 3 — backup 03 (9 Nov 2026)
- Star motion over time: a time slider under the region map runs from −100,000 to +100,000 years, with ▶ Time (plays forward
  at 2,000 years per second), Pause and Now.
- Velocities (relative to the neighbourhood's average motion; the box drifts along with its stars):
  - Stars, white dwarfs, brown dwarfs, rogue planets: random, spread growing with age — σx = 22.41 T^0.307, σy = 14.39 T^0.239,
    σz = 10.26 T^0.353 km/s, T in billions of years (Bobylev & Bajkova 2016). Typical star ≈ 35 km/s, i.e. ~12 ly per 100,000 years.
  - Neutron stars: birth kicks of young pulsars, log-normal, mean ln(v) = 5.60, spread 0.68 (Disberg & Mandel 2025), ~150–300 km/s.
  - Black holes: same spread as stars (their kicks are poorly known; my simplification).
  - Gas clouds and interstellar objects: their own stored speeds.
  - The box's x, y, z are taken as the Galaxy's U, V, W directions (my choice). Straight-line motion.
  - Velocities are rebuilt from each object's id (nothing extra stored) unless you edit them.
- Everything follows the clock: map positions (objects that drift out of the box are faded), distances in the list, nearest
  neighbours, travel planner distances, and the night sky from any planet in the region.
- Each object shows its velocity and how long it takes to move one light-year; velocity x/y/z are editable (Keep/Undo).
  Plausibility: speed capped at 550 km/s (escape speed of the Galaxy). Typed positions are present-day (year 0) positions.
- Time resets to "now" when switching or regenerating a region.
- All earlier tests pass. Comments added.

## Part 4 — backup 04 (9 Nov 2026)
- Live close-up view at the top of every region object's Inspector, with Pause/Play, a speed slider (real time up to 1 year
  per second) and scroll-to-zoom. Spins use real figures where known; looks are an artist's impression (labelled):
  - Stars: mottled spinning globe (estimated spin period); white dwarfs (spin shown as 1 day — they spin in hours to days);
  - Brown dwarfs: banded, glowing by their own heat (spin shown as 5 hours);
  - Neutron stars: spin at their real period; young ones (pulsars) sweep two beams from magnetic poles tilted 30°;
  - Black holes: dark shadow (≈2.6 × horizon size), photon ring, and background stars bent into arcs (gravitational lensing);
    no glowing disk because nothing is falling in;
  - Gas clouds: drifting glow, with a note that real ones are invisible to the eye;
  - Interstellar objects: elongated body tumbling every ~8 hours like 'Oumuamua (my working figure);
  - Rogue planets: dark, lit only faintly.
- "Save image" buttons: region map (under the map) and the night-sky window. Pictures are PNG with a title strip
  (name, view, time, box size or brightness limit).
- Fixes: white-dwarf size formula no longer breaks when an impossible mass is typed with "Keep it plausible" off;
  the random system generator no longer places its first planet inside a very small star (V1 bug; it now starts at least
  6 star-radii out).
- All tests pass.
