# Handoff (v1.0)

## State
Working, single file `index.html` (~890 lines + embedded data: GEO, photos, logo). Public URL: https://joeyaj.github.io/woosong-3d-campus/ . Version label: v1.

## Where things are in index.html
- `L` – UI strings (zh/ko/en). `RAW`, `OVR`, `TXT` – building list, corrections, descriptions.
- `M` majors, `O` offices, `FA` amenities, `FL`/`FT` floor guide + translations, `DORM`, `ROUTE`, `TOUR`.
- `PHOTO_SRC`, `LOGO` – embedded base64 (CSP of the first host only allowed data: images).
- `GEO` – OpenStreetMap data in metres: buildings, roads, areas, bus stops, subway exits.
- Scene: `special{}` per-building models (W13, W19, W7, 06, JCFS), `MAN` manual placements, nav grid + `astar`, trees, cars, people, Sol-i, season effects, `GATE_BUS` bus lines and tips.

## How to update
- Text, majors, offices, floors: edit the data arrays; no build needed.
- Bus lines/tips: `GATE_BUS` (source: wsu.ac.kr "찾아오시는 길 / 대중교통"). Re-check every semester.
- New photo: add to `PHOTO_SRC` keyed by building id.
- Re-fetch map data if buildings change (OSM API, local metres around 36.3356, 127.4444).
- Deploy: push to `main`; GitHub Pages serves the root.

## Known gaps
- Approximate positions: JCFS, S1–S5, 05, E6–E11 (not in OSM). W2-1 has label only.
- Facade colours/windows are generic; only W13, W19, W7 have custom details. Needs on-site photos.
- Western/northern gates and some bus stops were placed from map data without a field check.
- Mobile layout and GPS not verified on a real phone.
- Bus lines are from the web page at build time; no live arrivals.
- Photos/logo belong to the university; get permission before wider reuse. No code license set.

## Next ideas (ordered)
1) calibrate W7/W13/W19 with 6–10 site photos; 2) link floor guide to section views; 3) real-device test + "navigate from my location"; 4) live bus arrivals (Daejeon open API); 5) split photos/data into external files for caching.

## Rules for AI continuing this work
Keep three languages in sync. Never invent building data; mark unknowns. Do not put tokens, admin URLs or personal data in the repo. Keep the OSM attribution.
