# Datacom Software Development Job Simulation - Cinema Finder

[![React](https://img.shields.io/badge/React-18.2.0-blue.svg)](https://reactjs.org/)
[![Material UI](https://img.shields.io/badge/MUI-v5.11-007FFF.svg)](https://mui.com/)
[![MapLibre GL](https://img.shields.io/badge/MapLibre_GL-v2.4-blueviolet.svg)](https://maplibre.org/)
[![Leaflet](https://img.shields.io/badge/Leaflet-v1.9-green.svg)](https://leafletjs.com/)
[![Turf.js](https://img.shields.io/badge/Turf.js-Geospatial-orange.svg)](https://turfjs.org/)

An interactive web application developed as part of the **Datacom Software Development Job Simulation** on Forage. The Cinema Finder allows users to explore cinema locations across Australia and New Zealand, filter by franchise chains, dynamically switch between mapping engines, and locate the nearest cinemas using geospatial analysis.

---

## 🌟 Key Features

- **Dual Mapping Engine Support**:
  - Seamlessly switch between **MapLibre GL** (vector-based with MapTiler) and **Leaflet** (raster tile-based).
  - Preserves user preference locally across sessions via persisted state.
- **Geospatial Distance & Nearest Cinemas**:
  - Leverages browser Geolocation API and **Turf.js** (`@turf/distance`) to calculate distances between user coordinates and cinema locations.
  - Automatically identifies and ranks the top 15 nearest cinemas.
- **Comprehensive AU & NZ Cinema Data**:
  - Combines and validates cinema datasets across Australia (`auCinemas.json`) and New Zealand (`nzCinemas.json`).
  - Real-time country-level and franchise-level cinema counts.
- **Franchise Filtering & Interactive Navigation**:
  - Filter cinemas by franchise (Event Cinemas, Hoyts, Village Cinemas, Reading Cinemas, Dendy, independent chains).
  - Interactive sidebar: clicking any cinema triggers smooth fly-to camera animations (`map.snapTo` custom event listener) directly on the active map.
- **Optimized Performance**:
  - Utilizes `@loadable/component` for dynamic imports and code-splitting, isolating MapLibre and Leaflet bundles for efficient initial load times.
- **Modern Responsive UI**:
  - Designed with **Material UI (MUI v5)**, including responsive side navigation, clean typography, badge chips, and snackbar notifications via `notistack`.

---

## 🛠️ Tech Stack

| Category | Technologies |
|---|---|
| **Frontend Framework** | React 18, React Router v5 |
| **UI & Styling** | Material UI (MUI v5), Emotion, React Icons |
| **Mapping Libraries** | MapLibre GL, react-map-gl, Leaflet, react-leaflet |
| **Geospatial Calculations** | Turf.js (`@turf/distance`, `@turf/helpers`) |
| **Utilities & State** | Lodash, use-persisted-state, @use-it/event-listener, Notistack |
| **Testing** | Jest, React Testing Library |

---

## 📋 Simulation Tasks Overview

1. **Task 1: Project Setup & Codebase Familiarization**
   - Configured React environment and reviewed component hierarchy, routing, and data structures.
2. **Task 2: Data Aggregation & Breakdown Logic**
   - Implemented country-code tagging, franchise matching, and aggregation logic in `src/data/cinemas.js` and `src/data/franchises.js` with passing unit tests.
3. **Task 3: Dual Map Integration & Camera Snapping**
   - Implemented map components for both MapLibre GL and Leaflet, wiring custom `map.snapTo` event listeners to fly to selected cinema coordinates.
4. **Task 4: Geolocation & Distance Calculation**
   - Developed `useNearbyCinemas` hook in `src/data/nearbyCinemas.js` using Turf.js distance computations and geolocation positioning.

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/en/) (v16+ recommended)
- [npm](https://www.npmjs.com/) or [yarn](https://yarnpkg.com/)

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/agk7803/<repo-name>.git
   cd <repo-name>
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

### Running Locally

Start the local development server:
```bash
npm start
```
The application will open automatically at [http://localhost:3000](http://localhost:3000).

### Running Tests

Execute the unit tests (validates data breakdowns and counts):
```bash
npm test -- --watchAll=false
```

### Production Build

Create an optimized production build:
```bash
npm run build
```

---

## 📁 Project Structure

```text
├── public/                 # Static assets and HTML template
├── src/
│   ├── assets/             # Logos and icons
│   ├── components/
│   │   ├── CinemaList/     # Sidebar cinema list views & franchise filtering
│   │   ├── Map/            # Map wrapper, LeafletMap & MaplibreMap components
│   │   ├── AsideIndex.jsx  # Franchise overview & statistics
│   │   ├── CinemaMarkers.jsx # Markers for franchise cinema views
│   │   ├── NearbyCinemaMarkers.jsx # Markers for nearby cinema views
│   │   ├── TopBar.jsx      # Header with map engine selector
│   │   └── Layout.jsx      # Main application layout grid
│   ├── data/
│   │   ├── auCinemas.json  # Australian cinemas dataset
│   │   ├── nzCinemas.json  # New Zealand cinemas dataset
│   │   ├── cinemas.js      # Combined cinema data & country breakdown
│   │   ├── franchises.js   # Franchise definitions & matcher
│   │   └── nearbyCinemas.js# Turf.js distance calculation hook
│   ├── App.js              # Routing and loadable components
│   └── index.js            # Entry point
├── package.json
└── README.md
```

---

## 📄 Certificate & Attribution

- **Completion Certificate**: See [Datacom_Completion_Certificate.pdf](Datacom_Completion_Certificate.pdf) for the official certificate of completion.
- Built as part of the **Datacom Software Development Job Simulation** on [Forage](https://www.theforage.com/).
- Dataset and starter template provided by **Datacom**.
