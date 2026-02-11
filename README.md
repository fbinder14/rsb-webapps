# RSB Webapps

Management-Dashboard für interaktive Lern-Apps der Realschule Bobingen. Die Anwendung ermöglicht es Lehrkräften, kleine HTML/CSS/JS-Web-Apps direkt im Browser zu erstellen, zu bearbeiten und über GitHub Pages bereitzustellen — ohne Backend, ohne Build-System.

## Features

- **Code-Editor** — CodeMirror 5 mit Syntax-Highlighting (HTML, CSS, JS) und Dracula-Theme
- **Live-Vorschau** — Sandboxed Iframe zur direkten Vorschau vor dem Deployment
- **Ein-Klick-Deploy** — Veröffentlichung auf GitHub Pages über die GitHub REST API
- **App-Verwaltung** — Bestehende Apps bearbeiten, löschen und mit Metadaten versehen
- **Suche & Filter** — Volltextsuche, Filter nach Fach und Kategorie, 6 Sortieroptionen
- **Ordner-Ansicht** — Gruppierung der Apps nach Kategorien mit aufklappbaren Ordnern
- **QR-Codes** — Generierung von QR-Codes für jede App zum Teilen im Unterricht
- **KI-Beschreibungen** — Automatische Metadaten-Generierung (Fach, Stufe, Beschreibung) via Claude API

## Technologie

| Komponente | Technologie |
|---|---|
| Frontend | Vanilla JavaScript, Custom CSS |
| Editor | CodeMirror 5.65 |
| QR-Codes | QRCode.js 1.0 |
| KI (optional) | Anthropic Claude API |
| Hosting | GitHub Pages |
| Datenverwaltung | GitHub REST API |

Kein Build-Prozess, keine Abhängigkeiten, kein Backend — eine einzige `index.html` plus eine `descriptions.json` für die Metadaten.

## Projektstruktur

```
rsb-webapps/
├── index.html          # Dashboard (Single-Page-App)
├── descriptions.json   # Metadaten aller Apps (Fach, Stufe, Kategorie, Beschreibung)
├── apps/               # Bereitgestellte Lern-Apps (HTML-Dateien)
│   ├── tetris.htm
│   ├── banking.htm
│   └── ...
└── README.md
```

## Einrichtung

1. **Repository forken** oder ein eigenes erstellen
2. **GitHub Pages aktivieren** (Settings → Pages → Branch `main`)
3. Dashboard öffnen und über das **Zahnrad-Symbol** konfigurieren:
   - **GitHub-Benutzername**
   - **Repository-Name** (Standard: `rsb-webapps`)
   - **Personal Access Token** — Fine-grained Token mit `Contents: Read and write`-Berechtigung für das Repository
   - **Anthropic API Key** (optional) — für die automatische KI-Beschreibung

### GitHub Token erstellen

1. [GitHub Settings → Developer Settings → Fine-grained Tokens](https://github.com/settings/tokens?type=beta)
2. Token-Name und Ablaufdatum vergeben
3. Unter **Repository access** nur dieses Repository auswählen
4. Unter **Permissions → Repository permissions** → `Contents` auf `Read and write` setzen
5. Token generieren und im Dashboard eintragen

## Nutzung

### App erstellen

1. Dateiname eingeben (ohne `.html`)
2. HTML/CSS/JS im Editor schreiben
3. Optional: Vorschau anzeigen
4. **Deploy** klicken — die App ist sofort unter `https://<user>.github.io/<repo>/apps/<dateiname>.html` erreichbar

### App bearbeiten

In der App-Liste auf **Bearbeiten** klicken → der Code wird im Editor geladen und kann nach Änderung erneut deployed werden.

### Metadaten pflegen

Jede App kann mit folgenden Metadaten versehen werden:

| Feld | Beschreibung | Beispiel |
|---|---|---|
| Fach | Unterrichtsfach | Mathematik |
| Stufe | Jahrgangsstufe(n) | 7–9 |
| Kategorie | Thematische Einordnung | Naturwissenschaften |
| Beschreibung | Kurzbeschreibung | Interaktive Bruchrechnung mit Visualisierung |

Über den Button **KI-Beschreibung** können alle Felder automatisch aus dem Quellcode generiert werden.

### Kategorien

BWR, Wirtschaft & Recht, Mathematik, Englisch, Französisch, Deutsch, Naturwissenschaften, Geographie, Sport, Informatik, Tools, Sonstiges

## Lizenz

Dieses Projekt ist für den internen Schulgebrauch der Realschule Bobingen bestimmt.
