# Multan satellite hotspot dashboard

A static Leaflet map for exploring bundled satellite fire detections around Multan, with seasonal replay, layer controls, fire radiative power (FRP) styling and CSV export.

[Portfolio case study](https://musab-shahid-earth-observation.brinycourt4.chatgpt.site/projects/multan-hotspot-dashboard.html)

## Data status and interpretation

The application reads local JSON files for a 2025 season and an early-October 2026 snapshot. It **does not fetch a live feed**. Historical “live” labels in the interface refer to that saved snapshot, not continuously updated observations.

A satellite thermal detection alone does not prove crop-residue burning, identify a unique fire event, measure burned area or establish human exposure. FRP classes are display choices. Boundary provenance and complete extraction/deduplication metadata need further documentation.

## Files

| File | Role |
| --- | --- |
| [index.html](index.html) | Leaflet application, styling and interactions |
| [pts_compact.json](pts_compact.json) | 2025 compact records: latitude, longitude, day offset, FRP, satellite index, confidence |
| [p26.json](p26.json) | 2026 snapshot records |
| [bnd.json](bnd.json) | Boundary geometry |

The 2025 day offset is relative to 1 October 2025. Satellite indices in the application map to SNPP, N20 and N21. The source's top-level numeric counters should be checked against the data before reuse.

## Run locally

From this directory:

```sh
python -m http.server 8000
```

Open `http://localhost:8000/`. Serving over HTTP is needed for JSON fetches. Leaflet and Esri basemap tiles require an internet connection. No JavaScript build step is required.

The configured GitHub Pages destination, if enabled, is https://musab-shahid.github.io/multan-hotspot-dashboard/ . Its deployment was not independently verified in this documentation pass.

## Next improvements

Replace outdated live terminology; document source dates, coverage and filtering; test map interaction and CSV export on mobile and desktop; add independent evidence before labeling detections as residue-burning events.
