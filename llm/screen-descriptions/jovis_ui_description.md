# JOVIS Landing Page — UI Reconstruction Description

## 1. Overall page

**Viewport shown:** `420px × 936px`

The page is a **mobile-first landing page** for a product called **JOVIS**. It uses a very dark, almost black background with purple accents and a futuristic/AI/technology visual style.

```text
<body>
  <header>
    logo
    hamburger-menu
  </header>

  <main>
    <hero-visual>
      floating-icon
      floating-icon
      camera-lens
      floating-icon
      floating-icon
    </hero-visual>

    <hero-copy>
      headline
      description
      CTA button
    </hero-copy>

    <feature-grid>
      feature-card × 4
    </feature-grid>
  </main>
</body>
```

There is no visible footer in the screenshot.

---

## 2. Global visual style

### Background

The entire screen uses an extremely dark purple-black background.

Approximate base color:

```css
background: #05030e;
```

It is not pure black. There is a subtle purple tint throughout.

There are also localized purple glows around the central lens and CTA.

### Main palette

Approximate colors:

```css
--bg: #05030e;

--surface: #121119;
--surface-border: #292532;

--text-primary: #ffffff;
--text-secondary: #98949f;

--purple-light: #ad43ff;
--purple: #9138f4;
--purple-dark: #7130dd;

--icon-bg: #39204f;
--icon: #eee6ff;
```

The strongest brand element is a **purple/violet gradient**.

A suitable approximation:

```css
background: linear-gradient(
  90deg,
  #ad45ff 0%,
  #9137f4 50%,
  #7531e5 100%
);
```

---

## 3. Header

Approximate bounds:

```text
x: 20 → 393
y: 25 → 58
height: ~34px
```

Header layout:

```css
display: flex;
align-items: center;
justify-content: space-between;
padding: 24px 20px 0;
```

### Logo

Position approximately:

```text
x: 20px
y: 27px
```

Text:

**JOVIS**

Appearance:

- uppercase
- heavy/bold sans-serif
- approximately `32px`
- line-height around `1`
- tight letter spacing
- first part white
- final letters use purple gradient

A close CSS implementation:

```html
<div class="logo">
  <span>JO</span><span class="gradient-text">VIS</span>
</div>
```

```css
.logo {
  font-size: 32px;
  font-weight: 800;
  letter-spacing: -1.5px;
}
```

The purple begins around the **V**.

### Hamburger icon

Position:

```text
center ≈ x384px / y46px
```

Three horizontal lines:

- white/light gray
- about `18px` wide
- around `2px` thick
- gap approximately `4px`

It has no surrounding button container.

Approximate size:

```css
width: 18px;
height: 15px;
```

---

## 4. Hero visual / camera section

This occupies roughly:

```text
y: 112px → 328px
```

The visual is centered horizontally.

### Main camera lens

The central visual is a **large realistic camera lens** viewed directly from the front.

Approximate center:

```text
x: 208px
y: 216px
```

Approximate visible size:

```text
width: 180–190px
height: 180–190px
```

The lens consists of:

- black outer circular body
- several concentric metallic rings
- internal glossy glass layers
- purple reflections
- extremely dark central pupil
- multiple curved violet highlights
- subtle metallic gray details around the rim

The outer edge has a **purple glow**.

Approximation:

```css
filter:
  drop-shadow(0 0 8px rgba(145, 50, 245, .75))
  drop-shadow(0 0 24px rgba(145, 50, 245, .35));
```

Behind the lens is a larger diffuse violet halo.

Approximately:

```css
.hero-lens::before {
  content: "";
  position: absolute;
  inset: -25px;
  border-radius: 50%;
  background: radial-gradient(
    circle,
    rgba(143, 45, 255, .35),
    rgba(143, 45, 255, .08) 50%,
    transparent 72%
  );
  filter: blur(8px);
}
```

The photographic lens image itself has a transparent background.

---

## 5. Floating icon buttons around lens

There are **four floating rounded-square controls** positioned around the lens.

They are approximately:

```text
43–45px × 43–45px
```

with roughly:

```css
border-radius: 13px;
background: rgba(25, 17, 35, 0.85);
border: 1px solid rgba(155, 90, 205, .25);
```

They have subtle purple shadows/glows.

### Top-left

Position:

```text
x ≈ 114px
y ≈ 118px
size ≈ 44 × 44px
```

Icon: **camera outline**

White/light lavender line icon.

### Top-right

Position:

```text
x ≈ 250px
y ≈ 118px
size ≈ 44 × 44px
```

Icon: **sparkle / AI stars**

Approximately three stylized four-point sparkles.

### Bottom-left

Position:

```text
x ≈ 103px
y ≈ 269px
size ≈ 44 × 44px
```

Icon: **community / users**

Two stylized human outlines.

### Bottom-right

Position:

```text
x ≈ 263px
y ≈ 281px
size ≈ 44 × 44px
```

Icon: **upward growth/chart arrow**

A zigzag diagonal line ending in an arrow.

---

## 6. Hero headline

Starts approximately at:

```text
y: 362px
```

Centered horizontally.

Text:

> **Veja sua evolução**  
> **acontecer.**

Exact line arrangement:

```text
Veja sua evolução
acontecer.
```

The first line occupies almost the entire available width.

Approximate typography:

```css
font-family: Inter, Arial, sans-serif;
font-size: 39px;
font-weight: 800;
line-height: 1.08;
letter-spacing: -1.4px;
text-align: center;
```

Approximate width:

```css
max-width: 350px;
margin-inline: auto;
```

Colors:

- `"Veja sua"` → white
- `"evolução"` → purple/violet gradient
- `"acontecer."` → white

The gradient word is the main visual emphasis.

Example:

```css
.gradient-text {
  background: linear-gradient(90deg, #b344ff, #7138ec);
  background-clip: text;
  -webkit-background-clip: text;
  color: transparent;
}
```

---

## 7. Hero description

Position:

```text
top ≈ 468px
```

Text:

> Plataforma de evolução pessoal com câmera  
> inteligente, comunidades e performance.

Exactly two centered lines in the screenshot.

Approximate typography:

```css
font-size: 15px;
font-weight: 400;
line-height: 1.45;
text-align: center;
color: #97939e;
```

Width:

```css
max-width: 320px;
```

The text is subdued and significantly dimmer than the heading.

---

## 8. Main CTA button

Position approximately:

```text
x: 70px
y: 541px
width: 280px
height: 53px
```

Text:

**Começar agora**

Button appearance:

```css
height: 53px;
border-radius: 27px;
border: none;
```

Gradient:

```css
background: linear-gradient(
  90deg,
  #aa43ff 0%,
  #9138f5 50%,
  #7530e3 100%
);
```

There is a strong purple glow underneath/around it:

```css
box-shadow:
  0 6px 24px rgba(145, 48, 240, .42),
  0 0 18px rgba(145, 48, 240, .22);
```

Typography:

```css
font-size: 16px;
font-weight: 700;
color: white;
```

There is approximately `32px` of space between the description and the CTA.

---

## 9. Feature card grid

The feature section begins around:

```text
y: 633px
```

It has **two columns and two rows**.

Outer horizontal margin:

```text
30px
```

Column gap:

```text
12px
```

Approximate card width:

```text
174px
```

Result:

```text
30 + 174 + 12 + 174 + 30 = 420
```

Grid:

```css
.feature-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 12px;
  margin: 39px 30px 0;
}
```

First row height approximately:

```text
145px
```

Second row approximately:

```text
140px
```

---

## 10. Card styling

Each feature card has:

```css
background: #121119;
border: 1px solid #292632;
border-radius: 19px;
```

There is almost no obvious drop shadow. The distinction is primarily from the slightly lighter dark surface and thin border.

Approximate padding:

```css
padding: 16px;
```

All content is left aligned.

Card internal structure:

```text
[ icon ]

Feature title
Secondary description
```

The icon is positioned at the upper-left.

---

## 11. Feature card icon containers

Each card has a purple rounded-square icon container.

Approximate dimensions:

```text
36 × 36px
```

Appearance:

```css
.icon-box {
  width: 36px;
  height: 36px;
  border-radius: 10px;
  background: #39204f;
}
```

Icons themselves:

```css
width: 20px;
height: 20px;
stroke: #f2eaff;
stroke-width: ~1.7px;
```

The icons correspond directly to the floating icons around the hero camera.

---

## 12. Card 1

Position approximately:

```text
x: 30px
y: 633px
width: 174px
height: 145px
```

Icon: **camera outline**

Title:

> **Câmera inteligente**

Description:

> Capture sua jornada com  
> facilidade

Typography:

```css
font-size: 14px;
font-weight: 700;
line-height: 1.3;
color: #fff;
```

Description:

```css
font-size: 12.5px;
font-weight: 400;
line-height: 1.45;
color: #8f8a96;
```

---

## 13. Card 2

Position approximately:

```text
x: 216px
y: 633px
width: 174px
height: 145px
```

Icon: **AI sparkle/stars**

Title:

> **IA que se adapta e**  
> **aprende**

Description:

> Feedback personalizado

The title intentionally wraps after `"e"`.

---

## 14. Card 3

Position:

```text
x: 30px
y: 790px
width: 174px
height: ~140px
```

Icon: **two users/community**

Title:

> **Comunidade ativa**

Description:

> Evolua junto com a  
> comunidade

---

## 15. Card 4

Position:

```text
x: 216px
y: 790px
width: 174px
height: ~140px
```

Icon: **growth / rising arrow**

Title:

> **Evolução real**

Description:

> Veja seu progresso

---

## 16. Approximate vertical spacing

```text
0      Page start

27     Logo top
38     Hamburger top

118    Upper floating icons
128    Camera lens begins
216    Lens center
305    Lens ends
325    Floating visual region ends

365    Heading starts
441    Heading ends

468    Description starts
504    Description ends

541    CTA starts
594    CTA ends

633    Feature grid starts
778    First card row ends

790    Second card row starts
930    Cards end

936    Screenshot end
```

---

## 17. Recommended responsive container

Although the screenshot is exactly `420px` wide, the design should probably behave as a centered mobile container on larger screens.

```css
body {
  margin: 0;
  background: #05030e;
  color: #fff;
  font-family: Inter, Arial, sans-serif;
}

.page {
  width: 100%;
  max-width: 420px;
  min-height: 100vh;
  margin: 0 auto;
  overflow: hidden;
}
```

The header can use `20px` horizontal padding, while the card section uses `30px`.

---

## 18. Important visual characteristics to preserve

The composition relies heavily on **symmetry and center alignment** in the upper 60% of the page.

The camera lens must be the dominant decorative object, while the four icons orbit it asymmetrically but remain visually balanced.

The background should remain nearly black; making it ordinary gray or navy would noticeably change the design.

The headline should be very bold and compact, with `"evolução"` being the only colored word.

The CTA needs a stronger glow than any of the cards.

Cards should remain relatively flat and understated, using only a slightly lighter dark surface and thin purple-gray border.

The overall hierarchy is:

**camera lens → headline → CTA → feature cards → description text.**

For font matching, **Inter**, **SF Pro Display**, **Manrope**, or a similar modern geometric sans-serif will work, with **Inter 800** being a particularly close starting point.
