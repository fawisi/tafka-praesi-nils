# Asset-Manifest — Praesi Nils 2026-04-24

Inventur der Assets fuer die scroll-story. Alles, was in der Praesi am Ende sichtbar ist, landet in diesem Ordner.

**Visuelle Leitquelle:** FM-Praesi v4 — `/Users/fabianwillisimon/Documents/Claude_Code/FM_Präsi/index.html` ("Bauhaus / Aicher / Tegel TXL"). Tokens sind aus dieser Praesi in `../tokens-snapshot-2026-04-24.css` extrahiert.

## 1 — Status quo (Abschnitt 1 "Wo wir heute stehen")

### 1.1 TAFKA heute

| Asset | Quelle | Status |
|---|---|---|
| tafka.de Hero-Screenshot | **neu** — Playwright (https://www.tafka.de) | TODO |
| La-Lick-Pitchdeck Thumbnail | `/Users/fabianwillisimon/Documents/Claude_Code/lalick_präsentation/` — Playwright auf file:// | TODO |
| Wissensplattform-Clickdummy Thumb (optional) | `_archiv_wissensplattform/` | OPTIONAL |

### 1.2 Deutsche KI-Beratungen

Playwright-Screenshots (alle 1440x900, JPEG q85) — Stand nach erstem Lauf:

- [ ] Appanion → https://www.appanion.com — **Connection Timeout**, Retry manuell noetig (ggf. archive.org-Snapshot)
- [x] statworx → https://www.statworx.com
- [x] KI.Park → https://www.ki-park.de/ (nicht ki.park wie im Plan)
- [x] Mondula → https://mondula.com
- [x] eggs.ai → https://www.eggs.ai/
- [ ] Mind-Hyve → https://mind-hyve.de/ (optional, Backup)

Ziel: Beleg dass "deutsche KI-Beratungen teilen eine Formel" (weich, freundlich, hellblau, Illustration).

### 1.3 Grosse / Mittelstands-Beratungen

- [ ] PwC Digital → https://www.pwc.de/de/digitale-transformation.html
- [ ] Deloitte AI → https://www2.deloitte.com/de/de/pages/deloitte-analytics/solutions/ai.html
- [ ] Haufe → https://www.haufe-akademie.de/
- [ ] Bechtle → https://www.bechtle.com/de-de
- [ ] msg → https://www.msg.group/

Ziel: Beleg "die Grossen sehen aus wie einander" — Corporate-Blau, geometrische Photography-Patterns.

### 1.4 KI-Tools (eigener Markt)

- [ ] Langdock → https://www.langdock.com
- [ ] Scorprise (KI-Navigator-Referenz) → Public-Hero screenshoten, **keine Login-Seiten**

## 2 — Bestehende Screenshots (Abschnitt 3 Denkprozess + Referenzen)

Die Referenz-Screenshots aus `docs/screenshots/` existieren bereits und werden kuratiert:

### Phase0 (Reduktions-Referenz)
- `docs/screenshots/phase0/blog-01.png` bis `blog-20.png` — zwei kuratieren (Hero + typische Detail)
- Ziel: Beleg "man kann auch anders" (Phase0-Typo-Reduktion)

### Scoreprise (zukuenftiges KI-Navigator-UI — als Inspiration, nicht als Blueprint)
- `docs/screenshots/scoreprise/00-uebersicht.png`
- `docs/screenshots/scoreprise/01-carl.png` (Persona-Detail)
- `docs/screenshots/scoreprise/14-carl-detail-it.png`

### AI-First (Phase0-Adaption, Inspiration)
- `docs/screenshots/ai-first/00-homepage.png`
- `docs/screenshots/ai-first/05-enablement.png`

### Every.to (Content-Redaktion-Referenz)
- `docs/screenshots/every-to/00-homepage.png`
- `docs/screenshots/every-to/03-guides.png`

## 3 — Diagramme (Abschnitt 3 Denkprozess)

Bereits in `assets/diagrams/` kopiert:

- `ki-betriebssystem.svg` — **zentrales Diagramm aus FM-Praesi v4** (aus `/FM_Präsi/diagram-ki-betriebssystem.svg`). Leit-Visual fuer das TAFKA-KI-Betriebssystem.
- `ki-betriebssystem.html` — gleiches Diagramm als eigenstaendige HTML-Variante (fuer iframe oder als Referenz).
- `diagram-genai-4eck.svg` — GenAI-4-Eck (Aicher-Inspiration).
- `diagram-tafka-beratungsprozess.svg` — Beratungsprozess.
- `diagram-transformationskurve.svg` — Transformationskurve.

Weitere Referenzen (nicht kopiert, nur Quellen):

- `design-system/img/icc-lichtleitsystem.png` — Leitsystem-Prinzip Referenz.
- `design-system/img/icons-bauhaus-minimal.png` — Icon-Sprache-Referenz.

Diagramm-Kanon der Design-System-Story:
- `design-system/designs/01-intro.png`
- `design-system/designs/02-core.png`
- `design-system/designs/03-assets.png`
- `design-system/designs/04-guidelines.png`
- `design-system/designs/05-design-system.png`
- `design-system/designs/06-website-implementation.png`

## 4 — Mockups (Abschnitt 4 In konkreten Anwendungen)

**Pencil-Exports** aus `design-system/designs/tafka-design-system.pen` und `tafka-wireframes-new.pen`.

Status: **nicht vorhanden**. Entstehen in Phase 2 des Plans.

### 4.1 Sales
- [ ] Pitchdeck-Cover (neuer Stil)
- [ ] Angebots-PDF Titelseite
- [ ] Onepager

### 4.2 Content
- [ ] Whitepaper Titel (PwC-Textwand-Demonstration — bewusst textlastig!)
- [ ] Whitepaper Innenseite
- [ ] LinkedIn-Carousel (3 Slides)
- [ ] Case-Study-Card

### 4.3 Website
- [ ] Landingpage Hero (Screenshot aktueller Build)
- [ ] Leistungsseite
- [ ] Case-Study-Detail

### 4.4 Brand / Tools
- [ ] KI-Navigator-UI-Mockup
- [ ] Messe-Stand-Skizze
- [ ] Notizbuch/T-Shirt-Mockup

## 5 — Abflugtafel (Abschnitt 6)

Bereits kopiert nach `assets/tegel/stitch-00.png` bis `stitch-04.png`.

Die 5 Screens zeigen verschiedene Terminal-Praesentations-Layouts aus dem Stitch-Export. Sind **Startpunkt/Inspiration** fuer die Split-Flap-Implementierung, nicht der Final-Look.

**Style-Hinweis aus Stitch-Code (`design-system/img/Tegel/extracted/*/code.html`):**
- Strict 0px radius (`border-radius: 0px !important`)
- 4px solid border (`#101622`)
- 8px offset hard shadow (`8px 8px 0px 0px #101622`)
- Font: Space Grotesk + Chivo Mono
- Primary: #0b54da

**Konflikt dokumentiert in README.md.**

## 6 — Fonts

- [ ] Montserrat Subset (Heading)
- [ ] Poppins Subset (Body)
- [ ] Ggf. IBM Plex Mono Subset (Labels/Tokens)

Generiert per `glyphhanger` in Phase 2 (nach Finalisierung der Copy).

## Rechtlicher Hinweis

Jede Wettbewerber-Screenshot-Karte in der Praesi bekommt im Fuss das Label:

> Interne Arbeitsdatei — nicht weitergeben (§51 UrhG)

Praesi ist `noindex` + `robots.txt Disallow: /intern/praesi-nils/`.
