# 📦 NPM Guide

## Dostępne komendy

### Development

```bash
# Uruchom lokalny serwer (Python)
npm start
# lub
npm run dev

# Otwórz: http://localhost:8000
```

### Deployment

```bash
# Instalacja zależności (tylko pierwszy raz)
npm install

# Deploy na GitHub Pages
npm run deploy

# Deploy z czyszczeniem (usuwa pliki .md z gh-pages)
npm run deploy:clean
```

## Jak to działa?

### `npm start` / `npm run dev`
- Uruchamia Python HTTP server na porcie 8000
- Wymaga Python 3 w systemie
- Przydatne do lokalnego testowania

### `npm run deploy`
- Używa pakietu `gh-pages`
- Automatycznie tworzy branch `gh-pages`
- Kopiuje wszystkie pliki do tego brancha
- Pushuje na GitHub
- GitHub Pages automatycznie hostuje zawartość

### `npm run deploy:clean`
- Jak `deploy`, ale dodatkowo:
  - Usuwa pliki `.md` (dokumentacja nie jest potrzebna na live site)
  - Dodaje nowe pliki jeśli zostały utworzone

## Pierwsze użycie

1. **Zainstaluj Node.js** (jeśli nie masz):
   - Pobierz z https://nodejs.org/
   - Wersja LTS (Long Term Support) wystarczy

2. **Zainstaluj zależności:**
   ```bash
   npm install
   ```

3. **Skonfiguruj package.json:**
   - Zmień `homepage` URL na swoje repo
   - Zmień `repository.url` na swoje repo

4. **Deploy:**
   ```bash
   npm run deploy
   ```

## Aktualizacja strony

```bash
# 1. Edytuj pliki (JSON, HTML, CSS)
# 2. Testuj lokalnie
npm start

# 3. Commit zmiany
git add .
git commit -m "Update content"
git push

# 4. Deploy na GitHub Pages
npm run deploy
```

## Troubleshooting

### Problem: `npm: command not found`
**Rozwiązanie:** Zainstaluj Node.js z https://nodejs.org/

### Problem: `gh-pages: command not found`
**Rozwiązanie:** 
```bash
npm install
```

### Problem: `Permission denied`
**Rozwiązanie (Linux/Mac):**
```bash
sudo npm install -g npm
```

### Problem: Deploy nie działa
**Sprawdź:**
1. Czy masz dostęp do repozytorium?
2. Czy `homepage` w `package.json` jest poprawny?
3. Czy branch `gh-pages` istnieje?

**Debug:**
```bash
npm run deploy -- --verbose
```

## GitHub Actions vs npm deploy

### GitHub Actions (Zalecane)
✅ Automatyczny deploy przy każdym push  
✅ Nie wymaga npm lokalnie  
✅ Widoczny status w GitHub  
❌ Wymaga konfiguracji w Settings  

### npm deploy
✅ Pełna kontrola  
✅ Deploy tylko gdy chcesz  
✅ Działa offline  
❌ Wymaga npm  
❌ Trzeba pamiętać o komendzie  

## Dodatkowe komendy

### Sprawdź wersję
```bash
npm --version
node --version
```

### Wyczyść cache
```bash
npm cache clean --force
```

### Aktualizuj zależności
```bash
npm update
```

### Sprawdź outdated packages
```bash
npm outdated
```

## CI/CD Integration

Projekt ma już skonfigurowany GitHub Actions workflow w:
```
.github/workflows/deploy.yml
```

Możesz używać obu metod jednocześnie:
- GitHub Actions dla automatycznego deploymentu
- `npm run deploy` dla ręcznego deploymentu

---

**Potrzebujesz pomocy?** Zobacz [DEPLOYMENT.md](DEPLOYMENT.md)

