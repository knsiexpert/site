# 🚀 Szybki start - KNSI E-XPERT Website

## 1️⃣ Testowanie lokalne (TERAZ!)

Strona już działa lokalnie! Otwórz w przeglądarce:

```
http://localhost:8000
```

Serwer Python działa w tle. Jeśli chcesz go zatrzymać, użyj Ctrl+C w terminalu.

## 2️⃣ Edycja treści

Wszystkie treści są w katalogu `data/`:

```
data/
├── home.json         ← Strona główna (hero, highlights)
├── projects.json     ← Projekty AIS SC
├── goals.json        ← Cele i osiągnięcia
├── team.json         ← Skład zespołu
├── activity.json     ← Działalność koła
└── constitution.json ← Statut
```

**Przykład:** Aby zmienić tekst na stronie głównej:
1. Otwórz `data/home.json`
2. Znajdź sekcję `hero`
3. Zmień `title` lub `subtitle`
4. Zapisz plik
5. Odśwież przeglądarkę (Ctrl+F5)

## 3️⃣ Deployment na GitHub Pages

### A) Jeśli NIE masz jeszcze repozytorium:

```bash
# Inicjalizacja
git init
git add .
git commit -m "Initial commit"

# Połączenie z GitHub (zastąp YOUR_USERNAME)
git remote add origin https://github.com/YOUR_USERNAME/knmiexpert.git
git branch -M main
git push -u origin main
```

### B) Jeśli MAM już repozytorium:

```bash
git add .
git commit -m "Update website with JSON data structure"
git push
```

### C) Aktywacja GitHub Pages:

1. Idź do: **Settings** → **Pages**
2. Source: **main** branch, **/ (root)** folder
3. Kliknij **Save**
4. Gotowe! Strona będzie na: `https://YOUR_USERNAME.github.io/knmiexpert/`

## 4️⃣ Aktualizacja strony w przyszłości

Po każdej zmianie:

```bash
git add .
git commit -m "Opis zmian"
git push
```

GitHub automatycznie zaktualizuje stronę w 1-2 minuty.

## 📚 Więcej informacji

- **Szczegóły projektu:** [README.md](README.md)
- **Pełna instrukcja deployment:** [DEPLOYMENT.md](DEPLOYMENT.md)
- **Jak edytować treści:** [EDITING_GUIDE.md](EDITING_GUIDE.md)
- **Wszystkie linki:** [INDEX.md](INDEX.md)

## ⚡ Najczęstsze operacje

### Dodanie nowego projektu
1. Otwórz `data/projects.json`
2. Dodaj obiekt do tablicy `projects`:
```json
{
  "name": "Nowy projekt",
  "description": "Opis...",
  "team": ["Osoba 1", "Osoba 2"],
  "year": 2024,
  "images": []
}
```
3. Zapisz, testuj, commit, push!

### Aktualizacja zespołu
1. Otwórz `data/team.json`
2. Dodaj nowy rok lub członków do istniejącego:
```json
{
  "year": "2024/25",
  "board": ["..."],
  "members": ["Jan Kowalski", "..."]
}
```
3. Zapisz, testuj, commit, push!

### Zmiana linku "Dołącz do nas"
1. Otwórz `data/home.json`
2. Znajdź `hero.cta.href`
3. Zmień URL
4. Zapisz, testuj, commit, push!

## 🔧 Uruchomienie serwera lokalnego (gdy go zatrzymasz)

```bash
# Python
python -m http.server 8000

# Lub Node.js
npx http-server -p 8000
```

Następnie: http://localhost:8000

## ✅ Checklist przed pierwszym deployment

- [ ] Przetestowałem stronę lokalnie
- [ ] Wszystkie linki działają
- [ ] Dane w JSON są poprawne
- [ ] Stworzyłem repozytorium GitHub
- [ ] Wypchnąłem kod: `git push`
- [ ] Włączyłem GitHub Pages w Settings
- [ ] Strona jest dostępna online!

---

**Gotowe! Twoja strona jest teraz nowoczesna, łatwa w edycji i gotowa na GitHub Pages! 🎉**

