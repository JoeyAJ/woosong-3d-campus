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

## v1.1 (2026-11-16, same day as v1)

Requested by Joey after reviewing v1.

- **W13 sign corrected** against the official building photo: a box on top of the core with two navy faces (white ㅇㅅㄷ mark) and two white faces (green/blue/red ㅇㅅㄷ mark). The v1 sign used a wrong crop of the logo and a red pillar that does not exist. The tower also got ribbon windows, the dark glazed strip and the white banner panel.
- **Night scene fixed**: lamp light pools were drawn as opaque white squares (no texture). They now use a soft radial texture; ambient light is darker and bluish, ground and roads are darker, the sign is lit.
- **Facade styles checked against the 35 official photos**: ribbon windows for W1, W6, W10, W13, 05 and SolBridge (dark tower with a white core strip), nearly windowless wall for W2, barrel roof for W11.
- **Sol-i view**: in the Sol-i tour and the arrival route the camera now follows behind Sol-i at street level. Dragging the scene frees the camera until the next stop. The tour waits for Sol-i to arrive before moving on (it used a fixed 5.6 s timer).
- Tests: Playwright + SwiftShader screenshots of the W13 sign (day and night), night view and the route in Sol-i view. SwiftShader runs at about 1 fps, so motion was checked with a test-only time step, not at real speed. Not tested on a real phone.
