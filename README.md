[README_landingpage.md](https://github.com/user-attachments/files/31616422/README_landingpage.md)
# RailX GmbH – Unternehmens-Website

Website für ein Gleisbau- und Bahninfrastrukturunternehmen aus Herne. Statisch gebaut,
ohne Framework und ohne Build-Schritt – dafür schnell, wartbar und ohne laufende Abhängigkeiten.

**Live:** [railx-gleisbau.de](https://railx-gleisbau.de/)

---

## Über das Projekt

RailX führt Arbeiten an Gleisanlagen und Bahninfrastruktur durch, teilweise unter laufendem
Eisenbahnbetrieb. Die Website richtet sich an Auftraggeber aus dem Bahnumfeld und muss vor
allem zwei Dinge leisten: das Leistungsspektrum klar zeigen und Vertrauen über Referenzen
aufbauen. Entsprechend ist die Seite als eine durchgehende Landingpage aufgebaut, die von der
Leistungsübersicht über Referenzprojekte bis zum Kontakt führt.

Konzeption, Gestaltung und Umsetzung stammen von mir.

## Warum kein Framework

Die Seite besteht aus drei Dokumenten und braucht weder Routing noch Zustandsverwaltung.
Ein Framework hätte hier nur Build-Werkzeug, Abhängigkeiten und Update-Aufwand hinzugefügt,
ohne etwas zu lösen. Die Entscheidung war bewusst: HTML, CSS und etwas JavaScript, versionierte
Schriften im Repository und ein Deployment, das ohne Node-Umgebung auskommt.

## Aufbau

```
index.html              Startseite: Leistungen, Referenzen, Kontakt
impressum.html          Impressum
datenschutz.html        Datenschutzerklärung
fonts/                  lokal eingebundene Schriften (kein externer Request)
logo-railx.png          Logo
logo-railx-invers.png   Logo für dunkle Flächen
hero-railx.jpg          Hero-Bild Desktop
hero-railx-mobile.jpg   Hero-Bild Mobil
CNAME                   eigene Domain für GitHub Pages
.github/workflows/      Deployment bei jedem Push auf main
```

## Inhalte

Sieben Leistungsbereiche: Weichenerneuerung und -umbau, Schienenwechsel und Schienenarbeiten,
Gleis- und Oberbauarbeiten, Instandhaltung und Wartung, Bahninfrastruktur (Kabeltiefbau,
Entwässerung, Bahnsteige), Vegetationsarbeiten sowie Winterdienst.

Referenzprojekte: Bahnhof Remscheid, FZI Werk Paderborn, Bahnhof Gremberg und
Bahnhof Mönchengladbach.

## Technische Entscheidungen

**Schriften liegen im Repository.** Keine Einbindung über Google Fonts – das spart einen
externen Request, vermeidet eine datenschutzrechtliche Fragestellung und macht die Seite
unabhängig von einem fremden CDN.

**Zwei Hero-Bilder statt eines skalierten.** Für Mobilgeräte wird ein eigener Zuschnitt
ausgeliefert, damit auf schmalen Displays kein Bildinhalt verloren geht und keine unnötig
großen Dateien übertragen werden.

**Deployment über GitHub Actions.** Jeder Push auf `main` veröffentlicht die Seite über
GitHub Pages. Die Domain ist über die `CNAME`-Datei angebunden. Kein manuelles Hochladen,
kein FTP, keine Abweichung zwischen Repository und Live-Stand.

## Lokal starten

Die Seite braucht keinen Build. `index.html` lässt sich direkt im Browser öffnen. Für
saubere relative Pfade empfiehlt sich ein kleiner Server:

```bash
python3 -m http.server 8000
# http://localhost:8000
```

## Rechtliches

Impressum und Datenschutzerklärung liegen als eigene Seiten vor und sind aus dem Footer
verlinkt. Inhaltlich verantwortet sie das Unternehmen.

---

Umsetzung: **Eray Kara**
