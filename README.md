# KNSI E-XPERT Website

**Wersja: 3.10.1** | Premium 2025 Design — Navigation Configuration System

Strona internetowa Koła Naukowego Systemów Informatycznych E-XPERT — nowoczesna, dynamiczna strona z profesjonalnym designem.

## ✨ Nowe w wersji 3.10.0

- ⚙️ **Navigation Configuration** — osobny plik `navigation.json` z konfiguracją menu
- 📋 **Meta dane sekcji** — description, keywords, icon dla każdej strony
- 🎚️ **Kontrola widoczności** — łatwe włączanie/wyłączanie sekcji
- 🔢 **Sortowanie menu** — kontrola kolejności wyświetlania sekcji
- 🎯 **Dynamiczne generowanie** — menu automatycznie budowane z danych

## ✨ Nowe w wersji 3.9.0

- 🎨 **Industrial Style Images** — nowoczesna estetyka z etykietami "PREV"
- 🔲 **Double Border Frame** — offset shadow border effect
- 🔢 **Numbered Tags** — pomarańczowe numery na każdym obrazku
- ➡️ **Diagonal Arrow Indicator** — ikona strzałki w rogu (45° rotation)
- 🎭 **Diagonal Stripe Overlay** — repeating pattern na dole obrazka
- 🎬 **Advanced Hover States** — inverse colors, transforms, scale effects
- 📷 **Grayscale Filter** — 30% grayscale, full color on hover
- ⚡ **Label Animations** — "IMAGE" label z offset transform

## 🔥 Wersja 3.8.1

- 🎨 **Refined Gallery Design** — single images limited to 500px width, more elegant
- 🖼️ **Improved Image Loading** — crossorigin + referrerpolicy for imgur compatibility
- 💫 **Enhanced Lightbox** — zoom animations, blur backdrop, circular close button
- ⚡ **Error Handling** — graceful fallback for unavailable images
- 🎯 **Better Aesthetics** — subtle shadows, "PODGLĄD" label on hover
- ⌨️ **Keyboard Support** — press Escape to close lightbox

## 🔥 Wersja 3.7.0

- 🎨 **Gradient Hero Title** — czarno-pomarańczowo-złoty gradient z animacją (8s loop)
- 💪 **Ultra Bold Typography** — font-weight: 900, uppercase, tight spacing
- 💫 **Drop-shadow Effects** — dual drop-shadow (orange glow + dark shadow)
- 🌟 **Animated Underline** — 140px orange gradient z pulse animation
- 🎬 **2 Animations** — gradientShift (background) + pulse (underline)
- 📱 **Mobile Optimized** — wszystkie efekty zachowane, proporcjonalne rozmiary
- ✅ **Premium Look** — profesjonalny, dynamiczny design

## 📁 Struktura projektu

```
site/
├── index.html          # Główny plik strony
├── data/              # Katalog z danymi JSON
│   ├── home.json      # Strona główna i nawigacja
│   ├── projects.json  # Projekty
│   ├── goals.json     # Cele i osiągnięcia
│   ├── team.json      # Zespół
│   ├── activity.json  # Działalność
│   ├── constitution.json # Statut
│   └── footer.json    # Stopka (brand, kontakt, social)
├── package.json       # Konfiguracja npm
└── README.md          # Ten plik
```

## 🚀 Jak używać

### Lokalne uruchomienie

Strona wymaga serwera HTTP (pliki JSON nie mogą być ładowane bezpośrednio z systemu plików).

**Opcja 1: NPM (zalecane)** ✨
```bash
npm install  # tylko pierwszy raz
npm start    # automatycznie otwiera przeglądarkę
```

**Opcja 2: npx (bez instalacji)**
```bash
npx http-server -p 8000 -o
```

**Opcja 3: Python 3**
```bash
python -m http.server 8000
# Następnie otwórz: http://localhost:8000
```

### Edycja treści

Wszystkie treści strony znajdują się w plikach JSON w katalogu `data/`. Wystarczy edytować te pliki, aby zmienić zawartość strony:

- **home.json** - Hero section, highlights, nawigacja
- **projects.json** - Lista projektów AIS SC
- **goals.json** - Zrealizowane cele (timeline)
- **team.json** - Skład zespołu
- **activity.json** - Opis działalności
- **constitution.json** - Statut koła

## 🔗 Hash Routing

Strona wykorzystuje hash routing — każda sekcja ma własny adres URL:

- `/#home` — Strona główna
- `/#projects` — Projekty
- `/#goals` — Cele
- `/#team` — Zespół
- `/#activity` — Działalność
- `/#constitution` — Statut

### Zalety:
- ✅ **Bezpośrednie linki** — możesz linkować do konkretnej sekcji
- ✅ **Historia przeglądarki** — przyciski wstecz/dalej działają
- ✅ **Sharable URLs** — wysyłaj linki do konkretnych sekcji
- ✅ **SEO friendly** — Google indeksuje sekcje

### Przykład użycia:
```html
<!-- Link do zespołu -->
<a href="https://knsiexpert.github.io/site/#team">Nasz zespół</a>
```

## 🌐 Deployment na GitHub Pages

### Metoda 1: Automatyczny (GitHub Actions) ✅ ZALECANE

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/knsiexpert/site.git
git push -u origin main
```

**Na GitHub:**
1. Settings → Pages
2. Source: **GitHub Actions**
3. Gotowe! 🎉

Przy każdym `git push` strona automatycznie się zaktualizuje!

### Metoda 2: Ręczny deployment z npm

```bash
npm install
npm run deploy
```

### Szczegóły

Zobacz pełną instrukcję: [docs/DEPLOYMENT.md](docs/DEPLOYMENT.md)

### Własna domena

1. Utwórz plik `CNAME` z nazwą domeny
2. Skonfiguruj DNS
3. W GitHub: Settings → Pages → Custom domain

## 🎨 Design

Strona wykorzystuje nowoczesny design — minimalizm, industrial aesthetic i funkcjonalność.

### Kluczowe elementy:
- **Helvetica** jako główna czcionka
- **Czarno-biały** kontrast bez gradientów
- **2px gaps** w gridach (charakterystyczny dla Off-White™)
- **Labels** i instrukcje (STATEMENT, ZARZĄD, LINK, etc.)
- **Bold typography** z uppercase dla nagłówków
- **Numbering system** (01, 02, 03...) w kartach
- **Logo SVG** zintegrowane w nawigację

Więcej szczegółów: [docs/DESIGN_NOTES.md](docs/DESIGN_NOTES.md)

### Kolory

```css
:root {
    --black: #000;
    --white: #fff;
    --gray: #808080;
    --light-gray: #f5f5f5;
}
```

### Czcionki

```css
body {
    font-family: 'Helvetica', 'Arial', sans-serif;
    letter-spacing: -0.02em;
}
```

## 📝 Dodawanie nowych sekcji

1. Utwórz nowy plik JSON w katalogu `data/`
2. Dodaj link do niego w `home.json` w sekcji `site.nav`
3. Dodaj nową sekcję w `index.html`
4. Stwórz funkcję renderującą w JavaScript

## 🔧 Wymagania techniczne

- Nowoczesna przeglądarka z obsługą:
  - ES6+ JavaScript (async/await, fetch API)
  - CSS Grid i Flexbox
  - CSS Variables

## 📄 Licencja

© Koło Naukowe Systemów Informatycznych E-XPERT

## 💡 Wsparcie

W razie pytań lub problemów, skontaktuj się z opiekunem koła: **Piotr Porzuczek**
