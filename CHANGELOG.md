# Changelog

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

