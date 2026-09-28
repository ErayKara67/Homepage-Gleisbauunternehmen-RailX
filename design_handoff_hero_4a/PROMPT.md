Setze in `index.html` den Hero-Bereich nach Variante 4a um. Die vollständige Spezifikation steht in `design_handoff_hero_4a/README.md`. Die visuelle Referenz ist `design_handoff_hero_4a/referenz/Hero Varianten Runde 4.dc.html`, Abschnitt „4a“. Übernimm alles 1:1: Maße, Farben, Schriftgrößen und Texte exakt wie im README.

Kurzfassung:
1. **Abdunklung:** Das Titelfoto bleibt hell. Die radialen Ellipsen in `.hero-bg::after` werden ersetzt durch einen Verlauf nur am unteren Rand:
   - Desktop: 420px hoch
   - Tablet: 540px hoch
   - Handy: 420px hoch
   - Genaue Werte im README.
2. **Text unten:** Der Hero-Text sitzt unten (`align-items:flex-end`).
   - Desktop ≥1100px: zweispaltig. Links stehen Eyebrow und H1 (64px, 2 Zeilen), rechts Lead und beide Buttons in einer Zeile.
   - 561–1099px: einspaltig gestapelt.
   - ≤560px: H1 in 44px über 3 Zeilen, Buttons untereinander. Der Lead-Absatz wird im Hero ausgeblendet und steht dafür direkt unter dem Hero, vor den Kennzahlen.
3. **Hochformat-Bild:** Das Hochformat-Bild gilt auch für Tablets hochkant bis 1099px: `<source media="(max-width:820px), (max-width:1099px) and (orientation:portrait)">`.
4. **Texte:**
   - Lead: „Präqualifiziertes Fachunternehmen für Eisenbahninfrastruktur: Weichenerneuerungen, Schienenarbeiten, Gleis- und Oberbauarbeiten sowie Instandhaltung — auch unter laufendem Betrieb.“
   - Erste Kennzahl: „20+“ statt „10+“.
5. **Rot:** Überall `#E10613` (`var(--railx-orange)`), auch für `.hero h1 em` und `.stat-num span`. `--railx-orange-hell` wird dort nicht mehr verwendet. Die CSS-Kommentare zum Kontrast müssen entsprechend angepasst werden.
6. **Gleisraster:** `svg.rails` im Hero wird entfernt.
7. **Nicht anfassen:** Header, Aufbau des Kennzahlen-Bands, alle Abschnitte ab `#leistungen`, Meta-Tags und JSON-LD.

Prüfe danach im Browser die Breiten 1440, 1280, 1024, 834 (hochkant), 768, 390 und 360 und vergleiche 1440/834/390 mit den Screenshots in `design_handoff_hero_4a/screenshots/`:
- H1 und Buttons dürfen nicht ungewollt umbrechen.
- Kein Text liegt auf dem hellen Bildbereich ohne Verlauf.
- Das Team und die Weiche im Foto bleiben sichtbar.
