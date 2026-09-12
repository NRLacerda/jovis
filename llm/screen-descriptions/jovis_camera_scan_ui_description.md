# JOVIS Smart Coach Vision — Camera Scan Screen UI Reconstruction Description

## 1. Overall page

**Screenshot viewport:** `259px × 594px`

The screen is a **mobile camera-scanning interface** for the JOVIS app.

It uses the same dark JOVIS visual language as the dashboard:

- nearly black purple-tinted background
- violet branding
- white primary text
- muted gray-blue navigation icons
- bright purple scan frame
- central white capture button
- fixed bottom navigation

The main purpose of the screen is to scan a **nutrition label** using the camera.

Recommended semantic structure:

```text
<body>
  <div class="app-shell">

    <header class="camera-header">
      logo
      title
    </header>

    <main class="camera-screen">

      <section class="camera-preview">
        scan-status-pill

        camera-grid

        scan-target>
          corner-marker × 4
          focus-icon
          scan-instruction
        </scan-target>
      </section>

      <section class="capture-controls">
        gallery-button
        shutter-button
        camera-mode-button
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

The page is minimalist and camera-focused.

Primary visual hierarchy:

```text
JOVIS brand
↓
Smart Coach Vision
↓
large camera preview
↓
purple scan target
↓
capture controls
↓
bottom navigation
```

The camera area is much larger than any other component and dominates the center of the screen.

---

## 3. Approximate color palette

Recommended colors:

```css
:root {
  --bg: #08050d;

  --camera-bg-top: #0d1420;
  --camera-bg-bottom: #02060d;

  --text-primary: #ffffff;
  --text-secondary: #9a94a3;

  --purple: #b03dff;
  --purple-light: #c663ff;
  --purple-dark: #7825d6;

  --scan-fill: rgba(95, 20, 145, 0.24);

  --control-bg: #1a1920;
  --control-border: #4b4853;

  --nav-inactive: #788396;
  --nav-active: #c15bff;

  --divider: #211b28;
}
```

Base page background is approximately:

```css
background: #08050d;
```

---

## 4. Global typography

Use a modern sans-serif such as:

```css
font-family:
  Inter,
  "SF Pro Display",
  "SF Pro Text",
  Arial,
  sans-serif;
```

The screen uses:

- bold typography for product title
- white text for important labels
- compact small text for scan status and navigation
- very small centered instruction text inside the scan target

---

## 5. App shell

Approximate full-screen structure:

```css
.app-shell {
  width: 100%;
  max-width: 430px;
  min-height: 100vh;
  margin: 0 auto;
  background: #08050d;
  color: #fff;
  overflow: hidden;
}
```

The screenshot includes a thin gray strip on the far left edge and a dark border on the far right. These appear to be screenshot/device-frame artifacts and should normally **not** be recreated.

---

# 6. Header

Approximate vertical region:

```text
y: 38px → 77px
```

The entire header is centered horizontally.

It contains:

1. JOVIS logo
2. subtitle/title `"Smart Coach Vision"`

There are no visible back buttons, menus, notifications, or profile controls on this screen.

---

## 7. JOVIS logo

Approximate position:

```text
center-x: 135px
top: 38px
```

Text:

> **JOVIS**

Approximate typography:

```css
font-size: 20px;
font-weight: 800;
letter-spacing: -0.5px;
line-height: 1;
```

Color treatment:

- `JO` / white portion: `#ffffff`
- `VIS` / violet portion: purple gradient

Suggested implementation:

```html
<div class="logo">
  <span>JO</span><span class="logo-accent">VIS</span>
</div>
```

```css
.logo-accent {
  background: linear-gradient(90deg, #c04cff, #8e3df0);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
}
```

---

# 8. Screen title

Exact visible text:

> **Smart Coach Vision**

Approximate position:

```text
center-x: 135px
top: 65px
```

Approximate typography:

```css
font-size: 13px;
font-weight: 700;
line-height: 1.2;
color: #ffffff;
```

It sits directly under the logo with roughly `8–10px` vertical spacing.

---

# 9. Camera preview container

Approximate bounds:

```text
x: 27px
y: 95px
width: 217px
height: 319px
```

The camera preview is a large vertically oriented rounded rectangle.

Approximate style:

```css
.camera-preview {
  position: relative;
  width: calc(100% - 54px);
  height: 319px;
  margin: 16px auto 0;

  border-radius: 21px;
  overflow: hidden;

  background:
    linear-gradient(
      180deg,
      #101622 0%,
      #080d15 45%,
      #02060c 100%
    );
}
```

The preview is almost black at the bottom and slightly blue-gray at the top.

There is no actual camera image visible in the screenshot; the preview background is dark and abstract.

---

# 10. Camera preview grid

The preview contains a subtle rule-of-thirds style grid.

Visible grid lines:

- two vertical lines
- two horizontal lines

Approximate divisions:

```text
vertical lines:
x ≈ 98px
x ≈ 171px

horizontal lines:
y ≈ 201px
y ≈ 309px
```

Relative to the camera preview, these divide the area into approximately three columns and three rows.

Grid style:

```css
.camera-grid-line {
  position: absolute;
  background: rgba(110, 125, 145, 0.10);
}
```

Approximate line thickness:

```text
1px
```

The grid should be subtle and barely visible.

---

# 11. Scan status pill

Approximate bounds:

```text
x: 99px
y: 111px
width: 72px
height: 20px
```

Text:

> Nutri Scan ativo

Shape:

```css
border-radius: 999px;
```

Background:

```css
background: #08090c;
```

Border:

```css
border: 1px solid #29252f;
```

Text styling:

```css
font-size: 7px;
font-weight: 500;
color: #ffffff;
```

The pill is centered horizontally near the top of the camera preview.

---

# 12. Main scan target rectangle

Approximate bounds:

```text
x: 59px
y: 198px
width: 152px
height: 114px
```

This is the primary focus element.

It is a semi-transparent purple rectangle with:

- violet outline
- purple translucent interior
- four emphasized corner brackets
- neon/glow effect
- rounded corners

Approximate style:

```css
.scan-target {
  position: absolute;

  width: 152px;
  height: 114px;

  border: 1.5px solid #b848ff;
  border-radius: 13px;

  background: rgba(84, 18, 129, 0.28);

  box-shadow:
    0 0 6px rgba(185, 65, 255, 0.95),
    0 0 14px rgba(172, 48, 255, 0.55),
    inset 0 0 12px rgba(116, 27, 171, 0.16);
}
```

The purple target is significantly brighter than the camera background.

---

# 13. Scan-target corner markers

The rectangle has four **L-shaped corner brackets**.

They are larger/thicker than the normal rectangular border.

Each corner extends approximately:

```text
20–22px
```

Horizontal and vertical strokes:

```css
border-color: #cb69ff;
border-width: 2px;
```

Corner radius:

```text
8–10px
```

Approximate arrangement:

```text
┌                 ┐


      content


└                 ┘
```

The central portions of the rectangle edges are thinner than the corners.

---

# 14. Scan-target glow

Strong violet glow is visible especially:

- around the bottom edge
- around left/right corner markers
- around the upper-right corner

Recommended:

```css
filter: drop-shadow(
  0 0 7px rgba(180, 63, 255, 0.7)
);
```

The bottom edge has a noticeable horizontal purple bloom.

---

# 15. Central focus / scan icon

Approximate center:

```text
x: 135px
y: 238px
```

The icon resembles a **camera focus / scanning brackets** symbol.

Structure:

```text
┌─      ─┐

└─      ─┘
```

It consists of four isolated corner segments.

Approximate size:

```text
24px × 24px
```

Style:

```css
stroke: #d683ff;
stroke-width: 2px;
```

No solid center dot is visible.

---

# 16. Scan instruction

Exact visible text:

> Aponte para a  
> tabela  
> nutricional

Three centered lines.

Approximate position:

```text
center-x: 135px
top: 259px
```

Approximate typography:

```css
font-size: 8px;
font-weight: 500;
line-height: 1.4;
text-align: center;
color: #ffffff;
```

The instruction is fully contained inside the purple scan target.

---

# 17. Camera preview bottom area

Below the scan frame, the preview remains empty and dark.

There are no:

- extra controls
- labels
- captured thumbnails
- zoom controls
- flash controls
- timestamps

This negative space is important to preserve.

---

# 18. Capture-controls area

Approximate region:

```text
y: 479px → 532px
```

Three controls are aligned horizontally:

```text
gallery button
large shutter button
camera mode / scan button
```

Layout:

```css
.capture-controls {
  display: grid;
  grid-template-columns: 1fr auto 1fr;
  align-items: center;
}
```

The shutter is centered exactly in the page.

---

# 19. Left gallery button

Approximate bounds:

```text
x: 49px
y: 492px
width: 31px
height: 31px
```

Circular control.

Style:

```css
width: 31px;
height: 31px;
border-radius: 50%;

background: #1b1a21;
border: 1px solid #4e4a54;
```

Icon:

- white outline image/gallery icon
- small square landscape/photo symbol
- approximately `13px`

The icon is centered.

---

# 20. Main shutter button

Approximate bounds:

```text
x: 110px
y: 480px
width: 52px
height: 52px
```

This is the largest capture control.

Structure:

- white outer circular ring
- very pale gray inner circle
- darker thin inner outline

Approximate CSS:

```css
.shutter {
  width: 52px;
  height: 52px;
  border-radius: 50%;

  background: #ffffff;
  padding: 5px;
}
```

Inner circle:

```css
.shutter::before {
  content: "";
  display: block;

  width: 100%;
  height: 100%;

  border-radius: 50%;
  background: #fafafa;
  border: 2px solid #e4e4e4;
}
```

There is no purple accent on the shutter itself.

---

# 21. Right camera mode button

Approximate bounds:

```text
x: 190px
y: 492px
width: 31px
height: 31px
```

Same circular style as the gallery button:

```css
background: #1b1a21;
border: 1px solid #4e4a54;
border-radius: 50%;
```

Icon:

- white compact camera / scan icon
- approximately `13px`
- camera body with small corner/focus-like detailing

---

# 22. Bottom navigation

Approximate bounds:

```text
x: 0px
y: 542px
width: 259px
height: 52px
```

The nav is fixed to the bottom.

Style:

```css
.bottom-navigation {
  background: #08050d;
  border-top: 1px solid #211b28;

  display: grid;
  grid-template-columns: repeat(4, 1fr);
}
```

Each item contains:

```text
icon
label
```

All items are vertically centered.

---

# 23. Bottom navigation labels

Exact labels:

```text
Home
Câmera
Feed
Perfil
```

Approximate label typography:

```css
font-size: 7px;
font-weight: 400;
```

The active camera label is slightly brighter and purple.

---

# 24. Home navigation item

Position: first column.

Icon:

- outline house
- muted blue-gray

Label:

> Home

Inactive color:

```css
color: #788396;
```

---

# 25. Camera navigation item — active

Position: second column.

Icon:

- outline camera
- violet/purple

Label:

> Câmera

Active color:

```css
color: #c15bff;
```

The icon is the strongest colored nav icon.

No background pill or selection circle is used.

---

# 26. Feed navigation item

Position: third column.

Icon:

- trophy / award-like outline
- muted blue-gray

Label:

> Feed

Approximate inactive color:

```css
color: #788396;
```

The icon visually resembles a trophy or social achievement symbol.

---

# 27. Profile navigation item

Position: fourth column.

Icon:

- outline single-person silhouette

Label:

> Perfil

Inactive color:

```css
color: #788396;
```

---

# 28. Approximate vertical layout map

```text
0       screenshot top

39      JOVIS logo
65      Smart Coach Vision

95      camera preview begins

111     Nutri Scan ativo pill

198     scan target begins
312     scan target ends

414     camera preview ends

480     shutter begins
492     side control buttons begin
532     capture controls end

542     bottom navigation begins
594     screenshot ends
```

---

# 29. Approximate horizontal layout map

```text
0        screenshot edge

27       camera preview left
244      camera preview right

59       scan target left
211      scan target right

49       gallery control
110      shutter left
162      shutter right
190      camera-mode control

0–65     Home nav item
65–130   Câmera nav item
130–194  Feed nav item
194–259  Perfil nav item
```

---

# 30. Spacing system

Useful screenshot-scale values:

```css
--space-xs: 4px;
--space-sm: 8px;
--space-md: 14px;
--space-lg: 20px;
--space-xl: 27px;
```

Important gaps:

```text
logo → title: ~8px
title → camera preview: ~17px
camera preview → shutter area: ~65px
capture controls → bottom nav: ~10px
```

---

# 31. Border-radius system

Suggested values:

```css
--radius-preview: 21px;
--radius-scan: 13px;
--radius-pill: 999px;
--radius-round-control: 50%;
```

---

# 32. Icon family recommendation

Use thin rounded outline icons.

Good libraries:

- Lucide
- Phosphor
- Heroicons Outline

Suggested icon equivalents:

```text
Image / ImageIcon
Camera
Scan / Focus
House
Trophy
User
```

The central scan focus brackets may be easier to reproduce with custom CSS.

---

# 33. Responsive implementation guidance

The screenshot width is only `259px`, narrower than a typical modern mobile CSS viewport.

If reproducing at around `390px`, use proportional scaling rather than literal screenshot dimensions.

Approximate scale:

```text
390 / 259 ≈ 1.51
```

For example:

```text
camera preview:
217px screenshot width
→ ~327px at 390px viewport
```

Recommended responsive camera container:

```css
.camera-preview {
  width: calc(100% - 54px);
  max-width: 340px;
  aspect-ratio: 217 / 319;
}
```

The central scan target can scale relative to the camera preview:

```css
.scan-target {
  width: 70%;
  aspect-ratio: 152 / 114;
}
```

---

# 34. Recommended component hierarchy

```text
CameraPage
├── CameraHeader
│   ├── JovisLogo
│   └── ScreenTitle
│
├── CameraPreview
│   ├── CameraGrid
│   ├── ScanStatusPill
│   └── ScanTarget
│       ├── ScanCorner × 4
│       ├── FocusIcon
│       └── ScanInstruction
│
├── CaptureControls
│   ├── GalleryButton
│   ├── ShutterButton
│   └── CameraModeButton
│
└── BottomNavigation
    ├── Home
    ├── Câmera [active]
    ├── Feed
    └── Perfil
```

---

# 35. Exact visible text inventory

Use the following visible strings exactly:

```text
JOVIS

Smart Coach Vision

Nutri Scan ativo

Aponte para a
tabela
nutricional

Home
Câmera
Feed
Perfil
```

---

# 36. Important visual characteristics to preserve

For close visual reproduction, preserve the following:

1. The overall background is **very dark purple-black**.
2. The page header is **centered**, unlike the dashboard header.
3. The camera preview is a **large rounded vertical panel**.
4. The preview uses a **dark blue-black vertical gradient**.
5. A very subtle **3×3 camera grid** is visible.
6. The status pill `"Nutri Scan ativo"` is small and understated.
7. The scan frame is the strongest visual element inside the preview.
8. The scan frame uses a **semi-transparent purple fill**.
9. The frame has **bright violet corner markers**.
10. A **neon purple glow** surrounds the frame.
11. The central focus icon uses four detached corner segments.
12. The instruction text is exactly three centered lines.
13. The bottom part of the preview remains deliberately empty/dark.
14. The shutter button is large, white, and perfectly circular.
15. The two side capture controls are much smaller and dark.
16. The bottom navigation remains minimal and flat.
17. **Câmera** is the only active purple nav item.
18. No extra buttons, tabs, floating controls, or overlays should be added.

---

# 37. Visual hierarchy

The intended attention order is:

```text
JOVIS
↓
Smart Coach Vision
↓
camera preview
↓
purple scan target
↓
scan instruction
↓
white shutter button
↓
bottom navigation
```

The purple scan target and white shutter button create the strongest contrast.

The screen should feel like a **premium AI-assisted nutrition scanning camera interface**, with the active scanning region clearly emphasized while the rest of the UI remains visually quiet.
