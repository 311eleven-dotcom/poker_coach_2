# Poker Coach PWA – Deployment Guide

## Dateien
```
poker-pwa/
├── public/
│   ├── index.html      ← Die gesamte App
│   ├── manifest.json   ← PWA-Konfiguration
│   ├── sw.js           ← Service Worker (Offline-Support)
│   └── icons/
│       ├── icon-192.png
│       └── icon-512.png
└── vercel.json         ← Vercel-Konfiguration
```

---

## Deployment auf Vercel (kostenlos, ~5 Minuten)

### Option A – Via GitHub (empfohlen)

1. **GitHub Account** erstellen falls noch nicht vorhanden: https://github.com
2. **Neues Repository** erstellen (z.B. `poker-coach`)
3. **Dateien hochladen**: Den gesamten `poker-pwa` Ordner in das Repository
4. **Vercel Account** erstellen: https://vercel.com (kostenlos, mit GitHub anmelden)
5. **"New Project"** → GitHub Repository auswählen → **Deploy**
6. Fertig — du bekommst eine URL wie `https://poker-coach-xxx.vercel.app`

### Option B – Via Vercel CLI

```bash
npm install -g vercel
cd poker-pwa
vercel --prod
```

---

## App auf iPhone installieren

1. URL in **Safari** öffnen (nicht Chrome — nur Safari unterstützt PWA auf iOS)
2. Unten auf das **Teilen-Symbol** tippen (Quadrat mit Pfeil nach oben)
3. **"Zum Home-Bildschirm"** auswählen
4. Name bestätigen → **Hinzufügen**

Die App erscheint jetzt als Icon auf deinem Home-Screen und öffnet sich wie eine native App (ohne Browser-UI, Vollbild).

---

## Sprachaufnahme einrichten

Die App nutzt die **Web Speech API** von Safari/iOS.

- Beim ersten Tippen auf "Gedanken aufnehmen" fragt iOS nach **Mikrofon-Erlaubnis** → Erlauben
- Sprache wird **on-device** transkribiert (kein externer Service)
- Funktioniert auf Deutsch (`de-DE`)

Falls Mikrofon nicht verfügbar: Text wird nicht automatisch transkribiert, aber die Hand-Situation wird trotzdem an Claude gesendet.

---

## API-Key für automatische Analyse

Damit die KI-Analyse direkt in der App funktioniert:

1. **Anthropic API-Key** holen: https://console.anthropic.com
2. In der App: Eine Aktion ausführen (Fold/Call/Raise)
3. Im erscheinenden Dialog den API-Key eingeben
4. Key wird **lokal auf dem Gerät** gespeichert (localStorage)

**Kosten**: Jede Hand-Analyse kostet ca. 0.002–0.005 USD (sehr wenig).

> **Sicherheitshinweis**: Der API-Key wird nur auf deinem Gerät gespeichert und nur für Anfragen an api.anthropic.com verwendet. Er wird nie an andere Server gesendet.

---

## Funktionen

- ♠ Randomisierte Hand-Szenarien (Hand, Position, Stack, Spielertypen)
- ♣ 9 Spielerarchetypen mit realistischen VPIP/PFR/AF Stats
- ♥ Positionsbasierte Entscheidungslogik (Open, Facing Raise, Facing 3-Bet)
- ♦ Denkprozess-Checkliste (5 Punkte)
- 🎤 Sprachaufnahme mit Web Speech API
- 🤖 KI-Analyse via Claude (Sizing, Ranges, Spielertypen, Denkprozess)
- 📊 Skill-Tracking über Sessions
- 📝 Hand-Verlauf mit Scores
- 🌙 Dark Mode Support
- 📱 Offline-fähig (Service Worker)
