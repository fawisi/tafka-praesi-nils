# Interne Designsystem-Praesi fuer Nils (Scroll-Story)

**Audience:** intern, Nils Wadt.
**Status:** Phase 1 Setup abgeschlossen. Vier offene Entscheidungen aus Rollback 2026-04-24 am 2026-04-28 geklaert (A-D, siehe unten). Phase 2 (HTML-Bau) startbereit.
**Plan:** [`design-system/docs/plans/2026-04-24-feat-interne-designsystem-praesi-fuer-nils-plan.md`](../../docs/plans/2026-04-24-feat-interne-designsystem-praesi-fuer-nils-plan.md)
**Brainstorm:** [`design-system/docs/brainstorms/2026-04-24-nils-designsystem-praesi-brainstorm.md`](../../docs/brainstorms/2026-04-24-nils-designsystem-praesi-brainstorm.md)

## Was ist das?

Eine scrollbare HTML-Einzelseite in neun Abschnitten, die Nils vom aktuellen visuellen Status-quo ueber Marktvergleich und Denkprozess bis zum Varianten-Beweis und einer meditativen Abflugtafel fuehrt. Die Praesi ist **selbst der Beweis** fuer das neue Design System — sie nutzt Tokens, Typographie und Leitsystem-Prinzip live.

Framing: *"Die Frage ist nicht mehr, ob wir ein Design-System brauchen, sondern auf welches wir uns einigen."*

## Entscheidungen vor Phase 2 (2026-04-28)

| # | Frage | Entscheidung |
|---|---|---|
| **A** | Design-Grundlage | tafka.de-Start + neuer Stil-Ende + Morph dazwischen |
| **B** | tafka.de-Erscheinung | Echter Screenshot, full-bleed. Kein Hero-Nachbau, kein iframe. |
| **C** | Vorher/Nachher | Seite-an-Seite-Screenshots. Keine Token-Analyse-Karten. |
| **D** | Morph-Ziel | v4-Snapshot (`tokens-snapshot-2026-04-24.css`) ist fuehrend. |

## Design-Quelle — Zwei-Stil-Morph (tafka.de → v4)

Die Praesi **morpht visuell** zwischen zwei Stilen, waehrend Nils scrollt:

| Zustand | Quelle | Token-File |
|---|---|---|
| **Start-Stil** (Abschnitt 0-3) | Live-tafka.de (Hero-Screenshot) — hellblauer Gradient, weisse Pill-Cards, Royal-Blue Buttons, Poppins Black, 14-16px Radius, Pills, weiche diffuse Shadows | `tokens-snapshot-tafka-start.css` |
| **End-Stil** (Abschnitt 4-6) | FM-Praesi v4 ("Bauhaus / Aicher / Tegel TXL") — warmer Paper-Ton, TXL-Yellow, Archivo Black + Inter, 3px Radius, 1.5px Rule, harter Ink-Offset-Shadow | `tokens-snapshot-2026-04-24.css` |

**Wichtig:** Die Praesi baut weder tafka.de nach (kein Live-Hero-Clone, kein iframe) noch kopiert sie FM-Praesi-Komponenten. Sie rendert den Praesi-**Content** (aus outline.html) in zwei Stil-Zustaenden. Nur die **CSS-Variablen** und Komponenten-Looks (Buttons, Cards, Shadows, Radien, Typo) morphen — der Inhalt bleibt derselbe.

Der Morph laeuft am Ende von Abschnitt 3 ("Mein Denkprozess") via GSAP ScrollTrigger Scrub. Variablen-Namen sind in beiden Token-Files synchron; nur die Werte unterscheiden sich. `prefers-reduced-motion: reduce` ueberspringt den Morph und zeigt direkt den End-Zustand ab Abschnitt 4.

### Abweichung zum Live-Design-System

`design-system/tokens/design-tokens.css` und `design-system/CLAUDE.md` stehen (Stand 2026-04-24) auf dem Bauhaus-Brutalist-Stand (Montserrat/Poppins, 2px-Border, 4px-Offset-Shadow, 0px-Radius, Blau `#00369E` + Gold `#F4CA00`). Die Praesi verwendet bewusst den **v4-Zielzustand**, nicht die Live-Tokens. Ein Abgleich steht separat aus.

## Struktur

```
2026-04-24-nils-designsystem/
├── README.md                           # dieses File
├── tokens-snapshot-2026-04-24.css      # FM-Praesi-v4-Tokens, eingefroren
├── outline.html                        # Content-Outline, kein Styling/JS — Fabian-lesbar
├── index.html                          # (Phase 2, noch nicht da)
├── assets/
│   ├── MANIFEST.md                     # Asset-Inventur + TODOs
│   ├── screenshots/                    # tafka.de + Wettbewerber (Playwright)
│   ├── mockups/                        # Sales / Content / Website / Brand (Phase 2)
│   ├── diagrams/                       # ki-betriebssystem.svg + 3 bestehende SVGs
│   └── tegel/                          # Abflugtafel-Startbilder aus Stitch-Zips
└── fonts/                              # Subset Archivo Black + Inter + IBM Plex Mono (Phase 2)
```

`outline.html` ist die inhaltliche Skelett-Struktur ohne Styling — geeignet fuer Content-Review, bevor Phase 2 den eigentlichen HTML/CSS/JS-Bau startet.

## Bauen

```bash
cd website
npm run build:praesi            # Token-Snapshot + Screenshots + Copy nach public/intern
npm run build:praesi:shots      # Nur Screenshots (Playwright, 12 Wettbewerber)
npm run build:praesi:tokens     # Nur Token-Snapshot (falls noch nicht eingefroren)
npm run build:praesi:copy       # Nur Copy nach website/public/intern/praesi-nils/
```

Das Hauptscript liegt unter [`scripts/build-praesi.mjs`](../../../scripts/build-praesi.mjs). Playwright wird aus `website/node_modules` geladen.

Flags:
- `--no-shots` — Copy + Tokens, keine Screenshots.
- `--force` — bestehende Screenshots ueberschreiben (sonst skip).
- `--only tokens|shots|copy` — Einzeljob.

**Hinweis:** `build:praesi:tokens` schreibt den Snapshot automatisch nur dann, wenn er noch nicht existiert (Einfrier-Semantik). Der aktuell eingefrorene Snapshot ist **manuell aus FM-Praesi v4 extrahiert**, nicht aus design-tokens.css.

## Phase 1 — was in dieser Session fertig wurde

- [x] Feature-Branch `feat/nils-designsystem-praesi` vom `feat/website-dummy` abgezweigt.
- [x] Verzeichnisstruktur angelegt.
- [x] `tokens-snapshot-2026-04-24.css` mit FM-Praesi-v4-Tokens angelegt (Paper/Ink/TXL, 1.5px, 3px soft).
- [x] 4 Stitch-Zips entpackt, Tafel-Screens in `assets/tegel/` uebernommen (5 Screens, Split-Flap-Referenz).
- [x] Asset-Inventur als `assets/MANIFEST.md` — kuratierte bestehende Screenshots + Playwright-Liste fuer neue.
- [x] 4 Diagramme kopiert (`ki-betriebssystem.svg` aus FM-Praesi + 3 aus design-system/img).
- [x] `scripts/build-praesi.mjs` mit drei Jobs (Tokens, Shots, Copy) und 12-Wettbewerber-Liste.
- [x] `website/package.json` um 4 `build:praesi*`-Scripts ergaenzt.
- [x] Playwright-Screenshots erstmalig gezogen: **11 von 12 erfolgreich**. Offen: Appanion (Connection Timeout — Retry manuell).

## Phase 2 — Bauliste

1. **Content-Struktur aus outline.html uebernehmen**, dabei: "Akt" durch "Abschnitt" ersetzen, Texte um ~50% kuerzen (Leitsatz + kurzer Absatz pro Unterabschnitt), Nils-direkte-Ansprache minimieren (Augenhoehe, nicht Anrede).
2. **Mockups selbst bauen** (HTML/CSS/SVG) — keine Pencil-Exports noetig. Pitchdeck-Cover, Whitepaper-Textwand, Onepager, Case-Study, Website-Hero, KI-Navigator-UI entstehen direkt im HTML als v4-stilisierte Komponenten.
3. **Split-Screen-Vergleiche** (Alt vs. Neu) mit bestehenden Screenshots (PwC, Deloitte, Haufe, KI-Beratungen) links und selbst-gebauten v4-Mockups rechts.
4. **Scroll-Morph** am Ende von Abschnitt 3 — GSAP ScrollTrigger scrubbed die CSS-Variablen von Start-Snapshot (tafka-Stil) auf End-Snapshot (v4-Stil). `prefers-reduced-motion` ueberspringt den Morph.
5. Optional: Appanion und Scorprise nachziehen, falls Nils sie konkret vermisst (kein Blocker fuer V1).

## Rechtliches

Wettbewerber-Screenshots sind **interne Arbeitsdateien** gemaess §51 UrhG. Jede Screenshot-Karte in der Praesi bekommt im Fuss das Label:

> Interne Arbeitsdatei — nicht weitergeben (§51 UrhG)

Die Praesi wird unter `/intern/praesi-nils/` ausgeliefert mit `<meta name="robots" content="noindex,nofollow">` und `robots.txt Disallow: /intern/praesi-nils/`. Kein Login-Gate — Risiko bei interner Weitergabe bleibt.

## Kein Tracking, kein CTA

Bewusste Entscheidung (Plan, Brainstorm):

- Kein Plausible, kein GA, keine Heatmap, keine Custom-Events.
- Keine Gate-Buttons, kein Klick-Outro, kein Schlusssatz.
- Nils meldet sich auf seine Art (Mail, Slack, Anruf), wann er will.
- Feedback-Signal = direkter Call, nicht Dashboards.
