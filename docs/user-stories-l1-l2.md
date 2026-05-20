# User Stories · Anna-Mode (Hotelier) · L1 + L2

JTBD Level 1 und Level 2 aus der happyhotel-Strategie, übersetzt in User Stories. Nur zwei Personas: **Anna** als User, **Ray** als ihr AI Revenue Manager. Stories für den Experten-Mode (Kai) folgen separat.

---

## Die zwei Personas

### Anna · Owner / GM
Anna besitzt und führt ein 80-Zimmer-Hotel in Berlin. Sie ist keine Revenue-Managerin und will auch keine werden. Ihr Tag besteht aus Frühstücks-Service, Buchhaltung, Gästegesprächen, Bewerbungs-Interviews. Pricing erledigt sie heute "im Vorbeigehen" zwischen zwei Meetings, hat permanent das Gefühl, Geld liegen zu lassen, weiß aber nicht, wo. Sie misstraut komplizierten Tools, vertraut Menschen mehr als Software. Ihr Owner-Geschäftspartner stellt jeden Monat unbequeme Fragen, die sie spontan nicht beantworten kann.

**Sie will:** Klarheit, Entlastung, mehr Geld am Ende des Monats, ohne RM-Expertin werden zu müssen.

### Ray · AI Revenue Manager
Ray ist Annas eingestellter AI Revenue Manager. Kein Tool, kein Assistent: ein Mitarbeiter, den sie an Bord geholt hat. Ray hat Annas Strategie verstanden, ihre Eigenheiten gelernt, und arbeitet still im Hintergrund, bevor Anna morgens den Kaffee aufsetzt. Ray ist still, kompetent, erklärt sich auf Knopfdruck, fragt nach, wenn er unsicher ist. Ray will Anna nicht beeindrucken; Ray will Anna entlasten.

**Wichtig:** Hinter Ray arbeiten auch echte Menschen (das Hybrid-Modell der Strategie), aber Anna sieht keine separaten Personen oder Support-Channels. Ray repräsentiert das gesamte Hybrid-System; bei komplexen Fällen sagt Ray "ich kläre das" und liefert das Ergebnis, ohne dass Anna wissen muss, ob ein Mensch dahinter mitgearbeitet hat.

**Er kann:** alles, was ein Junior- bis Senior-RM könnte, in der Hälfte der Zeit, 24/7, lernfähig.

---

## Trust-Levels (gelten in jeder Story)

- **AUTO:** Ray macht still, Anna sieht es nur im Decision Log oder im Briefing
- **ALERT:** Ray macht und sagt Anna Bescheid
- **APPROVE:** Ray schlägt vor, Anna bestätigt mit einem Tap
- **ASK:** Ray fragt vorab, bevor er handelt

Defaults kommen aus dem gebuchten Tarif (Revenue Manager / Senior RM / Director); Anna kann pro Dimension feinjustieren.

---

## Ray-Interaktions-Pattern (kanonische Trigger)

Aus CLAUDE.md Sektion 11 etabliert. Stories nutzen diese Labels konsequent:

| Trigger | Pattern | Wann |
|---|---|---|
| **"Ray fragen"** Button | Modal Bottom-Sheet (Dashboard blurred) | Konkrete Entscheidungs-Delegation |
| Dotted-underline `.detail` Link | Inline Drilldown (Hairline-only, im Lese-Flow) | Kurze "warum"-Erklärung beim Lesen |
| **"Mit Ray besprechen"** Button | Embedded Sidekick + Spotlight (rechts angedockt) | Tieferes Gespräch über ein Thema |

---

## Level 1 · Execute & Monitor
Was Ray für Anna komplett übernimmt.

### Job 1.1 · Morgenritual & Tagesstatus

**US-1.1.1 · Ray bringt den Tag in einem Satz auf den Punkt**
Als Anna möchte ich morgens beim Kaffee von Ray in einem Satz hören, ob alles auf Kurs ist, damit ich nicht selbst Reports parsen muss.
- Ray meldet sich zwischen 06:00 und 08:00 (Anna wählt Uhrzeit)
- Der erste Satz beantwortet "läuft es?" mit einer Geld-Zahl, kein RM-Jargon
- Auch ruhige Nächte bekommen einen Eintrag ("alles ruhig, nichts zu tun")
- Anna kann jeden Punkt aufklappen (`.detail` dotted underline) oder ignorieren
- **Trust:** AUTO

**US-1.1.2 · Anna sieht "alles okay?" jederzeit in 3 Sekunden**
Als Anna möchte ich tagsüber im Vorbeigehen prüfen, ob alles in Ordnung ist, ohne ein Dashboard zu öffnen.
- Ein einziger Status-Indikator (grün, gelb, rot) in der Topbar
- Klick zeigt die letzten 3 Vorkommnisse mit Zeitstempel
- Rot löst Push-Notification aus, gelb nicht
- **Trust:** ALERT

**US-1.1.3 · Ray bereitet den Owner-Bericht vor**
Als Anna möchte ich für mein wöchentliches Owner-Meeting in 30 Sekunden einen präsentationsfähigen Bericht von Ray bekommen, damit ich nicht jede Woche Folien baue.
- Ein Klick erzeugt PDF oder Slides mit Highlights, KPIs, Top-Decisions des Zeitraums
- Anna wählt Tonfall (knapp oder ausführlich)
- Bericht ist faktisch korrekt; Ray validiert vor der Ausgabe
- Anna kann manuell editieren, bevor sie teilt
- **Trust:** APPROVE

---

### Job 1.2 · Raten in CRS, OTAs, Channel Manager pflegen

**US-1.2.1 · Preise wandern automatisch in alle Kanäle**
Als Anna möchte ich, dass jede Preisentscheidung von Ray automatisch in CRS, OTAs und Channel Manager landet, damit ich nie wieder zwei Systeme synchronisieren muss.
- Innerhalb 60 Sekunden nach jeder Entscheidung in allen aktiven Kanälen sichtbar
- Erfolg pro Kanal: ✓
- Bei Fehler 3 Auto-Retries, dann Eskalation
- **Trust:** AUTO

**US-1.2.2 · Sync-Fehler ohne Suchen**
Als Anna möchte ich von Ray proaktiv informiert werden, wenn ein Preis nicht durchgegangen ist, damit ich nicht jeden Morgen alle Kanäle einzeln prüfen muss.
- Bei Fehler nach 3 Retries: Push und Eintrag im Briefing
- Meldung enthält Kanal, Preis, Datum, vermutete Ursache
- Ray schlägt eine konkrete nächste Aktion vor (manuell prüfen, neu pushen, ignorieren)
- Anna kann via "Mit Ray besprechen" ins Detail gehen
- **Trust:** ALERT

**US-1.2.3 · Neue Rate Plans im Gespräch anlegen**
Als Anna möchte ich neue Tarife per Sprache oder Chat mit Ray anlegen, damit ich keine Konfigurations-Maske durchklicken muss.
- "Ray, erstell einen Frühbucher-Tarif für Juli, 10 % Rabatt, nicht stornierbar" → Ray macht Vorschlag (via "Ray fragen" Modal)
- Vorschlag enthält alle CRS- und OTA-Felder, Anna bestätigt einmalig
- Nach Bestätigung wird der Tarif auf allen verbundenen Kanälen ausgespielt
- **Trust:** APPROVE

---

### Job 1.3 · Preisparität überwachen

**US-1.3.1 · Parität wird leise repariert**
Als Anna möchte ich, dass Ray kleine Paritätsbrüche stillschweigend korrigiert, damit ich davon gar nichts mitbekomme.
- Ray vergleicht stündlich Annas Preise auf den Top-3-OTAs gegen das CRS
- Abweichungen unter 5 € auf maximal 2 Tagen werden auto-fixed
- Im Decision Log auffindbar als "Parity Auto-Fix"
- **Trust:** AUTO

**US-1.3.2 · Größere Paritätsprobleme klären**
Als Anna möchte ich bei größeren Paritätsproblemen klare Optionen von Ray statt nur Warnungen, damit ich entscheiden kann statt zu recherchieren.
- Wenn ein OTA-Partner systematisch unterbietet, eskaliert Ray an Anna
- Eskalation enthält drei Optionen (Partner kontaktieren, Vertragsklausel aktivieren, erstmal beobachten)
- Ray entwirft den Brief an den Partner, falls Option 1 gewählt wird
- "Mit Ray besprechen" öffnet die Diskussion
- **Trust:** APPROVE

---

### Job 1.4 · Wettbewerber täglich beobachten

**US-1.4.1 · Comp-Set bleibt aktuell ohne Knopfdruck**
Als Anna möchte ich, dass Ray die Wettbewerberpreise täglich erhebt, ohne dass ich irgendwo "Refresh" drücke.
- Tägliche Rateshop-Erfassung um 06:00 für die nächsten 90 Tage
- Preise im Decision Log mit Zeitstempel
- Ausfälle (z. B. Booking nicht erreichbar) werden retry-behandelt und im Status sichtbar
- **Trust:** AUTO

**US-1.4.2 · Ray erkennt Anomalien und folgt nicht blind**
Als Anna möchte ich, dass Ray offensichtlich falsche Wettbewerberpreise (Software-Pannen, Rate-Crashes) erkennt und filtert, damit meine Empfehlungen nicht in eine Preisspirale gezogen werden.
- Wenn ein Comp-Hotel über 25 % unter seinem 30-Tage-Schnitt liegt, markiert Ray es als Anomalie
- Anomalien werden 7 Tage aus den Empfehlungen ausgeklammert
- Im Briefing erscheint ein "Beobachtet, nicht reagiert"-Eintrag mit `.detail` Drilldown
- Anna kann Ray manuell überstimmen ("trotzdem matchen")
- **Trust:** AUTO

**US-1.4.3 · Marktposition als Story, nicht als Tabelle**
Als Anna möchte ich auf einen Blick sehen, wo ich im Markt stehe, in einem Satz von Ray.
- Eine Karte mit Narrative: "Du bist im oberen Drittel deines Comp-Sets (Platz 2 von 5), 8 € über dem Median"
- Visuell als Skala mit günstigster Position, Median, teuerster Position, Annas Marker
- Klick öffnet detaillierten Vergleich mit allen Comp-Hotels
- Hospitality-Realismus statt Premium-Top-Bragging
- **Trust:** AUTO

---

### Job 1.5 · Datenqualität sicherstellen

**US-1.5.1 · PMS-Probleme erledigt Ray oder eskaliert sie sichtbar**
Als Anna möchte ich bei PMS-Sync-Problemen weder Logs lesen noch Support anrufen müssen, damit ich mich um Gäste kümmern kann.
- Bei API-Fehler macht Ray 3 Auto-Retries innerhalb 10 Minuten
- Wenn das nicht reicht, übernimmt Ray (im Hintergrund inkl. menschlicher Hilfe) und informiert Anna nur, dass etwas läuft
- Status-Update mit ETA, sobald Ray etwas weiß
- Anna sieht keinen separaten Support-Channel; Ray bleibt der Ansprechpartner
- **Trust:** ALERT

**US-1.5.2 · Ray prüft Annas Zahlen, bevor sie hineinschaut**
Als Anna möchte ich sicher sein, dass meine Zahlen stimmen, ohne sie selbst zu prüfen.
- Ray macht tägliche Cross-Checks (PMS, Channel Manager, RMS)
- Diskrepanzen über 2 % werden im Briefing gemeldet
- Ray versucht Auto-Reconciliation; wenn nicht möglich, eskaliert er mit konkretem Vorschlag
- **Trust:** ALERT

---

## Level 2 · Tactical Decisions
Wo Ray Annas Strategie umsetzt: Auto-Execute innerhalb von Trust-Bändern, sonst Vorschlag.

### Job 2.1 · Preise setzen und umsetzen

**US-2.1.1 · Ray entscheidet innerhalb meines Vertrauens automatisch**
Als Anna möchte ich, dass Ray Preise im definierten Band (z. B. ±15 %, 0 bis 14 Tage Horizont) automatisch ausführt, damit ich nur bei Grenzwerten gefragt werde.
- Pro Trust-Dimension (Magnitude, Horizont, Kanal) gilt der Default des Tarifs
- Anna justiert pro Dimension feinkörnig nach
- Jede Auto-Entscheidung landet im Decision Log mit Begründung
- **Trust:** AUTO innerhalb Band

**US-2.1.2 · Ray erklärt jeden Preis im Lese-Flow**
Als Anna möchte ich für jeden Preis in Klartext sehen, warum Ray ihn so gesetzt hat, damit ich Vertrauen aufbauen kann.
- Klick auf eine Zelle der Preistabelle öffnet einen Inline Drilldown (`.detail` Pattern)
- 3 bis 5 Begründungs-Punkte mit konkreten Zahlen
- "Was-wäre-wenn"-Slider zeigt geschätzten Effekt einer manuellen Anpassung
- Anna kann das Reasoning als Notiz speichern oder mit ihrem Owner teilen
- Für tieferes Gespräch: "Mit Ray besprechen" Button im Drilldown-Footer
- **Trust:** ALWAYS sichtbar

**US-2.1.3 · Grenz-Entscheidungen in einem Tap freigeben**
Als Anna möchte ich Preisempfehlungen, die mein Trust-Band sprengen, mit einem Tap freigeben oder ablehnen, damit Approval-Schleifen nicht zur Last werden.
- Eskalierte Preise erscheinen in der Decisions-Inbox mit Frist
- Drei Aktionen aus der Inbox: Approve, Reject, "Ray fragen" (öffnet Modal)
- Wenn Frist verfällt, führt Ray die Default-Aktion aus (von Anna konfigurierbar)
- **Trust:** APPROVE

**US-2.1.4 · Anna kann Ray spontan stoppen**
Als Anna möchte ich bei unerwarteten Ereignissen (Stornowellen, Housekeeping-Engpass) Ray kurzfristig pausieren, ohne ihn ganz abzuschalten.
- "Notfall-Modus" für bis zu 24h aktivierbar; Ray pausiert Auto-Aktionen
- Während Pause macht Ray nur Vorschläge, Anna entscheidet
- Nach Aufhebung fragt Ray, ob die manuellen Änderungen Strategie werden sollen
- **Trust:** ASK (während Pause)

---

### Job 2.2 · Forecasts erstellen

**US-2.2.1 · Forecast in Geld, nicht in Prozent**
Als Anna möchte ich Rays Forecasts in Euro lesen können, damit ich sofort weiß, was es bedeutet.
- Hauptanzeige: "Mai schließt voraussichtlich bei 64.000 € (±4.000 €)"
- Konfidenz wird als Bandbreite, nicht als Statistik kommuniziert
- Forecast wird täglich neu berechnet; bei materieller Änderung (über 3 %) Notification von Ray
- **Trust:** AUTO

**US-2.2.2 · Ray erklärt Abweichungen vom Plan**
Als Anna möchte ich bei Forecast-vs-Budget-Abweichungen sofort den Grund von Ray verstehen, ohne ihn zu suchen.
- Wenn Forecast über 5 % vom Budget abweicht, gibt es einen erklärenden Eintrag im Briefing
- Erklärung benennt Top-3-Treiber (z. B. "Pfingsten +8.000 €, KW 28 −3.500 €, Direkt-Mix +1.200 €")
- Jeder Treiber ist via `.detail` aufklappbar und zeigt die zugrundeliegenden Daten
- **Trust:** ALERT

---

### Job 2.3 · Strategie reflektieren und präsentieren

**US-2.3.1 · Quartalsweises 1-on-1 mit Ray**
Als Anna möchte ich quartalsweise Rays Performance reviewen, damit ich aktiv steuere statt passiv zu konsumieren.
- Ray bereitet ein Review-Doc vor (Wins, Misses, Empfehlungen für nächstes Quartal)
- Anna geht es mit Ray durch (chat-basiert via "Mit Ray besprechen" oder als geführter Flow)
- Outcomes (geänderte Trust-Settings, neue Strategie-Eckpunkte) sind 1-Klick-übernehmbar
- **Trust:** ALWAYS

**US-2.3.2 · Ray attribuiert Decisions zu Outcomes**
Als Anna möchte ich für jeden Zeitraum sehen, welche Entscheidungen mir wirklich Geld gebracht haben, damit ich weiß, wo Ray funktioniert.
- Quartalsbilanz zeigt Top-5 wertvollste Auto-Entscheidungen mit konkreten € (vs. Rule-based Baseline)
- Auch Top-3 schlechteste Entscheidungen sichtbar (Lerneffekt)
- Bilanz ist als Owner-Bericht exportierbar
- **Trust:** AUTO

---

### Job 2.4 · Gruppen und Displacement

**US-2.4.1 · Ray triagiert jede Gruppenanfrage**
Als Anna möchte ich bei jeder Gruppenanfrage die Verdrängung in einem Satz von Ray verstehen, damit ich in 30 Sekunden entscheiden kann.
- Ray errechnet bei Eingang Brutto-Gruppenumsatz minus geschätzte Verdrängung
- Anzeige: "+2.856 € Brutto · −1.840 € Verdrängung · Netto +1.016 €"
- Drei Aktionen: Annehmen, Ablehnen, "Ray fragen" (öffnet Modal mit Detail-Analyse)
- **Trust:** APPROVE

**US-2.4.2 · Kleine Gruppen entscheidet Ray selbst**
Als Anna möchte ich kleine Gruppen-Anfragen (z. B. unter 10 Zimmer) ohne mein Zutun von Ray beantworten lassen, damit ich nur bei wirtschaftlich relevanten Anfragen gefragt werde.
- Auto-Entscheidung-Schwelle ist konfigurierbar
- Auto-akzeptierte und auto-abgelehnte Anfragen erscheinen im Tagesbriefing
- Anna kann jede Auto-Entscheidung 24h rückgängig machen
- **Trust:** AUTO innerhalb Schwelle

---

### Job 2.5 · Distributionskanal-Mix steuern

**US-2.5.1 · Ray zeigt den Kanalmix in einer Karte**
Als Anna möchte ich sehen, wie sich mein Kanalmix entwickelt, ohne Pivots zu bauen.
- Eine Karte zeigt aktuellen Mix als Donut und 90-Tage-Trend
- Wenn Direkt-Anteil unter Annas Ziel liegt, markiert Ray es und schlägt Maßnahmen vor
- Maßnahmen-Vorschläge enthalten geschätzte Wirkung
- **Trust:** AUTO (Anzeige)

**US-2.5.2 · Ray schlägt konkrete Promo-Aktionen vor**
Als Anna möchte ich von Ray konkrete Promo-Vorschläge (Genius, Mobile Rate, Direkt-Boost) bekommen, damit ich nicht selbst recherchieren muss.
- Ray scannt schwache Wochen und schlägt Maßnahmen vor
- Vorschlag enthält Maßnahme, Zeitraum, geschätzter Pickup, geschätzter Margen-Effekt
- Drei Aktionen: Aktivieren, Ablehnen, "Mit Ray besprechen"
- **Trust:** APPROVE

**US-2.5.3 · Booking.com-Hebel im Hintergrund**
Als Anna möchte ich, dass Ray Booking-spezifische Hebel (Genius-Discount, Mobile Rate, Score-Optimierung) in meinem Strategie-Rahmen automatisch nutzt.
- Ray zieht Hebel nur innerhalb Annas konfigurierter Margen-Untergrenze
- Aktionen erscheinen im Decision Log, nicht im täglichen Briefing (zu viel Lärm)
- Wöchentlich: Zusammenfassung "diese Woche habe ich X-mal Hebel gezogen, geschätzter Effekt Y €"
- **Trust:** AUTO

---

## Cross-Cutting Stories · wie Anna Ray steuert

**US-X.1 · Anna justiert Rays Befugnisse**
Als Anna möchte ich pro Dimension (Preis, Restriktionen, Distribution, Gruppen) feinjustieren, wie viel Ray ohne mich macht, damit Vertrauen graduell wachsen kann.
- Settings-Page mit pro-Dimension-Slider (Off, Suggest, Auto-Bounded, Full Auto)
- Defaults kommen aus dem gebuchten Tarif
- Bei jeder Änderung: Hinweis, was sich konkret verändert ("Preise ohne dein OK ab jetzt nur noch unter 14 Tage Horizont")

**US-X.2 · Anna findet jede Entscheidung wieder**
Als Anna möchte ich jede vergangene Entscheidung von Ray mit Begründung wiederfinden, damit ich Rückfragen vom Owner beantworten kann.
- Filterbar nach Datum, Typ, Auto-vs-Approval, Größter-Impact, Schlechteste-Outcomes
- Jede Entscheidung enthält Daten-Snapshot zum Entscheidungszeitpunkt
- Outcome (7d, 30d) wird automatisch nachgetragen

**US-X.3 · Anna steuert, wann Ray sie unterbricht**
Als Anna möchte ich kontrollieren, was mich wann unterbricht, damit Ray nicht zur Belastung wird.
- Pro Notification-Typ: Push, In-App, Email, Aus
- "Quiet Hours" (z. B. 20:00 bis 06:00); nur Critical durchbricht
- "Vacation Mode": Ray erledigt nur das Nötigste, Anna bekommt eine Wochenzusammenfassung

**US-X.4 · Anna kann Ray jederzeit fragen**
Als Anna möchte ich Ray jederzeit per Chat oder Sprache eine Frage stellen können, damit ich nicht durch Menüs suche.
- Persistenter "Ray fragen" Trigger (Topbar oder Floating Button)
- Ray antwortet im Modal Bottom-Sheet, mit Klartext und Daten-Verlinkungen, wenn relevant
- Vorgeschlagene Folgefragen unter jeder Antwort (Quick-Replies)

---

## Bevor wir das umsetzen: Annahmen mit Anna validieren

Diese Stories beruhen auf Hypothesen über Anna. Drei Sachen sollten 3–5 echte Owner/GM-Interviews validieren (Direction-Entscheidungen sind getroffen, hier geht es um Sprach- und Tonfall-Schliff):

1. **Sprache des Briefings.** Sagen Owners "ich habe verdient" oder "wir haben verdient"? Wollen sie die Geld-Zahl als Erstes oder als Letztes? Welches Wort für "Belegung" ist natürlich (Auslastung, Bett-Quote, …)?
2. **Ablehnungs-Schwelle für Auto-Execute.** Wann fühlt sich Auto zu viel an? Wo liegt die rote Linie pro Dimension (Preis-Magnitude, Horizont, Restriktionen, Gruppen)?
3. **Ray als Persona, in der Praxis.** Ray als Name ist gesetzt (siehe v4-Files). Offene Frage: trägt der Name in der echten User-Realität, oder fühlt es sich nach 2 Wochen kindisch an? Akzeptiert Anna die "eingestellter Mitarbeiter"-Metapher, oder reibt sie sich daran?

Diese Antworten verändern Tonfall, Defaults, Onboarding-Sprache, nicht die Funktionalität der Stories.
