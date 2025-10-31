# Changelog

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

