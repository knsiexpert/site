# Design Notes — Virgil Abloh Inspired

## 🎨 Koncepcja Designu

Strona została przeprojektowana w stylu **Virgila Abloha** — minimalistycznym, funkcjonalnym i z charakterem. Design łączy industrial aesthetic z nowoczesnym minimalizmem.

## Kluczowe Elementy Stylu

### 1. **Typography**
- **Font:** Helvetica (sans-serif)
- **Bold hierarchy:** Duże, wyraźne nagłówki (72px+)
- **Tight letter-spacing:** -0.02em do -0.03em
- **Uppercase dla nagłówków:** Wszystkie główne tytuły

### 2. **Kolory**
```css
--black: #000     /* Główny kolor */
--white: #fff     /* Tło */
--gray: #808080   /* Tekst pomocniczy */
```

**Bez gradientów, tylko czysty czarno-biały kontrast.**

### 3. **Grid System**
- **2px gaps** zamiast przestrzeni — tworzy charakterystyczną siatkę
- Czarne linie separujące elementy
- Hover effects — inwersja kolorów (czarny ↔ biały)

### 4. **Labels & Instructions** (signature Virgil)
- Małe etykiety w górnych rogach: "ZARZĄD", "STATEMENT", "O NAS", "LINK"
- `font-size: 8-10px`
- `letter-spacing: 0.2em`
- `opacity: 0.3-0.4`

### 5. **Borders**
- Grube, wyraźne: `2px` i `3px solid`
- Boxed elements zamiast cieni
- Industrial, surowy look

## Komponenty

### Logo SVG
- Zintegrowane w nawigację
- Height: 40px (desktop), 30px (mobile)
- Umieszczone obok nazwy "E-XPERT"

### Nawigacja
- Fixed, border-bottom: 2px
- Padding: 30px 40px
- Uppercase links: font-size 10px, letter-spacing 0.15em
- Active state: bold + underline

### Hero Section
- Ogromny tytuł: 140px (desktop)
- Left-aligned (nie centered)
- CTA z labelem "LINK" powyżej

### Highlight Cards
- Grid z 2px gaps + czarnym background
- Data-index w prawym górnym rogu (01, 02, 03...)
- Hover: czarne tło, biały tekst

### Projects
- **Grid layout:** rok (sticky) + treść
- Duży rok: 64px, bold
- Sticky position dla roku podczas scrollowania
- Team members: grid z 2px gaps

### Timeline (Goals)
- 3px linia po lewej
- Boxed items z border 2px
- Duże kropki na linii (20px, czarne)
- Padding: 40px wewnątrz boxów

### Team
- Zarząd: czarne tło, label "ZARZĄD"
- Członkowie: grid z hover effects
- 2px gaps między tagami

### Quote
- Border: 3px solid
- Decorative corner element (bottom-right)
- Label: "STATEMENT"
- Font-size: 28px, line-height: 1.5

### Articles (Statut)
- Numery artykułów: 60x60px boxes, top-left offset
- Border 2px wokół całego artykułu
- Padding: 50px

## Charakterystyczne cechy Virgila Abloha

✅ **"Cudzysłowy"** — już są w tytułach  
✅ **Labels/Instructions** — dodane wszędzie  
✅ **Industrial Grid** — 2px gaps, czarne linie  
✅ **Bold Typography** — Helvetica, uppercase  
✅ **Functional Aesthetic** — wszystko ma cel  
✅ **Minimalizm z charakterem** — prosty, ale nie nudny  
✅ **Hover interactions** — inwersja czarny/biały  
✅ **Numbering system** — 01, 02, 03 w cards  

## Responsywność

### Mobile (max-width: 768px)
- Logo: 30px
- Hero title: 48px
- Quote: 20px
- Padding zredukowany do 20px
- Timeline: mniejszy offset
- Wszystkie gridy: 1 kolumna

### Desktop (1400px+)
- Full layout z dużymi rozmiarami
- Sticky elements działają
- Grid: 2-4 kolumny w zależności od sekcji

## Techniczne Detale

### CSS Variables
```css
--border: 1px
letter-spacing: -0.02em (body)
letter-spacing: 0.15em (uppercase navigation)
line-height: 1.8 (body)
line-height: 1 (headings)
```

### Transitions
```css
transition: all 0.2s  /* Szybkie, minimalne */
```

### Font Weights
- Regular: 400
- Medium: 500
- Bold: 700

## Inspiracje

- **Off-White™** — labels, industrial aesthetic
- **Louis Vuitton Men's** — minimalizm z charakterem
- **Swiss Design** — grid system, Helvetica
- **Brutalism** — surowe formy, wyraźne elementy

## Brak Cringe

❌ Bez przesadnych animacji  
❌ Bez gradientów  
❌ Bez zbyt wielu kolorów  
❌ Bez Comic Sans 😄  
✅ Czysto, elegancko, funkcjonalnie  

---

**"DESIGN IS HONEST"** — Virgil Abloh

