# Development log (v1)

Built in one long Claude session, 2026-11 (Mon 16 Nov = v1 freeze).

1. **Concept** – studied Homescape; decided to keep only the 3D click-to-explore idea. Source material: official site, Korean and English campus maps.
2. **First build** – illustrated-map based scene (Three.js, single HTML file), building cards, majors/offices/amenities lists, floor guide, dorm room preview, trilingual UI.
3. **11 upgrades** – arrival route, amenities, dorm room preview, majors search, Sol-i guide, landmark shapes, seasons, East Campus + W2-1, zh/ko/en, QR/embed, my location.
4. **Path-finding fix** – the route and Sol-i crossed buildings. Added a cost grid, A*, line-of-sight smoothing and a reachability flood so everything walks around buildings.
5. **Quality pass** – official photos (35, embedded), logo, floor guide; docked caption so narration no longer covers the route; refined season effects.
6. **Precision rebuild (this version)** – the illustrated map was not to scale (Daedong Station is about 680 m south of W13). Rebuilt the scene from real OpenStreetMap footprints in metres (0.3 units/m, 3.5 m per storey) with official floor counts:
   - 0 building overlaps (checked by polygon intersection); buildings missing from OSM (JCFS, S1–S5, 05, E6–E11) are placed in free space near their official position and marked approximate
   - W13 rooftop university-mark sign; W7 colonnade and front garden (shrubs, seasonal beds) on the OSM garden area
   - GPS "my location" in the same metric frame (accuracy ring, live watch; HTTPS only)
   - Bus & subway card per gate with lines, nearest stop, walking minutes from the path network, and tips
   - Seasons: instanced trees by species (cherry, ginkgo, maple, zelkova, pine), bare branches, snow caps, leaf litter, falling petals/leaves/snow, coats and umbrellas, snow on cars
7. **Test** – Playwright + SwiftShader: overlap check, route steps, four seasons, views; screenshots reviewed. Mobile and GPS were not tested on a real device.

## Problems met
- Artifact sandbox blocks geolocation → location only works when self-hosted over HTTPS.
- Network proxy blocked Overpass → map data fetched from the OSM API through the browser.
- Early particles invisible/noisy → resized, thinned by camera distance.
- Tree count first too high (7.4k, oversized) → smaller trees, wider spacing.
