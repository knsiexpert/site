# Instrukcja wdrożenia na GitHub Pages

## Krok po kroku

### 1. Przygotowanie repozytorium

Jeśli nie masz jeszcze repozytorium GitHub:

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
2. Nazwa repozytorium: `knmiexpert` (lub dowolna inna)
3. Ustaw jako **Public**
4. **Nie** dodawaj README, .gitignore ani licencji (już mamy lokalne)
5. Kliknij "Create repository"

### 3. Połączenie z GitHub

```bash
# Dodaj remote (zastąp YOUR_USERNAME swoim nickiem)
git remote add origin https://github.com/YOUR_USERNAME/knmiexpert.git

# Ustaw główną gałąź
git branch -M main

# Wypchnij kod
git push -u origin main
```

### 4. Aktywacja GitHub Pages

1. Przejdź do swojego repozytorium na GitHub
2. Kliknij **Settings** (ustawienia)
3. Z lewego menu wybierz **Pages**
4. W sekcji "Source":
   - Branch: wybierz **main**
   - Folder: wybierz **/ (root)**
5. Kliknij **Save**

### 5. Gotowe!

Po kilku minutach Twoja strona będzie dostępna pod adresem:
```
https://YOUR_USERNAME.github.io/knmiexpert/
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
# Python
python -m http.server 8000

# Lub Node.js
npx http-server -p 8000
```

Następnie otwórz: http://localhost:8000

