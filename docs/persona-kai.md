# Persona — Kai · Senior Revenue Manager

**Die zweite Zielgruppe für happyhotel — Profi-Nutzer.** Beruflicher RM, betreut mehrere Häuser im Cluster oder einer Kette. Repräsentiert die größere etablierte Hotel-Branche, die bereits einen RM-Workflow hat und nicht "von Null" anfängt.

---

## 1. Identität

| | |
|---|---|
| **Name** | Kai R. |
| **Rolle** | Senior Revenue Manager · Cluster Lead |
| **Cluster** | 6 Hotels · 1 Resort, 2 Boutique, 3 Business · 280–620 Zimmer Range |
| **Kette / Eigner** | mittelgroße deutsche Gruppe, ~30 Häuser gesamt |
| **Team** | 1 Cluster Lead (Kai) + 2 Junior RMs unter ihm |
| **Alter / Hintergrund** | ca. 32 · BWL/Hospitality + RM-Zertifizierung · 8 Jahre RM-Erfahrung, davor 4 Jahre Operations |
| **Tarif (in unserem System)** | Revenue Director (20 €/Zimmer/Monat) |

---

## 2. Tag im Leben

- **8:00** — am Schreibtisch, zwei Monitore, Kaffee
- **8:15** — Cluster-Briefing: alle 6 Hotels durchsehen, Ausreißer markieren
- **9:00** — Daily Standup mit Junior RMs (Slack/Teams)
- **9:30–12:00** — Rate-Adjustments, Restrictions, Channel-Hygiene, AI-Empfehlungen reviewen
- **13:00** — Bi-weekly Calls mit Hotel-Direktoren (jedes Hotel alle 2 Wochen)
- **14:00–17:00** — Tiefer-Analyse, Pickup-Curves, Comp-Set-Anomalien, Forecast-Tuning
- **17:00** — Tagesabschluss-Report an die Geschäftsführung

> **Insight:** Kai verbringt **6–8 Stunden pro Tag** in RM-Tools. Geschwindigkeit pro Aktion zählt. Power-User-Shortcuts, dichte Information, Bulk-Actions sind Pflicht.

---

## 3. Goals & Motivations

- **RevPAR-Maximierung über alle 6 Hotels** — er wird daran gemessen
- **Skalieren ohne mehr Junior-RMs einstellen zu müssen** — AI als Force-Multiplier
- **Anomalien schnell erkennen und gegensteuern** — bevor sie eine ganze Woche kosten
- **Saubere Reportings für die GF** — er muss erklären können warum welche Entscheidung
- **Branchen-Reputation halten** — er ist auf RM-Konferenzen, kennt die Tools, will nicht mit "Spielzeug" arbeiten

## 4. Pain Points (heute, ohne Ray)

- Klick-intensive Pricing-Tools, repetitive Aktionen
- AI-Tools die ihm widersprechen ohne Begründung — er braucht Audit-Trail
- Cross-Property-Vergleiche sind in den meisten Tools nicht durchdacht
- Anomalien werden zu spät erkannt (z.B. Comp-Set-Hotel mit Software-Panne)
- Budget-Reports an die GF sind manueller Excel-Frickelkram

## 5. Sprache & Kommunikation

| Er sagt | Er kennt auch | Hat keine Geduld für |
|---|---|---|
| "Pickup ist 3× über Schnitt" | RevPAR · ADR · Occ · ARI · MPI · STR | "Du hast verdient" Sprache |
| "MinLOS 3 für KW 21 aktivieren" | Channel Manager · Restrictions · CTA/CTD | "Wetter-Icons" für Demand |
| "Comp-Set Median 134, du bist +8" | Pickup-Heatmap · Booking Curve · Pace | Kindergarten-UX |
| "Displacement: 12 Buchungen gegen 24 Zimmer" | Group Displacement · Yield Management | Fehlende Tastatur-Shortcuts |
| "Ray, override für Sa 18.5 auf 195" | Direct Bypass von AI Recs | Modale Pop-ups bei jedem Click |

**Form:** "Sie" oder "Du" je nach Setup (häufig per "Du" in jüngeren Häusern), präzise und kompakt, gerne Fachbegriffe.

---

## 6. UX-Prinzipien für Kai

1. **Tiefe vor Breite** — er braucht alle Daten, nicht eine kuratierte Auswahl
2. **AI als Copilot, nicht als Boss** — Ray empfiehlt, Kai entscheidet, immer mit One-Click-Override
3. **Reasoning sichtbar** — jede AI-Empfehlung mit Begründung, Pickup-Daten, Comp-Set-Kontext (er prüft jedes Mal)
4. **Bulk-Actions** — über mehrere Hotels und Tage gleichzeitig agieren können
5. **Dichte erlaubt** — er hat trainierte Augen für Tabellen, Heatmaps, dichte Charts (anders als Anna)
6. **Audit-Trail komplett** — jede Anpassung loggable, exportierbar, an die GF weitergebbar
7. **Tastatur-First** — Shortcuts für alles Wiederkehrende
8. **Cross-Property-Vergleiche überall** — Cluster-Sicht ist sein Mental-Modell, nicht Single-Property

## 7. Anti-References (was NICHT für Kai)

- ❌ Outcome-Sprache ohne Zahl ("Du hast 12 % mehr verdient" — er will absolute Werte UND Vergleichswerte)
- ❌ Wetter-Icons / niedliche Status-Wörter — er will Prozent, RevPAR, Pickup
- ❌ Single-Hotel-Fokus — er denkt im Cluster
- ❌ "Tagesbriefing als Front Door" — er kommt direkt in die Preistabelle
- ❌ Modal-First Workflows — er will Inline-Editing
- ❌ Versteckte Power-Features hinter "Mehr anzeigen" Klicks
- ❌ Lange Onboarding-Tours — er kennt RM-Tools, lass ihn arbeiten

---

## 8. Etablierte Patterns für Kai (Wireframe v4 Kopie)

- **Volle Preistabelle** als Front Door — 7 Tage × 4 Wochen, kompakt, klickbar
- **Hero-Stat in Charts** — italic Serif `+24 Zimmer Pickup` mit Mono-Context-Label und Delta-Zeile (vs. Vorjahr · vs. Plan)
- **Mockup-Card Pattern** für Pickup + Comp-Set — single weiße Card, hairline-getrennt, gleiche Höhe via flex
- **fin.ai Bar-Chart** — dotted/halftone Pattern, gleiche 40px Y-Achsen-Skalierung, Bars ohne Bottom-Border hinter sichtbarer Baseline
- **Comp-Set positioniert auf "Oberes Drittel"** — 5 Hotels, Du auf Rang 2 (nicht teuerste = hospitality-realistisch)
- **AI-Mark Diamond** auf Cells die Ray angefasst hat — visueller Audit-Trail in der Tabelle

## 9. Ray-Interaktions-Patterns für Kai (TODO · noch nicht gebaut)

Geplant in `wireframes/master/ai-rm-wireframes-v4-kai.html` (CSS vorbereitet, HTML noch offen):
1. **Empfehlung Deep-Dive Panel** — Ray öffnet Begründung mit Pickup-Curve, Comp-Set, Displacement-Modell, Ausführen/Anpassen/Ablehnen Buttons
2. **Decision Log / Audit-Trail** — was hat Ray getan, warum, mit welchem Outcome
3. **Verhalten konfigurieren** — Schwellenwerte (max ±%), Eskalationsregeln, Auto-Approve-Bereiche pro Hotel
4. (Optional) **Cross-Property Bulk-View** — Ray-Empfehlungen über alle 6 Hotels gleichzeitig reviewen

---

## 10. Geteilt mit Anna

Kai und Anna nutzen **dasselbe System, dieselbe KI, dasselbe Decision Log**. Was Ray für Anna entscheidet, sieht Kai im Audit-Trail. Was Kai konfiguriert, lernt Ray für Anna mit. Die Trennung ist **rein die Darstellungsschicht** — kein zweites System.

**Identity Routing**: Beim Login wird der Mode zugewiesen. Ein Hotel-Account kann beide Seats vergeben (z.B. wenn Kette-Hotels Anna-Mode für GMs UND Kai-Mode für Cluster-RM brauchen).
