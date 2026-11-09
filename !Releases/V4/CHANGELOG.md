# Guyanonymous' Orrery Explorer – V4

Released 2026-11-09. Builds on V3.

## Neighbouring regions (3×3×3 block)
- A **Neighbourhood** picker in the region view shows your region and its 26 neighbours as three 3×3 layers (Above / This level / Below).
- Click a box to move there. Only one region is viewable and editable at a time; the others act as background.
- Neighbours copy your starting region's settings and come from a fixed seed, so the same box always gives the same stars. They are only kept in memory until you visit one; visited ones are saved to your region library.
- Objects in neighbours have fixed ids and names, so links to them (like constellations) survive.

## Fuller, more realistic night skies
- Night skies include stars and white dwarfs from your region and all 26 neighbours, so views toward a region's edge are no longer sparse (an edge star went from about 2,000 to about 53,000 stars).
- **Every star is drawn.** The old "Faintest shown" slider is now **Exposure**: stars brighter than it are clear dots that grow with brightness; fainter ones are dim specks that fade with brightness, forming a soft haze.
- Brightness already includes distance, so nearer and more luminous stars stand out.

## Constellations
- From any night sky: click stars to join them, lift the pen to start a new line, name it and save.
- Lines follow the sky's curve and are cut neatly at the equator between the two charts; names sit in the middle of their stars.
- Show/hide, edit, rename and delete (with a confirm). Saved per star system. Every change goes through Keep / Undo.
- Clicking a star shows which constellations it is in.

## Work-in-progress backups
- Backup 01: neighbouring regions. Backup 02: exposure display. Backup 03: constellations.
