# Persona — Anna · Hotelier / Owner

**Die primäre Zielgruppe für happyhotel.** Owner/GM, kein professioneller Revenue Manager. Repräsentiert die "Missing Middle" der ICP-Definition: mittelgroße unabhängige Hotels, Owner trägt selbst die kommerzielle Verantwortung.

---

## 1. Identität

| | |
|---|---|
| **Name** | Anna B. |
| **Rolle** | Owner / GM, alleinverantwortlich |
| **Hotel** | Hotel Seeblick · Berlin · 80 Zimmer · Boutique · 4★ |
| **Umsatz** | ~ 2,4 M €/Jahr |
| **Team** | 12 FTE · Front Office, Service, Housekeeping, Küche · KEIN dedizierter Revenue Manager |
| **Alter / Hintergrund** | ca. 45 · Hotelfachschule · 18 Jahre Branche, 9 Jahre Hotelbesitzerin |
| **Tarif (in unserem System)** | Senior RM (12 €/Zimmer/Monat) |

---

## 2. Tag im Leben

- **6:30** — aufstehen, vor dem Frühstück kurzer Blick aufs Telefon
- **7:00–9:30** — Frühstücksservice, mit Gästen reden, Beschwerden, Operatives
- **10:00** — Büro: Buchhaltung, Personal, Bewertungen, Lieferantengespräche
- **11:00** — *Hier öffnet sie happyhotel das erste Mal heute* · liest Morning Briefing
- **12:00–17:00** — Termine, Booking-Anfragen, Marketing
- **17:00** — schaut nochmal kurz: gibt es Entscheidungen mit Frist?
- **abends** — Service, Gäste, ad-hoc

> **Insight:** Anna verbringt **maximal 15–20 Minuten pro Tag** in happyhotel, in 2–3 Sessions. Das Tool muss sich in diese Zeit fügen, nicht ihren Tag dominieren.

---

## 3. Goals & Motivations

- **Geld verdienen** — der einzige KPI, der für sie zählt. Alles andere ist Mittel zum Zweck.
- **Operativ entlastet sein** — sie hat 50 Themen pro Tag, Pricing soll nicht eines davon sein
- **Kontrolle behalten** ohne Expertise aufbauen zu müssen — sie hat ihren Steuerberater nicht gehasst, weil er die Steuern kann; sie will den gleichen Vertrauensvertrag mit Ray
- **Stolz auf ihr Hotel** — sie will, dass es premium wahrgenommen wird, nicht das billigste

## 4. Pain Points (heute, ohne Ray)

- Liest Excel-Reports, ohne zu wissen ob sie alles richtig macht
- Verpasst Pricing-Chancen, weil sie nicht 24/7 aufpassen kann
- Comp-Set-Tools sind zu komplex, sie versteht die Kennzahlen nicht
- Buchhaltung sagt erst Monate später, ob ein Monat gut war
- "Wenn ich einen RM einstellen würde, könnte ich mir das nicht leisten"

## 5. Sprache & Kommunikation

| Sie sagt | NICHT |
|---|---|
| "Wieviel hab ich verdient?" | "Wie ist mein RevPAR?" |
| "Der Mai war stark" | "Ø ADR 142 vs. STR Sample +4 Punkte" |
| "Pfingsten lief gut" | "Pickup Volume 71 % über Forecast" |
| "Soll ich die Gruppe annehmen?" | "Group Displacement Analysis" |
| "Was hast du heute Nacht gemacht?" | "Show me last automation log" |

**Form:** "Du" (geduzt), warm aber direkt, kein Smalltalk. Keine Emojis. Kein Marketing-Sprech.

---

## 6. UX-Prinzipien für Anna

1. **Bringschuld, nicht Holschuld** — das System kommt zu Anna (Briefing, Push, Inbox), Anna kommt nicht zum System
2. **Geld vor KPIs** — jede Zahl wird in Euro übersetzt, nicht in RevPAR/ADR
3. **Eine Erkenntnis pro Bildschirm** — keine 12-Spalten-Walls, klar kuratiert was wichtig ist
4. **Erklärbarkeit > Optimierung** — lieber "logisch und klar" als "wissenschaftlich perfekt"
5. **Hybrid sichtbar** — Ray (AI) + Marc/Lisa (Menschen) im selben Stream, nie als getrennter Support-Kanal
6. **Outcome-First Navigation** — wenn Tabs/Sections, dann nach Geschäftszielen, nicht nach Features
7. **Vertrauen abgestuft, nicht binär** — Anna sieht was Ray darf, was zu Marc geht, was zu ihr eskaliert wird

## 7. Anti-References (was NICHT für Anna)

- ❌ Brutalist / nerdy Wireframes — sie ist GM, nicht Designer
- ❌ Fachjargon ohne Übersetzung
- ❌ Customizable Dashboards — sie will nicht selbst kuratieren
- ❌ Multi-Tab-Workflows — sie hat dafür weder Zeit noch Geduld
- ❌ Trial & Error UX — jede Aktion muss sich sicher anfühlen
- ❌ "Power User" Features — die wären für Kai

---

## 8. Etablierte Patterns für Anna (Wireframe v4)

- **Daily Briefing** als Front Door — narrative Erzählung statt Dashboard, EB Garamond Serif Headlines
- **Trend-Pillen inline** im Body-Text (`28.420 € ↑ 12 %`) — sofortige visuelle Geld+Wachstum-Story
- **Decision-Card** mit Ray-fragen Button (Outline + Diamond) — One-Click-Eskalation an AI
- **Wochen-Outlook** mit Status-Words ("ruhig"/"stark"/"Pfingsten") statt Wetter-Icons oder KPIs
- **Ray-Strip** am Briefing-Ende — Marc/Lisa als Backup-Kollegen sichtbar
- **Detail-Links** mit dashed underline im Body-Text öffnen Inline-Drilldown ohne Modal-Bruch

## 9. Ray-Interaktions-Patterns für Anna (alle in `wireframes/master/ai-rm-wireframes-v4-anna.html`)

1. **Modal Bottom-Sheet** — fokussierte Ja/Nein-Decision Delegation
2. **Inline Drilldown** — Quick "warum" Erklärung im Lese-Flow
3. **Embedded Sidekick + Spotlight** — tieferes Gespräch zu einem Thema, mit Briefing dimm/blur
4. **Tabbed Modal · Multi-Session** — mehrere parallele Topic-Sessions, Tab-Wechsel ohne Faden-Verlust
