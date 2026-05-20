# happyhotel — AI Revenue Manager Design Exploration

This folder contains design exploration for happyhotel's next-generation AI Revenue Manager experience. Work is in German. User is Philipp Schulz (founder/product). Use this file as orientation before diving in.

---

## 1. Project context

happyhotel is a German hotel revenue management software company. Post Series A (April 2026). Strategic shift from "RMS tool vendor" to **outsourced commercial function** — AI + human experts owning pricing outcomes for hotels. November 2026 is the planned "credibility moment" for the relaunch.

The work in this folder explores **how the AI Revenue Manager experience should look and feel** — from radical conversation-first to dashboard-evolution-with-sidekick.

---

## 2. Strategy 2026 — TL;DR

(Full doc lives in `uploads/HAPPYHOTEL-Strategie 2026 - Post Series A - Long Read.pdf`. Summary below.)

**Vision:** "We deliver profitable demand, so hoteliers can focus entirely on creating exceptional guest experiences." Long-term: become the hotel's integrated commercial department (Revenue → Sales → Marketing).

**Mission (12–18 months):** Evolve from "pricing recommendations" to a hands-off AI Revenue Manager backed by an expert advisory team. Shift from software provider to trusted commercial partner.

**USP:** "happyhotel takes the weight of revenue management off your shoulders — no more complicated tools or costly specialists. Automation + human expertise, at a fraction of consultancy cost."

**ICP — Zwei Personas (siehe `persona-anna.md` und `persona-kai.md` für volle Profile):**
- **Anna · Owner/GM** — Mid-sized independent hotels, kein dedizierter RM, ~€2M Umsatz. Will Ergebnisse, kein RM-Expertentum. Primary persona, "Missing Middle".
- **Kai · Senior Revenue Manager** — Cluster Lead, 6 Häuser, Profi-Tools-User. Secondary persona, größere Ketten/Cluster. Beide nutzen dasselbe System, identity-based Routing.
- **PFLICHTLEKTÜRE** vor Design-Entscheidungen: `persona-anna.md` für Hotelier Mode, `persona-kai.md` für Experten Mode.

**Hybrid model — "One System. One History. One Source of Truth.":**
- AI handles monitoring, analysis, routine actions
- AI escalates when confidence is low
- Human RM experts (e.g. "Marc", "Lisa") handle complex/ambiguous situations
- Customer experience is one continuous workflow, not "tool + separate support"

**Pricing — keep room-based SaaS, repackage in 3 tiers (mirror RM seniority):**
- Revenue Manager — €8/room/month (min 25 rooms) — monitoring, alerts, price recs/auto-execute, guardrails, forecast, displacement, comp-set, annual review
- Senior Revenue Manager — €12/room/month (min 35) — adds restrictions, distribution recs, segmentation, multi-property, quarterly review, Rateshopper Pro, priority SLA
- Revenue Director — €20/room/month (min 50) — adds rate structure optimization, budgeting, group contracts, monthly review, dedicated POC, third-party adjustments

**Product principles (from the strategy doc):**
1. Results & business impact first (not dashboard depth)
2. Trust via transparency + hybrid delivery
3. Conversation-first experience (briefings replace dashboards-to-check)
4. Decisions as first-class objects + context memory as core IP

**Leading KPIs:** Results · Transparency & predictability · Degree of automation

**JTBD ladder (Levels 1–5):**
- L1 Revenue Analyst — execute & monitor (data hygiene). **AI automation potential: HIGH**
- L2 Revenue Manager — tactical decisions & optimization. **Medium-High**
- L3 Senior/Cluster RM — scale, govern, lead. **Medium**
- L4 Director of Revenue — strategic & cross-functional. **Medium**
- L5 Commercial Director — vision, profit, transformation. **Low**

The roadmap automates upward through this ladder.

---

## 3. Current product capabilities (April 2026)

Reviewed via screenshots in this folder (`Bildschirmfoto 2026-04-29 um *.png`):

- **Preistabelle** — calendar heatmap, central cockpit. Shows Belegung, ADR, RevPAR, Auslastung, Dein Preis auf booking.com (vs. comp-set), Single/Double Room prices, Restriktionen
- **Copilot RM** — already exists today. Chat-based report ("Zusammengefasste Preisänderungen") + Q&A about reports
- **AUTOPILOT toggle** in top bar — exists today, currently binary on/off (under-developed)
- **Pickup-Heatmap / Analyse** — Buchungen × Übernachtungen heatmap
- **Analyse 2.0** — chat-to-chart ("Beschreibe uns, was dein Chart anzeigen soll")
- **Custom Dashboards** — drag-and-drop widget builder
- **Mitbewerber** view (currently sparse)
- **Kalender** — events + pricing strategies, monthly view
- **Event editor** — name, category (Schulferien etc.), demand effect slider with ML suggestion
- **Migration zur neuen Preistabelle** — onboarding wizard
- **Pricing strategies** — apply % adjustment to events
- **PMS integrations** — Mews et al. Strategy: 4 high-quality PMS interfaces in 2026, deprecate Gastrodat

**Backend capabilities to package into the agent:**
Pricing recommendations + auto-execute · Forecast & pickup · Comp-set monitoring (Rateshopper) · Event-demand effect (ML) · Restrictions (MinLOS/CTA/CTD/inventory) · Channel/OTA hygiene · Distribution actions (promos, direct boost) · Displacement / group bookings · Multi-property reporting · Hybrid escalation to human experts · Decision log & reasoning.

---

## 4. Design principles agreed so far

These emerged from the conversation and should steer all future design work:

1. **Owner/GM is the user, NOT the professional RM.** No jargon. "Du hast 12.400 € verdient" instead of "RevPAR Pickup +0,4 vs STR Sample". Translate every metric into money, growth, or required action.
2. **Bringschuld, not Holschuld.** The system comes to the hotelier (briefing, push, inbox). Dashboards are drilldown, never the front door.
3. **Every action has a "Why".** Explainable > optimal. Logical > scientifically perfect. Reasoning visible at every cell/decision.
4. **Hybrid is visible.** Marc and Lisa (human RM experts) appear *in* the product, in the same stream as AI actions — not in a separate support channel. Embodies "One System, One History".
5. **Tarife = AI seniority.** You "hire" an AI Revenue Manager, then "promote" them to Senior, then to Director. Onboarding feels like hiring; quarterly reviews feel like 1-on-1s. This metaphor is the brand differentiator.
6. **Trust is graduated, not binary.** Replace the binary AUTOPILOT toggle with per-dimension trust levels (price magnitude, horizon, restrictions, channel, group size). Defaults come from the tier.

---

## 5. Work delivered in this folder

Three wireframe drafts ("Wurfs"), each opens directly in browser. Build on these — don't recreate.

### `ai-rm-wireframes.html` (Wurf 1)
Seven screens of one cohesive direction. Establishes the core IA:
- 0 — Three leading principles
- 1 — Morning Briefing as front door (shift handover)
- 2 — "Why this price?" — reasoning panel from a clicked cell
- 3 — Decisions Inbox (everything needing approval)
- 4 — Trust & Tier Settings (per-dimension granularity)
- 5 — Hybrid Chat (AI + human expert in same stream)
- 6 — Decision Log (audit + memory + proof)
- 7 — Onboarding as hiring an employee

### `ai-rm-wireframes-v2.html` (Wurf 2)
Six radically different packaging metaphors for the *same* capabilities. Used to open the solution space:
- 1 — **Pure Chat** (WhatsApp-style, no app, just messages)
- 2 — **Tagesschau** (newspaper morning edition, narrative)
- 3 — **Mission Control** (dense ops center, dark theme, multi-property)
- 4 — **Card Deck** (mobile, Tinder-style swipe decisions)
- 5 — **Strategy Canvas** (2D price × occupancy map, spatial)
- 6 — **Agent at Work** (Cursor-style sidebar copilot)

The likely answer is a combination — e.g. one default surface (Briefing/Chat for GMs) + a power mode (Mission Control for multi-property) + a mobile companion (Card Deck or Pure Chat).

### `ai-rm-wireframes-v3.html` (Wurf 3)
Dashboard evolution with AI sidekick. Originally built brutalist (heavy black borders, monospace, acid yellow), then **rebuilt as clean wireframe** per Philipp's feedback ("brutalist finde ich kacke"). Inter font, 1px borders, blue accent, soft cream background. Single-screen wireframe with rail-nav + briefing + persistent AI sidekick on right.

### `ai-rm-wireframes-v4.html` (Wurf 4 · Synthesis · iteration archive)
First v4 attempt — Marketing landing page mit beiden Personas Anna + Kai als Sections nebeneinander. Verworfen, weil Philipp keine Landing Page wollte sondern reine Wireframes der zwei Erfahrungen. Bleibt als Referenz / Iterationsarchiv.

### `ai-rm-wireframes-v4 Kopie.html` (Wurf 4 · Master · Tally-style)
Die zentrale gemeinsame Basis für Anna + Kai. **Premium Editorial Style** entlang `design.md` Spec: Instrument Serif (Display), Inter (Body), JetBrains Mono (Numbers + Mono-Tags), Ink-Blue Accent (`#1e3a5f`, kein sage green mehr), warmes Off-White (`#f6f5f1`).

Enthält **beide** Personas in einer Datei:
- **01 Hotelier Mode (Anna):** Briefing-Card als zentrales Dokument, Greeting, Stats-Stack, Decision-Card mit "Ray fragen" Button (Ink-Blue Outline + Diamond-Mark), 7-Tage-Outlook mit italic Status-Words ("ruhig"/"stark"/"Pfingsten") statt Wetter-Emojis, Ray-Strip am Ende (statt Marc).
- **02 Experten Mode (Kai):** Volle Preistabelle, dann zwei Mockup-Cards (Pickup + Comp-Set) im **fin.ai Bar-Chart Pattern** mit dotted halftone fills, Y-Axis-Hairlines (gleichmäßige 40px Skalierung), open-bottom Bars hinter sichtbarer Baseline.

Wichtige Design-Decisions in dieser Datei:
- Logo-Icon als SVG (nur das geometrische "h"-Treppen-Symbol, kein Wordmark) — color via `currentColor`, eingefärbt in accent
- Trend-Pillen (`↑ 12 %`) inline im Briefing-Text mit accent-soft Bg, scharfe Kanten
- `.detail` Drilldown-Links mit dashed underline (CSS `text-decoration: underline dashed`)
- Diamond-Marker (rotated 7×7 square, accent) als wiederkehrendes System-Element
- Card-Pattern: weiße Surface, 12px border-radius, subtle shadow (matching rest of UI, nicht das brutalere "warm outer + paper inner" pattern)
- Comp-Set positioniert Hotel als "Oberes Drittel" (2. von 5, nicht teuerste) — hospitality-realistisch, nicht "Premium-Top" Bragging
- Charts haben Hero-Stat (italic Serif `+24` + mono uppercase context) + Delta-Zeile statt 3 dry rows
- Zahlen durchgehend JetBrains Mono mit `tabular-nums` per design.md Spec
- "Marc" wurde umbenannt zu **"Ray"** (Chatbot-Name)

### `ai-rm-wireframes-v4-anna.html` (Anna Deep-Dive)
**Detailfile für Hotelier Mode — Ray Interaktions-Patterns.** Fünf Screens, jeweils mit Frame-Header + App-Frame Mock:
- **01 Daily Briefing** — Standard-Dashboard wie in v4 Kopie
- **02 Modal · Ray-Konversation** — iOS-style Bottom-Sheet Modal (full-width, bottom-anchored, top-rounded). Dashboard im Hintergrund mit `backdrop-filter: blur(4px)` + leichtem Dim (`rgba(20,22,30,0.06)`). Pull-Handle oben. Ray-Conversation mit Kontext-Banner, Anna-Frage → Ray-Antwort mit Mini-Forecast-Card, Suggested Follow-ups, Input. *Hinweis: Vorher-Zwischenstand "Floating Detached Panel" wurde verworfen für full-width Modal.*
- **03 Inline Drilldown** — Klick auf dotted-underline `.detail` Link expandiert Erklärung **inline im Briefing-Text** (zwischen den zwei Narrativ-Paragraphen). Hairline-only Pattern (per `/impeccable polish`): keine nested boxes, keine side-stripe border (Absolute Ban), kein eigener Background. Mono-Tag Header + Summary + Daten-Tabelle (Tag/Vorher/Neu/Grund) + Action-Row (primary button + ghost text-link). Komplettes Briefing umrahmt das Drilldown (Stats, Decision, Week, Ray-Strip nach dem Drilldown weiter sichtbar).
- **04 Embedded Sidekick + Spotlight** — Ray rechts fest verankert (3-col Grid: 88px rail + 1fr main + 420px ray-embedded), kein Float. Im Briefing-Bereich wird **nur das aktive Element scharf** dargestellt (Großgruppe Decision Card mit accent outline + soft shadow), alle anderen Briefing-Children werden via `filter: blur(2.5px); opacity: 0.42` ausgeblendet. Ray-Conversation rechts zeigt kontextuelle Tiefe (Anna fragt "Erklär mir die Verdrängung nochmal", Ray antwortet mit detaillierter Mini-Card).
- **05 Tabbed Modal · Multi-Session** — Wider Bottom-Sheet Modal (920px max, 600px high) mit gleicher Blur-Backdrop wie Section 02. **Tab-Strip oben** mit 4 parallelen Sessions (Topic-basiert, KEINE Person-Avatare): Großgruppe Berlin (active, live dot) · MinLOS Festwochenende (waiting dot) · Direkt-Kanal Boost (idle) · Rate-Strategie Sommer (idle). Aktiver Tab: weiß + accent-Border + Diamond-Marker prominent. Plus "+" Button rechts (36×36 Square mit 1.5px Accent-Outline + Ray-Diamond-Marker zentriert) für neue Session. Context-Bar zwischen Tabs und Body. Conversation tieferer Inhalt (Verhandlungs-Spielraum: "Anker bei 119 €, Spielraum bis 109 €").

**Verworfene Zwischenstände in Section 05** (vor Tabbed Modal):
- Linkedin-Style Person-Avatare (Ray + Marc + Lisa nebeneinander) — verworfen, weil Identity sollte Topic sein, nicht Person
- Topic-basierter Session Stack mit überlappenden Cards (negative margin) — verworfen ("sieht broken aus, partielle Buchstaben")
- Topic-basierter Stack mit 48×48 Icon-Chips — verworfen ("hmmm das ist es auch nicht")
- → Tabbed Modal als finale Lösung (cleaner, mehr screen real estate, sessions klar listbar)

### `ai-rm-wireframes-v4-kai.html` (Kai · WIP)
Aktuell nur Section 01 (Experten Mode). CSS für Ray-Panel ist vorbereitet, Detail-Screens (Empfehlung Deep-Dive, Verhalten konfigurieren) sind noch nicht gebaut. **Auf Wunsch von Philipp pausiert — separate Session.**

### `design.md` (Design Spec)
Tally-inspirierte Design-Spec mit konkreten Tokens. Authoritative source für:
- Schriften (Instrument Serif Display + DM Sans/Inter Body + JetBrains Mono)
- Farben (paper, warm, ink, accent, muted-text — alle als CSS-Vars)
- Typografie-Skala (clamp-basiert)
- Mockup-Card Pattern, Stat-Card-Stack, Italic Pull-Quote
- Anti-Patterns (keine border-radius auf Cards, keine Gradients/Shadows/Glow, kein bg-white)

### `PRODUCT.md` (Impeccable Skill Context)
Nutzer-Profil, Strategic Principles, Tone, Anti-References. Für `/impeccable` Skill als Context-File.

### `persona-anna.md` und `persona-kai.md` (Persona Reference)
**PFLICHTLEKTÜRE** vor jeder Design-Entscheidung. Vollständige Persona-Profile mit:
- Identität (Name, Rolle, Hotel-Kontext, Tier)
- Tag im Leben (wann kommt sie/er ins Tool, wie lange, in welchem Modus)
- Goals & Pain Points
- Sprach-Cheat-Sheet (sie sagt X, NICHT Y)
- UX-Prinzipien für die Persona
- Anti-References (was NICHT)
- Etablierte Patterns aus den Wireframes
- Geplante Patterns (TODO)

Anna ist Primary, Kai ist Secondary. Beide teilen dasselbe Datenmodell + Ray AI.

### `ai-rm-anna-standalone.html` (Standalone Briefing)
Daily Briefing als **edge-to-edge fullscreen Erlebnis**, ohne Wireframe-Wrapper. Gleiche Inhalte wie Section 01 in `ai-rm-wireframes-v4-anna.html`, aber:
- Kein Frame-Section / Eyebrow / Headline / Description Wrapper
- Kein App-Frame Border / Border-Radius / Shadow
- Page-Padding entfernt — UI läuft bis zur Viewport-Kante
- Topbar und h-rail (inkl. Setup) **sticky** beim Scrollen via `position: sticky` + `overflow: visible` Override
- Schrift: EB Garamond serif für Headlines (italic killed via global `em { font-style: normal }`)

Zum Aufzeigen wie sich das Produkt im Vollbild anfühlt — für User-Tests und Stakeholder-Demos.

### `ai-rm-design-system.html` (Design System Übersicht)
**Stakeholder-ready Design-System Showcase** im Slate&Bone-Stil (dotted dark background + cremefarbenes Container-Frame mit purple-blue 2.5px Outline + 4-Spalten Grid mit Pattern-Cards). Komplette Token + Patterns auf einer Seite:
- Color-Cards (Ink, Accent, Muted, Paper) mit 10-Step-Skala pro Farbe
- Typography-Cards (Display Instrument Serif "A*a*", Body Inter "Aa", Mono JetBrains Mono "Aa")
- Pattern A: Headline mit italic accent, Buttons (primary/ghost/ray), Stat-Block
- Pattern B: Mono-Tags + Diamond-Größenskala (s/m/l/xl), Trend-Pills + Status-Dots, Charts (dotted Bar-Chart Mini + dashed-underline Detail-Link)
- Bottom-Row: Decision-Card, Input mit Kontext-Anker, Tabs mit Ray-Diamond-Plus-Button, Mini-Briefing-Sample
- Eine Seite, alle Tokens und Komponenten — übergebbar an Stakeholder ohne fünf Wireframe-Sections durchgehen zu müssen.

---

## 6. User profile — Philipp Schulz

- Founder / product at happyhotel
- Communicates in German, "du" form
- Pattern: iterative wurfs. Says "nicht verwerfen, mache aber einen neuen Wurf" → always preserve previous attempts.
- Likes me to push the solution space (multiple distinct directions) before converging
- Aesthetic signal so far: brutalist wireframes preferred over polished mockups for this exploration phase
- Strategic mode — doc-driven, comfortable with abstraction, reads carefully

---

## 7. Open questions / context still missing

Asked but not yet answered:
1. **Customer discovery material** — Owner/GM interviews, transcripts, NPS themes, support tickets about trust. Critical for getting briefing language right.
2. **Today's Copilot RM + Autopilot baseline in numbers** — % adoption, top 3 user questions, current escalations. Needed to calibrate the November 2026 jump.
3. **RM Expert Team operating model** — size end-2026, hotels per expert, tools, touch-point promises per tier. Required to design "human in the product" credibly.

---

## 8. Design System / Tokens (ab Wurf 4)

Aus `design.md` synthesiert + projektspezifisch erweitert:

```css
/* Surfaces */
--bg:           #f6f5f1;   /* warm off-white page */
--shell:        #fafaf7;   /* slightly warmer */
--surface:      #ffffff;   /* white cards */
--surface-2:    #f7f6f2;   /* subtle elevation */

/* Ink */
--ink:          #18181a;   /* near-black */
--ink-2:        #3a3a3d;   /* body text */
--muted:        #6e6e72;   /* secondary text */
--subtle:       #a8a8ac;   /* tertiary */

/* Accent — Ink Blue (NOT sage green, NOT royal blue) */
--accent:       #1e3a5f;   /* main interactive */
--accent-soft:  #ebf0f6;   /* tinted bg */
--accent-line:  #b8c4d4;   /* hairline accent */
--accent-deep:  #14294a;   /* hover/pressed */

/* Borders */
--border:       #e6e5df;   /* hairlines */
--border-2:     #c9c8c2;   /* stronger */
--border-3:     #a6a5a0;
```

**Schriften:**
- `Instrument Serif` (italic + roman) — Headlines, Hero-Stats, Italic-Akzente in Body, Avatar-Buchstaben **(Master-Files)**
- `EB Garamond` — alternate Serif, getestet in `ai-rm-anna-standalone.html` und `ai-rm-wireframes-v4-anna.html` als Probe ob klassischere Renaissance-Antiqua passt
- `Inter` — Body Text (14–17px), UI Labels
- `JetBrains Mono` — Mono-Tags (10px uppercase 1.5–3px tracking), Numbers (tabular-nums), Data-Tables
- **Italic-Style auf Anna's Files killed** (per Philipp · `font-style: italic` → `normal` + globaler `em { font-style: normal }` Override). Akzent-Hervorhebung läuft jetzt nur noch über Farbe + Weight, nicht über Italic. **NICHT** in v4 Kopie / v4-kai übernommen — dort bleibt Italic-Akzent.

**Wiederkehrende Pattern:**
- **Diamond-Marker** (rotated 7×7 square in accent) als visuelles System-Element vor Tags und in CTAs
- **Mono-Tag** (10px, uppercase, 2.4px letter-spacing, accent oder muted)
- **Italic Serif Akzent** auf letztem Wort einer Headline
- **Hairlines** (`1px var(--border)`) statt nested boxes
- **Trend-Pillen** inline: `↑ 12 %` mit accent-soft Bg, mono tabular-nums
- **Status-Dots**: live (#22c55e) · waiting (accent) · idle (subtle)
- **Ray-Button-Pattern**: 1.5px accent border + accent text + Diamond-Marker davor (entweder mit Label "Ray fragen" oder Icon-Only 36×36 Square mit zentriertem Diamond)
- **Detail-Link**: dashed underline in accent (CSS `text-decoration: underline dashed`) für drilldown-Trigger im Body-Text
- **No em-dashes in copy** — comma/colon/parens (impeccable spec)

**Anti-Patterns (impeccable Bans):**
- Side-stripe borders (`border-left: 3px` als Akzent)
- Nested cards / multi-layered backgrounds
- Hero-metric template (big number + small label + supporting stats + gradient)
- Gradient text
- Modal-as-first-thought
- Card grids identisch repeated

---

## 9. How to continue this work

If starting a fresh session:
1. **Read this CLAUDE.md** (root) — orientation
2. **Read `docs/persona-anna.md` und `docs/persona-kai.md`** — PFLICHT vor Design-Entscheidungen
3. Open one of these in the browser je nach Bedarf:
   - `wireframes/master/ai-rm-wireframes-v4 Kopie.html` — Master state (Anna + Kai Dashboards)
   - `wireframes/master/ai-rm-wireframes-v4-anna.html` — 5 Ray-Interaktions-Pattern Deep-Dives
   - `wireframes/standalone/ai-rm-anna-standalone.html` — Daily Briefing edge-to-edge (User-Test ready)
   - `wireframes/design-system/ai-rm-design-system.html` — Token/Pattern Showcase (Stakeholder-ready)
4. Read `docs/design.md` for design tokens / typography / pattern spec
5. Read `docs/PRODUCT.md` if running `/impeccable` skill (it's the context file)

**Do NOT:**
- Recreate previous wurfs
- Use polished marketing-style mockups when wireframes are wanted
- Forget the Owner/GM ≠ professional RM distinction
- Treat the human experts as separate support — they live inside the product
- Auto-`open` files in the browser after edits — Philipp reloads selbst (siehe Memory)
- Side-stripe borders / nested cards (AI-slop Patterns, impeccable banned)
- Use sage green as accent (changed to ink-blue for happyhotel brand fit)
- Em-dashes (`—`) in body copy (impeccable spec — use commas/colons/parens)

---

## 10. File inventory

Project ist seit Mai 2026 in Subfolder organisiert. Struktur:

```
HappyHotel/
├── CLAUDE.md                                    ← this file (root, immer als erstes lesen)
│
├── docs/                                        ← markdown Dokumentation
│   ├── PRODUCT.md                               ← /impeccable context
│   ├── design.md                                ← Tally-style design spec (tokens, patterns)
│   ├── persona-anna.md                          ← Anna (Owner/GM) Persona · PFLICHT
│   ├── persona-kai.md                           ← Kai (Senior RM) Persona · PFLICHT
│   └── user-stories-l1-l2.md                    ← User Stories L1/L2 JTBD
│
├── wireframes/
│   ├── history/                                 ← Iterations-Archiv (nicht löschen, Referenz)
│   │   ├── ai-rm-wireframes.html                ← Wurf 1 (7 cohesive screens)
│   │   ├── ai-rm-wireframes-v2.html             ← Wurf 2 (6 packaging directions)
│   │   ├── ai-rm-wireframes-v3.html             ← Wurf 3 (Dashboard + Sidekick, clean wireframe)
│   │   └── ai-rm-wireframes-v4.html             ← Wurf 4 first iteration (landing-style)
│   │
│   ├── master/                                  ← aktive v4 Master-Files
│   │   ├── ai-rm-wireframes-v4 Kopie.html       ← Master (Anna + Kai, premium Tally-style)
│   │   ├── ai-rm-wireframes-v4-anna.html        ← Anna Deep-Dive (5 Ray-Patterns) · ⚠ EB Garamond, italic killed
│   │   ├── ai-rm-wireframes-v4-kai.html         ← Kai Section 01 (TODO: Ray detail screens)
│   │   └── ai-rm-wireframes-v4-kai-page1.html   ← Kai-Mode Page 1 (frühes Experiment)
│   │
│   ├── personas/                                ← Persona-Showcase HTML Pages (visuell)
│   │   ├── ai-rm-wireframes-v4-anna-persona.html (+ Kopie)
│   │   ├── ai-rm-wireframes-v4-kai-persona.html  (+ Kopie)
│   │   └── ai-rm-wireframes-v4-ray-persona.html  (+ Kopie)
│   │
│   ├── standalone/
│   │   └── ai-rm-anna-standalone.html           ← Anna Daily Briefing edge-to-edge, sticky chrome
│   │
│   └── design-system/
│       └── ai-rm-design-system.html             ← Tokens + Pattern Showcase (Slate&Bone-Style)
│
└── assets/
    ├── screenshots/                             ← Screenshots des heutigen happyhotel Produkts (13 PNGs vom 29.04.2026)
    └── references/
        └── fin-ai-detail.png                    ← fin.ai Visual-Referenz (Bar-Chart-Pattern Inspiration)
```

**Wichtige Pfad-Konventionen:**
- Markdown-Docs immer in `docs/`
- HTML-Wireframes nach Status sortiert (history → master → standalone/design-system)
- `personas/` enthält Visual-HTML-Cards der Personas (NICHT die markdown Persona-Profile, die liegen in `docs/`)
- `master/` ist wo aktiv weiterentwickelt wird

---

## 11. Ray-Interaktions-Patterns (etabliert in Anna-File)

Fünf distinkte Patterns für AI-Konversation — jeweils für andere User-Intentionen:

| Pattern | Trigger | Layout | When to use |
|---|---|---|---|
| **Modal Bottom-Sheet** (S. 02) | "Ray fragen" Button | Full-width Modal von unten, Dashboard mit blur(4px) Backdrop | Single Decision Delegation, fokussiertes Gespräch |
| **Inline Drilldown** (S. 03) | Dotted-underline `.detail` Link in Body-Text | Inline-Expansion zwischen Paragraphen, Hairline-only, kein Container | Quick "warum" / Erklärung im Lese-Flow |
| **Embedded Sidekick + Spotlight** (S. 04) | "Mit Ray besprechen" Button | Permanent rechts angedockt (420px), spotlight-Pattern auf relevanten Briefing-Teil, Rest blur+opacity | Tieferes Gespräch über ein einzelnes Thema |
| **Tabbed Modal · Multi-Session** (S. 05) | "Mit Ray besprechen" + bestehende Sessions vorhanden | Wider Bottom-Sheet (920px), Tab-Strip oben mit Topic-Sessions, Status-Dots, "+" Button mit Diamond | Mehrere parallele Themen, Wechsel zwischen Sessions |
| (Floating Detached Panel) | (verworfen) | Free-floating right side mit eigener Drop-Shadow | Zwischenstand vor Modal Bottom-Sheet |
| (Linkedin Person-Stack) | (verworfen) | Bottom-rechts gestapelte Person-Avatare (Ray + Marc + Lisa) | Identity sollte Topic sein, nicht Person — verworfen |
| (Topic Icon-Chips) | (verworfen) | 48×48 Mini-Chips mit Diamond + Status-Dot | "Hmm das ist es auch nicht" — durch Tabbed Modal ersetzt |

Strategy PDF lebt im Session uploads Ordner, nicht in diesem Directory.
