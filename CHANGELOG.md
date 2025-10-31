# Changelog

## [3.7.0] - 2024-10-31

### 🎨 Hero Title — Gradient Text & Premium Typography

#### ✨ Profesjonalny Gradient
- **Multi-color gradient** — czarny (40%) → pomarańczowy (60%) → złoty (100%)
- **Background-clip: text** — gradient wypełnia tekst
- **Animated gradient** — `gradientShift` animation, 8s loop
- **Background-size: 200%** — gradient przesuwa się w czasie

```css
background: linear-gradient(135deg, 
    #1c1b22 0%, #1c1b22 40%, 
    #ff6b00 60%, #ff8c00 80%, #ffa500 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
```

#### 🎯 Enhanced Typography
- **Font-weight: 900** — ultra bold (było 700)
- **Text-transform: uppercase** — ALL CAPS dla impact
- **Letter-spacing: -0.03em** — tight kerning (było -0.02em)
- **Line-height: 1.05** — kompaktowy (było 1.1)
- **Font-family** — dodany 'Arial Black' jako fallback

#### 💫 Drop-shadow Effects
- **Dual drop-shadow** — pomarańczowy glow + czarny cień
- **Filter instead of text-shadow** — działa z gradient text
```css
filter: drop-shadow(0 4px 12px rgba(255, 107, 0, 0.3))
        drop-shadow(0 2px 4px rgba(28, 27, 34, 0.2));
```

#### 🌟 Animated Underline
- **Szerszy** — 140px (było 120px), 6px height (było 5px)
- **Orange gradient** — #ff6b00 → #ff8c00 → #ffa500
- **Pulse animation** — subtleny efekt pulsowania (opacity + scaleX)
- **Stronger glow** — dual box-shadow z większą intensywnością
```css
animation: slideIn 0.8s ease-out, pulse 2s ease-in-out infinite;
```

#### 📱 Mobile Optimized
- **Font-weight: 900** — również na mobile
- **Underline 80px** — proporcjonalnie mniejszy (było 50px)
- **Height 4px** — proporcjonalnie (było 2px)
- **Gradient zachowany** — działa identycznie na mobile

#### 🎬 Animacje
**gradientShift** — 8s loop:
```css
0%, 100% { background-position: 0% center; }
50% { background-position: 100% center; }
```

**pulse** — 2s loop:
```css
0%, 100% { opacity: 1; transform: scaleX(1); }
50% { opacity: 0.8; transform: scaleX(0.95); }
```

#### 🚀 Rezultat
- ✅ **Mega profesjonalny** — gradient + ultra bold + uppercase
- ✅ **Dynamiczny** — animowany gradient + pulsujące podkreślenie
- ✅ **Premium look** — czarno-pomarańczowo-złoty gradient
- ✅ **Mocny impact** — weight 900 + tight spacing
- ✅ **Perfect mobile** — wszystkie efekty zachowane
- ✅ **Virgil Abloh vibes** — minimalistyczny ale z mocnym akcentem

## [3.6.0] - 2024-10-31

### 📦 Dynamic Footer — JSON-Based Configuration

#### ✨ Nowy plik: `data/footer.json`
Wszystkie dane stopki przeniesione do JSON dla łatwej edycji i utrzymania.

#### 📐 Struktura JSON
```json
{
  "brand": {
    "name": "...",
    "description": "...",
    "year": "2025",
    "established": "EST. 2015"
  },
  "navigation": {
    "title": "Nawigacja",
    "links": [...]
  },
  "contact": {
    "title": "Kontakt",
    "links": [...]
  },
  "social": {
    "title": "Social Media",
    "platforms": [...]
  },
  "bottom": {
    "copyright": "...",
    "credits": [...]
  }
}
```

#### 🔧 Implementacja
- **Funkcja `renderFooter()`** — ładuje `footer.json` i renderuje HTML
- **Dynamiczny HTML** — stopka budowana z template strings
- **attr(data-est)** — CSS ::before używa atrybutu dla EST. label
- **Wywołanie w `init()`** — renderFooter() dodane do inicjalizacji

#### 📝 Zawartość JSON
**Brand:**
- Nazwa koła (3 linie z <br>)
- Opis: "Od lat łączymy pasję..." (zmiana z "Od 2015 roku")
- Rok: 2025
- Established: EST. 2015

**Navigation:**
- 6 linków: Start, Projekty, Cele i misja, Zespół, Działalność, Statut

**Contact:**
- Email: knsi.expert@ug.edu.pl
- Uniwersytet Gdański
- Wydział WZR
- Wydział MFI

**Social Media:**
- GitHub (GH), Facebook (FB), LinkedIn (IN), Instagram (IG)

**Bottom:**
- Copyright: "© 2015–2025 KNSI E-XPERT • UNIWERSYTET GDAŃSKI • WYDZIAŁ ZARZĄDZANIA"
- Credits: OPEN SOURCE, GITHUB PAGES

#### 🚀 Korzyści
- ✅ **Łatwa edycja** — wszystkie dane w jednym pliku JSON
- ✅ **Separacja danych** — HTML/CSS/JS oddzielone od treści
- ✅ **Konsystencja** — format zgodny z resztą projektu
- ✅ **Dynamiczne renderowanie** — jak pozostałe sekcje
- ✅ **Utrzymywalność** — zmiana roku/linków bez dotykania HTML

#### 📦 Pliki zmienione
- `data/footer.json` — **NOWY** plik z danymi stopki
- `index.html` — funkcja `renderFooter()`, usunięte hardcoded dane
- CSS: `footer::before` używa `attr(data-est)`

## [3.5.1] - 2024-10-31

### 📚 Footer Update — Wydział WZR

#### ✨ Dodany link do Wydziału WZR
- **Wydział WZR** — dodany przed Wydziałem MFI w sekcji Kontakt
- **Link** — https://wzr.ug.edu.pl
- **Kolejność** — Uniwersytet Gdański → Wydział WZR → Wydział MFI

## [3.5.0] - 2024-10-31

### 🎯 Professional Footer — 2025 Edition

#### ✨ Virgil Abloh-Inspired Footer
- **Black background** — `background: var(--black)`, `color: var(--white)`
- **EST. 2015 label** — `position: absolute`, `font-size: 10px`, `letter-spacing: 0.2em`, `opacity: 0.4`
- **4-column grid** — `grid-template-columns: 2fr 1fr 1fr 1fr` (desktop), 1fr (mobile)
- **80px gaps** — spacing między kolumnami (desktop), 40px (mobile)

#### 🎨 Footer Components
**Brand Section:**
- **Large title** — `font-size: 28px`, `font-weight: 700`, `letter-spacing: 0.05em`
- **Description** — `font-size: 14px`, `opacity: 0.8`, max-width 400px
- **2025 Year badge** — `padding: 15px 30px`, `border: 2px solid`, `font-size: 32px`
- **Hover effect** — inverse colors + translateY(-2px)

**Navigation Links:**
- **All sections** — Start, Projekty, Cele, Zespół, Działalność, Statut
- **Hover animation** — `transform: translateX(5px)`, `opacity: 1`

**Contact Info:**
- Email: knsi.expert@ug.edu.pl
- Uniwersytet Gdański links
- Wydział MFI link

**Social Media:**
- **4 platforms** — GitHub (GH), Facebook (FB), LinkedIn (IN), Instagram (IG)
- **40x40px boxes** — `border: 2px solid`, centered text
- **Hover effect** — inverse colors + lift

#### 📱 Mobile Responsive
- **Single column** — `grid-template-columns: 1fr`
- **Reduced padding** — 60px 0 30px (było 100px/40px)
- **Smaller year badge** — 24px font (było 32px)
- **Vertical footer-bottom** — flex-direction: column
- **Centered text** — text-align: center
- **Smaller gaps** — 40px grid gap, 12px social gap

#### 🎯 Footer Bottom
- **Border-top** — `2px solid rgba(255, 255, 255, 0.2)`
- **Copyright** — © 2015–2025 KNSI E-XPERT • UNIWERSYTET GDAŃSKI
- **Credits** — OPEN SOURCE + GITHUB PAGES links
- **Opacity** — 0.6 dla subtelności

#### 📐 Technical Details
```css
footer {
    background: var(--black);
    color: var(--white);
    padding: 100px 0 40px;
    margin-top: 150px;
}
.footer-year {
    border: 2px solid var(--white);
    font-size: 32px;
    transition: all 0.3s ease;
}
.footer-year:hover {
    background: var(--white);
    color: var(--black);
}
```

#### 🚀 Rezultat
- ✅ **Profesjonalna stopka** — elegancka, minimalistyczna
- ✅ **2025 prominent** — duży, wyróżniony rok w ramce
- ✅ **Full navigation** — wszystkie sekcje w stopce
- ✅ **Social media** — 4 platformy z hover effects
- ✅ **Virgil Abloh style** — borders, gaps, typography, inverse hover
- ✅ **Mobile perfect** — single column, kompaktowe

## [3.4.2] - 2024-10-31

### 🍔 Hamburger Menu Fix + Navigation Scroll

#### 🔧 Problem
- **Hamburger menu nie działało** — błędne nazwy klas (menu-toggle vs mobile-menu)
- **Treść przykryta przez nav** — przy przełączaniu sekcji brak scroll to top
- **Menu nie zamykało się** — po kliknięciu w link menu pozostawało otwarte

#### ✅ Rozwiązanie
- **Poprawione nazwy klas** — `.mobile-menu` konsekwentnie w całym CSS
- **Naprawiona funkcja `toggleMenu()`** — teraz dodaje klasę `menu-open` do `<nav>`
- **Scroll to top** — przy każdej zmianie sekcji: `window.scrollTo({ top: 0, behavior: 'smooth' })`
- **Auto-close menu** — mobile menu zamyka się po kliknięciu w link

#### 🎨 Animacja hamburgera
- **Transform to X** — hamburger zmienia się w X gdy menu otwarte
- **Smooth transition** — `transition: all 0.3s ease` na wszystkich elementach
- **Desktop animation** — również działa na większych ekranach
```css
nav.menu-open .hamburger {
    background: transparent;
}
nav.menu-open .hamburger::before {
    transform: rotate(45deg);
    top: 0;
}
nav.menu-open .hamburger::after {
    transform: rotate(-45deg);
    top: 0;
}
```

#### 📱 Mobile Navigation
- **Max-height animation** — płynne rozwijanie menu (0 → 500px)
- **Z-index: 999** — nav-links zawsze na wierzchu
- **Border-bottom** — 1px solid gdy menu otwarte
- **Flex-direction: column** — vertical stack linków

#### 🎯 Rezultat
- ✅ **Hamburger działa** — kliknięcie otwiera/zamyka menu
- ✅ **Animacja X** — hamburger przekształca się w X
- ✅ **Treść nie przykryta** — scroll to top przy zmianie sekcji
- ✅ **UX perfect** — menu zamyka się po kliknięciu w link

## [3.4.1] - 2024-10-31

### 🔧 Mobile Fix — Unified Media Query

#### 🐛 Problem
- **6 rozproszonych media queries** — konflikty i nadpisywanie stylów
- **Niekonsystentne wartości** — różne fonty/padding w różnych miejscach
- **Overflow issues** — tekst wychodził poza ekran

#### ✅ Rozwiązanie
- **Jeden kompleksowy media query** — wszystko w jednym miejscu (945-1411 linia)
- **Spójne wartości** — zgrane czcionki i spacing w całym mobile
- **Max-width 100%** — container nie wychodzi poza ekran
- **Overflow-x: hidden** — body nie scrolluje poziomo

#### 📐 Unified Mobile Specs
- **Body font** — 14px base
- **Container padding** — 16px konsekwentnie
- **Section padding** — 80px 0 50px
- **Nav padding** — 14px 16px
- **Logo** — 32px height, 12px font
- **Hero h1** — clamp(24px, 9vw, 42px)
- **H2** — clamp(26px, 7vw, 40px)
- **Body text** — 13-14px
- **Labels** — 9-11px
- **Borders** — 2px (było 3px)
- **Card padding** — 28-35px (było 40-50px)

#### 🎯 Co zostało naprawione
- ✅ **Zero overflow** — wszystko się mieści
- ✅ **Spójne czcionki** — jedna hierarchia typograficzna
- ✅ **Menu działa** — max-height animation
- ✅ **Glassmorphism hero** — border-radius 2px
- ✅ **Wszystkie sekcje** — nav, hero, stats, about, highlights, projects, timeline, team, constitution, activity, quotes
- ✅ **2x2 stats grid** — poprawne borders
- ✅ **Single column** — about, highlights, projects, team

#### 🚀 Rezultat
**Perfect mobile experience** — kompaktowy, czytelny, bez overflow!

## [3.4.0] - 2024-10-31

### 📱 Kompleksowa Optymalizacja Mobile

#### ✨ Hero Section Mobile
- **Padding zmniejszony** — 110px top (było 150px), 50px bottom
- **H1 czcionka** — clamp(28px, 10vw, 48px) zamiast 36px/64px
- **Subtitle** — 16px (było 18px), line-height 1.5
- **CTA button** — padding 16px 40px, font-size 10px
- **Nav wyżej** — padding 16px (było 30px)

#### 📐 Zgranie czcionek
- **H2 sections** — clamp(28px, 8vw, 48px)
- **H3 about/highlights** — 14-16px
- **Project name** — 22px (mobile)
- **Timeline year** — 22px (mobile)
- **Article title** — 17px (mobile)
- **Body text** — 14px uniwersalnie
- **Labels** — 8-10px

#### 🎯 Zmniejszone spacing
- **Section padding** — 100px 0 60px (było 150px/120px)
- **Container padding** — 16px (było 20px)
- **Card padding** — 30-40px (było 50-70px)
- **Margins between** — 40-50px (było 60-90px)
- **Grid gaps** — 2px zachowane

#### 📦 Wszystkie sekcje
- ✅ **Hero** — kompaktowy, h1 wyżej
- ✅ **Stats** — 2x2 grid, mniejsze fonty
- ✅ **About** — jednokol., padding 40px/25px
- ✅ **Highlights** — 1 kolumna, 40px padding
- ✅ **Projects** — Year 48px, name 22px, desc 14px
- ✅ **Timeline** — 30px left padding, 2px line
- ✅ **Team** — 1 kolumna, 12px/10px fonts
- ✅ **Constitution** — Articles 30px padding
- ✅ **Activity** — Lead 30px padding, items 30px

#### 🔧 Technical Details
- **Border weights** — 2px (było 3px) na mobile
- **Logo** — 35px height (było 45px)
- **Border-left hero** — 3px accent
- **Responsive h1** — clamp z 10vw dla elastyczności

#### 🎯 Rezultat
- ✅ **Wszystko się mieści** — żaden tekst nie wychodzi
- ✅ **Zgrane czcionki** — spójne proporcje
- ✅ **Mniejsze spacing** — więcej treści na ekranie
- ✅ **Hero wyżej** — nagłówek bliżej góry
- ✅ **Czytelność** — 14px minimum dla body
- ✅ **Profesjonalny** — kompaktowy, ale nie ciasny

## [3.3.1] - 2024-10-31

### 🎨 Hero Box Redesign — Glassmorphism + Text Glow

#### ✨ Nowe podejście (bez dziwnych kształtów)
- **Usunięty clip-path** — Prosty, elegancki design
- **Glassmorphism** — Biały box z backdrop-filter blur(20px)
- **Orange accent** — Border-left: 5px solid dla wyróżnienia
- **Dual shadow** — Czarny + orange dla głębi

#### 💫 Text Enhancement
- **Mocny text-shadow** — Triple layer:
  - 0 2px 4px white (bliski)
  - 0 4px 12px white (średni)
  - 0 0 40px white (glow)
- **Subtitle shadow** — Delikatniejszy, double layer
- **Większa opacity** — Subtitle 0.85 → 0.9

#### 📐 Layout Details
- **Background** — rgba(255, 255, 255, 0.85) z blur
- **Border-radius** — 4px (subtelny)
- **Padding** — 80px 70px (desktop), 50px 30px (mobile)
- **Box-shadow** — Dual: dark + orange accent

#### 🎯 Rezultat
- ✅ **Tekst doskonale widoczny** na pattern
- ✅ **Glassmorphism** — Modern, trendy
- ✅ **Orange accent** — Virgil Abloh style
- ✅ **Clean & professional** — Bez dziwnych kształtów
- ✅ **Text glow** — Wyróżnia się perfekcyjnie

## [3.3.0] - 2024-10-31

### 🎨 Hero Content Box — Prostokąt ze ściętymi bokami

#### ✨ Ciekawy kształt za tekstem
- **Clip-path polygon** — Prostokąt ze ściętymi krawędziami (15% top-left, 0% top-right, 85% bottom-right, 100% bottom-left)
- **Background** — Białe tło rgba(255, 255, 255, 0.9) z backdrop-filter blur
- **Box shadow** — 0 20px 60px dla głębi
- **Border** — 3px solid rgba(28, 27, 34, 0.1) dla subtelnego outline

#### 🌈 Gradient overlay
- **::after element** — Dodatkowa warstwa z orange gradient
- **Linear gradient** — 135deg, rgba(255, 107, 0, 0.1) → transparent
- **Layered effect** — Pattern + gradient + white box + content

#### 📐 Layout
- **Padding hero-content** — 80px 60px (desktop), 50px 30px (mobile)
- **Negative margins** — left: -40px, right: -40px dla szerszego box
- **Z-index layers** — ::after (-2), ::before (-1), content (1)

#### 📱 Responsive
- **Mobile adjustments** — Mniejszy padding i margins (-20px)
- **Zachowany kształt** — Clip-path działa na wszystkich rozmiarach
- **Czytelność** — Tekst dobrze się odcina od tła

#### 🎯 Visual Impact
- **Tekst się odcina** — Wyraźnie widoczny na tle pattern
- **Industrial chic** — Skośne krawędzie w stylu Virgil Abloh
- **Modern & dynamic** — Geometryczne formy dodają energii
- **Professional** — Nie przytłacza, ale przyciąga uwagę

## [3.2.1] - 2024-10-31

### 🎨 Pattern Adjustment — Clean Body, Textured Hero

#### 🧹 Czysty Body
- **Usunięty pattern** — Body z czystym tłem `var(--white)`
- **Minimalistycznie** — Reszta strony bez textury
- **Focus na content** — Nic nie rozprasza od treści

#### ✨ Enhanced Hero Pattern
- **Większy wzór** — Geometryczny pattern 304x304px
- **Większa opacity** — 0.3 → 0.4 (bardziej widoczny)
- **Kompleksowy design** — Linie, połączenia, geometria
- **Dynamiczne tło** — Coś się dzieje, hero nie jest pusty!
- **Zachowany gradient** — Orange radial gradient + floating animation

#### 🎯 Philosophy
- **Hero wyróżniony** — Tylko główna sekcja ma pattern
- **Clean sections** — Pozostałe sekcje na czystym tle
- **Visual hierarchy** — Hero przyciąga uwagę
- **Better contrast** — Pattern tylko tam, gdzie potrzebny

## [3.2.0] - 2024-10-31

### 🎨 Hero Patterns — Subtelne tła SVG

#### ✨ Wzory z Hero Patterns
- **Pattern kropki** — Hero section z delikatnym wzorem kółek
  - Fill: `#e8e8ed` (light-gray)
  - Opacity: 0.3 (bardzo subtelne)
  - SVG pattern embedded inline
  
- **Pattern geometryczny** — Body background z liniami
  - Fill: `#d4d4d9` (subtle gray)
  - Opacity: 0.15 (ultra-subtelne)
  - Kompleksowy geometryczny wzór
  
- **Pattern dodatkowo** — Zmienne CSS z cross pattern
  - `--pattern-light` dla przyszłych zastosowań
  - Wzór krzyżyków jako opcja dla kart

#### 🌈 Visual Effects
- **Hero gradient** — Radial gradient z orange (rgba(255, 107, 0, 0.08))
- **Floating animation** — Zachowana animacja tła (20s)
- **Layered backgrounds** — Pattern + gradient overlay
- **Texture depth** — Dodana głębia wizualna bez przytłaczania

#### 🎯 Zastosowania
- Hero section: Wzór kropki + orange gradient
- Body: Geometryczny wzór globalnie
- Zachowana czystość białych kart (surface)
- Subtelność — wzory prawie niewidoczne, ale dodają teksturę

#### 💡 Design Philosophy
- **Ultra-subtle** — Patterns są ledwo widoczne
- **Modern texture** — Depth bez noise
- **Performance** — SVG inline (zero HTTP requests)
- **Accessibility** — Nie przeszkadzają w czytaniu
- **Virgil Abloh aesthetic** — Industrial texture, minimalistyczna elegancja

## [3.1.0] - 2024-10-31

### 🎨 Typography Redesign — Cute & Pleasant Headings

#### ✨ Nowa typografia nagłówków
- **System font stack** — SF Pro Display, Segoe UI, Helvetica Neue (native fonts dla lepszej czytelności)
- **Soft & friendly** — Obniżony font-weight (800→700 dla h1, 700→600 dla h2/h3)
- **Better spacing** — Pozytywny letter-spacing (0.01-0.02em) zamiast negatywnego
- **No uppercase** — Text-transform: none dla naturalniejszego wyglądu

#### 🎯 Szczegóły zmian:

**H1 (Hero):**
- Font-size: 140px → 130px (bardziej proporcjonalne)
- Font-weight: 800 → 700 (mniej agresywne)
- Letter-spacing: -0.05em → -0.02em (lepsze czytelność)
- Text-transform: uppercase → none
- Line-height: 0.95 → 1.1 (więcej przestrzeni)
- Accent line: gradient z orange + shadow glow

**H2 (Sekcje):**
- Font-size: 72px → 64px (bardziej delikatne)
- Font-weight: 700 → 600 (soft weight)
- Letter-spacing: -0.02em → 0.02em (przestronne)
- Text-transform: uppercase → none (naturalnie)
- Line-height: 1 → 1.2 (lepsza czytelność)
- **Gradient text** — Subtelny gradient czarny → orange (135deg)
- Accent line: 60px → 80px, gradient + glow shadow

**H3 & inne nagłówki:**
- Font-size: 18-20px → 19-21px
- Font-weight: 700 → 600
- Text-transform: uppercase → none
- Letter-spacing: 0.08em → 0.01em
- System fonts dla wszystkich

**Project names, Timeline years, Article titles:**
- Unified font-family (system stack)
- Reduced font-weight (600)
- Better letter-spacing
- No uppercase transform

#### 🌈 Visual Effects
- Gradient text dla h2 (black → accent)
- Gradient underlines z box-shadow glow
- Border-radius na accent lines (2-3px)
- Smooth transitions i animacje
- Better visual hierarchy

## [3.0.2] - 2024-10-31

### 🎯 Navigation Update

- **Zmiana nazwy w nawigacji** — "Home" → "Start"
- Lepsza przejrzystość interfejsu użytkownika
- Zachowany link `#home` w URL routing

## [3.0.1] - 2024-10-31

### 🎨 Enhanced Logo with 3D Animation

- **Większe logo** — Zwiększony rozmiar SVG z 40px → 60px (desktop), 30px → 45px (mobile)
- **3D rotacja** — Płynna animacja rotate3d (8s loop)
  - Obrót Y: 0° → 180° → 360° → 180° → 0°
  - Subtelny tilt X: ±5°
  - Transform-style: preserve-3d
- **Hover effect** — Pauza animacji + scale(1.1) + rotateY(180deg)
- **Większy font** — Nazwa koła: 20px → 22px, gap: 20px → 25px
- **Smooth transitions** — Cubic-bezier dla wszystkich transform

## [3.0.0] - 2024-10-31

### 🚀 Modern 2025 Redesign — Enhanced Layout & UX

#### ✨ Nowe Sekcje
- **Statystyki** — Dynamiczna sekcja z liczbami (10+ lat, 50+ członków, 6 projektów, 5 nagród)
  - Grid layout z hover effects
  - Karty z animacjami (transform, scale, color transitions)
  - Responsywny układ (2 kolumny na mobile)
  
- **O Nas** — Sekcja przedstawiająca koło
  - Lead paragraph z accent border (4px orange)
  - 3 karty z kluczowymi wartościami
  - Hover effects z accent line animation
  - Transform effects na kartach

#### 🎨 Enhanced Hero Section
- **Floating animation** — Subtle background gradient z animacją (20s loop)
- **Nowy layout** — Zwiększone padding (180px/120px)
- **Typografia** — Font-weight: 800, lepszy line-height (0.95)
- **Accent line** — Orange underline z slide-in animation (0.8s)
- **Responsive** — Lepsze fonty na mobile (36-64px)

#### 🎯 Improved Highlight Cards
- **Nowe wymiary** — 300px minWidth, większy padding (70px/50px)
- **Bottom accent** — Orange bar animation on hover (width: 0 → 100%)
- **Enhanced hover** — Scale effect (1.02), dłuższe transitions (0.4s)
- **Number styling** — Większe numery (12px), scale na hover (1.2)
- **Overflow hidden** — Czystsze animacje

#### 📐 Enhanced Projects Section
- **Większe spacing** — 80px padding, 80px gap
- **Accent hover** — Rok zmienia kolor na orange i scale (1.05)
- **Left padding animation** — Karta przesuwa się w prawo na hover
- **Większe fonty** — Project name: 32px, description: 16px
- **Sticky year** — Lepszy font-weight (800), opacity transitions
- **Team tags hover** — Transform i color change

#### 🎨 Global Improvements
- **Smooth scroll** — `scroll-behavior: smooth` na całej stronie
- **Font rendering** — `-webkit-font-smoothing: antialiased`
- **Better fonts** — 'Helvetica Neue', -apple-system, BlinkMacSystemFont
- **Cubic-bezier** — Wszędzie `cubic-bezier(0.4, 0, 0.2, 1)` dla smooth animations
- **Responsive refinements** — Lepsze breakpoints i mobile layouts
- **Accent color usage** — Więcej użyć `var(--accent)` (#ff6b00)

#### 📱 Mobile Enhancements
- **Hero mobile** — 150px/80px padding, lepsze font sizing
- **About lead** — 20px font, zmniejszony padding
- **Single column** — Wszystkie grids na 1fr na mobile
- **Reduced padding** — 50px/30px na kartach mobile

#### 📊 Data Structure Updates
- `home.json` — Nowa struktura `stats` (array) i `about` (object)
- `projects.json` — Projekt modernizacji z rokiem 2025
- JavaScript — Nowe renderowanie stats i about sections

#### 🎨 Design Philosophy
- **2025 aesthetic** — Modern, clean, minimalist
- **Virgil Abloh foundation** — Zachowany industrial design, labels, bold typography
- **Enhanced interactivity** — Więcej hover states, transforms, animations
- **Better spacing** — Więcej "white space", lepsze proporcje
- **Accent usage** — Orange jako highlight color

## [2.3.0] - 2024-10-31

### 🎨 Refined Color Palette & Enhanced Styling

- **Nowe kolory:**
  - Zamiast `#000` → `#1c1b22` (soft dark)
  - Zamiast `#fff` → `#f3f3f7` (warm light)
  - Dodano `--surface: #ffffff` dla kart
  - Dodano `--light-gray: #e8e8ed`
  
- **Home Page Improvements:**
  - Gradient background dla hero section
  - Większe fonty (h1 do 160px)
  - Shadow effects i subtle overlays
  - Lepsze spacing (120px margins)
  - Enhanced CTA button z animacją i cieniem
  
- **Highlight Cards:**
  - Białe tło (`--surface`)
  - Borders i subtle shadows
  - Lepsze hover effects z transform
  - Zwiększony padding (60px)
  
- **Quote Section:**
  - Większy font (32px)
  - Box shadows dla depth
  - Lepsze spacing
  
- **Navigation:**
  - Backdrop blur z opacity
  - Subtle shadow
  
- **Wszystkie karty:**
  - Smooth transitions (cubic-bezier)
  - Transform on hover
  - Consistent shadows
  - Białe tło z borderami

## [2.2.0] - 2024-10-31

### 🔗 Hash Routing

- **URL Routing** — każda sekcja ma własny adres
- Hash-based routing: `/#home`, `/#projects`, `/#team`, etc.
- **Linki bezpośrednie** — można linkować do konkretnej sekcji
- **Historia przeglądarki** — przyciski wstecz/dalej działają
- **Logo jako link** — kliknięcie w logo wraca do home
- **Smooth scroll** do góry przy zmianie sekcji

## [2.1.1] - 2024-10-31

### 📝 Aktualizacja treści

- **Dodano rok 2024/25** do sekcji zespołu
- Zaktualizowana lista członków koła (21 osób)
- Zarząd: Maciej Szuwarowski (Przewodniczący), Stanisław Malec (Wiceprzewodniczący)

## [2.1.0] - 2024-10-31

### 🎨 Redesign w stylu Virgila Abloha

- **Nowy design** inspirowany Virgilem Ablohem i Off-White™
- **Logo SVG** zintegrowane w nawigację
- **Industrial aesthetic:**
  - 2px gaps w gridach (charakterystyczny element)
  - Bold borders (2px, 3px solid)
  - Czarno-białe kontrasty
- **Labels i instrukcje** w stylu Virgila:
  - "STATEMENT", "ZARZĄD", "O NAS", "LINK"
  - Małe, uppercase, semi-transparent
- **Typography:**
  - Helvetica jako główna czcionka
  - Bold, uppercase headings (72px-140px)
  - Tight letter-spacing (-0.02em)
- **Numbering system** (01, 02, 03...) w highlight cards
- **Hover effects** — inwersja czarny/biały
- **Sticky elements** — rok w projektach
- **Responsive design** dostosowany do mobile

### 📦 Deployment
- **GitHub Actions** workflow dla automatycznego deploymentu
- **package.json** z npm scripts
- **gh-pages** support dla ręcznego deploymentu
- Dwie metody deployment: automatyczny i ręczny

### 📦 Nowe pliki
- `DESIGN_NOTES.md` - Szczegółowa dokumentacja designu
- `package.json` - Konfiguracja npm
- `.github/workflows/deploy.yml` - GitHub Actions workflow
- `NPM_GUIDE.md` - Przewodnik npm

## [2.0.0] - 2024-10-31

### ✨ Nowe funkcje

- **Dynamiczne ładowanie danych z JSON** - Wszystkie treści są teraz ładowane z plików JSON zamiast być hardcoded w HTML
- **Separation of concerns** - Dane oddzielone od prezentacji
- **Łatwiejsza edycja** - Aktualizacja treści wymaga tylko edycji plików JSON

### 🔄 Zmiany

- **Struktura projektu:**
  - `index.html` - zawiera tylko strukturę i logikę
  - `data/*.json` - wszystkie dane treściowe
  
- **Routing:**
  - Nawigacja budowana dynamicznie z `home.json`
  - Każda sekcja renderowana z osobnego pliku JSON

- **Organizacja danych:**
  - `home.json` - strona główna, hero, highlights, nawigacja
  - `projects.json` - projekty AIS SC
  - `goals.json` - cele i osiągnięcia (timeline)
  - `team.json` - skład zespołu z podziałem na lata
  - `activity.json` - działalność koła
  - `constitution.json` - statut koła

### 📦 Dodane pliki

- `README.md` - dokumentacja projektu
- `DEPLOYMENT.md` - instrukcja wdrożenia na GitHub Pages
- `EDITING_GUIDE.md` - przewodnik edycji treści
- `.gitignore` - pliki ignorowane przez git
- `_config.yml` - konfiguracja GitHub Pages

### 🎨 Zachowane funkcje

- ✅ Design i stylizacja (minimalistyczny, czarno-biały)
- ✅ Responsywność (mobile-first)
- ✅ Animacje i przejścia
- ✅ Menu mobilne (hamburger)
- ✅ Nawigacja SPA (Single Page Application)
- ✅ Scroll effects

### 🚀 Deployment

- Gotowa do wdrożenia na GitHub Pages
- Brak zależności zewnętrznych
- Działa z lokalnego serwera HTTP

### 📝 Dokumentacja

- Kompletna dokumentacja dla użytkowników
- Przewodnik deployment
- Instrukcje edycji treści
- Przykłady i dobre praktyki

## [1.0.0] - Wcześniej

### Początkowa wersja

- Statyczna strona z danymi w HTML
- Design minimalistyczny
- Podstawowa nawigacja

