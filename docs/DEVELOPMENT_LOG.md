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

## v1.2 (2026-11-16)

Joey's feedback on v1.1: Sol-i clips through things, is too dark at night, and the animation is crude; the west gate has a vehicle entrance; the W3 dorm door faces into the campus; add a switch for the falling effects.

- **Clipping**: walking cost now rises near walls, trees, lamps and parked cars (lamps and parked cars are blocked), so Sol-i keeps to the middle of paths. Building stop points moved from 2.2 to 3.2 units in front of the entrance. Sol-i is drawn at 0.5 scale in Sol-i view (0.75 otherwise). The camera tests the line behind Sol-i against building footprints and trees and pulls in / lifts instead of entering them.
- **Sol-i animation**: eased start and stop, step-driven hop, alternating legs, body sway and forward lean, squash and stretch, smoother turning.
- **Night**: Sol-i's materials glow, with a warm point light and halo.
- **West gate**: driveway from the street between W4 and W5 to the campus service road, gate pillars, raised barrier arm, guard booth; gate text updated (zh/ko/en).
- **W3**: entrance is chosen on a facade facing the campus interior.
- **Falling effects switch** in the toolbar (petals, leaves, snow); remembered per browser when storage is available.
- Tests: SwiftShader screenshots of the day and night route in Sol-i view; no page errors. Motion quality was not judged at real frame rate, and the west gate model was not seen in a close-up (it sits behind W4 from the default angle).
