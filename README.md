# KNSI E-XPERT Website

**Wersja: 3.33.0** | Modern Interactive Features

Oficjalna strona internetowa Koła Naukowego Systemów Informatycznych E-XPERT — nowoczesna, dynamiczna strona z profesjonalnym designem i pełnym trybem ciemnym.

## 📋 Szybki start

### Lokalne uruchomienie

Strona wymaga serwera HTTP do ładowania plików JSON.

**NPM (zalecane):**
```bash
npm install  # tylko pierwszy raz
npm start    # automatycznie otwiera przeglądarkę
```

**Python 3:**
```bash
python -m http.server 8000
# Otwórz: http://localhost:8000
```

**npx (bez instalacji):**
```bash
npx http-server -p 8000 -o
```

## ✏️ Jak edytować treści strony

### 🎯 Punkt wyjścia: Katalog `data/`

**Wszystkie treści strony znajdują się w plikach JSON w katalogu `data/`.**  
To jest jedyne miejsce, które musisz edytować, aby zmienić zawartość strony.

### 📂 Struktura plików danych

```
data/
├── home.json           # Strona główna, hero, statystyki, osiągnięcia
├── navigation.json     # Menu nawigacji i widoczność sekcji
├── projects.json       # Lista projektów
├── goals.json          # Cele i misja
├── team.json          # Skład zespołu (członkowie, zarząd)
├── gallery.json       # Galeria zdjęć
├── activity.json      # Działalność i historia
├── constitution.json  # Statut koła
├── recruitment.json   # Rekrutacja
└── footer.json        # Stopka (kontakt, social media)
```

### 🔧 Przykład edycji

**Zmiana tytułu strony głównej:**
```json
// data/home.json
{
  "hero": {
    "title": "NOWY TYTUŁ",  // ← zmień tutaj
    "subtitle": "Nowy podtytuł"
  }
}
```

**Dodanie nowego członka zespołu:**
```json
// data/team.json
{
  "content": {
    "years": [
      {
        "year": "2024/25",
        "members": [
          "Jan Kowalski",  // ← dodaj tutaj
          "..."
        ]
      }
    ]
  }
}
```

**Dodanie projektu:**
```json
// data/projects.json
{
  "projects": [
    {
      "title": "Nazwa projektu",
      "description": "Opis projektu",
      "tech": ["React", "Node.js"],
      "image": "url-do-obrazu",
      "links": {
        "github": "url",
        "demo": "url"
      }
    }
  ]
}
```

### 📖 Szczegółowa instrukcja

Pełny przewodnik edycji znajduje się tutaj: **[docs/EDITING_GUIDE.md](docs/EDITING_GUIDE.md)**

## 🌐 Deployment

### GitHub Pages (automatyczny)

```bash
git add .
git commit -m "Opis zmian"
git push origin main
```

Strona zaktualizuje się automatycznie po ~2 minutach.

**Konfiguracja:**
1. GitHub → Settings → Pages
2. Source: **GitHub Actions**
3. Gotowe! 🎉

Pełna instrukcja: **[docs/DEPLOYMENT.md](docs/DEPLOYMENT.md)**

## 🎨 Funkcje strony

### ✨ Aktualne możliwości (v3.33.0)

- 🎨 **5 motywów kolorystycznych** - orange, blue, green, purple, red
- 🌙 **Tryb ciemny** - automatyczny lub manualny przełącznik
- 🎬 **Animacje Lottie** - dynamiczne, kolorowe animacje
- 📱 **Full responsive** - idealne wyświetlanie na wszystkich urządzeniach
- 🖼️ **Galeria z lightbox** - nawigacja klawiaturą, licznik, zoom
- 🎠 **Karuzela zdjęć** - automatyczna, z manualną kontrolą
- 🔝 **Scroll to top** - nowoczesny przycisk przewijania do góry
- 👥 **Podświetlanie członków** - `team?member=jan-kowalski`
- 📊 **Dynamiczne dane** - wszystko zarządzane przez JSON
- 🔗 **Czyste URL-e** - routing bez hashtag'ów
- ⚡ **GitHub Actions** - automatyczny deployment

### 📋 Historia zmian

Pełna lista zmian i nowych funkcji: **[docs/CHANGELOG.md](docs/CHANGELOG.md)**

## 📁 Struktura projektu

```
site/
├── index.html              # Główny plik strony (nie edytuj!)
├── 404.html               # Przekierowania dla GitHub Pages
├── data/                  # ← EDYTUJ TUTAJ - wszystkie treści
│   ├── *.json            # Pliki z danymi strony
│   └── assets/           # Obrazy, animacje, logo
├── docs/                 # Dokumentacja
│   ├── EDITING_GUIDE.md  # Jak edytować treści
│   ├── CHANGELOG.md      # Historia zmian
│   └── DEPLOYMENT.md     # Jak wdrożyć stronę
├── package.json          # Konfiguracja npm
└── README.md            # Ten plik
```

## 🎯 Podświetlanie członków zespołu

Możesz linkować bezpośrednio do konkretnego członka:

```
https://knsiexpert.github.io/site/team?member=natalia-piankowska
```

Kafelek członka zostanie podświetlony pomarańczowym kolorem i strona automatycznie przewinie do niego.

**Generowanie slug'a:**
- Zamień spacje na myślniki: `Natalia Piankowska` → `natalia-piankowska`
- Tylko małe litery
- Usuń polskie znaki: `ą→a`, `ę→e`, `ł→l`, etc.

## 🎨 Motywy kolorystyczne

Zmiana motywu przez przyciski w nawigacji lub URL:

```
?theme=orange   # Pomarańczowy (domyślny) 🟠
?theme=blue     # Niebieski 🔵
?theme=green    # Zielony 🟢
?theme=purple   # Fioletowy 🟣
?theme=red      # Czerwony 🔴
```

## 🌙 Tryb ciemny

- **Automatyczny** - wykrywa ustawienia systemowe
- **Manualny** - przycisk ☀️/🌙 w nawigacji
- **Zapamiętywanie** - preferencje w localStorage

## 🔧 Routing strony

Strona używa nowoczesnego routingu bez hashtag'ów:

```
/                                # Strona główna
/projects                        # Projekty
/goals                           # Cele i misja
/team                            # Zespół
/team?member=piotr-porzuczek     # Podświetlony członek
/gallery                         # Galeria
/activity                        # Działalność
/constitution                    # Statut
/recruitment                     # Rekrutacja
```

## 📚 Dokumentacja

- 📖 **[EDITING_GUIDE.md](docs/EDITING_GUIDE.md)** - Szczegółowy przewodnik edycji treści
- 🚀 **[DEPLOYMENT.md](docs/DEPLOYMENT.md)** - Instrukcja wdrożenia
- 🎨 **[DESIGN_NOTES.md](docs/DESIGN_NOTES.md)** - Notatki o designie
- 📜 **[CHANGELOG.md](docs/CHANGELOG.md)** - Pełna historia zmian
- ⚡ **[QUICKSTART.md](docs/QUICKSTART.md)** - Szybki start
- 📦 **[NPM_GUIDE.md](docs/NPM_GUIDE.md)** - Przewodnik npm

## 🔧 Wymagania techniczne

Strona wymaga nowoczesnej przeglądarki z obsługą:
- ES6+ JavaScript (async/await, fetch API)
- CSS Grid i Flexbox
- CSS Variables
- History API

## 📄 Licencja

© 2001–2025 Koło Naukowe Systemów Informatycznych E-XPERT  
Uniwersytet Gdański • Wydział Zarządzania

## 💡 Wsparcie

**Opiekun koła:** Piotr Porzuczek  
**Website:** <https://porzuczek.pl>  
**GitHub:** [@peterporzuczek](https://github.com/peterporzuczek)

---

💡 **Pamiętaj:** Aby zmienić treści strony, edytuj pliki JSON w katalogu `data/`. To jedyne miejsce, które wymaga zmian!
