# Guyanonymous' Orrery Explorer

Build star systems and whole regions of space from real astrophysics, in a single HTML file that runs offline in any modern browser.
No install, no server: download the file for the version you want and open it.

## Versions

| Version | File | What it is |
|---|---|---|
| **V2** (latest) | [`!Releases/V2/Guyanonymous' Orrery Explorer V2.html`](!Releases/V2/) | Single systems **plus** regions of space up to 100 × 100 × 100 light-years |
| V1 | [`!Releases/V1/Guyanonymous' Orrery Explorer V1.html`](!Releases/V1/) | The original single-system app (titled "Orrery Workshop") |

Each version folder has a `CHANGELOG.md`. Git tags `v1` and `v2` mark each release.

## What V2 does

**Solar system view**
- Stars, planets, moons, asteroid belts, dwarf planets and comets, with every derived value worked out from physics (periods, temperatures, habitable zone, frost line, density, gravity, which gases a planet can hold, and more).
- Physics checks label anything Impossible, a Warning or a Note.
- "Keep it plausible" switch: finishing an edit adjusts related values so the result stays physically possible. Every change is listed with **Keep** and **Undo**.
- Binary stars: a companion star, its orbit, and the zones where planets can orbit stably.
- Live simulated 3D view of the selected planet (spinning, with its moons) or of the whole system, with time controls from real time to 10 years per second.
- Night sky charts (northern and southern) from any planet or moon.

**Region of space view**
- A box up to 100 × 100 × 100 light-years filled with realistic numbers of stars, white dwarfs, brown dwarfs, neutron stars, black holes, rogue planets, gas clouds and interstellar objects, based on published surveys.
- Rotatable 3D map and 2D top/front/side maps; click any object for its data; edit any object.
- "Populate all systems" builds planets for every star, with filters and region-wide statistics.

**Saving and exporting**
- Everything is kept in your browser automatically.
- Files: system JSON, whole library, region files (optionally with every system), planet table (CSV with NASA Exoplanet Archive column names), and Celestia catalogues (.ssc / .stc).

## Limits

- Main-sequence stars only for planetary systems (no giant stars).
- Temperatures are equilibrium values with no greenhouse effect.
- Orbits are fixed ellipses (no N-body simulation).
- Surface colours in the simulated view are an artist's impression.

## Sources

Key data sources are listed in each version's changelog and inside the app's region overview, including Kirkpatrick et al. 2024 (20-pc census), McKee et al. 2015, Sumi et al. 2023, Redfield & Linsky 2008, Raghavan et al. 2010, Holman & Wiegert 1999 and Kopparapu et al. 2013.
