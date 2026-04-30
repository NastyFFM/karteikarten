# Plan — Initial MVP

## Schritte

### 1. Datenmodell festlegen
```js
{
  decks: [
    { id, name, description, created, cards: [
      { id, front, back, box: 1, lastReview: 0, correctCount: 0, wrongCount: 0 }
    ]}
  ],
  stats: { totalReviews: 0, correctReviews: 0, lastStudyDate: null }
}
```

### 2. Persistenz-Layer (saveData/loadData)
- API-First, localStorage-Fallback
- Storage-Key: `pulseos-app-karteikarten`

### 3. UI-Struktur (Single-Page-App, View-Switching)
- View `home` → Deck-Liste
- View `deck` → Karten-Liste eines Decks
- View `study` → Lernmodus (Karte vorne/hinten + Buttons)
- View `cardEdit` → Karte hinzufuegen/bearbeiten (Modal)
- View `deckEdit` → Deck erstellen/bearbeiten (Modal)

### 4. Spaced Repetition (Leitner)
- Box-Intervalle: 1=1d, 2=2d, 3=4d, 4=8d, 5=16d
- Faellig wenn `now - lastReview >= intervalDays`
- Neue Karten (lastReview=0) immer faellig

### 5. Lernmodus
- Liste faellige Karten shufflen
- Pro Karte: Vorderseite zeigen → Klick → Rueckseite
- Buttons: Gewusst (Box +1, max 5) / Nicht gewusst (Box = 1)
- Nach letzter Karte: "Fertig!" + zurueck zum Deck

### 6. Backup Export/Import
- Download JSON mit Datum im Filename
- Upload mit Validierung (decks Array vorhanden)
- Confirm-Dialog bei Import (ueberschreibt aktuelle Daten)

### 7. Styling
- Dark Theme via CSS-Vars
- Responsive: Karten max-width 600px zentriert, Mobile stack
- Karte umdrehen: CSS transform + Klick-Event

### 8. PulseOS SDK Integration
- `onInput('data', ...)` — Karten-Liste empfangen und mergen
- `emit('state', state)` bei jeder Aenderung
- `onDataChanged` → reload

## Files
- `index.html` — komplette App
- `manifest.json` — bleibt wie ist (inputs/outputs/dataFiles passen)
- `data/state.json` — initial `{}`, wird bei erstem Save befuellt

## Stack-Check
- [x] Vanilla JS only
- [x] Single index.html
- [x] CSS variables
- [x] PulseOS SDK
- [x] localStorage fallback
- [x] Backup buttons

## Reihenfolge
1. HTML-Geruest + CSS-Vars
2. Daten-Layer (loadData/saveData)
3. State + render() Funktion
4. Home-View (Deck-Liste)
5. Deck-Editor + Card-Editor
6. Lernmodus + Leitner-Logik
7. Backup-Buttons
8. SDK-Integration
9. Test + Commit
