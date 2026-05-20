# Tally Homepage — Design Spec

Editorial, premium, ruhig. Inspiriert von Schweizer Typografie / Finanz-Editorials. Kein "AI slop", keine Gradients, keine Glow-Effekte. Cremefarbenes Papier statt Weiß, dunkle Tinte statt Schwarz, Forest-Green-Akzent statt Royal Blue. Mono-Labels als Strukturelement.

---

## 1. Stack

- **Next.js 15** (App Router) + **TypeScript**
- **Tailwind CSS v4** — Theme komplett in CSS via `@theme {}`, kein `tailwind.config` für Tokens
- **next/font/google** — Schriften als CSS-Variablen aufs `<html>`
- **shadcn/ui** für Button-Primitives (sonst inline styles)

> Hybrid-Ansatz: Tailwind nur für **Grid/Flex/Responsive** (`grid-cols-1 lg:grid-cols-2`, `hidden md:block`). Alle Farben, Spacing, Typografie über **inline `style`** mit CSS-Variablen. Erlaubt feinkörnige `clamp()`-Steuerung pro Element.

---

## 2. Schriften

```ts
// layout.tsx
const instrumentSerif = Instrument_Serif({ weight: ['400'], style: ['normal','italic'], variable: '--font-instrument-serif' })
const dmSans          = DM_Sans({ variable: '--font-dm-sans' })
const jetbrainsMono   = JetBrains_Mono({ variable: '--font-jetbrains-mono' })
```

Drei Rollen, klar getrennt:

| Rolle | Schrift | CSS-Variable | Einsatz |
|---|---|---|---|
| Display | Instrument Serif (400 + italic) | `--font-display` | Headlines, Hero, große Zahlen, Stat-Cards |
| Body | DM Sans | `--font-sans` | Fließtext, Subtitles, Beschreibungen |
| Mono | JetBrains Mono | `--font-mono` | Tags, Labels, Tabular Numerics |

Klassen `font-display` / `font-sans` / `font-mono` werden über das Theme-Mapping auflösbar.

**Italic ist Akzent, nicht Dekoration**: Das letzte Wort einer Headline wird in `<em>` gewickelt, italic, in `--color-accent` — Beispiel: *"Buchhaltung, die mitdenkt."* Das ist die DNA des Designs.

---

## 3. Farb-Tokens

In `globals.css` unter `@theme {}` definiert:

```css
@theme {
  --color-paper:        #faf9f6;  /* Hauptbackground — warmes Cream */
  --color-warm:         #f0ede6;  /* Card-Background, leicht dunkler */
  --color-ink:          #1a1a2e;  /* Primärtext — fast schwarz, leicht blau */
  --color-accent:       #2d5016;  /* Forest Green — DAS einzige farbige Element */
  --color-accent-bg:    #e6ede2;
  --color-muted-text:   #7a7568;  /* Sekundärtext — warmer Grauton */
  --color-border-muted: #d1cdc4;  /* Hairlines, Trennlinien */

  /* Pipeline-Stages — selten genutzt, für mehrstufige Diagramme */
  --color-purple: #4c1d95; --color-purple-bg: #ede9fc;
  --color-amber:  #7c4a03; --color-amber-bg:  #fdf4e1;
  --color-blue:   #1a3f6f; --color-blue-bg:   #e4ecf5;
}
```

**Regel**: 90% der Seite besteht aus 3 Farben — paper, ink, muted-text. Forest-Green wird **sehr** sparsam für genau eine Sache pro Block eingesetzt (italic-Wort, Erfolg-Indikator, Confidence-Score).

Body wird global gesetzt:
```css
body { background: var(--color-paper); color: var(--color-ink); }
```

---

## 4. Layout-System

```ts
// Konstanten der Section-Hülle
maxWidth:      '1100px'                           // schmaler als üblich = editorial
margin:        '0 auto'
paddingInline: 'clamp(1.25rem, 5vw, 4rem)'        // 20px → 64px
paddingTop:    'clamp(5rem, 10vw, 8rem)'          // großzügig
paddingBottom: 'clamp(5rem, 10vw, 8rem)'
```

**Hero** ist enger oben (`clamp(6rem, 12vw, 10rem)`), Folge-Sections luftig.

`clamp()` ist überall — keine festen Breakpoint-Sprünge. Typografie skaliert fließend mit der Viewport-Breite.

---

## 5. Typografie-Skala (alles `clamp`-basiert)

```ts
// Hero H1
fontSize:      'clamp(2.75rem, 5vw + 1rem, 5.5rem)'
lineHeight:    1.04
letterSpacing: '-0.02em'
fontWeight:    400
maxWidth:      '14ch'        // erzwingt Umbruch nach ~14 Zeichen — sehr editorial

// Section H2 (große Variante)
fontSize:      'clamp(2.25rem, 5vw + 0.5rem, 4.5rem)'
fontWeight:    300            // dünner als Hero — Hierarchie über weight
lineHeight:    1
textAlign:     center

// Section H2 (kleine Variante, mit Nummer)
fontSize:      'clamp(1.5rem, 3vw + 0.5rem, 2.5rem)'
fontWeight:    400

// Stat-Zahl (groß)
fontSize:      'clamp(3rem, 5vw, 4.5rem)'
fontFamily:    var(--font-display)

// Body
fontSize:      'clamp(1rem, 1.5vw + 0.5rem, 1.125rem)'
lineHeight:    1.7
maxWidth:      '38rem'        // Lesefluss-Breite
color:         var(--color-muted-text)
```

**Mono-Tag** (das wiederkehrende Strukturelement über jedem Block):
```ts
fontSize:      '10px'
textTransform: 'uppercase'
letterSpacing: '3px'           // sehr weit gespreizt
fontWeight:    600
color:         var(--color-accent)  // oder muted-text für sekundäre Tags
```

---

## 6. Section-Rhythmus (Reihenfolge auf der Homepage)

1. **HERO** — Mono-Tag, große H1 mit italic-Akzent, Subtitle, 2 CTAs (primary + outline), rechts animierte Mockup-Card
2. **CAPABILITIES** — Zentrierte H2, 3 Mockup-Cards (heller, dunkler, heller), darunter 4 Schritte mit Hairline-Top
3. **ENGINE BLUEPRINT** — Diagramm-Block (eigene Komponente)
4. **PERFORMANCE** — H2 mit Nummer-Präfix (`05`), Comparison-Canvas
5. **KUNDENSTIMMEN** — Großes italic Zitat links, Stat-Stacks rechts (Stat-Card → Logo-Grid → Mini-Stat-Card)
6. **CTA-BANNER** — Letzter Push

Jede Section ist alleinstehend — kein Übergang, kein Gradient. Hairlines (`1px var(--color-border-muted)`) statt Boxen.

---

## 7. Wiederverwendbare Patterns

### Numbered Feature Row mit Hairline-Top
```tsx
<div className="flex flex-col md:flex-row gap-6 md:gap-0">
  {items.map(f => (
    <div className="flex-1" style={{ paddingTop: 20 }}>
      <div style={{ height: 1, background: 'var(--color-border-muted)', marginBottom: 16 }} />
      <p style={{ fontSize: 16, color: 'var(--color-ink)' }}>{f.n}</p>      {/* "1. Erfassen" */}
      <p style={{ fontSize: 14, color: 'var(--color-muted-text)', lineHeight: 1.6 }}>{f.desc}</p>
      <Link style={{ fontSize: 13, textDecoration: 'underline', textDecorationColor: 'var(--color-border-muted)', textUnderlineOffset: 3 }}>
        Mehr erfahren
      </Link>
    </div>
  ))}
</div>
```

Format der Nummer: `"1. Erfassen"` — Punkt + Space, nicht Hash, nicht "Step 1".

### Mockup-Card (Belegerkennung-Stil)
- Outer: `background: var(--color-warm)`, `padding: 24`, **keine** `border-radius` (scharfe Kanten = premium)
- Header: Mono-Tag links + 6×6 Status-Dot rechts (`#4ade80` für ok)
- Inner-Card: `background: var(--color-paper)`, `1px solid var(--color-border-muted)`
- Key-Value-Reihen: links Mono `--color-muted-text` (Label), rechts Mono `--color-ink` (Wert)
- Tabular Numerics: `fontVariantNumeric: 'tabular-nums'` + `fontFamily: var(--font-geist-mono)` für Beträge

### Dark Code-Card
Ein einzelnes dunkles Element mittig: `background: #1e1e2e` (Catppuccin Mocha), Codetext `#cdd6f4`, mac-Window-Dots (`#f38ba8`, `#fab387`, `#a6e3a1`), Footer-Status in `#a6e3a1` mono uppercase.

### Stat-Card-Stack
Vertikal gestapelte Zellen ohne Gaps, abwechselnd `--color-warm` und kein Background. Trennung über `borderTop: 1px solid var(--color-border-muted)`. Innen: große Display-Zahl (`clamp(3rem, 5vw, 4.5rem)`), Mono-Label uppercase, optional Beschreibung.

### Italic Pull-Quote
```tsx
<blockquote className="font-display" style={{
  fontSize: 'clamp(1.75rem, 3.5vw + 0.5rem, 3rem)',
  fontStyle: 'italic',
  lineHeight: 1.15,
  letterSpacing: '-0.01em',
}}>
  "…"
</blockquote>
<div style={{ display: 'flex', alignItems: 'center', gap: 16, marginTop: 40 }}>
  <div style={{ width: 40, height: 1, background: 'var(--color-border-muted)' }} />
  <p style={{ fontSize: 14, color: 'var(--color-muted-text)' }}>Name, Rolle</p>
</div>
```

Die kurze Hairline (`width: 40, height: 1`) vor dem Attribut-Text ist Signature.

---

## 8. Animation (HeroJournal-Pattern)

Phasen-basiert, nicht zeit-basiert. Eine `phase`-State-Variable (0–5) treibt CSS, jede Phase = ein neues Element fades/slides in.

```ts
const TRANSITION = 'opacity 0.5s cubic-bezier(0.16, 1, 0.3, 1), transform 0.5s cubic-bezier(0.16, 1, 0.3, 1)'

const slideIn = (active: boolean) => ({
  opacity: active ? 1 : 0,
  transform: active ? 'translateX(0)' : 'translateX(18px)',
  transition: TRANSITION,
})
```

Trigger:
- `IntersectionObserver` mit `threshold: 0.3` setzt `started=true`
- `setTimeout`-Kette: 400ms / 1800ms / 2200ms / 3000ms / 3400ms zwischen den Phasen
- **Immer** `prefers-reduced-motion` respektieren → setze direkt finale Phase

Easing ausschließlich `cubic-bezier(0.16, 1, 0.3, 1)` (sanftes Auslaufen, kein Bounce).

---

## 9. Anti-Patterns (was nicht passiert)

- ❌ Keine Gradients, keine Schatten, keine Glow-Effekte
- ❌ Keine `border-radius` auf Cards (Hero-CTAs ausgenommen, da shadcn)
- ❌ Keine Emojis im Output
- ❌ Keine Icon-Sets ohne klaren Zweck
- ❌ Kein Royal Blue, kein Lila als Primärfarbe — Forest Green ist es
- ❌ Keine zentrierten Lauftexte, kein "alles mittig" — left-align dominiert
- ❌ Keine festen Pixel-Größen für Typo — alles `clamp()`
- ❌ Keine `bg-white` — immer `--color-paper` (`#faf9f6`)

---

## 10. Quick-Start in einem neuen Projekt

1. `pnpm add next-themes` (optional), `pnpm add geist` (für Geist Mono-Fallback)
2. Schriften per `next/font/google` einbinden, Variablen aufs `<html>` setzen
3. `globals.css` mit dem `@theme {}`-Block oben kopieren
4. Body: `background: var(--color-paper); color: var(--color-ink);`
5. Eine Section-Hülle als Convention etablieren (1100px maxWidth, clamp-Padding)
6. Mono-Tag, italic-Akzent in Headlines, Hairline-Trenner — diese 3 reichen für 80% des Looks
