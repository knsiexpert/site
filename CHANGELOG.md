# Changelog

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

