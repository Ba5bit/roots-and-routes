# Roots & Routes

Roots & Routes is a static interactive travel guide for exploring Sha Tin and Tai Po through a lower-impact, public-transport-friendly itinerary. The site combines a landing page, an interactive Leaflet map, detailed stop pages, photo galleries, multilingual audio guides, route to-do lists, and optional 360 panorama views.

## Project Overview

This is a client-side web app with no backend and no build step. It is written with HTML, CSS, and vanilla JavaScript modules.

- `index.html` defines the page structure, including the landing page, map view, desktop drawers, mobile utility sheet, stop detail page, lightbox, and panorama viewer.
- `style.css` handles the visual design, responsive layout, overlays, drawers, map controls, stop page, lightbox, and panorama viewer styling.
- `app.js` is now a small bootstrap file that wires together the app modules.
- `scripts/app/` contains the interactive app logic split by responsibility.
- `scripts/data/` contains itinerary, category, and audio-guide data.
- `scripts/map/` contains Leaflet marker icon helpers.
- `assets/` stores icons, photos, 360 panoramas, and multilingual audio files.

## Highlights

- Two curated route views:
  - Day 1 focuses on Tai Po, including public transport transfers, heritage stops, and optional add-ons.
  - Day 2 focuses on Sha Tin, including museum, temple, promenade, shopping, and walking-based exploration.
- Interactive Leaflet map with category-based markers and filters.
- Suggested itinerary panels for both desktop and mobile.
- Personal route to-do list stored in `localStorage`.
- Stop detail pages with route guidance, sustainability notes, estimated footprint text, photo galleries, audio guides, and 360 panorama views.
- Responsive experience with desktop drawers and a mobile utility sheet.

## Tech Stack

- HTML5
- CSS3
- Vanilla JavaScript modules
- [Leaflet](https://leafletjs.com/) for interactive maps
- CARTO Voyager raster tiles with OpenStreetMap attribution
- Google Fonts for typography

## Running Locally

Because the app uses JavaScript modules, run it through a local static server instead of opening `index.html` directly from the filesystem.

### Python

```powershell
python -m http.server 8000
```

### Node

```powershell
npx serve .
```

Then open the URL shown by the server, usually:

```text
http://localhost:8000
```

## Project Structure

```text
roots-and-routes/
|-- .github/
|   `-- workflows/
|       `-- static.yml
|-- assets/
|   |-- icons/
|   |-- photos/
|   |   `-- 360/
|   `-- sounds/
|       |-- cn/
|       |-- ct/
|       `-- en/
|-- scripts/
|   |-- app/
|   |   |-- audio-guide.js
|   |   |-- day-utils.js
|   |   |-- dom.js
|   |   |-- drawers.js
|   |   |-- landing.js
|   |   |-- legend.js
|   |   |-- map-controller.js
|   |   |-- map-ui.js
|   |   |-- media.js
|   |   |-- mobile-utility.js
|   |   |-- state.js
|   |   |-- stop-page.js
|   |   `-- todo.js
|   |-- data/
|   |   |-- audio-guides.js
|   |   |-- categories.js
|   |   `-- itinerary.js
|   `-- map/
|       `-- icons.js
|-- app.js
|-- index.html
|-- style.css
`-- README.md
```

## Module Guide

- `scripts/app/state.js` creates shared application state.
- `scripts/app/map-controller.js` initializes Leaflet, renders markers, switches days, and opens stops.
- `scripts/app/map-ui.js` binds map buttons, drawer buttons, and tooltip to-do actions.
- `scripts/app/stop-page.js` renders stop detail content and controls stop page opening/closing.
- `scripts/app/media.js` handles photo galleries, lightbox behavior, and 360 panorama viewer behavior.
- `scripts/app/legend.js` manages category filters and legend rendering.
- `scripts/app/todo.js` manages saved route to-do items in `localStorage`.
- `scripts/app/landing.js` renders landing-page route previews and landing interactions.
- `scripts/app/mobile-utility.js` controls the mobile filter/to-do/suggested sheet.
- `scripts/app/audio-guide.js` renders multilingual audio guide tabs and players.

## Deployment

The repository includes a GitHub Actions workflow at `.github/workflows/static.yml` that deploys the full static site to GitHub Pages whenever changes are pushed to the `main` branch.

## Notes for Future Development

- Route content lives in `scripts/data/itinerary.js`.
- Category labels, legend ordering, and footprint fallback text live in `scripts/data/categories.js`.
- Audio guide file mappings live in `scripts/data/audio-guides.js`.
- External assets such as Leaflet, map tiles, and Google Fonts require an internet connection.
- If the itinerary grows further, the data modules could be converted to JSON or generated from a spreadsheet.
