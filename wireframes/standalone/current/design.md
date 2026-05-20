# happyhotel · Ray Design System

Source of truth für Tokens, Typografie und Patterns wie sie aktuell in `dashboard.html`, `preise.html` und `ray.html` gelebt werden. Diese Spec ersetzt den Stand aus `/wireframes/design-system/ai-rm-design-system.html`.

Vor jeder Design-Entscheidung: dieses File + `docs/persona-anna.md` + `docs/persona-kai.md` lesen.

---

## 1. Brand & Personality

| Achse | Wahl | Begründung |
|---|---|---|
| Tone | Editorial · Premium · Vertraulich | Nicht SaaS-Dashboard. Nicht Consumer-App. Eher Wochenmagazin + Geschäftsbericht. |
| Persona | Vertrauter, der Geschäft führt | Ray ist Mitarbeiter, nicht Tool. Kommuniziert in vollständigen Sätzen, nicht in Widgets. |
| Aesthetic | Warm-Off-White Paper · Ink-Blue Akzent · Hairlines | Kein Dark Mode. Kein Glas-Effekt. Kein Gradient. |
| Voice | Du-Form. Geld in Euro. Kein Fachjargon. | Hotelier ≠ Revenue Manager. Übersetze jede Metrik in Geld, Wachstum oder fällige Aktion. |

**Brand Promise:** "Wir nehmen dir die Last des Revenue Management ab." Das Produkt soll sich anfühlen wie ein Brief vom Steuerberater — kompetent, vollständig, kalm. Nicht wie ein Cockpit.

---

## 2. Tokens — Colors

```css
:root {
  /* Surfaces — warm paper hierarchy */
  --bg:           #f6f5f1;   /* page background, warm off-white */
  --shell:        #fafaf7;   /* app shell, slightly warmer */
  --shell-2:      #efeeea;   /* shell hover / inactive nav */
  --surface:      #ffffff;   /* white cards */
  --surface-2:    #f7f6f2;   /* subtle elevation, decision card bg */

  /* Ink — text hierarchy */
  --ink:          #18181a;   /* near-black, headings + primary text */
  --ink-2:        #3a3a3d;   /* body text */
  --muted:        #6e6e72;   /* secondary text, labels */
  --subtle:       #a8a8ac;   /* tertiary, disabled, axis labels */

  /* Accent — Ink Blue (NICHT sage green, NICHT royal blue) */
  --accent:       #1e3a5f;   /* primary interactive, italic accents */
  --accent-soft:  #ebf0f6;   /* tinted backgrounds, trend pill */
  --accent-line:  #b8c4d4;   /* hairline accent, borders */
  --accent-deep:  #14294a;   /* hover/pressed */

  /* Borders — hairline hierarchy */
  --border:       #e6e5df;   /* default hairlines (1px) */
  --border-2:     #c9c8c2;   /* stronger borders, app frame */
  --border-3:     #a6a5a0;   /* strongest, hover states */

  /* Semantic — sparingly */
  --good:         #1e3a5f;   /* positive (uses accent for brand cohesion) */
  --bad:          #8c2f2f;   /* negative, used only for clear losses */
  --warn:         #8a6a3a;   /* warning, used only for clear warnings */
  --warn-soft:    #f1ece3;
}
```

**Wichtig:**
- `--good` ist bewusst gleich `--accent`. Positive Deltas erscheinen in der Brand-Farbe, nicht in Grün. Grün wirkt im warmen Paper-Kontext billig.
- `--bad` ausschließlich für Echtverluste (Storno, Pickup-Rückgang). Nicht für "schlechter als Plan".
- `--warn-soft` als Pill-Bg für Warnungen, nicht für ganze Surfaces.
- KEINE Grün/Rot Status-Stoplichter. KEIN sage green (`#7a8a6a` o. ä.). KEIN royal blue (`#3b5cff` o. ä.).

---

## 3. Tokens — Typography

### Schriften

```css
--font-display: "EB Garamond", Georgia, serif;
--font-sans:    "Inter", -apple-system, BlinkMacSystemFont, system-ui, sans-serif;
--font-mono:    "JetBrains Mono", "SF Mono", Menlo, monospace;
```

**Wechsel weg von Instrument Serif → EB Garamond:** EB Garamond hat klassischere Renaissance-Proportionen, weniger Display-Charakter, mehr "Geschäftsbericht". Italic-Cut wird **nicht verwendet** (siehe unten).

### Globale Italic-Killung

```css
em { font-style: normal; }
```

Akzent-Hervorhebung läuft über **Farbe + Weight**, nicht über Italic:

```html
<h1 class="brief-headline">Pfingsten war ein <em>Volltreffer.</em></h1>
```

```css
.brief-headline em {
  font-style: normal;           /* wichtig */
  font-weight: 500;
  color: var(--accent);
}
```

Hintergrund: Italic im EB Garamond wirkt zu literarisch / zu Roman für ein RM-Produkt. Roman + Accent-Color reicht.

### Typografische Skala

| Use Case | Familie | Size · Line · Tracking · Weight |
|---|---|---|
| Hero Headline (Briefing) | EB Garamond | 44px · 1.05 · -0.025em · 400 |
| Section H2 (Frame-Head) | EB Garamond | 64px · 1.02 · -0.03em · 400 |
| Card Title (Decision, Rec) | EB Garamond | 22px · 1.2 · -0.02em · 500 |
| Sub-Title (Greet, Modal) | EB Garamond | 28px · 1.1 · -0.02em · 400 |
| Stat Big (Briefing Stats) | EB Garamond | 28px · 1 · -0.02em · 400 |
| Stat Hero (Mockup Card) | EB Garamond | 48px · 1 · -0.025em · 400 |
| Body (Narrative) | Inter | 16px · 1.7 · 0 · 400 |
| Body Small | Inter | 14px · 1.55 · 0 · 400 |
| Card Sub | Inter | 14px · 1.6 · 0 · 400 (`--ink-2`) |
| UI Label / Button | Inter | 13px · 1 · -0.01em · 500 |
| Eyebrow (Mono Tag) | JetBrains Mono | 10–11px · 1 · 0.16–0.18em · 600 · UPPERCASE |
| Money / Numbers | JetBrains Mono | matches surrounding · `tabular-nums` · 500 · -0.02em |
| Delta / Trend Pill | JetBrains Mono | 11px · 1 · 0 · 500 · `tabular-nums` |

**Number Klasse:**

```css
.num {
  font-family: var(--font-mono);
  font-variant-numeric: tabular-nums;
  font-weight: 500;
  letter-spacing: -0.02em;
}
```

Alle Geldbeträge in Mono mit `tabular-nums`. Numerische Tabellen ebenfalls.

---

## 4. Tokens — Space & Radii

| Token | Wert | Use |
|---|---|---|
| `--radius-sm` | 6–8px | Buttons, Pills, Inputs |
| `--radius-md` | 10–12px | Inline-Cards (Decision, Day-Cell) |
| `--radius-lg` | 14–16px | Surface-Cards (Brief, Mockup, AI-Rec) |
| `--radius-pill` | 100px | Filter-Chips, Tier-Pills |

Spacing-Rhythmus: Multiples von 4 (4 · 8 · 12 · 16 · 20 · 24 · 32 · 48 · 64). Section-Padding: 48–80px. Card-Padding: 24–48px je nach Hierarchie.

Hairlines durchgehend **1px**, nie 2px. Borders auf App-Frame und Spotlight-Cards: 1.5px max (App-Frame: `--border-2`).

---

## 5. Patterns — Foundations

### 5.1 Diamond Marker

Rotated 7×7 Square in Accent. Wiederkehrendes System-Element vor Tags, in Buttons, als Bullet.

```html
<span class="diamond"></span>
```

```css
.diamond, .diamond-s { width:6px; height:6px; }
.diamond-m { width: 10px; height: 10px; }
.diamond-l { width: 16px; height: 16px; }
.diamond-xl { width: 24px; height: 24px; }
.diamond, .diamond-s, .diamond-m, .diamond-l, .diamond-xl {
  background: var(--accent);
  transform: rotate(45deg);
  display: inline-block;
}
```

Verwendung: Mono-Tag-Prefix · Ray-Button-Prefix · Section-Header-Prefix · CTA-Plus-Icon.

### 5.2 Mono Tag (Eyebrow)

```html
<span class="mono-tag"><span class="mark"></span>KW 18 · Briefing</span>
```

```css
.mono-tag {
  font-family: var(--font-mono);
  font-size: 10px;
  font-weight: 600;
  text-transform: uppercase;
  letter-spacing: 2.4px;
  color: var(--muted);
  display: inline-flex; align-items: center; gap: 8px;
}
.mono-tag.accent { color: var(--accent); }
.mono-tag .mark {
  width: 6px; height: 6px;
  background: var(--accent);
  transform: rotate(45deg);
}
```

### 5.3 Trend Pill (inline im Body-Text)

```html
<span class="trend up">
  <span class="arrow">↑</span>12 %
  <span class="trend-ref">vs. Vorjahr</span>
</span>
```

Charakteristisch: **trend-ref** als ankontextualisierende Mini-Referenz mit linker Hairline. Macht das Delta selbsterklärend ohne zusätzliche Caption.

```css
.trend {
  display: inline-flex;
  align-items: baseline;
  gap: 3px;
  padding: 1px 7px 2px;
  background: var(--accent-soft);
  border-radius: 3px;
  font-family: var(--font-mono);
  font-variant-numeric: tabular-nums;
  font-weight: 500;
  font-size: 11px;
  white-space: nowrap;
}
.trend.up { color: var(--accent); }
.trend.down { color: var(--bad); background: #fbeded; }
.trend .arrow { font-size: 9px; line-height: 1; }
.trend .trend-ref {
  font-family: "EB Garamond", serif;
  font-size: 14px;
  color: var(--accent);
  opacity: 0.8;
  padding-left: 6px;
  border-left: 1px solid var(--accent-line);
  letter-spacing: -0.01em;
}
```

### 5.4 Status Dot

```html
<span class="status-dot live">Live · Ray analysiert</span>
<span class="status-dot waiting">Wartet auf dich</span>
<span class="status-dot idle">Idle · vor 2 Std</span>
```

```css
.status-dot::before {
  content: ""; width: 7px; height: 7px; border-radius: 50%;
  display: inline-block; margin-right: 8px;
}
.status-dot.live::before    { background: #22c55e; }
.status-dot.waiting::before { background: var(--accent); }
.status-dot.idle::before    { background: var(--subtle); }
.status-dot.live::before    { animation: pulse 2.4s ease-in-out infinite; }
@keyframes pulse { 0%,100% { opacity: 1 } 50% { opacity: 0.4 } }
```

Live nutzt das einzige Grün im System. Bewusst (Status = universal sprache).

### 5.5 Detail Link (Drilldown)

```html
<a class="detail">heute Nacht 23 Preise angepasst</a>
```

```css
.detail {
  color: var(--accent);
  text-decoration: underline dashed var(--accent);
  text-underline-offset: 4px;
  text-decoration-thickness: 1px;
  cursor: pointer;
}
.detail:hover { opacity: 0.7; }
```

Dashed-Underline signalisiert: "hier gibt es Tiefe / Erklärung". Trigger für Inline-Drilldowns.

### 5.6 Hairline

```css
.hairline { border-top: 1px solid var(--border); margin: 12px 0; }
```

Verwendung: trennt Card-Inhalt vertikal **statt** nested boxes oder background-shifts.

---

## 6. Patterns — Buttons

### 6.1 Primary (Action)

Schwarz auf Paper. Stärkster Akzent.

```html
<button class="btn btn-primary">Annehmen</button>
```

```css
.btn { font-family: Inter; font-size: 13px; font-weight: 500; padding: 9px 18px; border-radius: 8px; border: none; cursor: pointer; }
.btn-primary { background: var(--ink); color: #fff; }
.btn-primary:hover { background: #000; }
```

### 6.2 Ghost (Sekundär)

```css
.btn-ghost { background: transparent; color: var(--ink-2); border: 1px solid var(--border-2); }
.btn-ghost:hover { border-color: var(--ink); }
```

### 6.3 Ray Button (Ray-Konversation triggern)

Outline in Accent + Diamond-Marker. Das einzige System-Element, das Ray als Aktor visuell markiert.

```html
<button class="btn btn-ray"><span class="ray-rune"></span>Ray fragen</button>
```

```css
.btn-ray {
  background: var(--surface);
  color: var(--accent);
  border: 1.5px solid var(--accent);
  display: inline-flex; align-items: center; gap: 8px;
}
.btn-ray:hover { background: var(--accent-soft); }
.btn-ray .ray-rune { width: 7px; height: 7px; background: var(--accent); transform: rotate(45deg); }
```

### 6.4 Ray Icon-Only (kompakt)

36×36 Square, 1.5px Accent-Outline, Diamond-Marker zentriert. Verwendung: Modal "+" Button, Inline-Trigger neben Cells.

### 6.5 Filter Pill (Ray Panel)

```css
.rpf { background: transparent; color: var(--muted); border: 1px solid var(--border); padding: 7px 14px; border-radius: 100px; }
.rpf.active { background: var(--accent); color: #fff; border-color: var(--accent); }
```

---

## 7. Patterns — Cards

### 7.1 Briefing Card (Hero, Hotelier Mode)

Die zentrale "Zeitungsseite". Weiße Surface, 16px Radius, 40–48px Padding, dezente Shadow.

```css
.brief {
  background: var(--surface);
  border: 1px solid var(--border);
  border-radius: 16px;
  padding: 40px 48px 36px;
  box-shadow: 0 1px 3px rgba(45,41,32,0.04);
}
```

Struktur (von oben nach unten):
1. **Brief-Meta** — Kicker (Mono-Tag) + Datum, bottom hairline
2. **Brief-Headline** — EB Garamond 44px, Italic-Wort als Accent
3. **Brief-Narrative** — Inter 16px/1.7, mit inline `money` · `trend` · `detail` Patterns
4. **Brief-Stats** — 3 Spalten, top + bottom hairline
5. **Brief-Decision** (optional) — inline decision card
6. **Brief-Week** — 7-Tage-Outlook Grid
7. **Brief-Ray** — Ray-Strip am Ende

### 7.2 Decision Card

Inline-Card innerhalb Briefing oder als eigene Surface.

```html
<div class="brief-decision">
  <div class="bd-meta">
    <span class="bd-tag"><span class="diamond"></span>Deine Freigabe nötig</span>
    <span class="bd-deadline">bis morgen 12:00</span>
  </div>
  <h3 class="bd-title">Großgruppe Berlin · 24 Zimmer</h3>
  <p class="bd-sub">Ankerpreis 119 €, Spielraum bis 109 €. Ohne Annahme verlieren wir die 7 Nächte.</p>
  <div class="bd-actions">
    <button class="btn btn-primary">Annehmen</button>
    <button class="btn btn-ghost">Ablehnen</button>
    <button class="btn btn-ray"><span class="ray-rune"></span>Mit Ray besprechen</button>
  </div>
</div>
```

`bd-actions` schiebt den Ray-Button per `margin-left: auto` an die rechte Seite.

### 7.3 Mockup Card (Daten-Visualisierung)

Zweispaltige Card: Hero-Stat links (EB Garamond 48px Accent + Delta-Zeile), Bar-Chart oder Comp-Block rechts. Pattern aus fin.ai übernommen.

```html
<div class="mockup-card">
  <div class="mc-head">
    <span class="mc-tag"><span class="diamond"></span>Pickup · 14 Tage</span>
    <span class="mc-dot"></span>
  </div>
  <div class="mc-inner">
    <div class="mc-stat">
      <div class="mc-stat-row"><span class="mc-stat-val">+24</span></div>
      <div class="mc-stat-context">
        <span>Nächte</span><span class="mc-stat-context-row">vs. Vorwoche</span>
      </div>
      <div class="mc-stat-deltas"><span class="d-arrow">↑</span><strong>12 %</strong><span class="d-sep">·</span>+1.016 €</div>
    </div>
    <div class="mc-chart"><!-- SVG bars --></div>
  </div>
</div>
```

Charts: dotted halftone fills + Y-Axis-Hairlines (gleichmäßige 40px Skalierung) + open-bottom bars hinter sichtbarer Baseline.

### 7.4 AI Rec Card (Ray Sidebar)

Kompakte Empfehlungskarte in der Side-Rail.

```html
<div class="ai-rec">
  <span class="ar-tag"><span class="diamond"></span>Empfehlung</span>
  <h4 class="ar-title">MinLOS 2 für 23.–25. Mai</h4>
  <div class="ar-spark"><!-- mini-chart --></div>
  <div class="ar-actions">
    <button class="btn btn-primary">Übernehmen</button>
    <button class="btn btn-ghost">Später</button>
  </div>
</div>
```

---

## 8. Patterns — Numbers & Stats

### 8.1 Stat Block (Big Number)

```html
<div class="stat-block">
  <span class="stat-label">Mai bisher</span>
  <span class="stat-value">28.420 <em>€</em></span>
  <span class="stat-delta">↑ 12 % vs. Vorjahr</span>
</div>
```

`stat-value` ist EB Garamond 28–48px. Das Currency-Symbol kann als `em` mit Accent-Color hervorgehoben werden.

### 8.2 Money Inline

```html
<span class="money">28.420 €</span>
```

```css
.money { font-family: var(--font-mono); font-weight: 700; font-variant-numeric: tabular-nums; }
```

Immer fett (700). Im Body grenzt es sich gegen Inter Regular ab — keine zusätzliche Markierung nötig.

---

## 9. Patterns — Week Outlook

7-Tage-Grid am Ende des Briefings. Drei Zustände:
- `bw-day` — neutral, weiße Surface, ein Status-Wort italic-Serif
- `bw-day strong` — accent-soft Background, "stark"-Label
- `bw-day event` — accent solid Background, white Text, Event-Marker

```html
<div class="bw-grid">
  <div class="bw-day">
    <div class="bw-dow">Mo<span class="bw-occ">68 %</span></div>
    <div class="bw-status">ruhig</div>
    <div class="bw-price">98 €</div>
    <div class="bw-bar"><div class="bw-bar-fill" style="width:68%"></div></div>
  </div>
  <div class="bw-day strong">…</div>
  <div class="bw-day event">…</div>
</div>
```

Status-Wort in EB Garamond Regular (nicht italic). Bewusst literarisch: "ruhig" / "stark" / "Pfingsten" / "Buchmesse".

---

## 10. Patterns — Comp Block (Comp-Set)

Horizontale Bar-Liste mit Hotel-Position. Hospitality-realistisch: positioniere "Du" als 2. von 5, nicht als Premium-Top.

```html
<div class="comp-block">
  <div class="comp-row"><span class="comp-name">Hotel Adler</span><div class="comp-bar"><div class="comp-fill" style="width:90%"></div></div><span class="comp-price">142 €</span></div>
  <div class="comp-row you"><span class="comp-name">Du</span><div class="comp-bar"><div class="comp-fill" style="width:74%"></div></div><span class="comp-price">119 €</span></div>
  <!-- … -->
</div>
```

`.comp-row.you` markiert die Hotel-Zeile mit Accent-Fill und subtilem Background-Tint.

---

## 11. Patterns — Price Heatmap

Preistabelle als Kalender-Heatmap. Jede Zelle (`pc`) zeigt Preis + Belegung + optional AI-Mark + Event.

```css
.pc { background: var(--surface); border: 1px solid var(--border); border-radius: 6px; padding: 8px 10px; }
.pc.strong { background: var(--accent-soft); border-color: var(--accent-line); }
.pc.weak   { background: var(--warn-soft); border-color: var(--border); }
.pc.event  { background: var(--accent); color: #fff; border-color: var(--accent); }
```

`.ai-mark` = kleines accent square top-right der Zelle, signalisiert AI-Empfehlung.

---

## 12. Patterns — Ray Panel & Conversation

Ray-Panel rechts angedockt (420px) oder als Modal Bottom-Sheet (full-width / 920px wider mit Tabs).

### Filter Pills + Section Header

```html
<div class="rp-filters">
  <button class="rpf active">Alle</button>
  <button class="rpf">Pinned</button>
  <button class="rpf">Wartet</button>
  <button class="rpf">Erledigt</button>
</div>
<div class="rp-section-head">Heute</div>
```

### Conversation Row

```html
<a class="rp-conv">
  <span class="rp-conv-status active"></span>
  <div class="rp-conv-content">
    <div class="rp-conv-title">Großgruppe Berlin</div>
    <div class="rp-conv-snippet">"Anker 119 €, Spielraum bis 109 €" <span class="sep">·</span> <span class="badge">3 Aktionen</span></div>
  </div>
  <div class="rp-conv-meta">
    <span class="rp-conv-time">vor 14 Min</span>
    <span class="rp-conv-msgs">8</span>
  </div>
</a>
```

Status-Dot Varianten: `active` (pulse) · `waiting` (accent 0.45) · `analysing` (animated) · `pinned` (filled) · `past` (subtle).

---

## 13. Patterns — Chain-of-Thought

Ray's Denkprozess als sichtbare Themen + Steps. Verwendung im Conversation-View.

```html
<div class="cot">
  <div class="cot-theme">
    <div class="cot-theme-head">
      <span class="cot-theme-num">01</span>
      <div class="cot-theme-title">Verdrängung prüfen</div>
      <span class="cot-theme-pill">±0 €</span>
    </div>
    <div class="cot-steps">
      <div class="cot-step">
        <span class="cot-step-bullet"></span>
        <div class="cot-step-content">
          <div class="cot-step-tag">Analyse <span class="cst-meta">vor 2 Min</span></div>
          <div class="cot-step-body">Pickup-Rate 14 Tage: <b>+24 Nächte</b>, Auslastung kommt aus eigenem Forecast.</div>
        </div>
      </div>
      <div class="cot-step decision">
        <span class="cot-step-bullet"></span>
        <div class="cot-step-content">
          <div class="cot-step-tag">Entscheidung</div>
          <div class="cot-step-body">Großgruppe annehmen: kein Displacement, +<span class="num">2.856 €</span></div>
        </div>
      </div>
    </div>
  </div>
</div>
```

Zwei Step-Typen: standard (subtle bullet) und `decision` (accent bullet + accent body bg). Ray reasoniert in nummerierten Themen, nicht in linearem Stream.

---

## 14. Conventions — was wir tun

- **Du-Form** durchgehend. Kein "Sie", kein "Ihr Hotel".
- **Geld in Euro** mit `tabular-nums`, Mono, fett.
- **Italic-Cut killed.** Akzent über Farbe + Weight.
- **Diamond als System-Element.** Wiederkehrend, in 4 Größen.
- **Hairlines statt Boxes.** Vertikale Trennung im selben Surface, nie nested cards.
- **Mono-Tags als Eyebrow.** Immer mit `letter-spacing` ≥ 0.16em, immer uppercase.
- **EB Garamond ausschließlich für Headlines, Stats, Status-Words.** Nie für Body.
- **Trend Pills mit `trend-ref`.** Delta ohne Referenz ist Lärm.
- **Pulse-Animation nur für `live`.** Sonst statische Dots.
- **Status-Wörter literarisch:** "ruhig" / "stark" / "Pfingsten" — nicht "+12 %" / "Belegung hoch" / "Event".

---

## 15. Anti-Patterns — was wir niemals tun

| Don't | Why |
|---|---|
| `border-left: 3px solid accent` als Akzent-Stripe | AI-Slop, sieht generisch aus |
| Nested Cards (Card-in-Card mit Background-Shift) | Optical noise, Hairlines reichen |
| Gradient Text, Gradient Backgrounds, Glow | Aesthetic Slop |
| Em-Dashes (`—`) im Body Copy | Kommata, Doppelpunkte, Klammern reichen |
| Modal als erste Lösung | Inline drilldown probieren |
| Stoplicht-Grün für positives Delta | `--good = --accent`, brand-cohärent |
| Sage Green / Royal Blue als Accent | nur Ink-Blue `#1e3a5f` |
| Italic Serif für Akzent | nur Roman + Color + Weight |
| Card-Grids identisch repeated (5× selbes Card-Pattern) | Hierarchie + Rhythmus brechen |
| Hero-metric Template (big number + small label + supporting stats + gradient bg) | "AI Dashboard" Slop |
| Glas-Effekt / Frosted-Glass | nicht im warmen Paper-Kontext |
| RM-Jargon im Hotelier-Mode ("RevPAR Pickup vs STR Sample") | Anna spricht Geld, nicht KPIs |

---

## 16. File-Inventar (Referenzen)

| File | Was zeigt es? |
|---|---|
| `dashboard.html` (current) | Anna Daily Briefing, edge-to-edge, sticky chrome, Week Outlook |
| `preise.html` (current) | Preistabelle Heatmap, Kai Experten-Mode, Price-Detail-Panel |
| `ray.html` (current) | Ray Panel, Conversation-View, Chain-of-Thought, Filter, Multi-Session |
| `design.html` (current) | Visueller Showcase aller Tokens + Patterns (Stakeholder-ready) |

Master-Wireframes leben weiterhin in `/wireframes/master/`. `current/` ist der aktuelle Produktstand.
