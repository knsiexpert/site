# KNSI E-XPERT Website

Strona internetowa Koła Naukowego Systemów Informatycznych E-XPERT.

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
│   └── constitution.json # Statut
└── README.md          # Ten plik
```

## 🚀 Jak używać

### Lokalne uruchomienie

Strona wymaga serwera HTTP (pliki JSON nie mogą być ładowane bezpośrednio z systemu plików).

**Opcja 1: NPM (zalecane)**
```bash
npm install  # tylko pierwszy raz
npm start
```

**Opcja 2: Python 3**
```bash
python -m http.server 8000
```

**Opcja 3: Node.js (npx)**
```bash
npx http-server -p 8000
```

Następnie otwórz: `http://localhost:8000`

### Edycja treści

Wszystkie treści strony znajdują się w plikach JSON w katalogu `data/`. Wystarczy edytować te pliki, aby zmienić zawartość strony:

- **home.json** - Hero section, highlights, nawigacja
- **projects.json** - Lista projektów AIS SC
- **goals.json** - Zrealizowane cele (timeline)
- **team.json** - Skład zespołu
- **activity.json** - Opis działalności
- **constitution.json** - Statut koła

## 🌐 Deployment na GitHub Pages

### Metoda 1: Automatyczny (GitHub Actions) ✅ ZALECANE

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/YOUR_USERNAME/knmiexpert.git
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

Zobacz pełną instrukcję: [DEPLOYMENT.md](DEPLOYMENT.md)

### Własna domena

1. Utwórz plik `CNAME` z nazwą domeny
2. Skonfiguruj DNS
3. W GitHub: Settings → Pages → Custom domain

## 🎨 Design

Strona wykorzystuje design inspirowany **Virgilem Ablohem** — minimalizmem, industrial aesthetic i funkcjonalnością.

### Kluczowe elementy:
- **Helvetica** jako główna czcionka
- **Czarno-biały** kontrast bez gradientów
- **2px gaps** w gridach (charakterystyczny dla Off-White™)
- **Labels** i instrukcje (STATEMENT, ZARZĄD, LINK, etc.)
- **Bold typography** z uppercase dla nagłówków
- **Numbering system** (01, 02, 03...) w kartach
- **Logo SVG** zintegrowane w nawigację

Więcej szczegółów: [DESIGN_NOTES.md](DESIGN_NOTES.md)

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
