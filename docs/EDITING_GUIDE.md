# Przewodnik edycji treści

## Jak edytować zawartość strony

Wszystkie treści są przechowywane w plikach JSON w katalogu `data/`. Każdy plik odpowiada jednej stronie.

## Pliki danych

### ⚙️ navigation.json - Konfiguracja nawigacji (NOWE!)

**Ten plik kontroluje całą strukturę menu i metadane strony:**

```json
{
  "site": {
    "name": "Koło Naukowe Systemów Informatycznych E‑XPERT",
    "short_name": "KNSI E‑XPERT",
    "tagline": "IT DLA LUDZI",
    "logo_svg": "<svg>...</svg>"
  },
  "sections": [
    {
      "id": "home",
      "title": "Start",
      "slug": "home",
      "href": "home.json",
      "icon": "🏠",
      "description": "Strona główna z najważniejszymi informacjami o kole",
      "keywords": ["home", "główna", "start"],
      "order": 1,
      "visible": true
    }
  ]
}
```

**Pola sekcji:**
- `id` — unikalny identyfikator (używany w URL hash: `#home`)
- `title` — nazwa wyświetlana w menu
- `slug` — przyjazny URL (opcjonalnie)
- `href` — plik JSON z danymi sekcji
- `icon` — emoji lub symbol
- `description` — tooltip i opis dla SEO
- `keywords` — tablica słów kluczowych
- `order` — kolejność (1 = pierwszy, 2 = drugi...)
- `visible` — `true` (widoczna) lub `false` (ukryta)

**Jak dodać nową sekcję do menu:**
1. Otwórz `data/navigation.json`
2. Dodaj nowy obiekt do array `sections`
3. Ustaw odpowiednią wartość `order` aby kontrolować pozycję
4. Zapisz - menu automatycznie się zaktualizuje!

### 📄 home.json - Strona główna

**Hero section:**
```json
"hero": {
  "title": "KNSI E‑XPERT — IT dla ludzi",
  "subtitle": "Opis...",
  "cta": {
    "label": "Dołącz do nas",
    "href": "https://teams.microsoft.com/..."
  }
}
```

**Highlights (karty wyróżnień):**
```json
"highlights": [
  {
    "title": "III miejsce — AIS Student Chapter (2015)",
    "text": "Opis osiągnięcia...",
    "image": "url_do_obrazka"
  }
]
```

### 📄 projects.json - Projekty

```json
"projects": [
  {
    "name": "SocialMonitor",
    "description": "Opis projektu...",
    "team": ["Imię Nazwisko", "Imię Nazwisko"],
    "year": 2022,
    "images": ["url"]
  }
]
```

### 📄 goals.json - Cele i osiągnięcia

```json
"content": {
  "years": [
    {
      "year": "2021/22",
      "projects": [
        "Opis osiągnięcia 1",
        "Opis osiągnięcia 2"
      ]
    }
  ]
}
```

### 📄 team.json - Zespół

```json
"content": {
  "supervisor": "Imię Nazwisko",
  "years": [
    {
      "year": "2023/24",
      "board": [
        "Imię Nazwisko – Przewodniczący Koła",
        "Imię Nazwisko – Wiceprzewodniczący"
      ],
      "members": [
        "Imię Nazwisko",
        "Imię Nazwisko"
      ]
    }
  ]
}
```

### 📄 activity.json - Działalność

```json
"content": {
  "lead": "Tekst wprowadzający...",
  "activities": [
    "Opis działalności 1",
    "Opis działalności 2"
  ],
  "mission_goals": [
    "Cel 1",
    "Cel 2"
  ],
  "industry_collaboration": [
    {
      "partner": "Nazwa firmy",
      "role": "Opis współpracy"
    }
  ]
}
```

### 📄 constitution.json - Statut

```json
"content": {
  "intro": {
    "institution": "Uniwersytet Gdański",
    "location": "Adres...",
    "date": "Sopot, marzec 2014"
  },
  "articles": [
    {
      "number": 1,
      "title": "Tytuł artykułu",
      "content": [
        "Punkt 1",
        "Punkt 2"
      ]
    }
  ]
}
```

## Wskazówki

### ✅ Dobre praktyki

1. **Zachowaj strukturę JSON** - nie usuwaj kluczy, tylko zmieniaj wartości
2. **Sprawdź składnię** - użyj https://jsonlint.com przed zapisaniem
3. **Testuj lokalnie** - zawsze testuj zmiany na localhost przed wdrożeniem
4. **Backup** - zrób kopię przed większymi zmianami
5. **Znaki specjalne** - używaj escape sequences dla polskich znaków nie powoduje problemów, ale możesz użyć `\"` dla cudzysłowów w tekście

### ❌ Częste błędy

```json
// ❌ ZŁE - brak przecinka
{
  "title": "Test"
  "subtitle": "Test2"
}

// ✅ DOBRE - z przecinkiem
{
  "title": "Test",
  "subtitle": "Test2"
}
```

```json
// ❌ ZŁE - przecinek po ostatnim elemencie
{
  "title": "Test",
  "subtitle": "Test2",
}

// ✅ DOBRE - bez przecinka na końcu
{
  "title": "Test",
  "subtitle": "Test2"
}
```

```json
// ❌ ZŁE - nieescapowane cudzysłowy
"text": "Projekt "SafeWatch" był..."

// ✅ DOBRE - escapowane cudzysłowy
"text": "Projekt \"SafeWatch\" był..."
```

## Dodawanie nowych elementów

### Dodanie nowego projektu

1. Otwórz `data/projects.json`
2. W tablicy `projects` dodaj nowy obiekt:

```json
{
  "name": "Nazwa projektu",
  "description": "Opis...",
  "team": ["Członek 1", "Członek 2"],
  "year": 2024,
  "images": []
}
```

### Dodanie nowego członka zespołu

1. Otwórz `data/team.json`
2. Znajdź odpowiedni rok
3. Dodaj imię i nazwisko do tablicy `members`:

```json
"members": [
  "Jan Kowalski",
  "Nowy Członek"  // <- tutaj
]
```

### Dodanie nowego osiągnięcia

1. Otwórz `data/goals.json`
2. Znajdź odpowiedni rok lub dodaj nowy:

```json
{
  "year": "2024/25",
  "projects": [
    "Nowe osiągnięcie..."
  ]
}
```

## Aktualizacja po zmianach

Po edycji plików JSON:

1. Zapisz plik
2. Przetestuj lokalnie:
   ```bash
   npm start
   # lub: npx http-server -p 8000 -o
   # lub: python -m http.server 8000
   ```
3. Otwórz http://localhost:8000 i sprawdź zmiany
4. Jeśli wszystko działa:
   ```bash
   git add data/
   git commit -m "Aktualizacja treści"
   git push
   ```

## Narzędzia pomocnicze

- **Walidator JSON:** https://jsonlint.com
- **Formatter JSON:** https://jsonformatter.org
- **Edytor:** VS Code z rozszerzeniem "JSON" (automatyczne formatowanie)

