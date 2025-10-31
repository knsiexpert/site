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

Aby uruchomić stronę lokalnie, potrzebujesz prostego serwera HTTP (pliki JSON nie mogą być ładowane bezpośrednio z systemu plików z powodu ograniczeń CORS).

**Opcja 1: Python 3**
```bash
python -m http.server 8000
```

**Opcja 2: Node.js (npx)**
```bash
npx http-server -p 8000
```

**Opcja 3: PHP**
```bash
php -S localhost:8000
```

Następnie otwórz przeglądarkę i przejdź do: `http://localhost:8000`

### Edycja treści

Wszystkie treści strony znajdują się w plikach JSON w katalogu `data/`. Wystarczy edytować te pliki, aby zmienić zawartość strony:

- **home.json** - Hero section, highlights, nawigacja
- **projects.json** - Lista projektów AIS SC
- **goals.json** - Zrealizowane cele (timeline)
- **team.json** - Skład zespołu
- **activity.json** - Opis działalności
- **constitution.json** - Statut koła

## 🌐 Deployment na GitHub Pages

### Krok 1: Utwórz repozytorium

1. Utwórz nowe repozytorium na GitHub (np. `knmiexpert.github.io`)
2. Skopiuj wszystkie pliki do repozytorium

### Krok 2: Commit i Push

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin https://github.com/TWOJ_USERNAME/knmiexpert.github.io.git
git push -u origin main
```

### Krok 3: Włącz GitHub Pages

1. Przejdź do Settings → Pages w swoim repozytorium
2. W sekcji "Source" wybierz **main** branch
3. Kliknij "Save"
4. Strona będzie dostępna pod adresem: `https://TWOJ_USERNAME.github.io/knmiexpert/`

### Opcja: Własna domena

Jeśli masz własną domenę:
1. Utwórz plik `CNAME` w głównym katalogu
2. Wpisz w nim swoją domenę (np. `e-xpert.pl`)
3. Skonfiguruj DNS u swojego dostawcy domeny

## 🎨 Dostosowanie

### Kolory

Kolory są zdefiniowane w zmiennych CSS na początku pliku `index.html`:

```css
:root {
    --black: #000;
    --white: #fff;
    --gray: #999;
    --light-gray: #f5f5f5;
    --accent: #ff6b00;
}
```

### Czcionki

Domyślnie używana jest czcionka `Helvetica Neue`. Można ją zmienić w:

```css
body {
    font-family: 'Helvetica Neue', Helvetica, Arial, sans-serif;
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
