# Initial MVP — Karteikarten

## Goal
Eine standalone Karteikarten-App fuer Schueler und Studenten zum Vokabel- und Faktenlernen mit einfachem Spaced-Repetition-System.

## App Type
Standalone Frontend-App, alles in einer index.html, deployt auf GitHub Pages oder PulseOS.

## Graph Ports (manifest.json)
- **inputs**: `data` — empfaengt externe Daten (z.B. Karten-Listen vom Graph)
- **outputs**: `state` — sendet aktuellen App-Zustand

## Data Files
- `state.json` — komplette App-State (Decks + Karten + Stats)

## User Stories
1. Als Schueler will ich **Stapel (Decks)** erstellen, um Karten thematisch zu gruppieren (z.B. "Englisch Klasse 9", "Bio Zellen").
2. Als Schueler will ich **Karten** mit Vorder- und Rueckseite hinzufuegen.
3. Als Schueler will ich **lernen** koennen: Karte sehen, umdrehen, gewusst/nicht-gewusst markieren.
4. Als Schueler will ich, dass schwierige Karten **oefter** drankommen (Spaced Repetition / Leitner-Box).
5. Als Schueler will ich Karten **bearbeiten und loeschen** koennen.
6. Als Nutzer will ich meine Daten als **Backup exportieren/importieren** koennen.
7. Die App soll **ohne Server** funktionieren (localStorage Fallback).

## Acceptance Criteria
- [x] Hauptansicht zeigt alle Decks mit Karten-Anzahl + Lernfortschritt
- [x] "+ Deck erstellen" mit Name + Beschreibung
- [x] Deck oeffnen → Karten-Liste + "Karte hinzufuegen" + "Lernen starten"
- [x] Karte hinzufuegen mit Vorder-/Rueckseite
- [x] Karte bearbeiten + loeschen
- [x] Lernmodus: Karte zeigt Vorderseite, Klick → Rueckseite, dann "Gewusst"/"Nicht gewusst"
- [x] Leitner-Box-System: Karten haben Level 1–5, Level 1 = jeden Tag, Level 5 = alle 16 Tage
- [x] "Gewusst" → Box +1, "Nicht gewusst" → Box auf 1 zurueck
- [x] Lernmodus zeigt nur Karten, die heute faellig sind (lastSeen + intervalDays)
- [x] Footer-Statistik: Total Karten, gelernt heute, Korrekt-Quote
- [x] Backup Export-Button (JSON Download) + Import-Button (JSON Upload)
- [x] localStorage Fallback wenn PulseOS API nicht erreichbar
- [x] CSS-Variablen statt hardcoded Farben
- [x] Responsive Design (Mobile + Desktop)

## Edge Cases
- Leere App (keine Decks) → Hinweistext + "Erstes Deck erstellen"
- Deck ohne Karten → "Keine Karten — Karte hinzufuegen"
- Lernmodus ohne faellige Karten → "Alle Karten gelernt heute! Komm morgen wieder."
- Ungueltiges Backup beim Import → Fehlermeldung, kein Datenverlust
- Sehr lange Texte auf Karten → CSS overflow + scrollbar

## Out of Scope (V1)
- Multimedia (Bilder/Audio auf Karten)
- Multi-User / Sync
- Tags / Filter / Suche
- Statistik-Charts
- Karten-Reihenfolge (manuell sortieren)
- Cloze deletion / Lueckentexte

## Stack Constraints
- Vanilla ES6+ JS in einer index.html
- CSS-Variablen: `--bg`, `--bg-card`, `--text`, `--text-dim`, `--teal`, `--border`, `--accent`
- PulseOS SDK: `onInput`, `emit`, `onDataChanged`
- Keine npm-Abhaengigkeiten, keine Frameworks
- localStorage Key: `pulseos-app-karteikarten`
