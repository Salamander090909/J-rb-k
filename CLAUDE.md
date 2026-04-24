# Jørbæk — Landing Page

## Prosjektoversikt

Bygg en luksøriøs landing page for **Jørbæk**, en etablert norsk klesbutikk med avdelinger på Holmensenteret (Nesbru), Trekanten og Rortunet. Butikken selger klassiske og trendy kvalitetsklær til jobb, fritid og fest for både menn og kvinner — pluss sko, vesker og smykker.

Filen skal hete `index.html` og ligge i roten av prosjektet. Alt (HTML, CSS, JS) samlet i én fil.

---

## Merkevare og identitet

**Tone:** Rolig, selvsikker luksus. Ikke pralende — heller tidløs og skandinavisk diskret.

**Fargepalett:**
- Bakgrunn: `#F5F2ED` (varm off-white/lin)
- Primær tekst: `#1A1A18` (nesten svart)
- Aksent: `#8B7355` (varm brun/gull — luksusnotat)
- Sekundær: `#C8BFB0` (beige muted)
- Hvit: `#FAFAF8`

**Typografi** (Google Fonts):
- Overskrifter: `Cormorant Garamond` (400, 500, 600) — editorial serif
- Brødtekst og UI: `Inter` (300, 400, 500)
- Liten caps / labels: Inter 400, letter-spacing 0.15em, uppercase

**Bildefilosofi:** Bruk `https://images.unsplash.com/` for placeholder-bilder. Velg bilder som passer luksus motebutikk — avanserte antrekk, naturlig lys, enkle bakgrunner. Bruk `?w=1200&q=80` for størrelse. Finn 5–6 relevante Unsplash-bilder manuelt og bruk deres faktiske URL-er.

---

## Sidestruktur og seksjoner

### 1. Navigasjon (sticky)
- Logo "JØRBÆK" til venstre — satt i Cormorant Garamond, letter-spacing 0.3em, 18px
- Meny-lenker til høyre: `Kolleksjon`, `Merker`, `Om oss`, `Butikker`
- Tynn 1px border-bottom som kun dukker opp når man scroller (JS scroll-listener)
- Bakgrunn: transparent → `#FAFAF8` med opacity-overgang ved scroll
- Ingen hamburger-meny på desktop, enkel stack på mobil

### 2. Hero — fullskjerm
- Fullskjerm bilde (viewport height 100vh)
- Mørk overlay (`rgba(0,0,0,0.28)`) over bildet
- Tekst sentrert, hvit:
  - Liten label øverst: `NY KOLLEKSJON 2025`
  - Stor overskrift (Cormorant, 80–96px på desktop): `Tidløs stil,\nnorsk sjel.`
  - Undertekst (Inter 300, 18px): `Kvalitetsklær for hverdag og fest — kuratert med omtanke.`
  - CTA-knapp: `Utforsk kolleksjonen` — outline-stil, hvit, hover fyller med aksent-farge
- Subtil fade-in animasjon på teksten (CSS, ikke bibliotek)

### 3. Merkebånd (Brand strip)
- Smal seksjon, lys bakgrunn
- En horisontal rekke med merkenavn i tekst: `Polo Ralph Lauren · GANT · Tiger of Sweden · Oscar Jacobson · J.Lindeberg · Eton · Les Deux · Stenströms`
- Cormorant Garamond italic, 15px, muted farge (`#8B7355`), letter-spacing
- Ingen logoer — ren typografi

### 4. Fremhevet kolleksjon (grid)
- Overskrift: `Utvalgte plagg`
- 3-kolonne grid på desktop, 2 på tablet, 1 på mobil
- 6 produktkort. Hvert kort:
  - Kvadratisk bilde (aspect-ratio 1/1, object-fit cover)
  - Under bildet: Merkenavn i caps (12px), Produktnavn (Cormorant 20px), Pris
  - Hover: bildet zoomer subtilt (transform scale 1.03, 0.4s ease)
  - Ingen box-shadow — heller en tynn border

### 5. Redaksjonell seksjon — split layout
- To kolonner: stor bildeblokk (60%) + tekst (40%)
- Tekst-siden:
  - Label: `OM JØRBÆK`
  - Overskrift (Cormorant, 48px): `Mer enn en klesbutikk`
  - Brødtekst (Inter 300, 16px, line-height 1.8): 2–3 setninger om at Jørbæk har holdt det gående siden 1970-tallet med fokus på personlig service og nøye utvalgte merker som passer norsk livsstil.
  - Lenke-tekst: `Les mer om oss →`

### 6. Merker — visuell grid
- Overskrift: `Våre merker`
- 4-kolonne grid med merkenavn som store tekst-blokker (ingen logoer)
- Hvert "kort" er en kvadrat med én myk bakgrunnsfarge fra paletten, merkenavnet sentrert
- Merker å vise: Ralph Lauren, GANT, Tiger of Sweden, Oscar Jacobson, J.Lindeberg, Eton, Les Deux, Lyle & Scott

### 7. Butikker
- Overskrift: `Finn oss`
- 3 kort (en per lokasjon):
  - **Holmensenteret**, Vogellund 6, 1394 Nesbru
  - **Trekanten**, Asker
  - **Rortunet**, Røyken
- Hvert kort: adresse, liten kart-ikon (SVG inline, ikke eksternt bibliotek), åpningstider (fiktive men realistiske)

### 8. Newsletter
- Mørk bakgrunn (`#1A1A18`), hvit tekst
- Overskrift: `Hold deg oppdatert`
- Kort tekst + e-postfelt + knapp
- Knappen: aksent-farge hover

### 9. Footer
- Logo, lenker i kolonner, copyright `© 2025 Jørbæk AS`
- Veldig minimalt — ingen sosiale ikoner unntatt Instagram (SVG inline)

---

## Kodestil — viktig

Koden skal se **menneskeskrevet** ut. Det betyr:

- **Ingen overdrevne kommentarer** — bare der det faktisk hjelper å forstå noe ikke-åpenbart
- **Naturlig CSS-struktur** — ikke alt er perfekt alfabetisk eller uniformt organisert. Noen regler er gruppert etter logikk, noen er korte one-liners, noen er litt lengre
- **Ingen `/* === SECTION START === */`-stil kommentarer** — skriv heller `/* nav */` eller bare ingen kommentar
- **Litt variasjon i spacing** — ikke identisk innrykk overalt, det er naturlig at en utvikler er litt inkonsistent
- **JS:** Bruk vanlig `const`/`let`, arrow functions, men også noen vanlige functions. Ingen klasse-hierarkier for noe så enkelt. Inline event-listeners er greit
- **Ikke DRY til det ekstreme** — litt gjentagelse i CSS er OK og normalt
- **Ingen utility-first klasser** — all CSS er custom, ikke Tailwind
- **Ingen bundler, ingen npm** — ren HTML/CSS/JS. Google Fonts via `<link>` er greit

---

## Animasjoner

Hold det subtilt:
- Hero-tekst: `opacity 0 → 1` + `translateY(20px → 0)` over 0.9s, 0.2s delay
- Produktkort: Intersection Observer for fade-in når de scroller inn (staggered med 80ms mellom hvert)
- Nav-bakgrunn: smooth transition ved scroll
- Ingen scroll-jacking, ingen parallax, ingen tunge animasjonsbiblioteker

---

## Responsivitet

- Mobile-first er ikke krav, men siden må fungere godt på 375px, 768px og 1440px
- Breakpoints: `768px` og `1100px`
- Hero-teksten skalerer ned (clamp er lov, men vanlige media queries er også OK)

---

## Ikke inkluder

- Ingen reell backend / form submission
- Ingen cookie-banner
- Ingen chat-widget
- Ikke lag `README.md` eller andre filer — kun `index.html`
