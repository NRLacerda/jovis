# JOVIS Dashboard — UI Reconstruction Description

## 1. Overall page

**Screenshot viewport:** `270px × 863px`

The image shows a **mobile dashboard/home screen** for the JOVIS app. The interface uses a very dark purple-black background, compact cards, violet brand accents, and small colored category/status icons.

The screen is vertically scrollable in concept, but the screenshot shows the complete visible home view including a **fixed bottom navigation bar**.

Recommended semantic structure:

```text
<body>
  <div class="app-shell">
    <header class="top-header">
      <div class="brand-and-greeting">
        logo
        greeting
        subtitle
      </div>

      <div class="header-actions">
        notification-button
        profile-avatar
      </div>
    </header>

    <main class="dashboard">
      <section class="scan-card">
        scan-copy
        camera-action-button
      </section>

      <section class="stats-grid">
        consistency-card
        evolution-score-card
      </section>

      <section class="challenge-card">
        challenge-label
        challenge-title
        challenge-progress-text
        progress-bar
      </section>

      <section class="communities">
        section-title
        community-card × 3
      </section>

      <section class="quick-feed">
        section-title
        feed-card × 2
      </section>
    </main>

    <nav class="bottom-navigation">
      nav-item × 4
    </nav>
  </div>
</body>
```

---

## 2. Global visual style

The design is a **dark fitness / wellness / AI dashboard**.

Key characteristics:

- nearly black purple-tinted page background
- slightly lighter purple-black cards
- thin violet borders around most cards
- white primary text
- muted lavender-gray secondary text
- saturated purple as the main brand/accent color
- small secondary accent colors:
  - green for nutrition/progress
  - blue for running/location
  - red/coral for one feed avatar
  - cyan/blue for another feed avatar

The UI is dense but orderly, with approximately `10px` horizontal page padding at the screenshot scale.

---

## 3. Approximate color palette

Colors sampled/estimated from the screenshot:

```css
:root {
  --bg: #0a0513;

  --surface-dark: #140f1c;
  --surface: #1a1324;
  --surface-strong: #1c1427;

  --border: #342044;
  --border-subtle: #2b1b39;

  --text-primary: #ffffff;
  --text-secondary: #aaa3b3;
  --text-muted: #8d8598;

  --purple: #a93cff;
  --purple-mid: #9334ec;
  --purple-dark: #6d24cf;
  --purple-soft: #5d2a7c;

  --green: #20d68a;
  --green-dark: #084f35;

  --blue: #2d9cf6;
  --blue-dark: #123d6a;

  --red: #ff5969;
}
```

The exact sampled background from large empty regions is close to:

```css
#0a0513
```

The most common card surface is close to:

```css
#1a1324
```

The large scan card is slightly darker, close to:

```css
#140f1c
```

---

## 4. Global typography

Use a clean modern sans-serif.

Good approximations:

```css
font-family:
  Inter,
  "SF Pro Display",
  "SF Pro Text",
  Arial,
  sans-serif;
```

The design uses:

- bold white text for headings and metrics
- regular white/light-gray text for body copy
- small muted lavender-gray text for metadata
- compact line heights

Suggested base:

```css
body {
  font-family: Inter, Arial, sans-serif;
  color: #fff;
  background: #0a0513;
}
```

Because the source screenshot is only `270px` wide, font sizes below refer to the screenshot scale. For a conventional `390–430px` CSS viewport, multiply most dimensions by approximately `1.4–1.55`.

---

## 5. Page shell

Approximate visible content width:

```text
x: 10px → 250px
```

Most sections use:

```css
margin-left: 10px;
margin-right: 20px;
```

or roughly:

```css
padding-inline: 10px 20px;
```

The right edge of the image contains a thin light-gray vertical strip. This appears to be a screenshot/device-frame artifact rather than part of the intended app UI and should normally **not** be recreated.

The same applies to the thin gray line along the very top edge.

---

## 6. Header

Approximate area:

```text
x: 10px → 250px
y: 26px → 84px
```

The header has two main columns:

```css
display: flex;
justify-content: space-between;
align-items: flex-start;
```

Left side contains:

1. JOVIS logo
2. greeting
3. small motivational subtitle

Right side contains:

1. notification/bell button
2. circular user avatar

---

## 7. JOVIS logo

Approximate position:

```text
x: 10px
y: 28px
```

Visible text:

> **JOVIS**

The logo is very small compared with the previous landing page.

Approximate typography:

```css
font-size: 10px;
font-weight: 800;
letter-spacing: -0.3px;
```

Color treatment:

- `"JO"` / most of the logo: white
- final brand letters: violet/purple

Approximation:

```html
<div class="brand">
  <span>JO</span><span class="brand-purple">VIS</span>
</div>
```

---

## 8. Greeting block

Approximate position:

```text
x: 10px
top: 50px
```

Primary greeting:

> **Olá, Carlos 👋**

Approximate typography:

```css
font-size: 14px;
font-weight: 500;
line-height: 1.2;
color: #fff;
```

The waving-hand emoji appears immediately after `"Carlos"`.

Secondary line:

> Foco hoje, resultado amanhã.

Approximate position:

```text
top: 75px
```

Approximate typography:

```css
font-size: 9px;
font-weight: 400;
color: #a39baa;
```

---

## 9. Notification button

Approximate center:

```text
x: 203px
y: 38px
```

Approximate size:

```text
27px × 27px
```

Shape:

```css
border-radius: 50%;
background: #1b1228;
border: 1px solid #342044;
```

Icon:

- white bell outline
- centered
- approximately `12–14px`

No badge/count is visible.

---

## 10. Profile avatar

Approximate center:

```text
x: 236px
y: 38px
```

Approximate size:

```text
27px × 27px
```

Perfect circle.

Background:

```css
background: linear-gradient(135deg, #ad36ff, #7d2eea);
```

Text:

> **CA**

Text styling:

```css
font-size: 8px;
font-weight: 600;
color: white;
```

The avatar has no image; it is an initials avatar.

---

# 11. Main scan / camera card

Approximate bounds:

```text
x: 10px
y: 114px
width: 240px
height: 108px
```

The card is wider than every other card.

Style:

```css
.scan-card {
  background: #140f1c;
  border: 1px solid #30203e;
  border-radius: 16px;
  padding: 16px;
}
```

Layout:

```css
display: flex;
justify-content: space-between;
align-items: flex-start;
```

The left side contains text.  
The right side contains a circular purple camera button.

---

## 12. Scan-card title

Exact visible text:

> **Pronto para escanear**  
> **algo novo?**

Approximate position:

```text
x: 26px
y: 134px
```

Approximate typography:

```css
font-size: 16px;
font-weight: 750;
line-height: 1.25;
letter-spacing: -0.3px;
color: #fff;
```

The title wraps into exactly two lines.

---

## 13. Scan-card description

Exact visible text:

> Use a câmera para analisar alimentos e  
> acompanhar sua evolução.

Approximate position:

```text
x: 26px
top: 178px
```

Approximate typography:

```css
font-size: 8.5px;
font-weight: 400;
line-height: 1.45;
color: #b1a9b8;
```

The copy is two lines.

---

## 14. Camera action button

Approximate bounds:

```text
x: 196px
y: 133px
width: 43px
height: 43px
```

Circular button.

```css
width: 43px;
height: 43px;
border-radius: 50%;
background: linear-gradient(135deg, #b13dff, #7c2ee5);
```

Icon:

- white camera outline
- approximately `20px`
- centered

The icon resembles a compact line-style camera with a circular lens.

---

# 15. Statistics grid

Starts approximately:

```text
y: 238px
```

Two cards in one row.

Grid:

```css
display: grid;
grid-template-columns: 1fr 1fr;
gap: 10px;
```

Approximate card widths:

```text
left card: 115px
right card: 115px
```

Approximate height:

```text
113px
```

Both cards share:

```css
background: #1a1324;
border: 1px solid #382049;
border-radius: 11px;
```

---

# 16. Consistency card

Approximate bounds:

```text
x: 10px
y: 238px
width: 115px
height: 113px
```

The content is centered.

### Circular progress ring

Approximate center:

```text
x: 68px
y: 281px
```

Approximate diameter:

```text
57px
```

The ring has:

- thick violet stroke
- dark center
- nearly complete circular progress
- a small gap near the upper-right/top region

Approximation:

```css
background:
  conic-gradient(
    #b144f5 0deg 356deg,
    #3a2648 356deg 360deg
  );
```

Use a centered pseudo-element to create the hollow center.

Ring thickness approximately:

```text
6px
```

Centered metric:

> **99%**

Typography:

```css
font-size: 15px;
font-weight: 800;
color: #fff;
```

Label below:

> Consistência

Approximate typography:

```css
font-size: 8px;
font-weight: 400;
color: #a9a1ae;
```

---

# 17. Evolution Score card

Approximate bounds:

```text
x: 135px
y: 238px
width: 115px
height: 113px
```

Centered metric:

> **86**

Approximate typography:

```css
font-size: 16px;
font-weight: 750;
color: #fff;
```

Directly beneath:

> /100

Approximate typography:

```css
font-size: 8px;
color: #9c94a4;
```

Below the metric is a small **purple bar-chart / equalizer icon**.

The icon consists of approximately **7 narrow rounded vertical bars** of varying heights.

Approximate dimensions:

```text
43px wide
18px high
```

Colors are violet/magenta, possibly with minor shade variation.

Label underneath:

> Evolution Score

Approximate typography:

```css
font-size: 8px;
color: #a9a1ae;
```

---

# 18. Active challenge card

Approximate bounds:

```text
x: 10px
y: 367px
width: 240px
height: 97px
```

Card style:

```css
background: #1a1324;
border: 1px solid #382049;
border-radius: 11px;
padding: 14px;
```

### Small status label

Text:

> Desafio ativo

Approximate color:

```css
color: #b74cff;
```

Approximate typography:

```css
font-size: 8px;
font-weight: 500;
```

### Challenge title

Text:

> **7 dias de alimentação limpa**

Approximate typography:

```css
font-size: 11px;
font-weight: 500;
color: #fff;
```

### Progress caption

Text:

> 5/7 dias concluídos

Approximate typography:

```css
font-size: 8px;
color: #aaa1b0;
```

---

## 19. Challenge progress bar

Approximate position:

```text
x: 24px
y: 444px
width: 212px
height: 5px
```

Track:

```css
height: 5px;
border-radius: 999px;
background: #393142;
overflow: hidden;
```

Progress fill appears approximately `71%` wide, consistent with `5/7`.

The fill uses a left-to-right gradient:

```css
background: linear-gradient(
  90deg,
  #20d991 0%,
  #4dcbce 35%,
  #8b39f3 70%,
  #b62cff 100%
);
```

This is one of the few elements combining green/cyan and violet.

---

# 20. Communities section

Approximate title position:

```text
x: 10px
y: 484px
```

Section heading:

> **Comunidades em destaque**

Approximate typography:

```css
font-size: 11px;
font-weight: 500;
color: #fff;
```

The community-card row begins around:

```text
y: 506px
```

Three equal cards.

Grid:

```css
display: grid;
grid-template-columns: repeat(3, 1fr);
gap: 7px;
```

Each card is approximately:

```text
75px × 81px
```

Card style:

```css
background: #1a1324;
border: 1px solid #382049;
border-radius: 9px;
padding: 10px;
```

Content is left aligned.

---

# 21. Community card 1 — Hipertrofia

Approximate bounds:

```text
x: 10px
y: 507px
width: 75px
height: 80px
```

Icon container:

```text
26px × 26px
```

Circular/dark-violet icon background.

Approximate color:

```css
background: #44205e;
```

Icon:

- purple flame
- centered

Title:

> Hipertrofia

Approximate typography:

```css
font-size: 8px;
font-weight: 500;
color: #fff;
```

Count:

> 2.4k

Approximate typography:

```css
font-size: 7px;
color: #9e96a5;
```

---

# 22. Community card 2 — Dieta

Approximate bounds:

```text
x: 93px
y: 507px
width: 75px
height: 80px
```

Icon container:

```css
background: #063e2c;
```

Icon:

- bright green fork-and-knife / nutrition symbol

Title:

> Dieta

Count:

> 1.8k

---

# 23. Community card 3 — Corrida

Approximate bounds:

```text
x: 176px
y: 507px
width: 74px
height: 80px
```

Icon container:

```css
background: #15375c;
```

Icon:

- blue map-pin/location-style symbol with circular center

Title:

> Corrida

Count:

> 3.1k

---

# 24. Quick feed section

Section title appears around:

```text
x: 10px
y: 607px
```

Text:

> **Feed rápido**

Approximate typography:

```css
font-size: 11px;
font-weight: 500;
color: #fff;
```

Two vertically stacked feed cards follow.

---

# 25. Feed card global style

Each feed item is a full-width rounded card.

Approximate width:

```text
240px
```

Style:

```css
background: #1a1324;
border: 1px solid #382049;
border-radius: 10px;
padding: 11px;
```

Internal structure:

```text
avatar | user-name                         timestamp
       | post line 1
       | post line 2
       | heart reaction count
```

The avatar sits at the upper-left.

Text content begins approximately `34px` to the right of the card's left edge.

---

# 26. Feed card 1

Approximate bounds:

```text
x: 10px
y: 631px
width: 240px
height: 84px
```

Avatar:

```text
26px diameter
```

Color:

```css
background: #ff5969;
```

Initials:

> MR

White text.

Username:

> **Maria Rodrigues**

Approximate typography:

```css
font-size: 8px;
font-weight: 500;
color: white;
```

Timestamp in upper-right:

> 2h

Approximate typography:

```css
font-size: 7px;
color: #9b93a1;
```

Post text:

> Consegui bater minha meta de 10k hoje!  
> Quem mais está no desafio?

Approximate typography:

```css
font-size: 8px;
line-height: 1.35;
color: #f0edf2;
```

Reaction row:

- purple outline heart icon
- count: `24`

Approximate icon size:

```text
10px
```

Reaction text color:

```css
color: #b85cff;
```

---

# 27. Feed card 2

Approximate bounds:

```text
x: 10px
y: 722px
width: 240px
height: 84px
```

Avatar:

```text
26px diameter
```

Color:

```css
background: #2498ed;
```

Initials:

> PS

Username:

> **Pedro Silva**

Timestamp:

> 5h

Post text:

> Dica: adicionem abacate no shake pós-treino.  
> Mudou tudo!

Reaction row:

- purple outline heart icon
- count: `18`

---

# 28. Bottom navigation

Approximate bounds:

```text
x: 0px
y: 812px
width: 267px
height: 51px
```

The navigation is visually fixed to the bottom.

Background:

```css
background: #09050f;
```

Top divider:

```css
border-top: 1px solid #1d1723;
```

Layout:

```css
display: grid;
grid-template-columns: repeat(4, 1fr);
align-items: center;
```

Each item contains:

```text
icon
label
```

Icons are about `14px`.

Labels are about `7px`.

Items:

1. **Home**
2. **Câmera**
3. **Feed**
4. **Perfil**

---

## 29. Bottom navigation active state

The **Home** tab is active.

Active icon:

- outlined house
- violet/purple

Active label:

> Home

Color:

```css
color: #b04cff;
```

The remaining tabs use muted gray/lavender:

```css
color: #81798c;
```

No pill or colored background is used for the selected item.

---

# 30. Bottom navigation icon descriptions

### Home

Icon:

- outline house
- simple roof shape
- purple when active

### Câmera

Icon:

- small outline camera
- muted gray

### Feed

Icon:

- outline speech/community/feed symbol
- visually resembles stacked/chat/network lines
- muted gray

### Perfil

Icon:

- single-person outline
- muted gray

---

# 31. Approximate vertical layout map

```text
0       Screenshot start / frame artifact

28      JOVIS logo
50      Greeting
75      Header subtitle

114     Scan card begins
222     Scan card ends

238     Statistics cards begin
351     Statistics cards end

367     Challenge card begins
464     Challenge card ends

484     "Comunidades em destaque"
507     Community cards begin
588     Community cards end

607     "Feed rápido"

631     Feed card 1 begins
715     Feed card 1 ends

722     Feed card 2 begins
806     Feed card 2 ends

812     Bottom navigation begins
863     Screenshot ends
```

---

# 32. Approximate horizontal layout map

```text
0       screenshot edge
10      primary content left margin

10–250  main full-width cards

Stats:
10–125   left stat card
135–250  right stat card

Communities:
10–85    Hipertrofia
93–168   Dieta
176–250  Corrida

267–269  screenshot/device-frame gray strip
```

---

# 33. Border radii

Useful approximations:

```css
--radius-large: 16px;   /* scan card */
--radius-card: 10px;    /* dashboard cards */
--radius-small: 8px;    /* small community cards */
--radius-pill: 999px;   /* progress bar */
```

Statistics/challenge/feed cards are around `10–12px`.

The main scan card is visibly more rounded, around `16px`.

---

# 34. Spacing system

A practical screenshot-scale spacing system:

```css
--space-1: 4px;
--space-2: 7px;
--space-3: 10px;
--space-4: 14px;
--space-5: 20px;
```

Common usage:

- page horizontal inset: `10px`
- grid gap: `7–10px`
- card inner padding: `11–16px`
- section-title to cards: `10–12px`
- major section spacing: `16–20px`

---

# 35. Icon style

Most icons are **thin outline icons** with rounded line caps.

Recommended icon families:

- Lucide
- Phosphor
- Heroicons outline

Likely equivalents:

```text
Bell
Camera
Flame
Utensils
MapPin
Heart
House
User
```

The Evolution Score graphic should be custom bars rather than a generic line-chart icon.

---

# 36. Responsive implementation guidance

The screenshot is only `270px` wide, which is narrower than a normal modern phone CSS viewport.

If recreating this at `390px` width, preserve proportions rather than literally using all screenshot pixel sizes.

Approximate scale factor:

```text
390 / 270 ≈ 1.44
```

For example:

```text
screenshot card width 240px
→ roughly 346px at a 390px viewport
```

A useful container:

```css
.app-shell {
  width: 100%;
  max-width: 430px;
  min-height: 100vh;
  margin: 0 auto;
  background: #0a0513;
  color: #fff;
}
```

Main content can use:

```css
.dashboard {
  padding: 0 14px 72px;
}
```

At conventional phone scale, use a bottom padding large enough to avoid content being covered by the fixed navigation.

---

# 37. Recommended component hierarchy

```text
App
├── Header
│   ├── Brand
│   ├── Greeting
│   ├── NotificationButton
│   └── Avatar
│
├── Dashboard
│   ├── ScanPromptCard
│   │   └── CameraButton
│   │
│   ├── StatsGrid
│   │   ├── ConsistencyCard
│   │   │   └── CircularProgress
│   │   └── EvolutionScoreCard
│   │       └── MiniBarChart
│   │
│   ├── ChallengeCard
│   │   └── ProgressBar
│   │
│   ├── CommunitySection
│   │   ├── CommunityCard(Hipertrofia)
│   │   ├── CommunityCard(Dieta)
│   │   └── CommunityCard(Corrida)
│   │
│   └── QuickFeed
│       ├── FeedCard(Maria Rodrigues)
│       └── FeedCard(Pedro Silva)
│
└── BottomNavigation
    ├── Home
    ├── Câmera
    ├── Feed
    └── Perfil
```

---

# 38. Exact visible text inventory

Use these strings exactly when reconstructing the screenshot:

```text
JOVIS

Olá, Carlos 👋
Foco hoje, resultado amanhã.

Pronto para escanear
algo novo?

Use a câmera para analisar alimentos e
acompanhar sua evolução.

99%
Consistência

86
/100
Evolution Score

Desafio ativo
7 dias de alimentação limpa
5/7 dias concluídos

Comunidades em destaque

Hipertrofia
2.4k

Dieta
1.8k

Corrida
3.1k

Feed rápido

Maria Rodrigues
2h
Consegui bater minha meta de 10k hoje!
Quem mais está no desafio?
24

Pedro Silva
5h
Dica: adicionem abacate no shake pós-treino.
Mudou tudo!
18

Home
Câmera
Feed
Perfil
```

---

# 39. Important visual characteristics to preserve

The following features are essential for visual similarity:

1. **Very dark purple-black background**, not neutral black.
2. **Cards are only slightly brighter than the page background.**
3. **Purple borders are subtle**, never bright neon outlines.
4. The main scan card is **wider, larger, and darker** than the statistic cards.
5. The circular camera CTA should be a **high-saturation violet focal point**.
6. The `99%` circular metric must use a **thick purple ring**.
7. The Evolution Score card must use the **small vertical equalizer/bar graphic**.
8. The challenge progress bar must transition from **green/cyan into purple**.
9. Community cards use **different accent colors by category**.
10. Feed avatars use solid bright colors and initials rather than photos.
11. The bottom navigation is **fixed, very dark, and understated**.
12. Only the active Home icon/label is violet.
13. Typography remains compact; avoid oversized dashboard text.
14. Cards maintain narrow gaps and a dense mobile-dashboard rhythm.

---

# 40. Visual hierarchy

The page's intended hierarchy is:

```text
Greeting
↓
Large scan prompt
↓
Daily statistics
↓
Active challenge
↓
Community discovery
↓
Social feed
↓
Persistent bottom navigation
```

Within the interface, the strongest visual accents are:

```text
purple camera CTA
→ 99% progress ring
→ Evolution Score bar chart
→ challenge progress gradient
→ community icons
→ feed avatars
```

The page should feel like a **premium dark wellness/fitness app dashboard with AI-assisted food scanning and social/community functionality**.
