# JOVIS — Create Post Screen UI Reconstruction Description

## 1. Overall page

**Screenshot viewport:** approximately `262px × 842px`

The screen is a **mobile social post creation interface** for the JOVIS app.

It follows the same visual system as the previous JOVIS screens:

- nearly black purple-tinted background
- white primary text
- muted gray/lavender secondary text
- violet/purple brand accent
- rounded dark cards
- thin purple-gray borders
- fixed bottom navigation
- compact mobile spacing

The purpose of the screen is to allow the user to:

1. add a photo
2. choose a quick post suggestion/category
3. write a caption
4. select where to share the post
5. publish the post

Recommended semantic structure:

```text
<body>
  <div class="app-shell">

    <header class="post-header">
      close-button
      page-title
      publish-button
    </header>

    <main class="post-content">

      <section class="photo-upload-area">
        upload-icon
        upload-title
        upload-subtitle
      </section>

      <section class="quick-suggestions">
        section-title
        suggestion-grid
          suggestion-card × 3
      </section>

      <section class="caption-section">
        section-title
        textarea
        character-counter
      </section>

      <section class="share-destinations-card">
        section-title
        option-row × 4
      </section>

      <section class="privacy-note">
        privacy-copy
      </section>

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

The page is visually dense but clean.

The strongest accent is violet/purple, used on:

- the publish button
- upload icon
- quick suggestion icons
- selected sharing options
- active Feed navigation item
- privacy notice border/background

The overall hierarchy is:

```text
header
↓
large photo upload area
↓
quick suggestions
↓
caption field
↓
sharing destinations
↓
privacy note
↓
bottom navigation
```

---

## 3. Approximate color palette

Recommended colors:

```css
:root {
  --bg: #09060f;

  --surface: #15111b;
  --surface-strong: #18131f;
  --surface-selected: #2a1740;

  --border: #342b3c;
  --border-soft: #2b2432;
  --border-purple: #6d2b89;

  --text-primary: #ffffff;
  --text-secondary: #aaa2af;
  --text-muted: #817989;

  --purple: #a93cff;
  --purple-light: #c46aff;
  --purple-dark: #7628d5;
  --purple-soft: #4c235f;

  --nav-inactive: #738091;
  --nav-active: #c158ff;

  --radio-empty: #6c7586;
}
```

Page background:

```css
background: #09060f;
```

Most card surfaces:

```css
background: #15111b;
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

- page title: bold, medium size
- section titles: bold, small
- upload title: bold, centered
- option text: small white
- helper/counter/privacy text: very small gray
- bottom nav labels: very small

---

# 5. Header

Approximate bounds:

```text
x: 18px → 257px
y: 19px → 47px
height: ~29px
```

Layout:

```css
display: grid;
grid-template-columns: 34px 1fr auto;
align-items: center;
```

Elements:

1. circular close button
2. centered page title
3. purple publish button

---

## 6. Close button

Approximate bounds:

```text
x: 18px
y: 20px
width: 24px
height: 24px
```

Shape:

```css
border-radius: 50%;
background: #15121a;
border: 1px solid #3a333f;
```

Icon:

- white `×`
- thin stroke
- approximately `12px`

No text label.

---

## 7. Header title

Exact text:

> **Criar publicação**

Approximate center:

```text
x: 120px
y: 31px
```

Typography:

```css
font-size: 14px;
font-weight: 700;
color: #ffffff;
```

---

## 8. Publish button

Approximate bounds:

```text
x: 196px
y: 20px
width: 61px
height: 24px
```

Exact text:

> **Publicar**

Style:

```css
background: linear-gradient(
  90deg,
  #bd5cff,
  #9b47f2
);
border: none;
border-radius: 999px;
```

Typography:

```css
font-size: 8px;
font-weight: 700;
color: #ffffff;
```

---

# 9. Photo upload area

Approximate bounds:

```text
x: 18px
y: 55px
width: 239px
height: 237px
```

This is the largest element on the page.

Appearance:

- dark fill
- large rounded rectangle
- dashed gray-purple border
- centered upload controls
- no image currently selected

Style:

```css
.photo-upload-area {
  border: 1px dashed #5c5165;
  border-radius: 15px;
  background: #121019;

  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
}
```

The dashed border is subtle and evenly spaced.

---

# 10. Upload icon button

Approximate bounds:

```text
x: 117px
y: 133px
width: 42px
height: 42px
```

Rounded-square container.

Style:

```css
background: #412353;
border: 1px solid #65407a;
border-radius: 10px;
```

Icon:

- upload/share arrow
- violet/light-purple
- approximately `20px`
- arrow points upward from a tray

Suggested icon:

```text
Upload
UploadCloud
SquareArrowUp
```

---

# 11. Upload title

Exact text:

> **Adicionar foto**

Approximate position:

```text
center-x: 137px
top: 187px
```

Typography:

```css
font-size: 10px;
font-weight: 700;
color: #ffffff;
text-align: center;
```

---

# 12. Upload helper text

Exact text:

> Toque para escolher da galeria

Approximate position:

```text
center-x: 137px
top: 205px
```

Typography:

```css
font-size: 7px;
font-weight: 400;
color: #aaa2af;
text-align: center;
```

---

# 13. Quick suggestions section

Section begins around:

```text
y: 307px
```

Title:

> **Sugestões rápidas**

Approximate typography:

```css
font-size: 9px;
font-weight: 700;
color: #ffffff;
```

Approximate left edge:

```text
x: 20px
```

---

# 14. Quick suggestion grid

Approximate bounds:

```text
x: 18px
y: 328px
width: 239px
height: 62px
```

Three equal cards in one row.

Layout:

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 7px;
```

Each card is approximately:

```text
75px × 62px
```

Style:

```css
background: #15111b;
border: 1px solid #33293b;
border-radius: 10px;
```

Content centered.

---

# 15. Quick suggestion card — Treino do dia

Approximate bounds:

```text
x: 18px
y: 328px
width: 75px
height: 62px
```

Icon container:

```text
25px × 25px
```

Style:

```css
background: #3a1f4d;
border-radius: 8px;
```

Icon:

- small violet fitness/dumbbell/activity-style icon
- centered

Exact label:

> Treino do dia

Typography:

```css
font-size: 7px;
font-weight: 500;
color: #ffffff;
```

---

# 16. Quick suggestion card — Refeição

Approximate bounds:

```text
x: 101px
y: 328px
width: 75px
height: 62px
```

Icon container:

- same violet square
- white/purple food/container icon

Exact label:

> Refeição

---

# 17. Quick suggestion card — Progresso

Approximate bounds:

```text
x: 184px
y: 328px
width: 73px
height: 62px
```

Icon container:

- same violet square
- progress/stack/photo-like icon

Exact label:

> Progresso

---

# 18. Caption section

Section title begins around:

```text
x: 19px
y: 405px
```

Exact title:

> **Legenda**

Typography:

```css
font-size: 9px;
font-weight: 700;
color: #ffffff;
```

---

# 19. Caption textarea

Approximate bounds:

```text
x: 18px
y: 426px
width: 239px
height: 81px
```

Style:

```css
background: #15111b;
border: 1px solid #342b3c;
border-radius: 16px;
padding: 14px;
resize: none;
```

Placeholder text:

> Escreva sobre sua jornada...

Approximate typography:

```css
font-size: 8px;
font-weight: 400;
color: #7e7786;
```

The placeholder sits near the top-left.

No entered text is present.

---

# 20. Character counter

Approximate position:

```text
x: 21px
y: 522px
```

Exact visible text:

> 0/500 caracteres

Typography:

```css
font-size: 6px;
font-weight: 400;
color: #8b8491;
```

Left aligned.

---

# 21. Share destinations card

Approximate bounds:

```text
x: 18px
y: 543px
width: 239px
height: 182px
```

Style:

```css
background: #15111b;
border: 1px solid #342b3c;
border-radius: 16px;
padding: 14px;
```

---

# 22. Share destinations title

Exact text:

> **Compartilhar em**

Approximate typography:

```css
font-size: 9px;
font-weight: 700;
color: #ffffff;
```

Approximate position:

```text
x: 31px
y: 560px
```

---

# 23. Sharing option rows

There are four full-width option rows stacked vertically.

Approximate width:

```text
212px
```

Approximate height:

```text
29px
```

Vertical gap:

```text
5px
```

Each row contains:

```text
radio/check circle
label
```

Two rows are selected, two are unselected.

---

# 24. Selected option style

Selected options:

```text
Meu Feed
Comunidade Fitness
```

Style:

```css
background: #2d1941;
border: 1px solid #75439b;
border-radius: 8px;
```

Selected indicator:

```text
14–15px circle
```

Background:

```css
background: #9e55ec;
```

Inside:

- white checkmark
- centered
- approximately `8px`

---

# 25. Unselected option style

Unselected options:

```text
Desafio 30 Dias
Corrida Matinal
```

Style:

```css
background: #201c25;
border: 1px solid #3a343f;
border-radius: 8px;
```

Indicator:

```text
13–14px circle
```

Style:

```css
border: 1.5px solid #788496;
background: transparent;
```

No inner dot.

---

# 26. Share option labels

Exact labels:

```text
Meu Feed
Comunidade Fitness
Desafio 30 Dias
Corrida Matinal
```

Approximate typography:

```css
font-size: 8px;
font-weight: 500;
color: #ffffff;
```

---

# 27. Privacy information card

Approximate bounds:

```text
x: 18px
y: 740px
width: 239px
height: 52px
```

The card uses a stronger purple border and purple-tinted background.

Style:

```css
background: #1e0927;
border: 1px solid #6e2385;
border-radius: 15px;
padding: 11px;
```

Exact visible text:

> Suas fotos de progresso são processadas sem filtros para  
> garantir autenticidade. Configure suas preferências de  
> privacidade nas configurações.

Approximate typography:

```css
font-size: 6.5px;
font-weight: 400;
line-height: 1.45;
color: #f1eaf4;
```

The text is left aligned.

There is no visible icon inside this card.

---

# 28. Bottom navigation

Approximate bounds:

```text
x: 0px
y: 790px
width: 262px
height: 52px
```

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

Each item contains icon above label.

---

# 29. Active navigation state

The active tab is:

> **Feed**

Active color:

```css
color: #c158ff;
```

The Feed icon is a violet trophy/achievement-style icon.

The other three items are muted blue-gray.

---

# 30. Home nav item

Icon:

- outline house
- muted blue-gray

Label:

> Home

---

# 31. Camera nav item

Icon:

- outline camera
- muted blue-gray

Label:

> Câmera

---

# 32. Feed nav item — active

Icon:

- trophy / award-style outline
- violet

Label:

> Feed

Approximate active color:

```css
color: #c158ff;
```

---

# 33. Profile nav item

Icon:

- outline person
- muted blue-gray

Label:

> Perfil

---

# 34. Approximate vertical layout map

```text
0       screenshot start

20      header begins
31      title baseline
44      header ends

55      photo upload area begins
292     upload area ends

308     "Sugestões rápidas"
328     suggestion cards begin
390     suggestion cards end

405     "Legenda"
426     textarea begins
507     textarea ends

522     character counter

543     share destinations card begins
725     share destinations card ends

740     privacy card begins
792     privacy card ends

790     bottom navigation begins
842     screenshot ends
```

---

# 35. Approximate horizontal layout map

```text
0       screenshot edge

18      main content left edge
257     main content right edge

quick cards:
18–93    Treino do dia
101–176  Refeição
184–257  Progresso

bottom nav:
0–65      Home
65–131    Câmera
131–196   Feed
196–262   Perfil
```

---

# 36. Spacing system

Useful screenshot-scale spacing values:

```css
--space-xs: 4px;
--space-sm: 7px;
--space-md: 10px;
--space-lg: 14px;
--space-xl: 18px;
```

Typical usage:

- page side inset: `18px`
- section title to component: `8–10px`
- card padding: `12–14px`
- quick-card gap: `7px`
- sharing row gap: `5px`
- major section gap: `14–18px`

---

# 37. Border-radius system

Recommended:

```css
--radius-large: 16px;
--radius-card: 10px;
--radius-small: 8px;
--radius-pill: 999px;
```

Usage:

- upload area: `15px`
- textarea/share/privacy cards: `15–16px`
- suggestion cards: `10px`
- option rows: `8px`
- publish button: pill

---

# 38. Icon style

Use thin rounded outline icons.

Recommended icon libraries:

- Lucide
- Phosphor
- Heroicons Outline

Suggested icon equivalents:

```text
X
Upload
Dumbbell / Activity
Utensils / Meal
Images / Layers
Check
House
Camera
Trophy
User
```

---

# 39. Responsive implementation guidance

The screenshot width is approximately `262px`, narrower than a standard modern mobile CSS viewport.

For a `390px` viewport:

```text
390 / 262 ≈ 1.49
```

Do not blindly scale every element. Preserve the relative proportions and use responsive width-based layout.

Recommended shell:

```css
.app-shell {
  width: 100%;
  max-width: 430px;
  min-height: 100vh;
  margin: 0 auto;
  background: #09060f;
}
```

Recommended main content:

```css
.post-content {
  padding: 0 18px 70px;
}
```

Main cards should use:

```css
width: 100%;
```

Quick suggestions:

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 10px;
```

---

# 40. Recommended component hierarchy

```text
CreatePostPage
├── CreatePostHeader
│   ├── CloseButton
│   ├── Title
│   └── PublishButton
│
├── PhotoUploadArea
│   ├── UploadIcon
│   ├── UploadTitle
│   └── UploadSubtitle
│
├── QuickSuggestions
│   ├── SuggestionCard(Treino do dia)
│   ├── SuggestionCard(Refeição)
│   └── SuggestionCard(Progresso)
│
├── CaptionSection
│   ├── Label
│   ├── Textarea
│   └── CharacterCounter
│
├── ShareDestinationsCard
│   ├── Title
│   ├── ShareOption(Meu Feed, selected)
│   ├── ShareOption(Comunidade Fitness, selected)
│   ├── ShareOption(Desafio 30 Dias, unselected)
│   └── ShareOption(Corrida Matinal, unselected)
│
├── PrivacyNotice
│
└── BottomNavigation
    ├── Home
    ├── Câmera
    ├── Feed [active]
    └── Perfil
```

---

# 41. Exact visible text inventory

Use these strings exactly:

```text
Criar publicação

Publicar

Adicionar foto

Toque para escolher da galeria

Sugestões rápidas

Treino do dia

Refeição

Progresso

Legenda

Escreva sobre sua jornada...

0/500 caracteres

Compartilhar em

Meu Feed

Comunidade Fitness

Desafio 30 Dias

Corrida Matinal

Suas fotos de progresso são processadas sem filtros para
garantir autenticidade. Configure suas preferências de
privacidade nas configurações.

Home

Câmera

Feed

Perfil
```

---

# 42. Important visual characteristics to preserve

For close reproduction, preserve the following:

1. The background is **almost black with a purple tint**.
2. The header uses three-part alignment: close button, centered title, publish button.
3. The publish button is a **small purple pill**, not a full-width CTA.
4. The photo area is a **large dashed rounded rectangle**.
5. The upload icon sits inside a violet rounded square.
6. The upload prompt is centered both horizontally and vertically.
7. Quick suggestions are three equally sized cards.
8. Each quick suggestion uses a violet icon tile.
9. The caption field is large and empty with muted placeholder text.
10. The character counter sits below the textarea and is left aligned.
11. The share destinations are grouped in one rounded card.
12. Selected options use a **purple filled row with checked circle**.
13. Unselected options use a darker neutral row with an empty outlined circle.
14. The privacy note uses a stronger purple tint and border than ordinary cards.
15. The bottom navigation is dark and fixed.
16. **Feed** is the active violet tab.
17. Typography should stay compact; do not enlarge labels excessively.
18. Keep consistent rounded corners and subtle borders throughout.

---

# 43. Visual hierarchy

The intended visual attention order is:

```text
Criar publicação
↓
photo upload area
↓
quick suggestions
↓
caption input
↓
sharing options
↓
privacy note
↓
bottom navigation
```

The screen should feel like a **premium dark social-post composer for a fitness/wellness app**, with the photo upload area acting as the main focus and the rest of the form progressively guiding the user toward publishing.
