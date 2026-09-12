# JOVIS Nutritional Result — UI Reconstruction Description

## 1. Overall page

**Screenshot viewport:** `254px × 711px`

The screen is a **mobile nutritional analysis result page** for the JOVIS app.

It follows the same dark JOVIS visual system used in the previous screens:

- very dark purple-black background
- white primary text
- muted lavender-gray secondary text
- thin purple borders
- violet/pink brand accents
- green used for positive nutrition indicators
- fixed bottom navigation
- compact stacked card layout

The screen presents the result of an AI-assisted scan of a food/supplement product.

Recommended semantic structure:

```text
<body>
  <div class="app-shell">

    <header class="result-header">
      title
      subtitle
    </header>

    <main class="result-content">

      <section class="product-summary-card">
        product-thumbnail
        product-info
        share-button
        nutrition-metrics
      </section>

      <section class="tag-row">
        tag × 3
      </section>

      <section class="ai-insights-card">
        section-title
        insight-list
      </section>

      <section class="nutrition-score-card">
        score-header
        gradient-progress-bar
      </section>

      <section class="recommendation-card">
        section-title
        recommendation-copy
      </section>

      <button class="history-button">
        icon
        label
      </button>

      <button class="scan-again-button">
        icon
        label
      </button>

    </main>

    <nav class="bottom-navigation">
      Home
      Câmera
      Feed
      Perfil
    </nav>

  </div>
</body>
```

---

## 2. Global visual style

The screen is a **results dashboard** with vertically stacked cards.

The visual hierarchy is:

```text
page title
↓
product summary
↓
classification tags
↓
AI insights
↓
nutrition score
↓
recommendation
↓
action buttons
↓
bottom navigation
```

The interface is dense but highly structured, with most content contained inside rounded cards.

---

## 3. Approximate color palette

Recommended colors:

```css
:root {
  --bg: #090510;

  --surface: #15111d;
  --surface-alt: #18121f;
  --surface-dark: #100c16;

  --border: #32223f;
  --border-strong: #562071;

  --text-primary: #ffffff;
  --text-secondary: #b0a8b6;
  --text-muted: #8d8595;

  --purple: #b12fff;
  --purple-mid: #9828ef;
  --purple-light: #cf6cff;

  --green: #08d86d;
  --green-dark: #074d2b;

  --yellow: #ffd335;

  --nav-inactive: #768092;
  --nav-active: #c15cff;

  --progress-track: #36303e;
}
```

Main page background:

```css
background: #090510;
```

Most cards use:

```css
background: #15111d;
```

---

## 4. Global typography

Use a modern sans-serif:

```css
font-family:
  Inter,
  "SF Pro Display",
  "SF Pro Text",
  Arial,
  sans-serif;
```

Typography hierarchy:

- page title: large, bold, centered
- section titles: medium-bold
- product name: bold
- metrics: bold numeric values
- labels/body text: small and muted
- button labels: bold
- navigation labels: very small

---

# 5. Page shell

Recommended:

```css
.app-shell {
  width: 100%;
  max-width: 430px;
  min-height: 100vh;
  margin: 0 auto;
  background: #090510;
  color: #fff;
}
```

Most visible content uses approximately:

```text
left margin: 10px
right margin: 10px
```

The screenshot includes thin dark/gray outer borders from the captured viewport. These should normally not be recreated.

---

# 6. Header

Approximate region:

```text
y: 6px → 42px
```

The header is centered.

It contains:

1. main title
2. small subtitle

---

## 7. Main page title

Exact text:

> **Resultado Nutricional**

Approximate position:

```text
center-x: 127px
top: 7px
```

Approximate typography:

```css
font-size: 18px;
font-weight: 800;
line-height: 1.1;
text-align: center;
color: #ffffff;
```

---

## 8. Header subtitle

Exact text:

> Análise completa com IA

Approximate position:

```text
center-x: 127px
top: 32px
```

Approximate typography:

```css
font-size: 6.5px;
font-weight: 400;
color: #8d8595;
text-align: center;
```

---

# 9. Product summary card

Approximate bounds:

```text
x: 10px
y: 56px
width: 234px
height: 169px
```

Style:

```css
.product-summary-card {
  background: #15111d;
  border: 1px solid #342241;
  border-radius: 16px;
  padding: 12px;
}
```

Internal structure:

```text
thumbnail | product name + portion        share button
          | score badge + benefit badge

divider

nutrition metrics in two-column table
```

---

# 10. Product thumbnail

Approximate bounds:

```text
x: 24px
y: 72px
width: 73px
height: 70px
```

The thumbnail is a dark product pack representation for whey protein.

Visual structure:

- outer rounded dark card
- stylized dark package/container
- thin gray-blue outlines
- small white text
- slight blue-purple tint
- centered product pack

Approximate container style:

```css
.product-thumb {
  width: 73px;
  height: 70px;
  border-radius: 12px;
  background: #0d111c;
  border: 1px solid #2c3350;
}
```

The inner package is a vertical rounded rectangle with layered outlines.

Visible package text:

```text
WHEY
PROTEIN
```

with a smaller illegible sublabel beneath.

The thumbnail is decorative and can be implemented as an image or simplified CSS illustration.

---

# 11. Product title and portion

Approximate position:

```text
x: 106px
y: 74px
```

Product name:

> **Whey Protein**  
> **Concentrado**

Exact two-line layout.

Approximate typography:

```css
font-size: 10px;
font-weight: 700;
line-height: 1.35;
color: #ffffff;
```

Portion line below:

> Porção: 30 g

Approximate typography:

```css
font-size: 7px;
font-weight: 400;
color: #aaa2b0;
```

---

# 12. Share button

Approximate bounds:

```text
x: 216px
y: 68px
width: 22px
height: 22px
```

Circular dark control.

Style:

```css
width: 22px;
height: 22px;
border-radius: 50%;

background: #201a27;
border: 1px solid #403649;
```

Icon:

- white share/network icon
- approximately `10px`

---

# 13. Product score badge

Approximate bounds:

```text
x: 106px
y: 121px
width: 43px
height: 22px
```

Text:

> **92/100**

Style:

```css
background: linear-gradient(90deg, #bd21ff, #8c22ef);
border-radius: 999px;
```

Typography:

```css
font-size: 8px;
font-weight: 700;
color: #ffffff;
```

---

# 14. Benefit badge

Approximate bounds:

```text
x: 154px
y: 121px
width: 71px
height: 22px
```

Text:

> Bom benefício

Style:

```css
background: #074d2b;
border: 1px solid #0e8a4a;
border-radius: 999px;
```

Typography:

```css
font-size: 7px;
font-weight: 600;
color: #10df71;
```

---

# 15. Product-card divider

A thin horizontal divider separates the summary information from the nutrition metrics.

Approximate position:

```text
x: 24px
y: 153px
width: 206px
height: 1px
```

Style:

```css
background: #2a2330;
```

---

# 16. Nutrition metrics table

Approximate region:

```text
x: 23px
y: 166px
width: 207px
height: 45px
```

The metrics are arranged in **two vertical columns**, each containing label/value pairs.

Left column:

```text
Calorias        120 kcal
Carboidratos      5 g
Sódio           160 mg
```

Right column:

```text
Proteínas       26 g
Gorduras         2 g
```

Approximate typography for labels:

```css
font-size: 7px;
font-weight: 400;
color: #9b93a3;
```

Approximate typography for values:

```css
font-size: 8px;
font-weight: 700;
color: #ffffff;
```

Values are aligned toward the right edge of each mini-column.

---

# 17. Tag row

Approximate region:

```text
x: 10px
y: 241px
height: 19px
```

Three compact pill tags appear horizontally.

Exact texts:

```text
Sem lactose
Alto teor proteico
Pós-treino
```

Each tag uses:

```css
background: #15111d;
border: 1px solid #3a3042;
border-radius: 999px;
padding: 5px 9px;
```

Approximate typography:

```css
font-size: 6.5px;
font-weight: 400;
color: #ffffff;
```

Approximate widths:

```text
Sem lactose: ~59px
Alto teor proteico: ~75px
Pós-treino: ~51px
```

Gaps are about `5–6px`.

---

# 18. AI insights card

Approximate bounds:

```text
x: 10px
y: 275px
width: 234px
height: 126px
```

Style:

```css
background: #15111d;
border: 1px solid #342241;
border-radius: 16px;
padding: 14px;
```

---

# 19. AI insights title

Exact text:

> **Insights da IA**

Approximate position:

```text
x: 24px
y: 291px
```

A small violet sparkle/star icon appears immediately to the left of the title.

Title typography:

```css
font-size: 10px;
font-weight: 700;
color: #ffffff;
```

Icon color:

```css
color: #c15cff;
```

Icon size:

```text
10–12px
```

---

# 20. AI insight bullet list

Three insight rows are visible.

Each bullet is a small yellow lightning/triangle-like marker aligned to the left.

Accent color:

```css
color: #ffd335;
```

### Insight 1

Text:

> Alto teor de proteína para recuperação  
> muscular.

Approximate typography:

```css
font-size: 7.5px;
line-height: 1.5;
color: #ffffff;
```

### Insight 2

Text:

> Baixo teor de carboidratos.

### Insight 3

Text:

> Auxilia no início de consumo em excesso.

The third line is small and visually similar to the others.

Approximate row spacing:

```text
10–13px
```

---

# 21. Nutrition score card

Approximate bounds:

```text
x: 10px
y: 417px
width: 234px
height: 59px
```

Style:

```css
background: #15111d;
border: 1px solid #342241;
border-radius: 14px;
padding: 13px;
```

---

# 22. Nutrition score header

Left text:

> **Nota Nutricional**

Right text:

> **92/100**

The right score uses violet text.

Approximate typography:

```css
font-size: 9px;
font-weight: 700;
```

Colors:

```css
left: #ffffff;
right: #c463ff;
```

Layout:

```css
display: flex;
justify-content: space-between;
align-items: center;
```

---

# 23. Nutrition score progress bar

Approximate position:

```text
x: 24px
y: 455px
width: 211px
height: 8px
```

Track:

```css
height: 8px;
border-radius: 999px;
background: #39323f;
overflow: hidden;
```

Fill is approximately `92%`.

The fill uses a green-to-purple gradient:

```css
background: linear-gradient(
  90deg,
  #05d96c 0%,
  #16cc8b 35%,
  #32b7b2 58%,
  #7c56df 80%,
  #ad47ff 100%
);
```

---

# 24. Recommendation card

Approximate bounds:

```text
x: 10px
y: 492px
width: 234px
height: 79px
```

This card has a stronger purple border than the other cards.

Style:

```css
background: #1a0d20;
border: 1px solid #64257e;
border-radius: 15px;
padding: 13px;
```

---

# 25. Recommendation title

Exact text:

> **Recomendação**

Approximate typography:

```css
font-size: 9px;
font-weight: 700;
color: #ffffff;
```

---

# 26. Recommendation body

Exact visible text:

> Produto excelente para pós-treino. Combine com  
> frutas para melhor aporte energético.

Approximate typography:

```css
font-size: 7.5px;
font-weight: 400;
line-height: 1.5;
color: #f1edf3;
```

Two lines.

---

# 27. Save-to-history button

Approximate bounds:

```text
x: 10px
y: 586px
width: 234px
height: 38px
```

Style:

```css
background: #15111d;
border: 1px solid #342241;
border-radius: 10px;
```

Contents centered horizontally:

```text
[save/history icon] Salvar no histórico
```

Exact text:

> **Salvar no histórico**

Approximate typography:

```css
font-size: 9px;
font-weight: 700;
color: #ffffff;
```

Icon:

- white outline save/history/document symbol
- approximately `11px`

---

# 28. Scan-again primary button

Approximate bounds:

```text
x: 10px
y: 631px
width: 234px
height: 40px
```

This is the strongest CTA on the page.

Style:

```css
background: linear-gradient(
  90deg,
  #bf17ff 0%,
  #9f14f2 50%,
  #8511e4 100%
);

border: none;
border-radius: 10px;
```

There is a visible violet glow, especially below and around the button.

Suggested:

```css
box-shadow:
  0 5px 16px rgba(170, 31, 255, 0.45),
  0 0 12px rgba(170, 31, 255, 0.25);
```

Contents:

```text
[scan icon] Escanear outro produto
```

Exact text:

> **Escanear outro produto**

Typography:

```css
font-size: 9px;
font-weight: 700;
color: #ffffff;
```

Icon:

- white scan/focus brackets
- approximately `11px`

---

# 29. Bottom navigation

Approximate bounds:

```text
x: 0px
y: 660px
width: 254px
height: 51px
```

The bottom navigation overlaps slightly visually with the lower CTA region due to the compact viewport.

Style:

```css
background: #08050d;
border-top: 1px solid #211b28;

display: grid;
grid-template-columns: repeat(4, 1fr);
```

Items:

```text
Home
Câmera
Feed
Perfil
```

Each contains:

```text
icon
label
```

---

# 30. Bottom navigation states

Unlike the previous camera screen, **Câmera remains the active tab** here.

Active item:

```text
Câmera
```

Active color:

```css
color: #c15cff;
```

Inactive items:

```css
color: #768092;
```

---

# 31. Home nav item

Icon:

- outline house
- muted blue-gray

Label:

> Home

---

# 32. Camera nav item — active

Icon:

- outline camera
- violet

Label:

> Câmera

---

# 33. Feed nav item

Icon:

- trophy/achievement-style symbol
- muted blue-gray

Label:

> Feed

---

# 34. Profile nav item

Icon:

- outline person
- muted blue-gray

Label:

> Perfil

---

# 35. Approximate vertical layout map

```text
0       screenshot start

7       page title
32      subtitle

56      product summary card begins
225     product summary card ends

241     tag row
260     tag row ends

275     AI insights card begins
401     AI insights card ends

417     nutrition score card begins
476     nutrition score card ends

492     recommendation card begins
571     recommendation card ends

586     save button begins
624     save button ends

631     primary scan-again CTA begins
671     CTA ends

660     bottom navigation begins
711     screenshot ends
```

The CTA and bottom navigation overlap slightly in vertical visual space due to the compact capture.

---

# 36. Approximate horizontal layout map

```text
0       screenshot edge

10      common content left edge
244     common content right edge

24      inner card content left edge
230     inner card content right edge

product summary:
24–97    thumbnail
106–225  product information
216–238  share button

bottom nav:
0–63      Home
63–127    Câmera
127–190   Feed
190–254   Perfil
```

---

# 37. Spacing system

Useful screenshot-scale values:

```css
--space-xs: 4px;
--space-sm: 7px;
--space-md: 10px;
--space-lg: 14px;
--space-xl: 16px;
```

Common usage:

- page inset: `10px`
- card padding: `12–14px`
- section gap: `15–17px`
- pill gap: `5–6px`
- title/body gap: `7–9px`

---

# 38. Border-radius system

Recommended values:

```css
--radius-large: 16px;
--radius-card: 14px;
--radius-button: 10px;
--radius-pill: 999px;
```

The larger information cards use approximately `14–16px`.

Buttons are slightly less rounded, approximately `10px`.

---

# 39. Icon style

Use thin rounded outline icons.

Recommended icon families:

- Lucide
- Phosphor
- Heroicons Outline

Suggested equivalents:

```text
Share2
Sparkles
Zap
Save
ScanLine
House
Camera
Trophy
User
```

---

# 40. Recommended responsive implementation

The source screenshot width is only `254px`.

For a typical `390px` mobile viewport:

```text
390 / 254 ≈ 1.54
```

Scale proportions rather than using literal screenshot dimensions.

Recommended page container:

```css
.app-shell {
  width: 100%;
  max-width: 430px;
  margin: 0 auto;
  background: #090510;
}
```

Recommended main content:

```css
.result-content {
  padding: 0 14px 72px;
}
```

For standard mobile width, full-width cards should occupy roughly:

```css
width: 100%;
```

within the padded content container.

---

# 41. Recommended component hierarchy

```text
NutritionResultPage
├── ResultHeader
│   ├── Title
│   └── Subtitle
│
├── ProductSummaryCard
│   ├── ProductThumbnail
│   ├── ProductInfo
│   │   ├── ProductName
│   │   ├── Portion
│   │   └── BadgeRow
│   │       ├── ScoreBadge
│   │       └── BenefitBadge
│   ├── ShareButton
│   ├── Divider
│   └── NutritionMetrics
│
├── TagRow
│   ├── SemLactose
│   ├── AltoTeorProteico
│   └── PosTreino
│
├── AIInsightsCard
│   ├── SectionTitle
│   └── InsightList
│
├── NutritionScoreCard
│   ├── ScoreHeader
│   └── GradientProgress
│
├── RecommendationCard
│   ├── Title
│   └── RecommendationText
│
├── SaveHistoryButton
├── ScanAgainButton
│
└── BottomNavigation
    ├── Home
    ├── Câmera [active]
    ├── Feed
    └── Perfil
```

---

# 42. Exact visible text inventory

Use these strings exactly:

```text
Resultado Nutricional

Análise completa com IA

Whey Protein
Concentrado

Porção: 30 g

92/100

Bom benefício

Calorias
120 kcal

Proteínas
26 g

Carboidratos
5 g

Gorduras
2 g

Sódio
160 mg

Sem lactose
Alto teor proteico
Pós-treino

Insights da IA

Alto teor de proteína para recuperação
muscular.

Baixo teor de carboidratos.

Auxilia no início de consumo em excesso.

Nota Nutricional

92/100

Recomendação

Produto excelente para pós-treino. Combine com
frutas para melhor aporte energético.

Salvar no histórico

Escanear outro produto

Home
Câmera
Feed
Perfil
```

---

# 43. Important visual characteristics to preserve

For close visual reproduction, preserve the following:

1. The page uses the same **dark purple-black background** as the rest of the JOVIS app.
2. The title is centered and visually dominant.
3. The product summary card is the largest information card.
4. The product thumbnail is dark, compact, and outlined in cool gray-blue.
5. The numeric score badge is bright violet.
6. The `"Bom benefício"` badge uses a dark-green background with bright-green text.
7. Nutrition facts are arranged in compact two-column rows.
8. The three product tags are small rounded outline pills.
9. The AI insights card uses a violet sparkle icon.
10. Individual insights use small yellow accent bullets/icons.
11. The nutrition score uses a **green-to-purple gradient bar**.
12. The recommendation card has a stronger violet border than normal cards.
13. `"Salvar no histórico"` is a dark secondary button.
14. `"Escanear outro produto"` is a bright purple primary CTA with glow.
15. The bottom nav remains dark and understated.
16. **Câmera** stays active in violet.
17. Avoid oversized typography; the screen is information-dense.
18. Keep section spacing compact and consistent.

---

# 44. Visual hierarchy

The strongest visual elements should appear in this order:

```text
Resultado Nutricional
↓
product summary
↓
92/100 + Bom benefício badges
↓
AI insights
↓
nutrition score gradient
↓
recommendation
↓
purple Escanear outro produto CTA
↓
bottom navigation
```

The overall screen should feel like a **premium AI nutrition-analysis result view**, combining health data, explainability, scoring, and actionable follow-up while remaining consistent with the dark JOVIS mobile interface.
