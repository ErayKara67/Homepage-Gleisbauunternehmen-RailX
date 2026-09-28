# Handoff: Hero-Bereich Variante 4a („Unteres Drittel")

## Überblick
Der Hero auf `index.html` soll das Titelfoto in voller Helligkeit zeigen. Statt der Ellipse um den Text wird nur der **untere Rand des Bildes** abgedunkelt. Der gesamte Text sitzt im unteren Drittel. Himmel, Bahnhof, Zug, Team und Weiche bleiben frei.

Außerdem gibt es drei Inhaltsänderungen:
- **Lead-Text:** Er beginnt jetzt mit „Präqualifiziertes Fachunternehmen …“.
- **Rot:** Überall wird das Signalrot `#E10613` verwendet, auch für „aufs Gleis.“ und die Kennzahlen-Zeichen.
- **Kennzahl:** Aus „10+ Jahre“ wird „20+ Jahre“.

## Über die Design-Dateien
Die Dateien in `referenz/` sind **Design-Referenzen in HTML**. Sie sind kein Produktionscode. Nachgebaut wird in der bestehenden `index.html` (reines HTML/CSS, keine Frameworks), mit den vorhandenen Klassen und CSS-Variablen.

- **Öffnen:** `referenz/Hero Varianten Runde 4.dc.html` im Browser öffnen und zum Abschnitt **4a** scrollen.
- **Rahmen:** Er ist in drei Rahmen dargestellt: Desktop 1440×900, Tablet hochkant 834×1112 und Handy 390×844.

## Fidelity
**High-Fidelity.** Maße, Farben und Schriftgrößen unten sind final und sollen 1:1 übernommen werden.

## Nicht ändern
- **Header:** `.header`, Navigation, Burger und Logo-Größen bleiben wie sie sind.
- **Kennzahlen-Band:** `.kennzahlen-band` und `.hero-stats` bleiben in Aufbau, Abständen und Kacheln. Nur die zwei Punkte unter „Inhalt“ ändern sich.
- **Übrige Seite:** Alle Abschnitte ab `#leistungen` bleiben unverändert.
- **Bilder und Metadaten:** Bilddateien, `alt`-Texte, JSON-LD und Meta-Descriptions bleiben unverändert.

## Inhalt (exakt)
- **Eyebrow:** `Weichenbau · Gleis- & Oberbau · Instandhaltung`. Sie bleibt unverändert.
- **H1:** `Wir bringen Ihr Projekt` + Umbruch + `<em>aufs Gleis.</em>`.
  - Desktop und Tablet: **2 Zeilen**.
  - Handy (≤560px): **3 Zeilen** („Wir bringen / Ihr Projekt / aufs Gleis.“).
- **Lead:** `Präqualifiziertes Fachunternehmen für Eisenbahninfrastruktur: Weichenerneuerungen, Schienenarbeiten, Gleis- und Oberbauarbeiten sowie Instandhaltung — auch unter laufendem Betrieb.`
- **Buttons:** `Projekt anfragen` (primär, mit Pfeil) und `Leistungen ansehen` (ghost). Sie bleiben unverändert.
- **Kennzahl 1:** `20+` / `Jahre Branchen­erfahrung`. Vorher stand dort 10+.

## Farben
| Zweck | Wert |
|---|---|
| Signalrot: Buttons, `h1 em`, `.stat-num span`, Eyebrow-Strich | `#E10613` (`--railx-orange`) |
| Nachtblau | `#1a1f2e` (`--railx-dark`) |
| Lead auf Foto | `rgba(255,255,255,.86)` |
| Lead unter dem Foto (nur Handy) | `rgba(255,255,255,.8)` |
| Ghost-Button-Rahmen im Hero | `rgba(255,255,255,.45)` |

`--railx-orange-hell` (#FA404B) wird im Hero und in den Kennzahlen **nicht mehr** verwendet. Das ist eine bewusste Entscheidung des Kunden. Die Kommentare zur 3:1-Messung im CSS müssen entsprechend angepasst werden.

## Layout je Breite

### Desktop (≥1100px), Referenz 1440×900
- **`.hero`:** `min-height:100vh`, `align-items:flex-end`, `padding:146px 0 56px`.
- **Bild:** `.hero-bg img` mit `object-position:center 55%` (wie bisher).
- **Abdunklung:** Nur unten. `.hero-bg::after` hat `top:auto; bottom:0; height:420px`:
  `linear-gradient(0deg, rgba(26,31,46,.94) 0%, rgba(26,31,46,.74) 42%, rgba(26,31,46,0) 100%)`.
- **`.hero-content`:** Innerhalb von `.wrap` (1200px): `max-width:none; display:grid; grid-template-columns:640px minmax(0,1fr); gap:56px; align-items:end`.
  - **Linke Spalte:** Eyebrow (`margin-bottom:16px`) und H1.
  - **Rechte Spalte:** Lead und Buttons.
- **H1:** `font-size:64px; line-height:1.02`, weiß, `em` in `#E10613`.
- **Lead:** `font-size:16.5px; line-height:1.6; max-width:none; margin-top:0`.
- **Buttons:** `margin-top:24px; gap:12px`, je `padding:15px 22px; white-space:nowrap`. Beide müssen in einer Zeile stehen.
- **Kennzahlen-Band:** Folgt direkt unter dem Hero, unverändert (4 Spalten).

### Tablet (561–1099px), Referenz 834×1112
- **Bild:** `hero-railx-mobile.jpg` (Hochformat), `object-position:center 40%`.
  - `<source media>` wird erweitert, damit auch Tablets hochkant über 820px das Hochformat bekommen:
    `media="(max-width:820px), (max-width:1099px) and (orientation:portrait)"`.
- **Abdunklung:** `height:540px`:
  `linear-gradient(0deg, rgba(26,31,46,.95) 0%, rgba(26,31,46,.78) 45%, rgba(26,31,46,0) 100%)`.
- **`.hero`:** `align-items:flex-end`, `padding-bottom:52px`.
  - Die Mindesthöhe bleibt: `100svh` ab ≤820px, sonst `100vh`.
- **`.hero-content`:** Einspaltig, gestapelt: Eyebrow (`margin-bottom:16px`), H1, Lead, Buttons.
- **H1:** `font-size:clamp(2.75rem, 7.6vw, 4rem); line-height:1.02` (64px bei 834px), 2 Zeilen.
- **Lead:** `margin-top:18px; font-size:17px; line-height:1.6; max-width:620px`.
- **Buttons:** `margin-top:28px; gap:12px`, je `padding:15px 30px`, nebeneinander.
- **Kennzahlen-Band:** Darunter, 2×2 (wie bisher ab ≤900px).

### Handy (≤560px), Referenz 390×844
- **Bild:** Hochformat, `object-position:center 40%`.
- **Abdunklung:** `height:420px`:
  `linear-gradient(0deg, rgba(26,31,46,.96) 0%, rgba(26,31,46,.8) 48%, rgba(26,31,46,0) 100%)`.
- **`.hero`:** `min-height:100svh`, `align-items:flex-end`, `padding-bottom:28px`.
- **Eyebrow:** `display:flex; align-items:flex-start; font-size:11px; letter-spacing:.14em; line-height:1.5; margin-bottom:12px`.
  - Der Strich (`::before`) hat `width:22px; flex:none; margin-top:7px`.
- **H1:** `font-size:44px; line-height:1.02`, **3 Zeilen**. Dafür gibt es einen zusätzlichen `<br class="br-handy">` nach „Wir bringen“, der nur ≤560px sichtbar ist.
- **Buttons:** Untereinander, volle Breite, `margin-top:24px; gap:10px; padding:14px 20px`.
- **Lead im Hero:** Wird **ausgeblendet**. Derselbe Text steht stattdessen als eigener Absatz direkt unter dem Hero, **vor** der roten Oberkante der Kennzahlen:
  - Hintergrund `#1a1f2e`, `padding:28px 24px 30px`, `font-size:16px; line-height:1.6`, Farbe `rgba(255,255,255,.8)`.
  - Umsetzung: `<p class="hero-lead-unten">` im `.kennzahlen-band` vor `.hero-stats`. Er ist standardmäßig `display:none`, bei ≤560px sichtbar; gleichzeitig ist `.hero .hero-lead` bei ≤560px `display:none`.
- **Kennzahlen:** 2×2, unverändert.

## Sonstiges
- **`svg.rails`:** Das Gleisraster im Hero entfällt. Es ist in der Referenz nicht enthalten.
- **Radiale Ellipsen:** Die radialen Ellipsen in `.hero-bg::after` (inkl. der Regeln für 1199px und 820px) werden durch die obigen Verläufe ersetzt.
- **Buttons:** Hover und Übergänge bleiben wie in `.btn-primary` / `.btn-ghost`.

## Assets
Die folgenden Dateien liegen alle bereits im Repo:
- **Bilder:** `hero-railx.jpg`, `hero-railx-mobile.jpg`
- **Logos:** `logo-railx-invers.png`, `logo-railx.png`
- **Schriften:** `fonts/*` (Barlow Condensed 500/600/700, Inter 400–700)

## Dateien
- `screenshots/4a-desktop-1440.png`, `screenshots/4a-tablet-834.png`, `screenshots/4a-handy-390.png` (2x): Soll-Zustand je Breite inkl. Kennzahlen-Band — zum direkten Vergleich mit dem Ergebnis.
- `referenz/Hero Varianten Runde 4.dc.html`: alle Varianten. **4a** ist die gewählte.
- `referenz/Hero Kopfzeile.dc.html` und `referenz/Hero Kennzahlen.dc.html`: Teilbausteine der Referenz.
- `PROMPT.md`: fertiger Prompt für Claude Code.
