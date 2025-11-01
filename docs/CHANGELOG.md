# Changelog

## [3.19.3] - 2025-01-01

### 📏 Achievements Cards Alignment

#### Wszystkie kafelki mają jednolitą wysokość tytułów, opisów i obrazów

**Problem:**
W sekcji "Nasze osiągnięcia" karty miały różną wysokość tekstu, przez co zdjęcia były na różnych poziomach i całość wyglądała nierówno.

**Rozwiązanie:**
Dodano flexbox layout do kart oraz stałe minimalne wysokości dla tytułów i opisów.

**Zmiany CSS - Desktop:**

```css
/* Karta jako flex container */
.highlight-card {
    display: flex;
    flex-direction: column;
}

/* Stała wysokość tytułu */
.highlight-card h3 {
    min-height: 44px;  /* ~2 linie tekstu */
}

/* Stała wysokość opisu */
.highlight-card p {
    min-height: 80px;  /* ~3-4 linie tekstu */
    margin-bottom: 0;
}

/* Obrazek zawsze na dole */
.highlight-image {
    margin-top: auto;  /* wypycha do dołu */
    padding-top: 30px;
}

/* Poprawka pozycji dekoracyjnej ramki */
.highlight-image::before {
    top: calc(30px - 8px);  /* było: top: -8px */
}

.highlight-card:hover .highlight-image::before {
    top: calc(30px - 12px);  /* było: top: -12px */
}
```

**Zmiany CSS - Mobile:**

```css
.highlight-card h3 {
    min-height: 36px;  /* mniejsza dla mobile */
}

.highlight-card p {
    min-height: 60px;  /* mniejsza dla mobile */
}

.highlight-image {
    margin-top: auto;
    padding-top: 20px;  /* mniejszy padding */
}

.highlight-image::before {
    top: calc(20px - 6px);
}

.highlight-card:hover .highlight-image::before {
    top: calc(20px - 8px);
}
```

**Diagram layoutu:**

```
┌─────────────────────────────────────────────────┐
│ KARTA 1            KARTA 2            KARTA 3   │
│ ┌───────────────┐  ┌───────────────┐  ┌───────┐│
│ │ Tytuł         │  │ Długi tytuł   │  │ Tytuł ││
│ │ (44px min)    │  │ na dwie linie │  │       ││
│ ├───────────────┤  ├───────────────┤  ├───────┤│
│ │ Opis tekstu   │  │ Krótki opis   │  │ Opis  ││
│ │ (80px min)    │  │               │  │ tekstu││
│ │               │  │               │  │       ││
│ ├───────────────┤  ├───────────────┤  ├───────┤│ ← Wszystkie obrazy na tej samej linii
│ │[  Obrazek   ]│  │[  Obrazek   ]│  │[Obraz]││
│ │[  200px     ]│  │[  200px     ]│  │[200px]││
│ └───────────────┘  └───────────────┘  └───────┘│
└─────────────────────────────────────────────────┘
```

**PRZED:**
```
┌────────────────────────────────────┐
│ Krótki tytuł                       │
│ Krótki opis                        │
│ [Obrazek]  ← wysoko               │
│                                     │
├────────────────────────────────────┤
│ Bardzo długi tytuł na dwie linie   │
│ Długi opis rozciągnięty            │
│ na kilka linii tekstu              │
│ [Obrazek]  ← nisko                │
└────────────────────────────────────┘
```

**PO:**
```
┌────────────────────────────────────┐
│ Krótki tytuł                       │
│ (pozostała przestrzeń pusta)       │
│ Krótki opis                        │
│ (pozostała przestrzeń pusta)       │
│ [Obrazek]  ← na tej samej linii   │
│                                     │
├────────────────────────────────────┤
│ Bardzo długi tytuł na dwie linie   │
│ (wypełnione całe 44px)             │
│ Długi opis rozciągnięty            │
│ na kilka linii tekstu              │
│ [Obrazek]  ← na tej samej linii   │
└────────────────────────────────────┘
```

**Efekt:**
- ✅ **Perfekcyjne wyrównanie** — wszystkie obrazy zaczynają się na tej samej wysokości
- ✅ **Wizualna spójność** — karty wyglądają profesjonalnie i uporządkowanie
- ✅ **Flexbox magic** — `margin-top: auto` wypycha obrazki do dołu
- ✅ **Responsive** — różne wysokości dla desktop i mobile
- ✅ **Zachowana estetyka** — dekoracyjne ramki (::before) nadal działają poprawnie

**Wysokości:**
- **Desktop:** h3 = 44px, p = 80px
- **Mobile:** h3 = 36px, p = 60px

## [3.19.2] - 2025-01-01

### 📐 Activity Section Layout Improvement

#### Sekcja "O NAS" przeniesiona pod kolumny dla lepszej hierarchii informacji

**Problem:**
Użytkownik najpierw widział długą sekcję "O NAS" z historią, a potem dopiero konkretne działania koła.

**Rozwiązanie:**
Zmieniono kolejność - najpierw pokazujemy co koło robi (kolumny z działaniami, celami, współpracą), a potem historię.

**Struktura PRZED:**
```
DZIAŁALNOŚĆ
└── O NAS (historia - długi tekst)
└── [Kolumny]
    ├── Lewa: Konkursy, projekty, szkolenia...
    └── Prawa: Cele i misja, Współpraca, Mapa
```

**Struktura PO:**
```
DZIAŁALNOŚĆ
└── [Kolumny]
    ├── Lewa: Konkursy, projekty, szkolenia...
    └── Prawa: Cele i misja, Współpraca, Mapa
└── O NAS (historia - długi tekst)
```

**Zmiany w `index.html`:**
```javascript
// PRZED - O NAS na górze
activityContent.innerHTML = `
    <h2>"${data.title.toUpperCase()}"</h2>
    
    ${data.content.about ? `
        <div>O NAS...</div>
    ` : ''}
    
    <div style="display: grid;">
        <!-- Kolumny -->
    </div>
`;

// PO - O NAS na dole
activityContent.innerHTML = `
    <h2>"${data.title.toUpperCase()}"</h2>
    
    <div style="display: grid;">
        <!-- Kolumny -->
    </div>
    
    ${data.content.about ? `
        <div style="margin-top: 60px;">O NAS...</div>
    ` : ''}
`;
```

**Efekt:**
- ✅ **Lepsza hierarchia** — najpierw konkretna działalność, potem historia
- ✅ **Lepszy UX** — użytkownik szybciej widzi co koło robi obecnie
- ✅ **Logiczny flow** — od "co robimy" do "skąd przyszliśmy"
- ✅ **Mobile responsive** — nadal działa na małych ekranach

**Layout Desktop:**
```
┌─────────────────────────────────────────────────────────┐
│  DZIAŁALNOŚĆ                                           │
│                                                          │
│  ┌────────────────┬────────────────────────────────┐   │
│  │ Konkursy       │ Cele i misja                    │   │
│  │ Projekty       │ - cel 1                         │   │
│  │ Szkolenia      │ - cel 2                         │   │
│  │ Testowanie     │                                  │   │
│  │ Popularyzacja  │ Współpraca z przemysłem         │   │
│  │                │ [Madkom] [Neoteric] [...]       │   │
│  │                │                                  │   │
│  │                │ Lokalizacja                      │   │
│  │                │ [Google Maps]                   │   │
│  └────────────────┴────────────────────────────────┘   │
│                                                          │
│  O NAS                                                  │
│  Koło Naukowe Systemów Informatycznych E-XPERT...      │
│  [długi tekst historyczny]                             │
└─────────────────────────────────────────────────────────┘
```

## [3.19.1] - 2025-01-01

### 🎨 Logo SVG Fix

#### Poprawiono wyświetlanie logo (było widoczne jako mała kropka)

**Problem:**
Logo wyświetlało się jako mała kropka zamiast pełnego symbolu E-XPERT.

**Rozwiązanie:**
Użyto poprawnego SVG z pliku `data/e-xpert-symbol.svg`.

**Zmiany w `navigation.json`:**
```json
{
  "site": {
    "logo_svg": "<svg xmlns=\"http://www.w3.org/2000/svg\" viewBox=\"-30 0 740 380\">
      <g transform=\"translate(-162 -143)\">
        <path fill=\"currentColor\" d=\"M504 447l-1 1h-2...\"/>
      </g>
    </svg>"
  }
}
```

**Kluczowe poprawki:**
1. **viewBox** — zmieniono z `-30.0 0.0 740.0 380.0` na `-30 0 740 380`
2. **fill attribute** — dodano `fill="currentColor"` bezpośrednio w elemencie `<path>`
3. **Namespace cleanup** — usunięto namespace prefix `ns0:`

**PRZED:**
```svg
<svg viewBox="-30.0 0.0 740.0 380.0">
  <path d="..." fill="currentColor" />
</svg>
```

**PO:**
```svg
<svg viewBox="-30 0 740 380">
  <g transform="translate(-162 -143)">
    <path fill="currentColor" d="..." />
  </g>
</svg>
```

**Efekt:**
- ✅ Logo E-XPERT wyświetla się poprawnie
- ✅ Zachowano gradient border i glow effect
- ✅ Animacja 3D rotation działa poprawnie
- ✅ Responsive na mobile i desktop

## [3.19.0] - 2025-01-01

### 🖼️ Enhanced Carousel — Dual-Row Display on Desktop

#### Dodano 3 zdjęcia i 2 rzędy na desktop

**Zmiany w `home.json`:**
```json
"images": [
  "https://i.imgur.com/KbCxaWl.jpeg",
  "https://i.imgur.com/cMbL4Zv.jpeg",
  "https://i.imgur.com/kTqJvzR.jpeg",
  "https://i.imgur.com/g8piQkb.jpeg",
  "https://i.imgur.com/oeWjiYh.jpeg",
  "https://i.imgur.com/HFihwiH.jpeg",
  "https://i.imgur.com/gyHGyJ1.jpeg",
  "https://i.imgur.com/dPTYUzW.jpeg",
  "https://i.imgur.com/XirvXmJ.jpeg",
  "https://i.imgur.com/JH7C0Yt.jpeg",  // NOWE
  "https://i.imgur.com/MNa0Pfh.jpeg",  // NOWE
  "https://i.imgur.com/APBdSnN.jpeg"   // NOWE
]
```

**CSS Desktop - 2 rzędy:**
```css
.carousel-group {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  grid-template-rows: repeat(2, 1fr);  /* NOWE - 2 rzędy */
  gap: 30px;
}
```

**JavaScript - Grupy po 6 zdjęć:**
```javascript
// PRZED - grupy po 3
for (let i = 0; i < data.us.images.length; i += 3) {
  groups.push(data.us.images.slice(i, i + 3));
}

// PO - grupy po 6 (2 rzędy x 3 kolumny)
for (let i = 0; i < data.us.images.length; i += 6) {
  groups.push(data.us.images.slice(i, i + 6));
}

// Zaktualizowano absoluteIndex
const absoluteIndex = (groupIndex * 6 + index) % data.us.images.length;  // było * 3
```

**CSS Mobile - bez zmian:**
```css
@media (max-width: 768px) {
  .carousel-group {
    grid-template-columns: 1fr;
    grid-template-rows: auto;  /* pojedyncza kolumna */
    gap: 50px;
  }
}
```

**Porównanie:**

| Wersja | Zdjęć | Desktop (widok) | Mobile (widok) | Grupa |
|--------|-------|-----------------|----------------|-------|
| **3.18.x** | 9 | 3 zdjęcia (1x3) | 1 zdjęcie | 3 zdjęcia |
| **3.19.0** | 12 | 6 zdjęć (2x3) | 1 zdjęcie | 6 zdjęć |

**Layout Desktop:**
```
┌─────────────────────────────────────┐
│  [Img 1]   [Img 2]   [Img 3]       │  Rząd 1
│  [Img 4]   [Img 5]   [Img 6]       │  Rząd 2
└─────────────────────────────────────┘
```

**Nowe zdjęcia z gallery.json:**
- JH7C0Yt
- MNa0Pfh
- APBdSnN

**Efekt:**
- ✅ **Więcej zawartości** — 6 zdjęć naraz zamiast 3
- ✅ **Lepsza prezentacja** — 2 rzędy wykorzystują przestrzeń pionową
- ✅ **12 zdjęć total** — większa różnorodność
- ✅ **Mobile responsive** — nadal 1 kolumna na małych ekranach
- ✅ **Smooth transitions** — seamless infinite loop działa poprawnie

## [3.18.3] - 2025-01-01

### 📍 Google Maps Marker Fix

#### Poprawiono wyświetlanie pinezki na mapie

**Problem:**
- Mapa nie wyświetlała markera/pinezki na adresie
- Użyty był zbyt skomplikowany format URL

**Rozwiązanie:**
```html
<!-- PRZED - bez markera -->
src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2323.86..."

<!-- PO - z markerem -->
src="https://maps.google.com/maps?q=Piaskowa+9C,+Sopot&t=&z=15&ie=UTF8&iwloc=&output=embed"
```

**Parametry URL:**
- `q=Piaskowa+9C,+Sopot` - wyszukiwanie adresu (automatycznie dodaje marker)
- `z=15` - poziom zoom (optymalny dla pojedynczego adresu)
- `output=embed` - format dla osadzenia w iframe

**Efekt:**
- ✅ **Czerwona pinezka widoczna** — marker dokładnie na adresie Piaskowa 9C
- ✅ **Prostszy URL** — łatwiejszy w utrzymaniu
- ✅ **Lepsze centrum** — mapa wyśrodkowana na adresie
- ✅ **Zoom 15** — optymalny poziom przybliżenia

## [3.18.2] - 2025-01-01

### 🗺️ Google Maps Location Integration

#### Dodano mapę Google Maps z lokalizacją Koła

**Dodano:**
- **Sekcja "LOKALIZACJA"** w prawej kolumnie pod współpracą z przemysłem
- **Mapa Google Maps** z pinezką na adres Koła
- **Adres tekstowy** nad mapą

**Adres:**
```
Piaskowa 9C, 81-862 Sopot
```

**Implementacja:**
```html
<h3 style="margin-top: 50px; ...">LOKALIZACJA</h3>
<p style="margin-bottom: 20px; ...">
    Piaskowa 9C, 81-862 Sopot
</p>
<div style="width: 100%; height: 300px; border: 2px solid var(--black); overflow: hidden;">
    <iframe 
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2323.86..."
        width="100%" 
        height="300" 
        style="border:0;" 
        allowfullscreen="" 
        loading="lazy" 
        referrerpolicy="no-referrer-when-downgrade">
    </iframe>
</div>
```

**Parametry:**
- **Wysokość**: 300px
- **Border**: 2px solid black (spójny z designem)
- **Loading**: lazy (optymalizacja wydajności)
- **Allowfullscreen**: możliwość otwarcia na pełnym ekranie
- **Referrerpolicy**: no-referrer-when-downgrade (bezpieczeństwo)

**Pozycjonowanie w prawej kolumnie:**
```
┌──────────────────────┬──────────────────────┐
│ LEWA KOLUMNA         │ PRAWA KOLUMNA        │
├──────────────────────┼──────────────────────┤
│ • KONKURSY           │ CELE I MISJA         │
│ • PROJEKTY           │ • Cel 1, 2, 3...     │
│ • SZKOLENIA          │                      │
│ • TESTOWANIE         │ WSPÓŁPRACA Z PRZEM.  │
│ • POPULARYZACJA      │ [Madkom] [Neoteric]  │
│                      │ [Bright] [Staples]   │
│                      │                      │
│                      │ LOKALIZACJA          │
│                      │ Piaskowa 9C, Sopot   │
│                      │ [Mapa Google Maps]   │
└──────────────────────┴──────────────────────┘
```

**Efekt:**
- ✅ **Łatwa lokalizacja** — użytkownicy wiedzą gdzie znajduje się Koło
- ✅ **Interaktywna mapa** — możliwość zoom, przesuwania, otwarcia w Google Maps
- ✅ **Spójny design** — czarna ramka pasuje do reszty strony
- ✅ **Optymalizacja** — lazy loading nie spowalnia początkowego ładowania strony
- ✅ **Profesjonalny wygląd** — jak na stronach firm

## [3.18.1] - 2025-01-01

### 📊 Two-Column Activity Layout — Professional Grid

#### Przeprojektowano layout sekcji działalności na dwukolumnowy

**Problem:**
- Sekcje "CELE I MISJA" i "WSPÓŁPRACA Z PRZEMYSŁEM" były pod tabelką działalności
- Layout wertykalny marnował przestrzeń
- Strona była zbyt długa

**Rozwiązanie - Grid Layout:**
```html
<div style="display: grid; grid-template-columns: 1fr 1fr; gap: 60px;">
  <div>
    <!-- Lewa kolumna: KONKURSY, PROJEKTY, SZKOLENIA, TESTOWANIE, POPULARYZACJA -->
    <div class="activity-list">...</div>
  </div>
  
  <div>
    <!-- Prawa kolumna: CELE I MISJA + WSPÓŁPRACA Z PRZEMYSŁEM -->
    <h3>CELE I MISJA</h3>
    <ul>...</ul>
    
    <h3>WSPÓŁPRACA Z PRZEMYSŁEM</h3>
    <p>...</p>
    <div><!-- Przyciski firm --></div>
  </div>
</div>
```

**Responsive:**
```css
@media (max-width: 968px) {
  #activityContent > div[style*="grid-template-columns"] {
    grid-template-columns: 1fr !important;
    gap: 40px !important;
  }
}
```

**Layout:**
```
┌─────────────────────────────────────────────┐
│                                             │
│  O NAS (pełna szerokość)                   │
│                                             │
└─────────────────────────────────────────────┘

┌──────────────────────┬──────────────────────┐
│ LEWA KOLUMNA         │ PRAWA KOLUMNA        │
├──────────────────────┼──────────────────────┤
│ • KONKURSY           │ CELE I MISJA         │
│ • PROJEKTY           │ • Cel 1              │
│ • SZKOLENIA          │ • Cel 2              │
│ • TESTOWANIE         │ • Cel 3              │
│ • POPULARYZACJA      │                      │
│                      │ WSPÓŁPRACA Z PRZEM.  │
│                      │ [Madkom] [Neoteric]  │
│                      │ [Bright] [Staples]   │
└──────────────────────┴──────────────────────┘
```

**Parametry:**
- **Gap**: 60px (desktop), 40px (mobile)
- **Breakpoint**: 968px
- **Kolumny**: 1fr 1fr (równe szerokości)
- **margin-top**: 40px (odsunięcie od sekcji "O NAS")

**Zmiany w h3:**
- `margin-top: 0` w prawej kolumnie (było 60px)
- Zachowano `margin-top: 60px` w poprzednich wersjach

**Efekt:**
- ✅ **Lepsze wykorzystanie przestrzeni** — dwie kolumny obok siebie
- ✅ **Profesjonalny layout** — grid jak na stronach korporacyjnych
- ✅ **Krótsza strona** — zawartość bardziej kompaktowa
- ✅ **Lepsza organizacja** — działalności po lewej, cele i partnerzy po prawej
- ✅ **Responsive** — automatycznie przełącza się na jedną kolumnę na mobile

## [3.18.0] - 2025-01-01

### 🎯 Professional Typography & Kerning — Corporate Standard

#### Przeprojektowano typografię według standardów korporacyjnych

**Inspiracja:** Strona [Madkom](https://madkom.pl/) - profesjonalna firma IT dla administracji publicznej

**Główne zmiany typograficzne:**

**1. Font-family - System Fonts:**
```css
/* PRZED */
font-family: 'Helvetica Neue', 'Helvetica', 'Arial', -apple-system, sans-serif;

/* PO - profesjonalny system font stack */
font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', 'Roboto', 
             'Oxygen', 'Ubuntu', 'Cantarell', 'Helvetica Neue', 'Arial', sans-serif;
```

**2. Letter-spacing - Profesjonalny kerning:**
```css
/* Body */
body: -0.01em           /* było -0.02em */

/* Nagłówki */
h2: -0.025em           /* było 0.02em */
h3: -0.015em           /* było 0.01em */

/* Logo */
.logo: -0.01em         /* było 0.1em */
.logo-text: -0.01em    /* było 0.08em */

/* Nawigacja */
.nav-links a: 0.08em   /* było 0.15em */

/* Przyciski firm */
partners: 0.02em       /* było 0.1em */
```

**3. Rozmiary fontów - Optymalizacja:**
```css
body: 16px              /* było 15px */
h2: max 56px            /* było 64px */
h3: 20px                /* było 19px */
.nav-links a: 11px      /* było 10px */
.logo: 20px             /* było 22px */
partners: 15px          /* było 17px */
```

**4. Line-height - Lepsza czytelność:**
```css
body: 1.65              /* było 1.8 */
paragraphs: 1.7         /* było 1.9 */
lists: 2.0              /* było 2.2 */
```

**5. Font-weight - Bardziej stonowany:**
```css
body: 400               /* dodano */
.nav-links a: 600       /* było 500 */
.logo: 600              /* było 700 */
partners: 600           /* było 700 */
h2: 700                 /* było 600 */
```

**6. Padding - Zoptymalizowany:**
```css
partners: 14px 28px     /* było 16px 32px */
```

**Porównanie przed/po:**

| Element | Przed | Po | Zmiana |
|---------|-------|-----|--------|
| **Body font-size** | 15px | 16px | +1px |
| **Body letter-spacing** | -0.02em | -0.01em | +0.01em |
| **Body line-height** | 1.8 | 1.65 | -0.15 |
| **H2 max-size** | 64px | 56px | -8px |
| **H2 letter-spacing** | 0.02em | -0.025em | -0.045em |
| **H3 letter-spacing** | 0.01em | -0.015em | -0.025em |
| **Nav letter-spacing** | 0.15em | 0.08em | -0.07em |
| **Logo letter-spacing** | 0.1em | -0.01em | -0.11em |
| **Przyciski letter-spacing** | 0.1em | 0.02em | -0.08em |

**Efekt:**
- ✅ **Profesjonalny wygląd** — przestrzeń jak na stronie korporacyjnej
- ✅ **Lepsza czytelność** — optymalne odstępy między znakami
- ✅ **Negatywny kerning** — nowoczesne, ciasne nagłówki
- ✅ **System fonts** — natywne czcionki systemowe
- ✅ **Spójność** — jednolita typografia w całej witrynie
- ✅ **Nie wygląda jak "stronka studencka"** — poziom korporacyjny

## [3.17.1] - 2025-01-01

### 🎨 Fixed Partner Buttons Contrast — Black Background

#### Poprawiono czytelność przycisków firm na białym tle

**Problem:**
- Przyciski firm były nieczytelne na białym tle strony
- Zbyt mały kontrast między tłem przycisku a tłem strony
- Tekst trudny do odczytania

**Rozwiązanie:**
```css
/* PRZED - nieczytelne */
background: var(--surface);     /* jasne tło */
border: 2px solid var(--border);
color: var(--white);

/* PO - wyraźnie widoczne */
background: var(--black);       /* czarne tło */
border: 3px solid var(--black); /* grubszy border */
color: var(--white);            /* biały tekst */
```

**Hover effect - jeszcze lepszy:**
```javascript
onmouseover="
  this.style.borderColor='var(--accent)';
  this.style.background='var(--accent)';  /* pomarańczowe tło */
  this.style.color='var(--black)';        /* czarny tekst */
  this.style.transform='translateY(-2px)';
  this.style.boxShadow='0 4px 16px rgba(255,107,0,0.3)';
"

onmouseout="
  this.style.borderColor='var(--black)';
  this.style.background='var(--black)';   /* powrót do czarnego */
  this.style.color='var(--white)';
  this.style.transform='translateY(0)';
  this.style.boxShadow='none';
"
```

**Staples Solutions (bez linku):**
```css
background: #333;        /* ciemnoszary */
border-color: #333;
opacity: 0.9;           /* lekko przygaszone */
```

**Kontrast:**
| Element | Tło | Tekst | Border | Kontrast |
|---------|-----|-------|--------|----------|
| **Linki** | Czarne | Biały | 3px czarny | ✅ Wysoki |
| **Hover** | Pomarańczowy | Czarny | 3px pomarańczowy | ✅ Wysoki |
| **Staples** | #333 | Biały | 3px #333 | ✅ Wysoki |

**Efekt:**
- ✅ **Przyciski wyraźnie widoczne** — czarne na białym tle
- ✅ **Tekst czytelny** — biały na czarnym
- ✅ **Lepszy hover** — accent color z czarnym tekstem
- ✅ **Profesjonalny wygląd** — silny kontrast, czytelne nazwy firm

## [3.17.0] - 2025-01-01

### 📚 Enhanced Activity Page — Comprehensive About Section

#### Dodano rozbudowaną sekcję "O NAS" i poprawiono czytelność

**Nowa sekcja "O NAS" w `activity.json`:**
```json
{
  "about": "Koło Naukowe Systemów Informatycznych E-XPERT powstało w 2001 roku..."
}
```

Sekcja zawiera:
- Historia powstania (2001)
- Pierwsze projekty (mobileWZR)
- Dołączenie do AIS SC (2015)
- Ważne projekty (SafeWatch, CyberWatch, Unity, SNet, Eris, Apollo)
- Rozwój kultury współpracy
- Nowsze inicjatywy (SocialMonitor, UniGo)
- Cyfrowa transformacja (GitHub Pages)
- Obecna działalność
- Opiekunowie (prof. Kuciapski, prof. Wrycza, mgr Porzuczek)

**Typografia sekcji "O NAS":**
```css
h3 {
  font-size: 24px;
  font-weight: 700;
  margin-bottom: 30px;
}

p {
  font-size: 17px;      /* było 14-16px */
  line-height: 1.9;     /* było ~1.6 */
  text-align: justify;  /* dodano */
  margin-bottom: 25px;
}
```

**Poprawki w całej sekcji Działalność:**

**1. Nazwy firm — znacząco większy font:**
```css
font-size: 17px;          /* było 15px */
font-weight: 700;         /* było 600 */
padding: 16px 32px;       /* było 14px 28px */
letter-spacing: 0.1em;    /* było 0.08em */
```

**2. Usunięto strzałki z list:**
```html
<!-- PRZED -->
<li>→ Cel pierwszy</li>

<!-- PO -->
<li>Cel pierwszy</li>
```

```css
ul {
  list-style: none;       /* usunięto default bullets */
  padding-left: 0;        /* usunięto wcięcie */
  font-size: 17px;        /* większy font */
  line-height: 2.2;       /* większy spacing */
}
```

**3. Spójne nagłówki H3:**
```css
h3 {
  font-size: 24px;        /* było różnie 18-22px */
  font-weight: 700;       /* dodano */
  margin-top: 60px;
}
```

**4. Etykiety działań:**
```css
strong {
  font-size: 16px;
  font-weight: 700;
}

span {
  font-size: 16px;
  line-height: 1.7;
}
```

**Struktura sekcji:**
```
DZIAŁALNOŚĆ
└─ O NAS (nowa sekcja)
   └─ 11 akapitów historii
└─ KONKURSY, PROJEKTY, SZKOLENIA, TESTOWANIE, POPULARYZACJA
└─ CELE I MISJA (bez strzałek)
└─ WSPÓŁPRACA Z PRZEMYSŁEM (większe przyciski)
```

**Efekt:**
- ✅ **Pełna historia** — od 2001 do dziś, wszystkie ważne projekty
- ✅ **Nazwy firm czytelne** — 17px bold, większy padding
- ✅ **Czyste listy** — bez strzałek, lepszy spacing
- ✅ **Spójny design** — wszystkie h3 jednakowej wielkości
- ✅ **Profesjonalny wygląd** — justified text, lepszy line-height

## [3.16.1] - 2025-01-01

### 📖 Improved Readability & Conditional Links

#### Poprawiono czytelność i usunięto link dla Staples Solutions

**Zmiany w czytelności:**
```css
/* Większy font i spacing */
font-size: 15px;           /* było ~14px */
padding: 14px 28px;        /* było 12px 24px */
letter-spacing: 0.08em;    /* było 0.05em */
gap: 25px;                 /* było 20px */

/* Opis */
font-size: 16px;           /* dodano */
line-height: 1.6;          /* dodano */
margin-bottom: 40px;       /* było 30px */
```

**Warunkowe renderowanie:**
```javascript
if (partner.url) {
  // Renderuj jako <a> z hover effects
  return `<a href="${partner.url}" target="_blank">...</a>`;
} else {
  // Renderuj jako <span> bez linku
  return `<span style="border-color: var(--gray); opacity: 0.8;">...</span>`;
}
```

**Staples Solutions:**
```json
{
  "name": "Staples Solutions"
  // brak "url" - nie będzie klikalny
}
```

**Wizualne rozróżnienie:**
| Partner | URL | Styl |
|---------|-----|------|
| Madkom | ✅ | Biała ramka, hover effect |
| Neoteric | ✅ | Biała ramka, hover effect |
| Bright Inventions | ✅ | Biała ramka, hover effect |
| Staples Solutions | ❌ | Szara ramka, opacity 0.8 |

**Efekt:**
- ✅ **Lepsza czytelność** — większy tekst, lepszy spacing
- ✅ **Jasne komunikaty** — wizualnie widać co jest linkiem
- ✅ **Staples bez URL** — wyświetlany ale nieklikany
- ✅ **Profesjonalny wygląd** — większe przyciski, lepszy kontrast

## [3.16.0] - 2025-01-01

### 🤝 Enhanced Industry Partners Section

#### Rozbudowano sekcję współpracy z przemysłem

**Dodano:**
- **4 firmy partnerskie** z linkami do ich stron
- **Opis współpracy** — kontekst o praktykach, stażach i warsztatach
- **Interaktywne przyciski** — każdy partner jako klikalny link

**Nowa struktura danych w `activity.json`:**
```json
"industry_collaboration": {
  "description": "Koło współpracowało z wieloma firmami z branży IT...",
  "partners": [
    {
      "name": "Madkom",
      "url": "https://madkom.pl"
    },
    {
      "name": "Neoteric",
      "url": "https://neoteric.eu"
    },
    {
      "name": "Bright Inventions",
      "url": "https://brightinventions.pl"
    },
    {
      "name": "Staples Solutions",
      "url": "https://staples-solutions.com"
    }
  ]
}
```

**Styling:**
```css
/* Flex layout dla responsywności */
display: flex;
flex-wrap: wrap;
gap: 20px;

/* Przyciski firm */
padding: 12px 24px;
background: var(--surface);
border: 2px solid var(--border);
font-weight: 600;
letter-spacing: 0.05em;

/* Hover effect */
border-color: var(--accent);
transform: translateY(-2px);
box-shadow: 0 4px 12px rgba(255, 107, 0, 0.2);
```

**Partnerzy:**
- ✅ **Madkom** — https://madkom.pl
- ✅ **Neoteric** — https://neoteric.eu
- ✅ **Bright Inventions** — https://brightinventions.pl
- ✅ **Staples Solutions** — https://staples-solutions.com

**UX:**
- 🔗 Linki otwierają się w nowej karcie (`target="_blank"`)
- 🎨 Smooth hover animations
- 📱 Responsive flex layout
- ✨ Accent color highlight na hover

## [3.15.6] - 2025-01-01

### 💫 Hover Shadow Visible — Increased Padding

#### Zwiększono padding dla pełnego efektu cienia

**Problem:**
- Box-shadow na hover (30px radius) był częściowo ucięty
- Offset border na hover (-20px) potrzebował więcej miejsca
- Artystyczny glow effect nie był w pełni widoczny

**Rozwiązanie:**
```css
.carousel-wrapper {
  padding: 50px 0;  /* było 30px */
}

.carousel-wrapper-inner {
  margin: -50px 0;  /* kompensuje padding */
  padding: 50px 0;
}
```

**Kalkulacja przestrzeni:**
- Offset border na hover: `-20px` (top/left)
- Box-shadow radius: `30px`
- **Razem potrzebne:** ~50px przestrzeni

**Mobile:**
```css
@media (max-width: 768px) {
  .carousel-wrapper {
    padding: 30px 0;  /* było 20px */
  }
  
  .carousel-wrapper-inner {
    margin: -30px 0;
    padding: 30px 0;
  }
}
```

**Efekt:**
- ✅ **Pełny cień na hover** — `box-shadow: 0 0 30px rgba(255, 107, 0, 0.3)` w pełni widoczny
- ✅ **Offset borders** — -20px (hover) nie są ucięte
- ✅ **Glow effect** — pomarańczowy blask pełny i wyraźny
- ✅ **3D depth** — maksymalny efekt głębi

## [3.15.5] - 2025-01-01

### 🎨 Full Artistic Effect — Offset Borders Visible

#### Naprawiono ucięte elementy ::before

**Problem:**
- Offset borders (::before) były ucięte przez `overflow: hidden`
- Tracony był artystyczny efekt podwójnej ramki
- 3D effect nie był w pełni widoczny

**Rozwiązanie - Dual Overflow System:**
```html
<div class="carousel-wrapper">          <!-- overflow: visible -->
  <button class="carousel-nav-prev">   <!-- przyciski na zewnątrz -->
  <button class="carousel-nav-next">
  <div class="carousel-wrapper-inner"> <!-- overflow: hidden -->
    <div class="carousel-track">       <!-- sliding -->
      <div class="carousel-group">...
```

**CSS:**
```css
.carousel-wrapper {
  position: relative;
  width: 100%;
  overflow: visible;  /* pozwala na widoczność ::before */
  padding: 30px 0;    /* miejsce na wystające elementy */
}

.carousel-wrapper-inner {
  overflow: hidden;   /* ukrywa sliding poza viewport */
  margin: -30px 0;    /* kompensuje padding */
  padding: 30px 0;
}

.carousel-item {
  overflow: visible;  /* ::before może wystać */
}
```

**Efekt:**
- ✅ **Offset borders w pełni widoczne** — artystyczny efekt 3D zachowany
- ✅ **Smooth sliding** — overflow: hidden na inner div
- ✅ **Przyciski nawigacji** — działają poprawnie (poza inner div)
- ✅ **30px padding** — przestrzeń dla wystających elementów (top: -15px, bottom: 15px)
- ✅ **Mobile responsive** — 20px padding na mobile

#### Struktura overflow
| Element | Overflow | Rola |
|---------|----------|------|
| `.carousel-wrapper` | visible | Pokazuje ::before |
| `.carousel-wrapper-inner` | hidden | Ukrywa sliding |
| `.carousel-item` | visible | ::before może wystać |
| `.carousel-item::before` | - | Offset border (-15px) |

## [3.15.4] - 2025-01-01

### 🟦 Square Images & No Height Limit — Full Design Visible

#### Zwiększono jeszcze bardziej wysokość i usunięto limit

**Zmieniono aspect ratio na kwadrat:**
```css
.carousel-item {
  aspect-ratio: 1/1;  /* było 4/3, wcześniej 16:9 */
}
```
- **Kwadratowe zdjęcia** — maksymalna wysokość
- **Większa powierzchnia** — lepszy showcase fotografii
- **Równe proporcje** — estetyczny wygląd

**Usunięto limit wysokości:**
```css
.carousel-wrapper {
  /* USUNIĘTO: max-height: 650px */
  overflow: hidden;
}
```
- **Brak ograniczeń** — design się nie ucina
- **Pełna wysokość** — zdjęcia wyświetlają się w całości
- **Overflow visible** — offset borders widoczne poza kontenerem

**Zachowane:**
- ✅ **overflow: visible** na `.carousel-item` — offset borders nie są ucięte
- ✅ **Wszystkie efekty stylu** — double borders, stripes, gradients
- ✅ **Responsywność** — działa na desktop i mobile

#### Progresja wysokości
| Wersja | Aspect Ratio | Max Height | Wysokość (dla width 400px) |
|--------|--------------|------------|----------------------------|
| 3.15.0 | 16:9 | 500px | ~225px |
| 3.15.3 | 4:3 | 650px | ~300px |
| 3.15.4 | 1:1 | brak | ~400px |

## [3.15.3] - 2025-01-01

### 📐 Taller Images & Clean Style — Focus on Photos

#### Zwiększono wysokość i usunięto napisy

**Zmieniono aspect ratio:**
```css
.carousel-item {
  aspect-ratio: 4/3;  /* było 16:9 */
}
```
- **Wyższe zdjęcia** — lepszy format dla portretowych kadrów
- **Lekko przycięte boki** — object-fit: cover zapewnia focus na centrum

**Zwiększono max-height:**
```css
.carousel-wrapper {
  max-height: 650px;  /* było 500px */
}
```

**Usunięto wszystkie napisy:**
```css
.carousel-item-label,    /* "MOMENT" */
.carousel-item-number,   /* Numery 01, 02, 03 */
.carousel-item-code {    /* KNSI-E-XPERT-2025-XXX */
  display: none;
}
```

**Zachowane elementy stylu:**
- ✅ **Double border frames** — offset shadow border
- ✅ **Diagonal stripes** — animowane paski na dole
- ✅ **Gradient overlays** — pomarańczowy gradient na hover
- ✅ **Image zoom** — scale(1.05) na hover
- ✅ **Smooth transitions** — wszystkie animacje

#### Efekt
- **Czystsze zdjęcia** — bez rozpraszających tekstów
- **Więcej przestrzeni** — wyższe obrazy (4:3)
- **Focus na treść** — zdjęcia w centrum uwagi
- **Zachowany styl** — wszystkie fancy efekty pozostają

## [3.15.2] - 2025-01-01

### ⬅️➡️ Navigation Controls — Manual Group Switching

#### Dodano przyciski nawigacji
Użytkownik może teraz manualnie przełączać grupy zdjęć:

**Przyciski:**
```html
<button class="carousel-nav carousel-nav-prev" onclick="prevGroup()">‹</button>
<button class="carousel-nav carousel-nav-next" onclick="nextGroup()">›</button>
```

**Styling:**
```css
.carousel-nav {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  width: 50px;
  height: 50px;
  background: var(--black);
  color: var(--white);
  font-size: 20px;
  opacity: 0.8;
  z-index: 20;
}

.carousel-nav:hover {
  background: var(--accent);
  color: var(--black);
  opacity: 1;
  transform: translateY(-50%) scale(1.1);
}
```

**Funkcje JavaScript:**
```javascript
function prevGroup() {
  if (currentGroupIndex === 0) {
    // Jump to last group for seamless backward loop
    currentGroupIndex = totalGroups;
    slideToGroup(currentGroupIndex, true);
    setTimeout(() => {
      currentGroupIndex--;
      slideToGroup(currentGroupIndex);
    }, 50);
  } else {
    currentGroupIndex--;
    slideToGroup(currentGroupIndex);
  }
  // Reset autoplay timer
  clearInterval(carouselInterval);
  startCarouselAutoplay(5000);
}

function nextGroup() {
  currentGroupIndex++;
  slideToGroup(currentGroupIndex);
  
  if (currentGroupIndex === totalGroups) {
    // Jump to first group for seamless forward loop
    setTimeout(() => {
      currentGroupIndex = 0;
      slideToGroup(0, true);
    }, 800);
  }
  // Reset autoplay timer
  clearInterval(carouselInterval);
  startCarouselAutoplay(5000);
}
```

#### Funkcjonalność
- **Przycisk lewo (‹)**: Przechodzi do poprzedniej grupy
- **Przycisk prawo (›)**: Przechodzi do następnej grupy
- **Infinite loop**: Działa w obie strony bez końca
- **Auto-reset timer**: Po manualnej zmianie timer autoplay resetuje się
- **Hover effect**: Przyciski zmieniają kolor na pomarańczowy
- **Scale animation**: Powiększenie o 10% na hover

#### Mobile
```css
@media (max-width: 768px) {
  .carousel-nav {
    width: 40px;
    height: 40px;
    font-size: 16px;
  }
  
  .carousel-nav-prev { left: 5px; }
  .carousel-nav-next { right: 5px; }
}
```

## [3.15.1] - 2025-01-01

### 🔧 Carousel Display Fix

#### Naprawiono wyświetlanie 3 zdjęć obok siebie
- **Usunięto gap z track** — grupy stykają się idealnie
- **Padding w grupach** — 30px padding zapewnia odstępy
- **Uproszczony transform** — `translateX(${offset}%)` bez dodatkowych kalkulacji
- **width: 100%** w grupach zamiast min-width
- **will-change: transform** dla lepszej wydajności

```css
.carousel-track {
  display: flex;
  transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
  will-change: transform;
  /* USUNIĘTO gap: 30px */
}

.carousel-group {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 30px;
  width: 100%;  /* zamiast min-width: 100% */
  flex-shrink: 0;
  padding: 0 30px;  /* DODANO - spacing wewnątrz grupy */
}
```

```javascript
// Uproszczony transform bez gap compensation
const offset = index * -100;
track.style.transform = `translateX(${offset}%)`;
```

## [3.15.0] - 2025-01-01

### 🎠 Infinite Sliding Carousel — Grupa po grupa

#### 🔄 Kompletna zmiana mechanizmu karuzeli
Przejście z pojedynczych zdjęć fade na przesuwającą się karuzelę grup:
- **Grupy po 3 zdjęcia obok siebie** — zmienia się cała grupa (3 zdjęcia równolegle), nie pojedyncze zdjęcia
- **Sliding effect** — przesuwanie zamiast fade over
- **Infinite loop** — nieskończona pętla z bezszwowym powrotem do początku
- **Auto-slide** — automatyczne przesuwanie co 5 sekund
- **16:9 aspect ratio** — zachowany horyzontalny format
- **Max height 500px** — kompaktowa sekcja
- **Left-aligned headers** — nagłówki wyrównane do lewej (jak reszta strony)

#### 🎠 Sliding Carousel Mechanism
```javascript
function slideToGroup(index, instant = false) {
  const offset = index * -100;
  track.style.transform = `translateX(calc(${offset}% - ${index * 30}px))`;
}

function nextGroup() {
  currentGroupIndex++;
  slideToGroup(currentGroupIndex);
  
  // Seamless loop - jump to first after showing duplicate
  if (currentGroupIndex === totalGroups) {
    setTimeout(() => {
      currentGroupIndex = 0;
      slideToGroup(0, true); // instant, no transition
    }, 800);
  }
}
```

#### ♾️ Infinite Loop Implementation
```html
<!-- Groups structure -->
<div class="carousel-track">
  <div class="carousel-group"><!-- Group 1: Images 1,2,3 --></div>
  <div class="carousel-group"><!-- Group 2: Images 4,5,6 --></div>
  <div class="carousel-group"><!-- Group 3: Images 7,8,9 --></div>
  <div class="carousel-group"><!-- Duplicate Group 1 for seamless loop --></div>
</div>
```
- **Duplicate first group** — dodana na końcu
- **Instant jump** — po pokazaniu duplikatu wraca do prawdziwej pierwszej
- **No visual glitch** — użytkownik nie widzi przeskoku

#### 🏷️ Premium Design Elements (przywrócone)
**"MOMENT" Labels**:
```css
.carousel-item-label {
  top: -30px;
  left: -5px;
  background: var(--black);
  padding: 6px 16px;
}
.carousel-item-label::before { content: '"'; }
.carousel-item-label::after { content: '"'; }
```

**Numbered Tags**:
```css
.carousel-item-number {
  width: 50px;
  height: 50px;
  background: var(--accent);
  bottom: -5px;
  right: -5px;
}
```

**Code Labels**:
```html
<div class="carousel-item-code">KNSI-E-XPERT-2025-001</div>
```

**Diagonal Stripes**:
```css
.carousel-item-stripe {
  background: repeating-linear-gradient(45deg, ...);
  animation: stripeMove 20s linear infinite;
}
```

**Double Border Frame**:
```css
.carousel-item::before {
  /* Offset border */
  top: -15px; left: -15px; right: 15px; bottom: 15px;
}
.carousel-item-inner {
  /* Main border */
  border: 4px solid var(--black);
}
```

#### 📐 Layout & Formatting
```css
.carousel-section h2 {
  text-align: left; /* wyrównanie do lewej */
}

.carousel-wrapper {
  max-height: 500px; /* ograniczenie wysokości sekcji */
}

.carousel-group {
  display: grid;
  grid-template-columns: repeat(3, 1fr); /* 3 zdjęcia obok siebie */
  gap: 30px;
  min-width: 100%; /* grupa zajmuje całą szerokość */
}

.carousel-item {
  aspect-ratio: 16/9;
  overflow: visible; /* dla offset border */
}
```
- **3 kolumny w grupie**: Każda grupa pokazuje 3 zdjęcia równolegle
- **Max height 500px**: Kompaktowa sekcja
- **Left-aligned headers**: Spójność z resztą strony
- **Horyzontalny format 16:9**: Nie ucina boków zdjęć
- **Responsive**: Automatyczne dostosowanie wysokości

#### 💫 Smooth Transitions
```css
.carousel-track {
  transition: transform 0.8s cubic-bezier(0.4, 0, 0.2, 1);
}
```
- **0.8s duration** — wystarczająco długie dla płynności
- **cubic-bezier** — premium easing
- **Gap compensation** — `calc(${offset}% - ${index * 30}px)`

#### 🎯 Auto-play & Controls
- **5 seconds interval** — dłuższy dla komfortu oglądania
- **Pause on hover** — użytkownik może zatrzymać
- **Automatic restart** — po opuszczeniu myszką
- **Infinite loop** — nigdy się nie kończy

#### 📱 Mobile Experience
```css
@media (max-width: 768px) {
  .carousel-group {
    grid-template-columns: 1fr;
    gap: 50px;
  }
}
```
- **Vertical scroll** — każde zdjęcie osobno
- **50px gap** — większe odstępy
- **Zachowane efekty** — wszystkie etykiety i animacje
- **Ukryte cudzysłowy** — przy tytule sekcji

#### 📏 Porównanie mechanizmów
| Element | 3.13.0 | 3.13.1 | 3.14.0 | 3.15.0 |
|---------|--------|--------|--------|--------|
| Mechanizm | Full carousel | Random fade | Static grid | Sliding groups |
| Zmiana | Slide | Single fade | No change | Group slide |
| Loop | Manual | Random | - | Infinite auto |
| Transition | Slide | Fade 1.5s | - | Slide 0.8s |
| Display | 1 image | 4 images | 3 images | 3 images |
| Format | Full width | Square | 16:9 | 16:9 |
| Etykiety | Dots, counter | None | None | Labels, numbers, codes |
| Auto-play | Yes | Yes | No | Yes (groups) |

#### 🎨 Design Philosophy
**Industrial/Premium Style:**
- ✅ Offset border frames
- ✅ Quotation marks
- ✅ Bold typography labels
- ✅ Numbered elements
- ✅ Diagonal animated stripes
- ✅ Code identifiers
- ✅ Gradient overlays
- ✅ Smooth transitions

**UX Improvements:**
- ✅ Group sliding (easier to follow)
- ✅ Infinite loop (never ends)
- ✅ Longer interval (5s vs 4s)
- ✅ Pause on hover
- ✅ 16:9 format (no cropping)

## [3.14.0] - 2025-01-01

### 🎨 Premium Gallery "To My" — Clean & Minimalist

#### 🔄 Redesign na minimalistyczną galerię
Sekcja "To My" przekształcona na czystą, elegancką galerię bez rozpraszających elementów:
- **3 kolumny** zamiast 4 (desktop) — więcej przestrzeni dla każdego zdjęcia
- **1 kolumna** na mobile — pełna uwaga na każdym zdjęciu
- **16:9 aspect ratio** — horyzontalny format, pełne zdjęcia bez ucięć boków
- **30px gap** — optymalny spacing między obrazami
- **9 zdjęć** w puli (dodano 1 nowe)

#### 📐 Aspect Ratio — Horizontal Format
```css
.carousel-item {
  aspect-ratio: 16/9;  /* Horyzontalny format */
  overflow: hidden;
}

.carousel-item img {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: center;
}
```
- **16:9 format**: Zachowuje pełną szerokość zdjęć
- **No cropping**: Nie ucina boków obrazów
- **Responsive**: Automatyczne dostosowanie wysokości
- **object-fit: cover**: Wypełnia kontener bez zniekształceń

#### 🖼️ Clean Design — Bez zasłaniających elementów
```html
<div class="carousel-item">
  <div class="carousel-item-inner">
    <img src="..." alt="..." />
  </div>
</div>
```
- **Usunięte**: Etykiety, numery, kody
- **Czysty widok**: Tylko zdjęcie
- **No overlays**: Brak tekstów zasłaniających obraz
- **Focus on content**: Pełna uwaga na fotografiach

#### 🎨 Minimalist Border System
```css
.carousel-item {
  border: 3px solid var(--black);
  box-shadow: 0 10px 40px rgba(28, 27, 34, 0.15);
}

.carousel-item:hover {
  border-color: var(--accent);
  transform: translateY(-8px);
  box-shadow: 0 20px 60px rgba(28, 27, 34, 0.25);
}
```
- **Single border**: Prosta 3px ramka
- **Hover effect**: Zmiana koloru na pomarańczowy
- **Lift animation**: translateY(-8px) na hover
- **Shadow enhancement**: Pogłębienie cienia przy hover

#### 🔍 Image Effects
```css
.carousel-item img {
  filter: grayscale(0.15) contrast(1.05);
  transform: scale(1);
  transition: opacity 1.5s ease-in-out, 
              transform 0.6s cubic-bezier(0.4, 0, 0.2, 1), 
              filter 0.4s ease;
}

.carousel-item:hover img {
  transform: scale(1.08);
  filter: grayscale(0) contrast(1.1);
}
```
- **Lekki grayscale**: 15% dla spójności
- **Zoom on hover**: scale(1.08) — delikatne powiększenie
- **Smooth animations**: cubic-bezier dla premium feel
- **Fade transition**: 1.5s dla spokojnej zmiany

#### 📱 Mobile Experience
```css
@media (max-width: 768px) {
  .carousel-container {
    grid-template-columns: 1fr;  /* 1 kolumna */
    gap: 40px;
  }
  
  .carousel-item {
    aspect-ratio: 16/9;  /* Zachowane 16:9 */
    border-width: 2px;
  }
}
```
- **Pełna szerokość**: każde zdjęcie zajmuje cały ekran
- **40px gap**: przestrzeń między zdjęciami
- **Zachowany aspect ratio**: 16:9 również na mobile
- **Thinner border**: 2px zamiast 3px

#### 🎯 Random Rotation (zachowane)
- **Smart algorithm**: Unika duplikatów
- **Smooth fade**: 1.5s opacity transition
- **Random slots**: Losowy wybór pozycji
- **Random images**: Losowy obraz z puli 9
- **Auto-play**: Co 4 sekundy
- **Pause on hover**: Zatrzymanie przy najechaniu

#### 📏 Porównanie z poprzednimi wersjami
| Element | 3.13.0 | 3.13.1 | 3.14.0 |
|---------|--------|--------|--------|
| Kolumny (desktop) | 1 (carousel) | 4 | 3 |
| Kolumny (mobile) | 1 | 2 | 1 |
| Format | Full width | Square | 16:9 horizontal |
| Wysokość | 675px | 250px | auto (16:9) |
| Gap | - | 2px | 30px |
| Liczba zdjęć | 8 | 8 | 9 |
| Style | Carousel | Compact grid | Clean gallery |
| Etykiety | Counter, dots | - | None |
| Animacje | Slide | Fade | Fade + lift |
| Border | Single | None | Single with hover |

#### 🎨 Design Philosophy
**Minimalist Principles:**
- ✅ Clean design bez rozpraszaczy
- ✅ Focus na treści (zdjęcia)
- ✅ Prosty border system
- ✅ Subtle hover effects
- ✅ Optimal spacing
- ✅ Horizontal format (16:9)
- ✅ No text overlays
- ✅ Smooth animations

## [3.13.1] - 2025-01-01

### 🎨 Grid "To My" — 4 zdjęcia w rzędzie z losową rotacją

#### 🔄 Zmiana layoutu
Karuzela przekształcona z pojedynczego dużego obrazu na grid 4 obrazów obok siebie:
- **Desktop**: 4 obrazy w jednym rzędzie (250px wysokości każdy)
- **Mobile**: 2 obrazy w rzędzie (150px wysokości każdy)
- **Compact**: Znacznie niższa sekcja (poprzednio aspect-ratio 16:9)

#### 🔀 Losowa rotacja obrazów
- **Random slots**: Co 4 sekundy losowo wybierany jest jeden z 4 slotów
- **Random images**: Wybrany slot otrzymuje nowe losowe zdjęcie z puli 8
- **Smart selection**: Algorytm unika wyświetlania obecnie pokazywanych obrazów
- **Smooth fade**: Płynne przejście opacity (1.2s) podczas zmiany

#### 🎨 Nowy design
```css
.carousel-container {
  display: grid;
  grid-template-columns: repeat(4, 1fr);  /* 4 kolumny */
  gap: 2px;  /* minimalne odstępy */
  background: var(--black);  /* separator */
}

.carousel-item {
  height: 250px;  /* fixed height */
  background: var(--light-gray);
}

.carousel-item img {
  object-fit: cover;
  filter: grayscale(0.2);
  opacity: 0;
  transition: opacity 1.2s ease-in-out;
}

.carousel-item img.active {
  opacity: 1;
}
```

#### 🔧 Nowy JavaScript
```javascript
- getRandomImage() — wybiera losowy obraz z puli (unika duplikatów)
- changeRandomImage() — zmienia losowy slot na nowy obraz
- initCarousel(interval) — inicjalizacja z auto-play
- Pause/Resume on hover (zachowane)
```

#### 📱 Mobile responsywność
```css
@media (max-width: 768px) {
  .carousel-container {
    grid-template-columns: repeat(2, 1fr);  /* 2 kolumny */
  }
  .carousel-item {
    height: 150px;
  }
}
```

#### ❌ Usunięte elementy
- Wskaźniki (dots) — nie są już potrzebne
- Licznik (counter) — nie ma sensu przy losowej zmianie
- Slajdy — zastąpione fixed grid

#### ✅ Zachowane funkcje
- **Pause on hover** — zatrzymanie podczas najechania
- **Auto-play** — automatyczna zmiana co 4 sekundy
- **Fade effect** — płynne przejścia
- **Error handling** — ukrywanie niepoprawnych obrazów
- **Grayscale filter** — spójność z resztą strony
- **Hover enhancement** — usunięcie grayscale przy hover

#### 📏 Porównanie wymiarów
| Element | Poprzednio (3.13.0) | Teraz (3.13.1) |
|---------|---------------------|----------------|
| Desktop width | 1200px max | 1200px max |
| Desktop height | ~675px (16:9) | 250px (fixed) |
| Mobile height | ~900px (4:3) | 300px (2×150px) |
| Liczba widocznych | 1 obraz | 4 obrazy (desktop), 2 (mobile) |
| Zmiana | sekwencyjna | losowa |

## [3.13.0] - 2025-01-01

### 🎠 Karuzela "To My" — Photo Carousel on Homepage

#### ✨ Nowa sekcja w home.json
Dodana sekcja `us` z 8 wybranymi zdjęciami z galerii:
```json
"us": {
  "title": "To My",
  "subtitle": "Zdjęcia z naszej działalności",
  "images": [8 URLs],
  "interval": 4000
}
```

#### 🎬 Automatyczna karuzela z fade effect
- **Fade transitions** — płynne przejścia opacity (1.5s ease-in-out)
- **Auto-play** — automatyczna zmiana co 4 sekundy
- **Pause on hover** — zatrzymanie podczas najechania myszką
- **Infinite loop** — cykliczne przechodzenie przez wszystkie zdjęcia

#### 🖱️ Interaktywne elementy
- **Wskaźniki (dots)** — 8 kropek na dole do manualnej nawigacji
- **Licznik** — "1 / 8" w prawym górnym rogu
- **Active states** — pomarańczowa kropka dla aktywnego slajdu
- **Hover effects** — animacje scale na kropkach

#### 🎨 Design
- **Kontener**: 3px czarna ramka, cień, aspect-ratio 16:9
- **Background**: szare tło podczas ładowania
- **Wskaźniki**: białe z pomarańczowym akcentem dla aktywnego
- **Licznik**: ciemne tło z blur backdrop
- **Grayscale filter**: lekki (0.15) dla spójności z galerią

#### 📱 Responsywność
- **Desktop**: max-width 1200px, aspect-ratio 16:9, 3px border
- **Mobile**: aspect-ratio 4:3, 2px border, mniejsze wskaźniki

#### 🔧 JavaScript funkcje
```javascript
- initCarousel(interval) — inicjalizacja z auto-play
- goToSlide(index) — przejście do konkretnego slajdu
- nextSlide() — następny slajd (cyklicznie)
- startCarouselAutoplay(interval) — start auto-play
- Pause/Resume on hover events
```

#### 📍 Pozycja na stronie
Karuzela "To My" umieszczona między sekcjami:
1. Stats (statystyki)
2. About (O nas)
3. **Us (To My)** ← NOWA KARUZELA
4. Highlights (Nasze osiągnięcia)

#### 📸 Wybrane zdjęcia
8 zdjęć z galerii (IDs: 1, 4, 7, 10, 13, 16, 19, 22):
- Różnorodne momenty z działalności koła
- Wydarzenia, spotkania, warsztaty
- Reprezentatywne dla społeczności E-XPERT

## [3.12.1] - 2025-01-01

### 👨‍🏫 Opiekunowie Koła — Rozszerzenie Historii

#### 📚 Dodane informacje o opiekunach
- **Prof. Michał Kuciapski** — opiekun koła w latach wcześniejszych
- **mgr Piotr Porzuczek** — przejął opiekę nad kołem w 2020 roku

#### 📝 Zmiany w plikach
- `data/activity.json` — dodane pole `advisors` w sekcji `history`
- `index.html` — renderowanie informacji o opiekunach jako 4. punkt w historii

#### 🎨 Wizualizacja
- **Label:** "Opiekunowie koła:"
- **Treść:** Chronologiczny opis zmian opiekuna
- **Styl:** Spójna z pozostałymi punktami historii (bold label, gray text)

## [3.12.0] - 2025-01-01

### 📜 Historia Koła — Poprawki i Rozszerzenie

#### 📅 Poprawione daty
- **2007 → 2001** — koło powstało w styczniu 2001 roku
- **Reaktywacja** — 2012 rok (studenci Informatyki i Ekonometrii)
- **24+ lat działalności** — zaktualizowane w statystykach (2001-2025)
- **Copyright** — © 2001–2025 KNSI E-XPERT (wcześniej 2007–2025)

#### 📖 Historia koła w `activity.json`
Dodana nowa sekcja `history` z trzema kluczowymi informacjami:

**Katedra:**
- Koło działa przy Katedrze Informatyki Ekonomicznej Wydziału Zarządzania Uniwersytetu Gdańskiego

**Powstanie (2001):**
- Styczeń 2001 roku — grupa studentów chcących rozwinąć wiedzę z informatyki w biznesie
- Po kilku latach intensywnej działalności koło przestało funkcjonować

**Reaktywacja (2012):**
- Studenci Informatyki i Ekonometrii z kilku roczników reaktywowali koło
- Tworzą zgrane grupy mimo różnic w wiedzy i doświadczeniu
- Pracują nad kilkoma projektami jednocześnie

#### 🎨 Wizualizacja historii
- **Box design** — szare tło, pomarańczowy border-left (4px)
- **Typography** — nagłówek "HISTORIA KOŁA" (22px)
- **Struktura** — 3 paragrafy z bold labels: Katedra, Powstanie, Reaktywacja
- **Spacing** — 50px margin-bottom, 30px padding

#### 📊 Zmienione pliki
- `data/footer.json` — copyright 2001–2025
- `data/home.json` — "24+ Lat działalności" + "Od 2001"
- `data/activity.json` — dodana sekcja `history`
- `docs/CHANGELOG.md` — aktualizacje dat w dokumentacji
- `index.html` — renderowanie nowej sekcji historii

#### 💡 Rezultat
- ✅ **Dokładna historia** — kompletna timeline od 2001
- ✅ **Kontekst** — informacja o Katedrze i Wydziale
- ✅ **Przejrzystość** — jasny podział na powstanie i reaktywację
- ✅ **Wizualny akcent** — wyróżniony box na początku sekcji

## [3.11.1] - 2025-01-01

### 🔧 Footer Navigation Update

#### Dodane
- **Galeria w stopce** — link do galerii dodany do sekcji nawigacji w stopce
- **Poprawna kolejność** — Galeria przed Statutem (5. pozycja)

#### Kolejność nawigacji
1. Start
2. Projekty
3. Cele i misja
4. Zespół
5. **Galeria** 📷 (nowy)
6. Statut
7. Działalność

## [3.11.0] - 2025-01-01

### 📷 Gallery System — Professional Photo Gallery

#### ✨ New Gallery Section
- **`data/gallery.json`** — 26 zdjęć z działalności koła
- **Grid layout** — 4 kolumny (desktop), 2 (tablet), 1 (mobile)
- **Industrial styling** — bordered grid z numbered tags
- **Hover effects** — zoom, grayscale removal, overlay, icon

#### 🖼️ Enhanced Lightbox
- **Navigation buttons** — okrągłe przyciski ‹ › po bokach
- **Counter display** — "5 / 26" na dole lightboxa
- **Keyboard navigation** — Arrow Left/Right dla nawigacji
- **Smooth transitions** — fade in/out, disable buttons at ends
- **Conditional UI** — przyciski widoczne tylko w galerii

#### 🎨 Visual Design
- **Gallery Grid**:
  - 4 kolumny z 20px gap (desktop)
  - 2 kolumny z 18px gap (tablet)
  - 1 kolumna z 16px gap (mobile)
  - aspect-ratio 4:3 dla wszystkich obrazów
- **Hover Effects**:
  - Offset border animation (-8px)
  - Image scale (1.08)
  - Grayscale filter (0.2 → 0)
  - Gradient overlay z bottom
  - Zoom icon (🔍) fade in
- **Numbered Tags**:
  - 32x32px czarne kwadraty z białym borderem
  - Orange background on hover
  - Transform scale(1.1) on hover

#### 🚀 Technical Implementation
```javascript
- renderGallery() — renders grid from JSON
- openGalleryLightbox(index) — opens at specific image
- showGalleryImage() — displays image with nav/counter
- navigateGallery(direction) — moves +1 or -1
- Keyboard: ArrowLeft, ArrowRight, Escape
```

#### 📱 Responsive Behavior
- **Desktop**: 4-column grid, 60px nav buttons, 40px spacing
- **Tablet**: 2-column grid
- **Mobile**: 1-column grid, 50px nav buttons, 15px spacing
- **Lightbox**: adaptive padding, smaller counters on mobile

#### 🔗 Navigation
- Added to `navigation.json` as section 5
- Icon: 📷
- Order: Home → Projects → Goals → Team → **Gallery** → Constitution → Activity

## [3.10.1] - 2025-01-01

### 🧹 Content Cleanup

#### Usunięte wzmianki
- Usunięto wszystkie referencje do zewnętrznych inspiracji designerskich
- Zaktualizowano opisy w README.md, CHANGELOG.md, DESIGN_NOTES.md
- Poprawiono opisy projektów w projects.json i goals.json
- Zmieniono komentarze w index.html

#### Rezultat
- Fokus na własnym, oryginalnym designie
- Industrial aesthetic jako rdzeń stylistyczny
- Profesjonalne, uniwersalne nazewnictwo

## [3.10.0] - 2025-01-01

### ⚙️ Navigation Configuration System — Centralized Menu Management

#### 📋 New Configuration File
- **`data/navigation.json`** — dedicated navigation configuration file
- **Site metadata** — name, short_name, tagline, logo_svg
- **Sections array** — complete menu structure with extended metadata

#### 🎯 Section Properties
Each section now includes:
- `id` — unique identifier (used in URL hash)
- `title` — display name in menu
- `slug` — URL-friendly name
- `href` — JSON data file for the section
- `icon` — emoji or symbol for visual identity
- `description` — tooltip text and SEO description
- `keywords` — search keywords array
- `order` — sort order (1, 2, 3...)
- `visible` — boolean to show/hide in menu

#### 🔄 JavaScript Updates
- `initNavigation()` now loads `navigation.json` instead of `home.json`
- Menu dynamically generated from `sections` array
- Tooltips automatically added to nav links from `description` field
- Page title uses `tagline` from navigation config

#### ✅ Benefits
- Easier menu management without touching HTML
- Add/remove/reorder sections via simple JSON edits
- SEO-friendly with descriptions and keywords
- Centralized site structure configuration
- Better maintainability and scalability

## [3.8.0] - 2025-11-01

### 🖼️ Image Gallery — Project Screenshots Display

#### ✨ Responsive Image Gallery
- **Adaptive grid layout** — 1, 2, or 3+ images automatically arranged
- **Single image** — Full-width display
- **Two images** — Side-by-side grid
- **Three+ images** — Three-column grid (desktop), single column (mobile)
- **Lazy loading** — Images load only when needed for performance

#### 💫 Interactive Effects
- **Hover animations** — Lift effect (translateY -4px) + scale(1.05)
- **Orange accent border** — Appears on hover with smooth transition
- **Magnifying glass icon** — 🔍 appears in center on hover
- **Smooth transitions** — cubic-bezier(0.4, 0, 0.2, 1)

#### 🔍 Lightbox Viewer
- **Full-screen image view** — Click any image to view full-size
- **Dark overlay** — rgba(28, 27, 34, 0.95) background
- **Click to close** — Close by clicking anywhere or × button
- **Body scroll lock** — Prevents page scrolling when lightbox open
- **Fade-in animation** — Smooth entrance effect

#### 📐 Technical Implementation
```css
.project-images {
    display: grid;
    gap: 15px;
    aspect-ratio: 16/10;
}
.project-image-wrapper:hover {
    transform: translateY(-4px);
    box-shadow: 0 12px 32px rgba(28, 27, 34, 0.15);
    border-color: var(--accent);
}
```

#### 📱 Mobile Optimized
- **Single column** — All images stack vertically
- **Optimized spacing** — 10px gap (desktop: 15px)
- **Touch-friendly** — Larger tap targets
- **Smaller lightbox controls** — 36px close button (desktop: 48px)
- **Reduced padding** — 20px lightbox padding (desktop: 40px)

#### 🎯 Smart Handling
- **Graceful degradation** — No images? No problem (nothing displays)
- **Automatic layout** — Grid adjusts based on image count
- **Performance** — Images lazy-load, lightbox renders only when needed

#### 📊 Projects with Images
7 projects now display screenshots:
- ✅ Modernizacja Strony (1 image)
- ✅ Modernizacja konta Github (1 image)
- ✅ UniGo (2 images)
- ✅ SocialMonitor (1 image)
- ✅ CyberWatch (1 image)
- ✅ SafeWatch (3 images)
- ✅ mobileWZR (1 image)

#### 🚀 Rezultat
- ✅ **Beautiful galleries** — Professional image presentation
- ✅ **Responsive** — Perfect on all devices
- ✅ **Interactive** — Hover effects + lightbox
- ✅ **Fast** — Lazy loading + optimized
- ✅ **Accessible** — Works without images

## [3.7.1] - 2024-10-31

### 🎨 Navigation Logo — Professional Gradient Text

#### ✨ Animated Gradient Logo
- **Multi-color gradient** na tekście nawigacji "KNSI E-XPERT"
- **Smooth animation** — 10s loop z gradientShift
- **Hover effects** — elevated drop-shadow & translateY
- **Ultra-bold typography** — font-weight: 800, enhanced spacing

```css
.logo-text {
    background: linear-gradient(135deg, 
        #1c1b22 0%, #1c1b22 35%, 
        #ff6b00 55%, #ff8c00 75%, #ffa500 100%);
    -webkit-background-clip: text;
    -webkit-text-fill-color: transparent;
    animation: navGradientShift 10s ease-in-out infinite;
}
```

## [3.7.0] - 2024-10-31

### 🎨 Hero Title — Gradient Text & Premium Typography

#### ✨ Profesjonalny Gradient
- **Multi-color gradient** — czarny (40%) → pomarańczowy (60%) → złoty (100%)
- **Background-clip: text** — gradient wypełnia tekst
- **Animated gradient** — `gradientShift` animation, 8s loop
- **Background-size: 200%** — gradient przesuwa się w czasie

```css
background: linear-gradient(135deg, 
    #1c1b22 0%, #1c1b22 40%, 
    #ff6b00 60%, #ff8c00 80%, #ffa500 100%);
-webkit-background-clip: text;
-webkit-text-fill-color: transparent;
```

#### 🎯 Enhanced Typography
- **Font-weight: 900** — ultra bold (było 700)
- **Text-transform: uppercase** — ALL CAPS dla impact
- **Letter-spacing: -0.03em** — tight kerning (było -0.02em)
- **Line-height: 1.05** — kompaktowy (było 1.1)
- **Font-family** — dodany 'Arial Black' jako fallback

#### 💫 Drop-shadow Effects
- **Dual drop-shadow** — pomarańczowy glow + czarny cień
- **Filter instead of text-shadow** — działa z gradient text
```css
filter: drop-shadow(0 4px 12px rgba(255, 107, 0, 0.3))
        drop-shadow(0 2px 4px rgba(28, 27, 34, 0.2));
```

#### 🌟 Animated Underline
- **Szerszy** — 140px (było 120px), 6px height (było 5px)
- **Orange gradient** — #ff6b00 → #ff8c00 → #ffa500
- **Pulse animation** — subtleny efekt pulsowania (opacity + scaleX)
- **Stronger glow** — dual box-shadow z większą intensywnością
```css
animation: slideIn 0.8s ease-out, pulse 2s ease-in-out infinite;
```

#### 📱 Mobile Optimized
- **Font-weight: 900** — również na mobile
- **Underline 80px** — proporcjonalnie mniejszy (było 50px)
- **Height 4px** — proporcjonalnie (było 2px)
- **Gradient zachowany** — działa identycznie na mobile

#### 🎬 Animacje
**gradientShift** — 8s loop:
```css
0%, 100% { background-position: 0% center; }
50% { background-position: 100% center; }
```

**pulse** — 2s loop:
```css
0%, 100% { opacity: 1; transform: scaleX(1); }
50% { opacity: 0.8; transform: scaleX(0.95); }
```

#### 🚀 Rezultat
- ✅ **Mega profesjonalny** — gradient + ultra bold + uppercase
- ✅ **Dynamiczny** — animowany gradient + pulsujące podkreślenie
- ✅ **Premium look** — czarno-pomarańczowo-złoty gradient
- ✅ **Mocny impact** — weight 900 + tight spacing
- ✅ **Perfect mobile** — wszystkie efekty zachowane
- ✅ **Minimalistyczny design** — z mocnym akcentem kolorystycznym

## [3.6.0] - 2024-10-31

### 📦 Dynamic Footer — JSON-Based Configuration

#### ✨ Nowy plik: `data/footer.json`
Wszystkie dane stopki przeniesione do JSON dla łatwej edycji i utrzymania.

#### 📐 Struktura JSON
```json
{
  "brand": {
    "name": "...",
    "description": "...",
    "year": "2025",
    "established": "EST. 2001"
  },
  "navigation": {
    "title": "Nawigacja",
    "links": [...]
  },
  "contact": {
    "title": "Kontakt",
    "links": [...]
  },
  "social": {
    "title": "Social Media",
    "platforms": [...]
  },
  "bottom": {
    "copyright": "...",
    "credits": [...]
  }
}
```

#### 🔧 Implementacja
- **Funkcja `renderFooter()`** — ładuje `footer.json` i renderuje HTML
- **Dynamiczny HTML** — stopka budowana z template strings
- **attr(data-est)** — CSS ::before używa atrybutu dla EST. label
- **Wywołanie w `init()`** — renderFooter() dodane do inicjalizacji

#### 📝 Zawartość JSON
**Navigation:**
- 6 linków: Start, Projekty, Cele i misja, Zespół, Działalność, Statut

**Contact:**
- Email: knsi.expert@ug.edu.pl
- Uniwersytet Gdański
- Wydział WZR
- Wydział MFI

**Social Media:**
- GitHub (GH), Facebook (FB), LinkedIn (IN), Instagram (IG)

**Bottom:**
- Copyright: "© 2001–2025 KNSI E-XPERT • UNIWERSYTET GDAŃSKI • WYDZIAŁ ZARZĄDZANIA"
- Credits: OPEN SOURCE, GITHUB PAGES

#### 🚀 Korzyści
- ✅ **Łatwa edycja** — wszystkie dane w jednym pliku JSON
- ✅ **Separacja danych** — HTML/CSS/JS oddzielone od treści
- ✅ **Konsystencja** — format zgodny z resztą projektu
- ✅ **Dynamiczne renderowanie** — jak pozostałe sekcje
- ✅ **Utrzymywalność** — zmiana roku/linków bez dotykania HTML

#### 📦 Pliki zmienione
- `data/footer.json` — **NOWY** plik z danymi stopki
- `index.html` — funkcja `renderFooter()`, usunięte hardcoded dane
- CSS: `footer::before` używa `attr(data-est)`

## [3.5.1] - 2024-10-31

### 📚 Footer Update — Wydział WZR

#### ✨ Dodany link do Wydziału WZR
- **Wydział WZR** — dodany przed Wydziałem MFI w sekcji Kontakt
- **Link** — https://wzr.ug.edu.pl
- **Kolejność** — Uniwersytet Gdański → Wydział WZR → Wydział MFI

## [3.5.0] - 2024-10-31

### 🎯 Professional Footer — 2025 Edition

#### ✨ Professional Footer Design
- **Black background** — `background: var(--black)`, `color: var(--white)`
- **EST. 2015 label** — `position: absolute`, `font-size: 10px`, `letter-spacing: 0.2em`, `opacity: 0.4`
- **4-column grid** — `grid-template-columns: 2fr 1fr 1fr 1fr` (desktop), 1fr (mobile)
- **80px gaps** — spacing między kolumnami (desktop), 40px (mobile)

#### 🎨 Footer Components
**Brand Section:**
- **Large title** — `font-size: 28px`, `font-weight: 700`, `letter-spacing: 0.05em`
- **Description** — `font-size: 14px`, `opacity: 0.8`, max-width 400px
- **2025 Year badge** — `padding: 15px 30px`, `border: 2px solid`, `font-size: 32px`
- **Hover effect** — inverse colors + translateY(-2px)

**Navigation Links:**
- **All sections** — Start, Projekty, Cele, Zespół, Działalność, Statut
- **Hover animation** — `transform: translateX(5px)`, `opacity: 1`

**Contact Info:**
- Email: knsi.expert@ug.edu.pl
- Uniwersytet Gdański links
- Wydział MFI link

**Social Media:**
- **4 platforms** — GitHub (GH), Facebook (FB), LinkedIn (IN), Instagram (IG)
- **40x40px boxes** — `border: 2px solid`, centered text
- **Hover effect** — inverse colors + lift

#### 📱 Mobile Responsive
- **Single column** — `grid-template-columns: 1fr`
- **Reduced padding** — 60px 0 30px (było 100px/40px)
- **Smaller year badge** — 24px font (było 32px)
- **Vertical footer-bottom** — flex-direction: column
- **Centered text** — text-align: center
- **Smaller gaps** — 40px grid gap, 12px social gap

#### 🎯 Footer Bottom
- **Border-top** — `2px solid rgba(255, 255, 255, 0.2)`
- **Copyright** — © 2001–2025 KNSI E-XPERT • UNIWERSYTET GDAŃSKI
- **Credits** — OPEN SOURCE + GITHUB PAGES links
- **Opacity** — 0.6 dla subtelności

#### 📐 Technical Details
```css
footer {
    background: var(--black);
    color: var(--white);
    padding: 100px 0 40px;
    margin-top: 150px;
}
.footer-year {
    border: 2px solid var(--white);
    font-size: 32px;
    transition: all 0.3s ease;
}
.footer-year:hover {
    background: var(--white);
    color: var(--black);
}
```

#### 🚀 Rezultat
- ✅ **Profesjonalna stopka** — elegancka, minimalistyczna
- ✅ **2025 prominent** — duży, wyróżniony rok w ramce
- ✅ **Full navigation** — wszystkie sekcje w stopce
- ✅ **Social media** — 4 platformy z hover effects
- ✅ **Industrial style** — borders, gaps, typography, inverse hover
- ✅ **Mobile perfect** — single column, kompaktowe

## [3.4.2] - 2024-10-31

### 🍔 Hamburger Menu Fix + Navigation Scroll

#### 🔧 Problem
- **Hamburger menu nie działało** — błędne nazwy klas (menu-toggle vs mobile-menu)
- **Treść przykryta przez nav** — przy przełączaniu sekcji brak scroll to top
- **Menu nie zamykało się** — po kliknięciu w link menu pozostawało otwarte

#### ✅ Rozwiązanie
- **Poprawione nazwy klas** — `.mobile-menu` konsekwentnie w całym CSS
- **Naprawiona funkcja `toggleMenu()`** — teraz dodaje klasę `menu-open` do `<nav>`
- **Scroll to top** — przy każdej zmianie sekcji: `window.scrollTo({ top: 0, behavior: 'smooth' })`
- **Auto-close menu** — mobile menu zamyka się po kliknięciu w link

#### 🎨 Animacja hamburgera
- **Transform to X** — hamburger zmienia się w X gdy menu otwarte
- **Smooth transition** — `transition: all 0.3s ease` na wszystkich elementach
- **Desktop animation** — również działa na większych ekranach
```css
nav.menu-open .hamburger {
    background: transparent;
}
nav.menu-open .hamburger::before {
    transform: rotate(45deg);
    top: 0;
}
nav.menu-open .hamburger::after {
    transform: rotate(-45deg);
    top: 0;
}
```

#### 📱 Mobile Navigation
- **Max-height animation** — płynne rozwijanie menu (0 → 500px)
- **Z-index: 999** — nav-links zawsze na wierzchu
- **Border-bottom** — 1px solid gdy menu otwarte
- **Flex-direction: column** — vertical stack linków

#### 🎯 Rezultat
- ✅ **Hamburger działa** — kliknięcie otwiera/zamyka menu
- ✅ **Animacja X** — hamburger przekształca się w X
- ✅ **Treść nie przykryta** — scroll to top przy zmianie sekcji
- ✅ **UX perfect** — menu zamyka się po kliknięciu w link

## [3.4.1] - 2024-10-31

### 🔧 Mobile Fix — Unified Media Query

#### 🐛 Problem
- **6 rozproszonych media queries** — konflikty i nadpisywanie stylów
- **Niekonsystentne wartości** — różne fonty/padding w różnych miejscach
- **Overflow issues** — tekst wychodził poza ekran

#### ✅ Rozwiązanie
- **Jeden kompleksowy media query** — wszystko w jednym miejscu (945-1411 linia)
- **Spójne wartości** — zgrane czcionki i spacing w całym mobile
- **Max-width 100%** — container nie wychodzi poza ekran
- **Overflow-x: hidden** — body nie scrolluje poziomo

#### 📐 Unified Mobile Specs
- **Body font** — 14px base
- **Container padding** — 16px konsekwentnie
- **Section padding** — 80px 0 50px
- **Nav padding** — 14px 16px
- **Logo** — 32px height, 12px font
- **Hero h1** — clamp(24px, 9vw, 42px)
- **H2** — clamp(26px, 7vw, 40px)
- **Body text** — 13-14px
- **Labels** — 9-11px
- **Borders** — 2px (było 3px)
- **Card padding** — 28-35px (było 40-50px)

#### 🎯 Co zostało naprawione
- ✅ **Zero overflow** — wszystko się mieści
- ✅ **Spójne czcionki** — jedna hierarchia typograficzna
- ✅ **Menu działa** — max-height animation
- ✅ **Glassmorphism hero** — border-radius 2px
- ✅ **Wszystkie sekcje** — nav, hero, stats, about, highlights, projects, timeline, team, constitution, activity, quotes
- ✅ **2x2 stats grid** — poprawne borders
- ✅ **Single column** — about, highlights, projects, team

#### 🚀 Rezultat
**Perfect mobile experience** — kompaktowy, czytelny, bez overflow!

## [3.4.0] - 2024-10-31

### 📱 Kompleksowa Optymalizacja Mobile

#### ✨ Hero Section Mobile
- **Padding zmniejszony** — 110px top (było 150px), 50px bottom
- **H1 czcionka** — clamp(28px, 10vw, 48px) zamiast 36px/64px
- **Subtitle** — 16px (było 18px), line-height 1.5
- **CTA button** — padding 16px 40px, font-size 10px
- **Nav wyżej** — padding 16px (było 30px)

#### 📐 Zgranie czcionek
- **H2 sections** — clamp(28px, 8vw, 48px)
- **H3 about/highlights** — 14-16px
- **Project name** — 22px (mobile)
- **Timeline year** — 22px (mobile)
- **Article title** — 17px (mobile)
- **Body text** — 14px uniwersalnie
- **Labels** — 8-10px

#### 🎯 Zmniejszone spacing
- **Section padding** — 100px 0 60px (było 150px/120px)
- **Container padding** — 16px (było 20px)
- **Card padding** — 30-40px (było 50-70px)
- **Margins between** — 40-50px (było 60-90px)
- **Grid gaps** — 2px zachowane

#### 📦 Wszystkie sekcje
- ✅ **Hero** — kompaktowy, h1 wyżej
- ✅ **Stats** — 2x2 grid, mniejsze fonty
- ✅ **About** — jednokol., padding 40px/25px
- ✅ **Highlights** — 1 kolumna, 40px padding
- ✅ **Projects** — Year 48px, name 22px, desc 14px
- ✅ **Timeline** — 30px left padding, 2px line
- ✅ **Team** — 1 kolumna, 12px/10px fonts
- ✅ **Constitution** — Articles 30px padding
- ✅ **Activity** — Lead 30px padding, items 30px

#### 🔧 Technical Details
- **Border weights** — 2px (było 3px) na mobile
- **Logo** — 35px height (było 45px)
- **Border-left hero** — 3px accent
- **Responsive h1** — clamp z 10vw dla elastyczności

#### 🎯 Rezultat
- ✅ **Wszystko się mieści** — żaden tekst nie wychodzi
- ✅ **Zgrane czcionki** — spójne proporcje
- ✅ **Mniejsze spacing** — więcej treści na ekranie
- ✅ **Hero wyżej** — nagłówek bliżej góry
- ✅ **Czytelność** — 14px minimum dla body
- ✅ **Profesjonalny** — kompaktowy, ale nie ciasny

## [3.3.1] - 2024-10-31

### 🎨 Hero Box Redesign — Glassmorphism + Text Glow

#### ✨ Nowe podejście (bez dziwnych kształtów)
- **Usunięty clip-path** — Prosty, elegancki design
- **Glassmorphism** — Biały box z backdrop-filter blur(20px)
- **Orange accent** — Border-left: 5px solid dla wyróżnienia
- **Dual shadow** — Czarny + orange dla głębi

#### 💫 Text Enhancement
- **Mocny text-shadow** — Triple layer:
  - 0 2px 4px white (bliski)
  - 0 4px 12px white (średni)
  - 0 0 40px white (glow)
- **Subtitle shadow** — Delikatniejszy, double layer
- **Większa opacity** — Subtitle 0.85 → 0.9

#### 📐 Layout Details
- **Background** — rgba(255, 255, 255, 0.85) z blur
- **Border-radius** — 4px (subtelny)
- **Padding** — 80px 70px (desktop), 50px 30px (mobile)
- **Box-shadow** — Dual: dark + orange accent

#### 🎯 Rezultat
- ✅ **Tekst doskonale widoczny** na pattern
- ✅ **Glassmorphism** — Modern, trendy
- ✅ **Orange accent** — industrial style
- ✅ **Clean & professional** — Bez dziwnych kształtów
- ✅ **Text glow** — Wyróżnia się perfekcyjnie

## [3.3.0] - 2024-10-31

### 🎨 Hero Content Box — Prostokąt ze ściętymi bokami

#### ✨ Ciekawy kształt za tekstem
- **Clip-path polygon** — Prostokąt ze ściętymi krawędziami (15% top-left, 0% top-right, 85% bottom-right, 100% bottom-left)
- **Background** — Białe tło rgba(255, 255, 255, 0.9) z backdrop-filter blur
- **Box shadow** — 0 20px 60px dla głębi
- **Border** — 3px solid rgba(28, 27, 34, 0.1) dla subtelnego outline

#### 🌈 Gradient overlay
- **::after element** — Dodatkowa warstwa z orange gradient
- **Linear gradient** — 135deg, rgba(255, 107, 0, 0.1) → transparent
- **Layered effect** — Pattern + gradient + white box + content

#### 📐 Layout
- **Padding hero-content** — 80px 60px (desktop), 50px 30px (mobile)
- **Negative margins** — left: -40px, right: -40px dla szerszego box
- **Z-index layers** — ::after (-2), ::before (-1), content (1)

#### 📱 Responsive
- **Mobile adjustments** — Mniejszy padding i margins (-20px)
- **Zachowany kształt** — Clip-path działa na wszystkich rozmiarach
- **Czytelność** — Tekst dobrze się odcina od tła

#### 🎯 Visual Impact
- **Tekst się odcina** — Wyraźnie widoczny na tle pattern
- **Industrial chic** — Skośne krawędzie dla dynamicznego wyglądu
- **Modern & dynamic** — Geometryczne formy dodają energii
- **Professional** — Nie przytłacza, ale przyciąga uwagę

## [3.2.1] - 2024-10-31

### 🎨 Pattern Adjustment — Clean Body, Textured Hero

#### 🧹 Czysty Body
- **Usunięty pattern** — Body z czystym tłem `var(--white)`
- **Minimalistycznie** — Reszta strony bez textury
- **Focus na content** — Nic nie rozprasza od treści

#### ✨ Enhanced Hero Pattern
- **Większy wzór** — Geometryczny pattern 304x304px
- **Większa opacity** — 0.3 → 0.4 (bardziej widoczny)
- **Kompleksowy design** — Linie, połączenia, geometria
- **Dynamiczne tło** — Coś się dzieje, hero nie jest pusty!
- **Zachowany gradient** — Orange radial gradient + floating animation

#### 🎯 Philosophy
- **Hero wyróżniony** — Tylko główna sekcja ma pattern
- **Clean sections** — Pozostałe sekcje na czystym tle
- **Visual hierarchy** — Hero przyciąga uwagę
- **Better contrast** — Pattern tylko tam, gdzie potrzebny

## [3.2.0] - 2024-10-31

### 🎨 Hero Patterns — Subtelne tła SVG

#### ✨ Wzory z Hero Patterns
- **Pattern kropki** — Hero section z delikatnym wzorem kółek
  - Fill: `#e8e8ed` (light-gray)
  - Opacity: 0.3 (bardzo subtelne)
  - SVG pattern embedded inline
  
- **Pattern geometryczny** — Body background z liniami
  - Fill: `#d4d4d9` (subtle gray)
  - Opacity: 0.15 (ultra-subtelne)
  - Kompleksowy geometryczny wzór
  
- **Pattern dodatkowo** — Zmienne CSS z cross pattern
  - `--pattern-light` dla przyszłych zastosowań
  - Wzór krzyżyków jako opcja dla kart

#### 🌈 Visual Effects
- **Hero gradient** — Radial gradient z orange (rgba(255, 107, 0, 0.08))
- **Floating animation** — Zachowana animacja tła (20s)
- **Layered backgrounds** — Pattern + gradient overlay
- **Texture depth** — Dodana głębia wizualna bez przytłaczania

#### 🎯 Zastosowania
- Hero section: Wzór kropki + orange gradient
- Body: Geometryczny wzór globalnie
- Zachowana czystość białych kart (surface)
- Subtelność — wzory prawie niewidoczne, ale dodają teksturę

#### 💡 Design Philosophy
- **Ultra-subtle** — Patterns są ledwo widoczne
- **Modern texture** — Depth bez noise
- **Performance** — SVG inline (zero HTTP requests)
- **Accessibility** — Nie przeszkadzają w czytaniu
- **Industrial aesthetic** — tekstura, minimalistyczna elegancja

## [3.1.0] - 2024-10-31

### 🎨 Typography Redesign — Cute & Pleasant Headings

#### ✨ Nowa typografia nagłówków
- **System font stack** — SF Pro Display, Segoe UI, Helvetica Neue (native fonts dla lepszej czytelności)
- **Soft & friendly** — Obniżony font-weight (800→700 dla h1, 700→600 dla h2/h3)
- **Better spacing** — Pozytywny letter-spacing (0.01-0.02em) zamiast negatywnego
- **No uppercase** — Text-transform: none dla naturalniejszego wyglądu

#### 🎯 Szczegóły zmian:

**H1 (Hero):**
- Font-size: 140px → 130px (bardziej proporcjonalne)
- Font-weight: 800 → 700 (mniej agresywne)
- Letter-spacing: -0.05em → -0.02em (lepsze czytelność)
- Text-transform: uppercase → none
- Line-height: 0.95 → 1.1 (więcej przestrzeni)
- Accent line: gradient z orange + shadow glow

**H2 (Sekcje):**
- Font-size: 72px → 64px (bardziej delikatne)
- Font-weight: 700 → 600 (soft weight)
- Letter-spacing: -0.02em → 0.02em (przestronne)
- Text-transform: uppercase → none (naturalnie)
- Line-height: 1 → 1.2 (lepsza czytelność)
- **Gradient text** — Subtelny gradient czarny → orange (135deg)
- Accent line: 60px → 80px, gradient + glow shadow

**H3 & inne nagłówki:**
- Font-size: 18-20px → 19-21px
- Font-weight: 700 → 600
- Text-transform: uppercase → none
- Letter-spacing: 0.08em → 0.01em
- System fonts dla wszystkich

**Project names, Timeline years, Article titles:**
- Unified font-family (system stack)
- Reduced font-weight (600)
- Better letter-spacing
- No uppercase transform

#### 🌈 Visual Effects
- Gradient text dla h2 (black → accent)
- Gradient underlines z box-shadow glow
- Border-radius na accent lines (2-3px)
- Smooth transitions i animacje
- Better visual hierarchy

## [3.0.2] - 2024-10-31

### 🎯 Navigation Update

- **Zmiana nazwy w nawigacji** — "Home" → "Start"
- Lepsza przejrzystość interfejsu użytkownika
- Zachowany link `#home` w URL routing

## [3.0.1] - 2024-10-31

### 🎨 Enhanced Logo with 3D Animation

- **Większe logo** — Zwiększony rozmiar SVG z 40px → 60px (desktop), 30px → 45px (mobile)
- **3D rotacja** — Płynna animacja rotate3d (8s loop)
  - Obrót Y: 0° → 180° → 360° → 180° → 0°
  - Subtelny tilt X: ±5°
  - Transform-style: preserve-3d
- **Hover effect** — Pauza animacji + scale(1.1) + rotateY(180deg)
- **Większy font** — Nazwa koła: 20px → 22px, gap: 20px → 25px
- **Smooth transitions** — Cubic-bezier dla wszystkich transform

## [3.0.0] - 2024-10-31

### 🚀 Modern 2025 Redesign — Enhanced Layout & UX

#### ✨ Nowe Sekcje
- **Statystyki** — Dynamiczna sekcja z liczbami (10+ lat, 50+ członków, 6 projektów, 5 nagród)
  - Grid layout z hover effects
  - Karty z animacjami (transform, scale, color transitions)
  - Responsywny układ (2 kolumny na mobile)
  
- **O Nas** — Sekcja przedstawiająca koło
  - Lead paragraph z accent border (4px orange)
  - 3 karty z kluczowymi wartościami
  - Hover effects z accent line animation
  - Transform effects na kartach

#### 🎨 Enhanced Hero Section
- **Floating animation** — Subtle background gradient z animacją (20s loop)
- **Nowy layout** — Zwiększone padding (180px/120px)
- **Typografia** — Font-weight: 800, lepszy line-height (0.95)
- **Accent line** — Orange underline z slide-in animation (0.8s)
- **Responsive** — Lepsze fonty na mobile (36-64px)

#### 🎯 Improved Highlight Cards
- **Nowe wymiary** — 300px minWidth, większy padding (70px/50px)
- **Bottom accent** — Orange bar animation on hover (width: 0 → 100%)
- **Enhanced hover** — Scale effect (1.02), dłuższe transitions (0.4s)
- **Number styling** — Większe numery (12px), scale na hover (1.2)
- **Overflow hidden** — Czystsze animacje

#### 📐 Enhanced Projects Section
- **Większe spacing** — 80px padding, 80px gap
- **Accent hover** — Rok zmienia kolor na orange i scale (1.05)
- **Left padding animation** — Karta przesuwa się w prawo na hover
- **Większe fonty** — Project name: 32px, description: 16px
- **Sticky year** — Lepszy font-weight (800), opacity transitions
- **Team tags hover** — Transform i color change

#### 🎨 Global Improvements
- **Smooth scroll** — `scroll-behavior: smooth` na całej stronie
- **Font rendering** — `-webkit-font-smoothing: antialiased`
- **Better fonts** — 'Helvetica Neue', -apple-system, BlinkMacSystemFont
- **Cubic-bezier** — Wszędzie `cubic-bezier(0.4, 0, 0.2, 1)` dla smooth animations
- **Responsive refinements** — Lepsze breakpoints i mobile layouts
- **Accent color usage** — Więcej użyć `var(--accent)` (#ff6b00)

#### 📱 Mobile Enhancements
- **Hero mobile** — 150px/80px padding, lepsze font sizing
- **About lead** — 20px font, zmniejszony padding
- **Single column** — Wszystkie grids na 1fr na mobile
- **Reduced padding** — 50px/30px na kartach mobile

#### 📊 Data Structure Updates
- `home.json` — Nowa struktura `stats` (array) i `about` (object)
- `projects.json` — Projekt modernizacji z rokiem 2025
- JavaScript — Nowe renderowanie stats i about sections

#### 🎨 Design Philosophy
- **2025 aesthetic** — Modern, clean, minimalist
- **Industrial foundation** — zachowany industrial design, labels, bold typography
- **Enhanced interactivity** — Więcej hover states, transforms, animations
- **Better spacing** — Więcej "white space", lepsze proporcje
- **Accent usage** — Orange jako highlight color

## [2.3.0] - 2024-10-31

### 🎨 Refined Color Palette & Enhanced Styling

- **Nowe kolory:**
  - Zamiast `#000` → `#1c1b22` (soft dark)
  - Zamiast `#fff` → `#f3f3f7` (warm light)
  - Dodano `--surface: #ffffff` dla kart
  - Dodano `--light-gray: #e8e8ed`
  
- **Home Page Improvements:**
  - Gradient background dla hero section
  - Większe fonty (h1 do 160px)
  - Shadow effects i subtle overlays
  - Lepsze spacing (120px margins)
  - Enhanced CTA button z animacją i cieniem
  
- **Highlight Cards:**
  - Białe tło (`--surface`)
  - Borders i subtle shadows
  - Lepsze hover effects z transform
  - Zwiększony padding (60px)
  
- **Quote Section:**
  - Większy font (32px)
  - Box shadows dla depth
  - Lepsze spacing
  
- **Navigation:**
  - Backdrop blur z opacity
  - Subtle shadow
  
- **Wszystkie karty:**
  - Smooth transitions (cubic-bezier)
  - Transform on hover
  - Consistent shadows
  - Białe tło z borderami

## [2.2.0] - 2024-10-31

### 🔗 Hash Routing

- **URL Routing** — każda sekcja ma własny adres
- Hash-based routing: `/#home`, `/#projects`, `/#team`, etc.
- **Linki bezpośrednie** — można linkować do konkretnej sekcji
- **Historia przeglądarki** — przyciski wstecz/dalej działają
- **Logo jako link** — kliknięcie w logo wraca do home
- **Smooth scroll** do góry przy zmianie sekcji

## [2.1.1] - 2024-10-31

### 📝 Aktualizacja treści

- **Dodano rok 2024/25** do sekcji zespołu
- Zaktualizowana lista członków koła (21 osób)
- Zarząd: Maciej Szuwarowski (Przewodniczący), Stanisław Malec (Wiceprzewodniczący)

## [2.1.0] - 2024-10-31

### 🎨 Redesign w Industrial Style

- **Nowy design** z minimalistycznym, industrial aesthetic
- **Logo SVG** zintegrowane w nawigację
- **Industrial aesthetic:**
  - 2px gaps w gridach (charakterystyczny element)
  - Bold borders (2px, 3px solid)
  - Czarno-białe kontrasty
- **Labels i instrukcje** w industrial style:
  - "STATEMENT", "ZARZĄD", "O NAS", "LINK"
  - Małe, uppercase, semi-transparent
- **Typography:**
  - Helvetica jako główna czcionka
  - Bold, uppercase headings (72px-140px)
  - Tight letter-spacing (-0.02em)
- **Numbering system** (01, 02, 03...) w highlight cards
- **Hover effects** — inwersja czarny/biały
- **Sticky elements** — rok w projektach
- **Responsive design** dostosowany do mobile

### 📦 Deployment
- **GitHub Actions** workflow dla automatycznego deploymentu
- **package.json** z npm scripts
- **gh-pages** support dla ręcznego deploymentu
- Dwie metody deployment: automatyczny i ręczny

### 📦 Nowe pliki
- `DESIGN_NOTES.md` - Szczegółowa dokumentacja designu
- `package.json` - Konfiguracja npm
- `.github/workflows/deploy.yml` - GitHub Actions workflow
- `NPM_GUIDE.md` - Przewodnik npm

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

