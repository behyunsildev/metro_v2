# AGENTS.md - Development Guide

## Project Structure
- **Type**: Static HTML/JavaScript visualization project
- **Framework**: Vanilla JavaScript with D3.js v7.8.5 (CDN)
- **Purpose**: Seoul subway map with fisheye lens distortion effect

## Running the Project
- Open `index.html` directly in a browser, or
- Use any local HTTP server: `python3 -m http.server 8000` or `npx http-server`

## Code Style

### File Organization
- All code is in `index.html` (HTML, CSS, JavaScript)
- Station and connection data defined in JavaScript arrays
- `subway_data.json` contains raw data (not currently used in code)

### JavaScript Conventions
- Use `const` for all immutable variables (line color maps, station arrays, connections)
- Use `let` only for loop counters and truly mutable values
- Function names: camelCase (`applyFisheyeEffect`, `handleStationMouseOver`)
- Data structures: objects with properties (`{id, name, x, y, lines}`)

### D3.js Patterns
- Use method chaining for D3 operations
- Event handlers: `on("event", handler)`
- Transitions: `.transition().duration(800).ease(d3.easeCubicOut)`
- Line generators: `d3.line()` with curve interpolation

### Naming Conventions
- Station IDs: Korean names in hangul (e.g., "강남", "서울역")
- Line names: Full Korean names with "호선" suffix (e.g., "1호선", "신분당선")
- Functions: Descriptive verbs (draw, apply, handle, generate, subdivide)

## Modifying Station/Line Data
- Stations: Add to `stations` array with `{id, name, x, y, lines: []}`
- Connections: Add to `connections` array with `{line, path: [stationIds]}`
- Line colors: Update `lineColors` object with hex color codes
- Terminal stations: Update `getTerminalStations()` for line number badges
