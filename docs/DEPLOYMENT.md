# Instrukcja wdrożenia na GitHub Pages

## 🚀 Automatyczny deployment (ZALECANE)

Projekt jest skonfigurowany z **GitHub Actions** do automatycznego deploymentu!

### 1. Przygotowanie repozytorium

```bash
# Inicjalizacja git (jeśli jeszcze nie zrobione)
git init

# Dodanie wszystkich plików
git add .

# Pierwszy commit
git commit -m "Initial commit - KNSI E-XPERT website"
```

### 2. Utworzenie repozytorium na GitHub

1. Przejdź na https://github.com/new
2. Nazwa repozytorium: `site` (lub dowolna inna)
3. Ustaw jako **Public**
4. **Nie** dodawaj README, .gitignore ani licencji (już mamy lokalne)
5. Kliknij "Create repository"

### 3. Połączenie z GitHub

```bash
# Dodaj remote (przykład dla organizacji knsiexpert)
git remote add origin https://github.com/knsiexpert/site.git

# Ustaw główną gałąź
git branch -M main

# Wypchnij kod
git push -u origin main
```

### 4. Aktywacja GitHub Pages

1. Przejdź do swojego repozytorium na GitHub
2. Kliknij **Settings** → **Pages**
3. W sekcji "Build and deployment":
   - Source: wybierz **GitHub Actions**
4. To wszystko! 🎉

### 5. Automatyczny deployment

Od teraz przy każdym `git push` do `main`:
- GitHub Actions automatycznie zbuduje i wdroży stronę
- Zobacz status w zakładce **Actions** na GitHub
- Strona będzie dostępna pod: `https://knsiexpert.github.io/site/`

---

## 📦 Ręczny deployment z npm (ALTERNATYWA)

Jeśli wolisz ręczny deployment:

### 1. Instalacja zależności

```bash
npm install
```

### 2. Deploy

```bash
npm run deploy
```

Gotowe! Skrypt automatycznie:
- Utworzy branch `gh-pages`
- Skopiuje pliki
- Wypchnę na GitHub
- Strona będzie dostępna za kilka minut

### 3. Aktualizacja w przyszłości

```bash
# Wprowadź zmiany w plikach
git add .
git commit -m "Update content"
git push

# Deploy na GitHub Pages
npm run deploy
```

---

## 📝 Oba podejścia

### GitHub Actions (Automatyczny) ✅ ZALECANE
**Zalety:**
- ✅ W pełni automatyczny
- ✅ Deploy przy każdym push
- ✅ Nie wymaga npm/node lokalnie
- ✅ Widoczny status w Actions

**Wady:**
- ❌ Wymaga konfiguracji Settings

### npm gh-pages (Ręczny)
**Zalety:**
- ✅ Pełna kontrola
- ✅ Deploy tylko gdy chcesz
- ✅ Działa offline

**Wady:**
- ❌ Wymaga npm/node
- ❌ Trzeba pamiętać o `npm run deploy`

---

## 🔧 Konfiguracja

### Zmiana URL w package.json

Jeśli Twoje repo ma inną nazwę:

```json
{
  "homepage": "https://YOUR_USERNAME.github.io/YOUR_REPO_NAME"
}
```

### Zmiana brancha w workflow

Edytuj `.github/workflows/deploy.yml`:

```yaml
on:
  push:
    branches:
      - main  # zmień na inny branch jeśli potrzeba
```

## Aktualizacja strony

Po każdej zmianie w plikach JSON lub HTML:

```bash
git add .
git commit -m "Opis zmian"
git push
```

GitHub Pages automatycznie zaktualizuje stronę w ciągu 1-2 minut.

## Własna domena (opcjonalnie)

Jeśli masz domenę e-xpert.pl:

1. Utwórz plik `CNAME` w głównym katalogu:
   ```
   e-xpert.pl
   ```

2. W ustawieniach DNS swojej domeny dodaj rekord:
   - Typ: **CNAME** (dla subdomen) lub **A** (dla głównej domeny)
   - Host: **@** (lub subdomena)
   - Wartość: **YOUR_USERNAME.github.io**

3. W ustawieniach GitHub Pages wpisz swoją domenę w polu "Custom domain"

## Rozwiązywanie problemów

### Strona nie ładuje danych

- Sprawdź konsolę przeglądarki (F12)
- Upewnij się, że wszystkie pliki JSON są w katalogu `data/`
- Sprawdź czy nie ma błędów składni w JSON (użyj https://jsonlint.com)

### 404 Not Found

- Upewnij się, że GitHub Pages jest włączone
- Sprawdź czy adres URL zawiera nazwę repozytorium
- Poczekaj kilka minut na propagację zmian

### Stara wersja strony

- Wymuś odświeżenie: Ctrl+F5 (Windows) lub Cmd+Shift+R (Mac)
- Wyczyść cache przeglądarki
- GitHub Pages może potrzebować kilku minut na aktualizację

## Testowanie lokalne

Zawsze testuj zmiany lokalnie przed wdrożeniem:

```bash
# NPM (zalecane) - automatycznie otwiera przeglądarkę
npm start

# Lub npx (bez instalacji)
npx http-server -p 8000 -o

# Lub Python
python -m http.server 8000
```

Następnie otwórz: http://localhost:8000

