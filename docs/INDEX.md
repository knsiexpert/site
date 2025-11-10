# 📚 Dokumentacja - Indeks

Witaj w dokumentacji strony KNSI E-XPERT!

## 🚀 Szybki start

1. **[README.md](README.md)** - Podstawowe informacje o projekcie
2. **[DEPLOYMENT.md](DEPLOYMENT.md)** - Jak wdrożyć stronę na GitHub Pages
3. **[EDITING_GUIDE.md](EDITING_GUIDE.md)** - Jak edytować treści strony

## 📁 Pliki projektu

### Główne pliki
- `index.html` - Główny plik strony (HTML + CSS + JavaScript)

### Dane (katalog data/)
- `navigation.json` - Konfiguracja menu i metadane strony
- `home.json` - Strona główna, hero, highlights
- `projects.json` - Lista projektów AIS SC
- `goals.json` - Zrealizowane cele (timeline)
- `team.json` - Skład zespołu (z podziałem na lata)
- `gallery.json` - Galeria zdjęć
- `activity.json` - Działalność koła
- `constitution.json` - Statut koła
- `recruitment.json` - Informacje o rekrutacji
- `publications.json` - Publikacje i blog
- `footer.json` - Stopka i kontakt
- `presentation-ais.json` - Prezentacja historii AIS SC

### Dokumentacja
- `README.md` - Główny README projektu
- `DEPLOYMENT.md` - Instrukcje wdrożenia
- `EDITING_GUIDE.md` - Przewodnik edycji
- `CHANGELOG.md` - Historia zmian
- `INDEX.md` - Ten plik

### Konfiguracja
- `.gitignore` - Pliki ignorowane przez git
- `_config.yml` - Konfiguracja GitHub Pages
- `package.json` - Konfiguracja npm i deployment
- `.github/workflows/deploy.yml` - GitHub Actions workflow

## 📖 Przewodniki krok po kroku

### Dla redaktorów treści
1. Przeczytaj [EDITING_GUIDE.md](EDITING_GUIDE.md)
2. Edytuj pliki w katalogu `data/`
3. Testuj lokalnie: `python -m http.server 8000`
4. Commituj zmiany

### Dla programistów
1. Przeczytaj [README.md](README.md) - struktura projektu
2. Zobacz `index.html` - kod źródłowy
3. Zrozum jak działa routing i renderowanie
4. Testuj przed deployment

### Dla administratorów
1. Przeczytaj [DEPLOYMENT.md](DEPLOYMENT.md)
2. Skonfiguruj GitHub Pages
3. Opcjonalnie: dodaj własną domenę
4. Monitoruj dostępność

## 🔗 Przydatne linki

- **GitHub Pages docs:** https://pages.github.com/
- **JSON Validator:** https://jsonlint.com
- **Git Guide:** https://git-scm.com/book/pl/v2

## ❓ Najczęściej zadawane pytania

**Q: Jak dodać nowy projekt?**
A: Edytuj `data/projects.json`, dodaj nowy obiekt do tablicy `projects`.

**Q: Jak zmienić tekst na stronie głównej?**
A: Edytuj `data/home.json`, sekcja `hero` lub `highlights`.

**Q: Jak zaktualizować skład zespołu?**
A: Edytuj `data/team.json`, dodaj nowy rok lub członków do istniejącego roku.

**Q: Jak dodać nową stronę?**
A: 
1. Utwórz nowy plik JSON w `data/`
2. Dodaj sekcję w `data/navigation.json` z odpowiednim `id`, `title`, `href` i `order`
3. Strona automatycznie pojawi się w menu
4. Upewnij się, że plik JSON ma poprawną strukturę

**Q: Strona nie ładuje danych lokalnie?**
A: Musisz użyć serwera HTTP (nie można otworzyć pliku bezpośrednio z systemu plików). Użyj: 
```bash
npm start
# lub: npx http-server -p 8000 -o
# lub: python -m http.server 8000
```

## 📞 Kontakt

W razie pytań lub problemów:
- Opiekun koła: **Piotr Porzuczek**
- Repozytorium: [GitHub](https://github.com/knsiexpert/site)

---

**Ostatnia aktualizacja:** 10 stycznia 2025

