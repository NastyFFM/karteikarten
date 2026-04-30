# Progress — Initial MVP

## Status: [x] done

| Schritt | Status | Notiz |
|---------|--------|-------|
| 1. Datenmodell | [x] done | decks[] mit cards[], box-system, stats |
| 2. Persistenz (saveData/loadData) | [x] done | API-First + localStorage Fallback |
| 3. UI-Struktur (View-Switching) | [x] done | home/deck/study + Modals |
| 4. Spaced Repetition (Leitner) | [x] done | Box 1-5, Intervalle 1/2/4/8/16 Tage |
| 5. Lernmodus | [x] done | Shuffle, Flip, Gewusst/Nicht-gewusst, Session-Stats |
| 6. Backup Export/Import | [x] done | JSON Download + Upload mit Validierung |
| 7. Styling (Dark, CSS-Vars, Responsive) | [x] done | --bg --bg-card --teal --border etc. |
| 8. PulseOS SDK Integration | [x] done | onInput('data') importiert Decks, onDataChanged reload, emit('state') |

## Acceptance Criteria — alle erfuellt
- [x] Hauptansicht mit Deck-Liste + Karten-Anzahl + faellige
- [x] Deck CRUD (erstellen, bearbeiten, loeschen)
- [x] Karten CRUD (front/back)
- [x] Lernmodus mit Flip + Gewusst/Nicht-gewusst
- [x] Leitner Box 1-5 mit Intervallen
- [x] Faellige Karten gefiltert nach lastReview + intervalDays
- [x] Footer-Statistik (Decks, Karten, faellig, Trefferquote)
- [x] Backup Export + Import
- [x] localStorage Fallback ohne Server
- [x] CSS-Variablen
- [x] Responsive (Mobile media query)

## Naechste Schritte (V2 ideen)
- Bilder/Audio auf Karten
- Tags + Suche
- Statistik-Charts ueber Zeit
- Cloze deletion
- Sync ueber WebRTC zwischen Geraeten
