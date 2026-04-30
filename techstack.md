# Tech Stack — Karteikarten

## Project Type
Standalone App — eigenes Git-Repo neben PulseOS

## Allowed
- Vanilla ES6+ JavaScript
- Everything in ONE index.html (HTML + CSS + JS)
- PulseOS SDK: <script src="/sdk.js"></script>
- CSS variables: var(--bg), var(--text), var(--teal), var(--border), var(--bg-card), var(--text-dim)
- Node.js built-ins only server-side (http, fs, path, crypto)

## Forbidden
- No npm, no node_modules, no build tools
- No frontend frameworks (React, Vue, Angular)
- No separate .js/.css files for PulseOS apps

## manifest.json Required Fields
name, icon, color, description, inputs, outputs, dataFiles

## Data API
- Read: GET /app/karteikarten/api/<file>
- Write: PUT /app/karteikarten/api/<file>

## Standalone-Faehigkeit (PFLICHT)
Jede App MUSS auch ohne PulseOS-Server funktionieren (GitHub Pages).

### Daten-Persistenz
- Primaer: PulseOS API (fetch /app/.../api/...)
- Fallback: localStorage (key: pulseos-app-karteikarten)
- Immer try/catch: API zuerst, bei Fehler localStorage

### Backup Export/Import (PFLICHT)
Jede App braucht:
- downloadBackup() — App-Daten als JSON herunterladen
- uploadBackup() — JSON hochladen und wiederherstellen
- UI-Buttons dafuer (z.B. im Footer oder Settings-Bereich)
- Dateiname: karteikarten-backup-YYYY-MM-DD.json
