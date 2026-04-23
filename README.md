# Poker Coach PWA v2 — Deployment Guide

## Was neu ist in v2
- **Komplette Hand-Simulation**: Preflop → Flop → Turn → River
- **Sprachaufnahme vor jeder Entscheidung**: App fragt aktiv nach deiner Einschätzung
- **Auswertung erst am Schluss**: Alle Entscheide werden nach der Hand gemeinsam analysiert
- **Spielertyp-Kürzel am Tisch**: LAG, NIT, REG, CS, FI, TAG, REC sichtbar ohne Tab-Wechsel
- **API-Key Fix**: Keine Validierung mehr — alle gültigen Keys werden akzeptiert
- **CORS-Fix**: Header `anthropic-dangerous-direct-browser-access: true` für Browser-Anfragen

---

## Deployment auf Vercel

### Existierendes Vercel-Projekt updaten (empfohlen)
1. ZIP herunterladen und entpacken
2. Dateien in dein bestehendes GitHub Repository kopieren (alte Dateien überschreiben)
3. Git commit & push → Vercel deployed automatisch

### Neu deployen
1. GitHub Repository erstellen
2. Alle Dateien hochladen
3. Vercel: New Project → Import → Deploy

---

## iPhone Installation
1. URL in **Safari** öffnen
2. Teilen-Symbol → "Zum Home-Bildschirm"
3. Fertig

---

## API-Key einrichten
1. Settings-Tab (⚙ oben rechts) öffnen
2. API-Key von https://console.anthropic.com eingeben
3. "Speichern" tippen
4. Key wird lokal gespeichert — grünes Häkchen bestätigt Speicherung

**Wichtig**: Der Key braucht keine spezielle Validierung mehr — gib ihn einfach so ein wie er ist.

---

## Spielablauf
1. **Sprachaufnahme**: Bevor du handelst, fragt die App nach deiner Einschätzung
   - Roten Knopf tippen → sprechen → nochmal tippen zum Stoppen
   - Automatischer Wechsel zur Aktionsauswahl
   - Oder "Überspringen" für direkte Aktion
2. **Aktion wählen**: Fold / Call / Raise mit Slider
3. **Nächste Strasse**: App simuliert Gegner-Reaktionen und zeigt nächste Karten
4. **Auswertung**: Nach River (oder Fold) erscheint die komplette KI-Analyse aller Entscheide

---

## Spielertyp-Kürzel am Tisch
- **LAG** = Loose Aggressive (Maniac)
- **NIT** = Nit / Super Nit
- **REG** = Aggro Reg
- **CS** = Calling Station
- **FI** = Passive Fish
- **TAG** = Tight Reg
- **REC** = Recreational
