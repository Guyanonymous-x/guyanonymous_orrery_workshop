# Guyanonymous' Orrery Explorer

Build star systems and whole regions of space from real astrophysics, in a single HTML file that runs offline in any modern browser.
No install, no server: download the file for the version you want and open it.

## Versions

| Version | File | What it is |
|---|---|---|
| **V4** (latest) | [`!Releases/V4/Guyanonymous' Orrery Explorer V4.html`](!Releases/V4/) | V3 plus a 3×3×3 block of neighbouring regions, fuller night skies with every star drawn, and constellations you draw yourself |
| V3 | [`!Releases/V3/Guyanonymous' Orrery Explorer V3.html`](!Releases/V3/) | V2 plus triple/quadruple stars, habitability ranking, travel planner, star motion over time, close-ups and image saving |
| V2 | [`!Releases/V2/Guyanonymous' Orrery Explorer V2.html`](!Releases/V2/) | Single systems **plus** regions of space up to 100 × 100 × 100 light-years |
| V1 | [`!Releases/V1/Guyanonymous' Orrery Explorer V1.html`](!Releases/V1/) | The original single-system app (titled "Orrery Workshop") |

Each version folder has a `CHANGELOG.md` with the full history of that version.

## What's new in V4

- **Neighbouring regions**: a cube picker shows your region and its 26 neighbours (a 3×3×3 block). Click one to move there and explore or edit it.
- **Fuller night skies**: stars from all 27 regions are included, so skies toward a region's edge are no longer sparse.
- **Every star drawn**: the sky slider is now **Exposure**. Bright stars are bigger dots; faint ones are dim specks that form a soft haze.
- **Constellations**: join stars with lines, name the shape and save it with the star system. Show, hide, edit or delete them, with Keep and Undo.

## What's new in V3

- **Triple and quadruple stars**, with stable planet zones at every level.
- **Earth Similarity Index** for every planet, plus a "most Earth-like planets" ranking and filter for each region.
- **Travel planner** between any two objects: real spacecraft speeds, fractions of light speed (with time aboard the ship), or your own speed.
- **Star motion** over ±100,000 years with a time slider; the map, distances, travel planner and night sky follow the clock.
- **Close-ups** of every region object (pulsars with sweeping beams, black holes bending starlight, and more).
- **Night sky** now shows the system's own planets, moons and companion stars.
- **Save images** of the region map and the night-sky charts.

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
