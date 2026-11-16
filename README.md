# Woosong University 3D Campus Preview｜又松大學 3D 校園預覽｜우송대학교 3D 캠퍼스 미리보기

**Version 1.2 (2026-11-16)** · Live: https://joeyaj.github.io/woosong-3d-campus/

A single-file Three.js web page for prospective and new international students. It shows the West and East Campuses of Woosong University in 3D, built on real OpenStreetMap building footprints with the official floor counts.

## What it does
- 3D campus (West + East) with building labels, filters, search by building / major / amenity
- Arrival route (Daedong Station → South Gate → W16 → W7 → W1 → W3) with the mascot Sol-i walking around buildings (grid A* path-finding)
- Official photos, floor guide, dorm room preview (1/2/4-person)
- Bus & subway info per gate, with tips (lines from the university "Getting here" page)
- Four seasons and night mode, trilingual UI (中文 / 한국어 / English)
- Share link, QR code and iframe embed code; "My location" (GPS, HTTPS only)

## Run / host
No build step. Open `index.html`, or host the file on any HTTPS site. It loads Three.js r0.170 from jsDelivr.
Embed: `<iframe src="https://joeyaj.github.io/woosong-3d-campus/" width="100%" height="720" style="border:0" allow="geolocation; fullscreen"></iframe>`

## Docs
- [docs/PURPOSE.md](docs/PURPOSE.md) – why this exists, scope, audience
- [docs/DEVELOPMENT_LOG.md](docs/DEVELOPMENT_LOG.md) – how it was built, decisions, problems
- [HANDOFF.md](HANDOFF.md) – state, data map, how to update, known gaps

## Attribution
Map geometry © OpenStreetMap contributors, ODbL (https://www.openstreetmap.org/copyright). Photos, logo, floor guide, major and bus-line information come from the Woosong University website and remain the property of the university. This is an unofficial preview prepared by a staff member of the International Exchange Office, China Team, and is not an official university service. No license is granted for reuse of the code, photos or logo without permission.
