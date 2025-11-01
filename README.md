# KNSI E-XPERT Website

**Wersja: 3.23.1** | Refined Theme Switcher

Strona internetowa Koła Naukowego Systemów Informatycznych E-XPERT — nowoczesna, dynamiczna strona z profesjonalnym designem.

## ✨ Nowe w wersji 3.23.1

- 🎯 **Subtelniejsze przyciski motywów** — mniejsze, bardziej dyskretne
- 📍 **Umieszczenie na dolnej krawędzi** — przyciski wystawają z dolnej ramki nawigacji
- 🎨 **Centralne wyrównanie** — przyciski wycentrowane pod nawigacją
- ✨ **Delikatne animacje** — hover przesuwa przycisk do góry
- 👁️ **Mniejsza nachałność** — półprzeźroczyste w spoczynku

### Jak używać:
Kliknij na małą kolorową kropkę pod nawigacją, aby zmienić motyw strony:
- 🟠 Pomarańczowy (domyślny)
- 🔵 Niebieski
- 🟢 Zielony
- 🟣 Fioletowy
- 🔴 Czerwony

## ✨ Nowe w wersji 3.23.0

- 🎨 **Przyciski zmiany motywu w nawigacji** — eleganckie kulki kolorystyczne
- 🖱️ **One-click theme switching** — zmiana motywu jednym kliknięciem
- ✨ **Aktywny stan** — wizualne oznaczenie wybranego motywu
- 🎯 **Brak parametrów URL** — motyw zmienia się przez localStorage
- 📱 **Responsywne** — mniejsze przyciski na mobile

## ✨ Nowe w wersji 3.22.2

- 📱 **Optymalizacja karuzeli na mobile** — wyświetlanie tylko 3 zdjęć zamiast 12
- ⚡ **Szybsze ładowanie** — mniejsze zużycie danych na urządzeniach mobilnych
- 🎨 **Lepszy UX mobile** — karuzela dopasowana do małych ekranów

## ✨ Nowe w wersji 3.22.1

- 📝 **Tekst wprowadzający w Cele i Misja** — dodano akapit opisujący misję koła
- 🎯 **Kontekst historyczny** — tekst oparty na charakterze i wartościach z sekcji "O nas"
- ✨ **Lepszy UX** — czytelniejsze wprowadzenie przed listą zrealizowanych celów

## ✨ Nowe w wersji 3.22.0

- 🎨 **System dynamicznych motywów** — 5 gotowych motywów kolorystycznych
- 🔗 **Zmiana przez URL** — `?theme=blue`, `?theme=green`, `?theme=purple`, `?theme=red`
- 💾 **Zapamiętywanie** — wybrany motyw zapisywany w localStorage
- 🌈 **5 motywów** — orange (domyślny), blue, green, purple, red
- ⚡ **Instant switching** — zmiana motywu bez przeładowania strony

### Dostępne motywy:
- 🟠 **Orange** — `?theme=orange` (domyślny)
- 🔵 **Blue** — `?theme=blue`
- 🟢 **Green** — `?theme=green`
- 🟣 **Purple** — `?theme=purple`
- 🔴 **Red** — `?theme=red`

## ✨ Nowe w wersji 3.21.0

- 🎨 **Scentralizowane zmienne kolorów** — jeden punkt zmiany dla całego motywu
- 🔧 **Zmienne CSS dla akcentu** — `--accent`, `--accent-rgb`, `--accent-light`, `--accent-lighter`
- 🌈 **Zmienne dla gradientów** — `--gradient-primary`, `--gradient-hero`, `--gradient-text`, `--gradient-underline`
- ✨ **Łatwa zmiana motywu** — wystarczy zmienić wartości w `:root`
- 🚀 **Wszystkie kolory pomarańczowe** — teraz używają zmiennych CSS

## ✨ Nowe w wersji 3.20.3

- 🔧 **404.html poprawiony** — automatyczna detekcja base path
- 💻 **Localhost działa** — przekierowania działają lokalnie i na GitHub Pages
- ✅ **Uniwersalne rozwiązanie** — wykrywa `/site/` lub `/` automatycznie

## ✨ Nowe w wersji 3.20.2

- 🐛 **Poprawka błędu** — usunięto duplikowaną deklarację zmiennej `basePath`
- ✅ **SyntaxError naprawiony** — funkcja `initNavigation()` działa poprawnie

## ✨ Nowe w wersji 3.20.1

- 🖱️ **Cursor styling** — paragrafów mają teraz `cursor: default`
- 🎨 **Ukryte zaznaczenie** — transparentne style `::selection` dla lepszego UX
- 🏛️ **Uniwersytet Gdański** — dodany jako partner współpracy w działalności
- 🔤 **"GALERIA"** — tytuł w stylu reszty (wielkie litery z apostrofami)

## ✨ Nowe w wersji 3.20.0

- 🔗 **Czyste URL-e** — brak hashtagów, routing używa History API
- 📍 **Przyjazne linki** — `/projekty` zamiast `/#projekty`
- 🔄 **404.html dla GitHub Pages** — prawidłowe przekierowania dla SPA
- 🌐 **SEO friendly** — lepsze URLs dla wyszukiwarek
- ⚡ **Popstate API** — nowoczesny routing z przyciskami wstecz/naprzód przeglądarki
- 🎯 **Base path support** — działa w podkatalogach (np. `/site/`)

## ✨ Nowe w wersji 3.19.3

- 📏 **Jednolita wysokość kart** — wszystkie kafelki w "Nasze osiągnięcia" mają ten sam układ
- 🎯 **Stałe wysokości** — tytuły (min. 44px) i opisy (min. 80px) na tej samej wysokości
- 🖼️ **Wyrównane obrazy** — wszystkie zdjęcia zaczynają się na tej samej linii
- 📐 **Flexbox layout** — każda karta używa flex column dla perfekcyjnego układu
- ✨ **Responsive** — zachowano spójność na desktop (44px/80px) i mobile (36px/60px)

## ✨ Nowe w wersji 3.19.2

- 📐 **Nowy układ sekcji działalności** — sekcja "O NAS" przeniesiona pod kolumny
- 📊 **Lepszy flow** — najpierw kolumny z konkretnymi działaniami, potem historia
- 🎯 **Lepsza hierarchia** — bardziej logiczny układ informacji
- ✨ **Improved UX** — użytkownik najpierw widzi co koło robi, potem czyta historię

## ✨ Nowe w wersji 3.19.1

- 🎨 **Poprawka logo SVG** — logo wyświetla się poprawnie zamiast małej kropki
- ✅ **Prawidłowy viewBox** — ustawiono viewBox na `-30 0 740 380`
- 🔧 **Atrybut fill** — dodano `fill="currentColor"` dla poprawnego renderowania

## ✨ Nowe w wersji 3.19.0

- 🖼️ **12 zdjęć w karuzeli** — dodano 3 nowe zdjęcia (było 9, teraz 12)
- 📐 **2 rzędy na desktop** — karuzela pokazuje 6 zdjęć naraz (2 rzędy po 3)
- 🔢 **Grupy po 6 zdjęć** — każda grupa zawiera 6 zdjęć zamiast 3
- 📱 **Mobile bez zmian** — nadal 1 kolumna z pojedynczymi zdjęciami
- ✨ **Lepsze wykorzystanie przestrzeni** — więcej zawartości widocznej na raz

## ✨ Nowe w wersji 3.15.2

- ⬅️➡️ **Navigation Buttons** — przyciski lewo/prawo do manualnej nawigacji
- 🖱️ **Manual Control** — kliknij aby przełączyć grupę
- 🔄 **Auto-reset Timer** — timer resetuje się po manualnej zmianie
- 🎨 **Styled Buttons** — czarne przyciski z hover effect (pomarańczowe)
- 📱 **Mobile Optimized** — mniejsze przyciski (40px) na mobile
- ♾️ **Seamless Loop** — działa w obie strony (forward/backward)

## ✨ Nowe w wersji 3.15.0

- 🎠 **Sliding Carousel** — przesuwana karuzela grup po 3 zdjęcia obok siebie
- ♾️ **Infinite Loop** — nieskończona pętla, bezszwowy powrót do początku
- 📐 **16:9 Aspect Ratio** — horyzontalny format bez ucięć boków
- 📏 **Max Height 500px** — kompaktowa sekcja
- 📍 **Left-aligned Headers** — nagłówki wyrównane do lewej jak w reszcie strony
- 🏷️ **Premium Labels** — "MOMENT" etykiety z cudzysłowami
- 🔢 **Numbered Tags** — duże pomarańczowe numery (50×50px)
- 📟 **Code Labels** — identyfikatory "KNSI-E-XPERT-2025-XXX"
- 🌊 **Diagonal Stripes** — animowane paski na dole obrazów
- 🔲 **Double Border Frames** — offset border z efektem hover
- 🎭 **Gradient Overlays** — pomarańczowy gradient na hover
- 🔍 **Image Zoom** — scale(1.05) transform przy hover
- 💫 **Smooth Slide** — 0.8s cubic-bezier transition
- ⏱️ **Auto-slide** — automatyczna zmiana co 5 sekund
- ⏸️ **Pause on Hover** — zatrzymanie podczas najechania
- 📷 **9 zdjęć** — 3 grupy po 3 zdjęcia
- 📱 **Mobile Responsive** — 1 kolumna vertical scroll

## ✨ Nowe w wersji 3.13.0

- 🎠 **Karuzela "To My"** — automatyczna karuzela ze zdjęciami z działalności
- 🎬 **Fade Effect** — płynne przejścia między zdjęciami (1.5s)
- 🖱️ **Interaktywne wskaźniki** — kropki do manualnej nawigacji
- ⏱️ **Auto-play** — automatyczna zmiana co 4 sekundy
- ⏸️ **Pause on Hover** — zatrzymanie podczas najechania myszką
- 🔢 **Licznik** — "1 / 8" pokazujący aktualny slajd
- 📷 **8 wybranych zdjęć** — najlepsze momenty z galerii
- 📱 **Fully Responsive** — aspect ratio 16:9 (desktop), 4:3 (mobile)

## ✨ Nowe w wersji 3.12.0

- 📅 **Poprawione daty** — koło powstało w 2001, reaktywacja w 2012
- 📜 **Historia koła** — nowa sekcja w Działalności z pełną historią
- 🏛️ **Katedra** — informacja o Katedrze Informatyki Ekonomicznej
- 🔢 **24+ lat działalności** — zaktualizowane statystyki (2001-2025)
- ©️ **Copyright** — poprawiony na © 2001–2025

## ✨ Nowe w wersji 3.11.0

- 📷 **Gallery System** — pełnoprawna galeria zdjęć z `gallery.json`
- 🖼️ **Grid Layout** — 4 kolumny (desktop), 2 (tablet), 1 (mobile)
- ⬅️➡️ **Navigation** — strzałki poprzedni/następny w lightboxie
- 🔢 **Counter** — licznik "5 / 26" pokazujący pozycję
- ⌨️ **Keyboard** — strzałki lewo/prawo, Escape do zamknięcia
- 🎨 **Industrial Style** — offset border effect, numbered tags
- 🔍 **Zoom Icon** — ikona lupy na hover
- 📱 **Fully Responsive** — działa idealnie na wszystkich urządzeniach

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
