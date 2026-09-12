# JOVIS — Communities Screen UI Reconstruction Description

## 1. Overall page

**Screenshot viewport:** `249px × 873px`

The screen is a **mobile communities/social screen** for the JOVIS app.

It follows the same established JOVIS design language:

- nearly black purple-tinted background
- white primary text
- muted gray/lavender secondary text
- dark rounded cards
- thin purple-gray borders
- bright violet/magenta accents
- small saturated avatar/icon colors
- compact spacing and typography

The screen is vertically scrollable and shows four major sections:

1. page header
2. featured challenges
3. weekly ranking
4. community feed
5. discover communities

The screenshot ends while the second item in **Descobrir comunidades** is still visible, so the page likely continues below.

Recommended semantic structure:

```text
<body>
  <div class="app-shell">

    <header class="communities-header">
      <div class="title-group">
        page-title
        member-count
      </div>

      <button class="search-button">
        search-icon
      </button>
    </header>

    <main class="communities-content">

      <section class="featured-challenges">
        section-title
        challenge-grid
          challenge-card × 2
      </section>

      <section class="weekly-ranking">
        section-title
        ranking-row × 3
      </section>

      <section class="community-feed">
        section-title
        feed-card × 3
      </section>

      <section class="discover-communities">
        section-title
        community-discovery-card × N
      </section>

    </main>

  </div>
</body>
```

No fixed bottom navigation is visible in this screenshot.

---

## 2. Global visual style

The page is a dark social/community dashboard focused on:

- active challenges
- community leaderboard/ranking
- social activity
- discovering interest-based communities

Visual hierarchy:

```text
Comunidades
↓
featured challenge cards
↓
ranking list
↓
community feed
↓
discover community cards
```

The featured challenge cards use the strongest magenta/purple color in the upper half of the screen.

The rest of the interface is deliberately subdued so the bright challenge cards and call-to-action buttons stand out.

---

## 3. Approximate color palette

Recommended colors:

```css
:root {
  --bg: #08050e;

  --surface: #16121c;
  --surface-alt: #19141f;
  --surface-deep: #100c16;

  --border: #34293d;
  --border-soft: #2b2332;

  --text-primary: #ffffff;
  --text-secondary: #aaa2b1;
  --text-muted: #81798a;

  --purple: #a638ff;
  --purple-light: #c84cff;
  --purple-dark: #6c27d4;

  --magenta: #df20c4;
  --magenta-dark: #9d19c5;

  --orange: #ff8b00;
  --orange-dark: #e45a00;

  --blue: #6672f5;
  --gray-rank: #7c8493;

  --icon-purple-bg: #40204f;
  --icon-purple-border: #67317e;

  --button-purple: #9f45f3;
  --button-purple-light: #b85cff;
}
```

Base page background:

```css
background: #08050e;
```

Most cards:

```css
background: #16121c;
```

---

## 4. Global typography

Use a clean modern sans-serif such as:

```css
font-family:
  Inter,
  "SF Pro Display",
  "SF Pro Text",
  Arial,
  sans-serif;
```

The UI uses:

- bold section titles
- small white names/titles
- very small muted metadata
- compact body copy
- bold badge/button text

The screenshot is only `249px` wide, so font sizes below refer to this narrow source scale.

---

# 5. Page shell

Recommended:

```css
.app-shell {
  width: 100%;
  max-width: 430px;
  min-height: 100vh;
  margin: 0 auto;
  background: #08050e;
  color: #fff;
}
```

Approximate common horizontal inset:

```text
13–14px
```

Most full-width cards span approximately:

```text
x: 13px → 239px
```

for a width of about:

```text
226px
```

---

# 6. Header

Approximate bounds:

```text
x: 14px → 239px
y: 7px → 39px
```

The header is split into:

- left-aligned title and member count
- right-aligned circular search button

Layout:

```css
display: flex;
justify-content: space-between;
align-items: flex-start;
```

A thin divider appears below the header.

---

## 7. Page title

Exact text:

> **Comunidades**

Approximate position:

```text
x: 14px
y: 7px
```

Approximate typography:

```css
font-size: 17px;
font-weight: 800;
line-height: 1.1;
color: #ffffff;
```

---

## 8. Community member count

Exact text:

> 12.4 mil membros • 1.2 mil online

Approximate position:

```text
x: 14px
y: 30px
```

Approximate typography:

```css
font-size: 6.5px;
font-weight: 400;
color: #8d8595;
```

The centered separator is a bullet:

```text
•
```

---

# 9. Search button

Approximate bounds:

```text
x: 215px
y: 8px
width: 23px
height: 23px
```

Circular dark button.

Style:

```css
width: 23px;
height: 23px;
border-radius: 50%;
background: #17131d;
border: 1px solid #3a303f;
```

Icon:

- white outline magnifying glass
- approximately `10–12px`
- centered

---

# 10. Header divider

Approximate position:

```text
y: 40px
```

Thin horizontal line across almost the full viewport.

Suggested:

```css
border-bottom: 1px solid #211a27;
```

---

# 11. Featured challenges section

Section begins around:

```text
y: 61px
```

Section heading:

> **🔥 Desafios em destaque**

Approximate typography:

```css
font-size: 10px;
font-weight: 700;
color: #ffffff;
```

The flame emoji appears immediately before the text.

---

# 12. Featured challenge grid

Approximate bounds:

```text
x: 14px
y: 84px
width: 226px
height: 105px
```

Two challenge cards arranged horizontally.

Layout:

```css
display: grid;
grid-template-columns: repeat(2, 1fr);
gap: 6px;
```

Approximate card width:

```text
110px
```

Approximate card height:

```text
105px
```

Each card has two visual zones:

```text
bright colored upper banner
dark lower information area
```

Card style:

```css
.challenge-card {
  overflow: hidden;
  border-radius: 13px;
  border: 1px solid #35263f;
  background: #17131d;
}
```

---

# 13. Challenge card upper area

Approximate height:

```text
59px
```

The upper half is a bright violet/magenta block.

Left card:

```css
background: linear-gradient(
  135deg,
  #9f20f4 0%,
  #e322c5 100%
);
```

Right card:

```css
background: linear-gradient(
  135deg,
  #8d1dec 0%,
  #dc1dba 100%
);
```

No large image or illustration is visible; the background itself is the graphic element.

---

# 14. XP badge

Each challenge card has a small dark pill at the upper-right of the bright colored region.

Left card text:

> +250 XP

Right card text:

> +180 XP

Approximate size:

```text
39–43px wide
14px high
```

Style:

```css
background: rgba(54, 12, 77, 0.85);
border-radius: 999px;
```

Typography:

```css
font-size: 6px;
font-weight: 700;
color: #ffffff;
```

---

# 15. Challenge card 1 — Shape de Verão

Exact title:

> **Shape de Verão**

Approximate position:

```text
x: 23px
y: 154px
```

Typography:

```css
font-size: 7.5px;
font-weight: 700;
color: #ffffff;
```

Metadata row:

```text
👥 2.4k    ⏱ 3 dias restantes
```

Visible labels:

```text
2.4k
3 dias restantes
```

Approximate typography:

```css
font-size: 6px;
font-weight: 400;
color: #aaa2b0;
```

Small outline icons precede each value.

---

# 16. Challenge card 2 — 30 Dias de Leitura

Exact title:

> **30 Dias de Leitura**

Approximate typography:

```css
font-size: 7.5px;
font-weight: 700;
color: #ffffff;
```

Metadata:

```text
1.8k
12 dias restantes
```

Again, small muted user/time icons precede the values.

---

# 17. Weekly ranking section

Section heading approximately:

```text
x: 14px
y: 211px
```

Exact text:

> **🏆 Ranking da Semana**

Typography:

```css
font-size: 10px;
font-weight: 700;
color: #ffffff;
```

Trophy emoji appears before the text.

---

# 18. Ranking list

Three ranking cards are stacked vertically.

Approximate common bounds:

```text
x: 13px
width: 227px
height: 45px
```

Approximate vertical positions:

```text
row 1: y 233px
row 2: y 282px
row 3: y 332px
```

Spacing between rows:

```text
4–5px
```

Card style:

```css
background: #17131d;
border: 1px solid #34293d;
border-radius: 11px;
```

Each row contains:

```text
rank badge
avatar
name + XP
award/ribbon icon
```

---

# 19. Ranking row 1 — Carlos Alves

Rank badge:

> #1

Approximate badge:

```text
20px × 20px
```

Circular orange background:

```css
background: #ff8b00;
```

Text:

```css
font-size: 7px;
font-weight: 700;
color: #ffffff;
```

Avatar:

```text
24px circle
```

Background:

```css
background: linear-gradient(135deg, #d94dea, #bf32cd);
```

Initials:

> CA

Name:

> **Carlos Alves**

XP:

> 2.450 XP

Approximate typography:

```css
.name {
  font-size: 7.5px;
  font-weight: 700;
  color: #ffffff;
}

.xp {
  font-size: 6px;
  color: #9b93a2;
}
```

Right side:

- small violet outline award/ribbon icon

---

# 20. Ranking row 2 — Marina Costa

Rank badge:

> #2

Background:

```css
background: #7c8493;
```

Avatar:

```css
background: linear-gradient(135deg, #dd45e8, #c52bcf);
```

Initials:

> MC

Name:

> **Marina Costa**

XP:

> 2.180 XP

Same violet award/ribbon icon at right.

---

# 21. Ranking row 3 — João Silva

Rank badge:

> #3

Background:

```css
background: #e45a00;
```

Avatar initials:

> JS

Name:

> **João Silva**

XP:

> 1.940 XP

Same right-side violet award icon.

---

# 22. Community feed section

Section title approximately:

```text
x: 14px
y: 397px
```

Exact text:

> **Feed da comunidade**

Typography:

```css
font-size: 10px;
font-weight: 700;
color: #ffffff;
```

Three feed cards follow.

---

# 23. Feed card global style

Approximate width:

```text
226px
```

Card style:

```css
background: #17131d;
border: 1px solid #34293d;
border-radius: 11px;
padding: 10px;
```

Each card contains:

```text
avatar + user info

post body

reaction row
```

---

# 24. Feed card 1 — Pedro Lima

Approximate bounds:

```text
x: 13px
y: 417px
width: 227px
height: 92px
```

Avatar:

```text
24px circle
```

Color:

```css
background: #6672f5;
```

Initials:

> PL

Username:

> **Pedro Lima**

Timestamp:

> 2h atrás

Post text:

> Finalmente bati meu recorde pessoal no supino! 💪  
> 120kg x 5 reps. Muito feliz com a evolução!

Approximate typography:

```css
font-size: 7px;
font-weight: 400;
line-height: 1.45;
color: #ffffff;
```

Reaction row:

```text
♡ 42    comment-icon 8
```

Counts:

```text
42
8
```

Icons and counts use muted gray.

---

# 25. Feed card 2 — Ana Ferreira

Approximate bounds:

```text
x: 13px
y: 517px
width: 227px
height: 93px
```

Avatar initials:

> AF

Avatar color:

```css
background: #6672f5;
```

Username:

> **Ana Ferreira**

Timestamp:

> 5h atrás

Post text:

> Dica: aumentar a ingestão de proteína pela manhã  
> mudou completamente meus resultados. Recomendo!

Reaction counts:

```text
67
15
```

---

# 26. Feed card 3 — Rafael Santos

Approximate bounds:

```text
x: 13px
y: 617px
width: 227px
height: 93px
```

Avatar initials:

> RS

Avatar color:

```css
background: #6672f5;
```

Username:

> **Rafael Santos**

Timestamp:

> 1d atrás

Post text:

> Alguém mais fazendo o desafio Shape de Verão?  
> Vamos trocar dicas nos comentários! 🔥

Reaction counts:

```text
89
23
```

---

# 27. Feed avatar style

All visible feed avatars use nearly the same blue-violet background.

Approximate:

```css
.feed-avatar {
  width: 24px;
  height: 24px;
  border-radius: 50%;
  background: #6672f5;

  display: grid;
  place-items: center;

  color: #fff;
  font-size: 7px;
  font-weight: 600;
}
```

---

# 28. Feed metadata

Usernames use bright white.

Timestamps use muted gray.

Approximate:

```css
.username {
  font-size: 7.5px;
  font-weight: 700;
  color: #ffffff;
}

.timestamp {
  font-size: 6px;
  font-weight: 400;
  color: #8d8595;
}
```

Timestamp sits directly below username rather than at the far right.

---

# 29. Feed reaction row

Each post contains:

- outline heart icon
- heart count
- outline comment bubble icon
- comment count

Approximate icon size:

```text
8–9px
```

Color:

```css
color: #96909e;
```

Layout:

```css
display: flex;
align-items: center;
gap: 5px;
```

with a slightly larger gap between the heart group and comment group.

---

# 30. Discover communities section

Section begins around:

```text
x: 14px
y: 729px
```

Exact heading:

> **Descobrir comunidades**

Typography:

```css
font-size: 10px;
font-weight: 700;
color: #ffffff;
```

The screenshot shows:

1. one complete community discovery card
2. the upper portion of a second card

---

# 31. Discovery card global style

Approximate dimensions:

```text
x: 13px
width: 227px
height: 67px
```

Style:

```css
background: #17131d;
border: 1px solid #34293d;
border-radius: 11px;
padding: 10px;
```

Layout:

```text
category icon | community title/details | Entrar button
```

Use:

```css
display: grid;
grid-template-columns: auto 1fr auto;
align-items: center;
gap: 9px;
```

---

# 32. Discovery card 1 — Hipertrofia

Approximate bounds:

```text
x: 13px
y: 750px
width: 227px
height: 67px
```

Icon container:

```text
34px × 34px
```

Rounded square.

Style:

```css
background: #3b1747;
border: 1px solid #6a287c;
border-radius: 9px;
```

Icon:

- yellow/orange flexed-biceps symbol
- centered

Community title:

> **Hipertrofia**

Description:

> Técnicas e dicas para ganho de  
> massa muscular

Member count:

> 45.2k membros

Approximate typography:

```css
.title {
  font-size: 7.5px;
  font-weight: 700;
  color: #ffffff;
}

.description {
  font-size: 6px;
  line-height: 1.3;
  color: #aaa2b0;
}

.members {
  font-size: 6px;
  color: #837b8a;
}
```

---

# 33. Join button

Exact text:

> **Entrar**

Approximate size:

```text
40px × 20px
```

Style:

```css
background: linear-gradient(
  90deg,
  #a842f6,
  #8a37e8
);
border: none;
border-radius: 999px;
```

Typography:

```css
font-size: 7px;
font-weight: 700;
color: #ffffff;
```

---

# 34. Discovery card 2 — Corrida

Only the upper portion is visible at the bottom of the screenshot.

Approximate start:

```text
y: 824px
```

Title:

> **Corrida**

Description:

> Treinos, maratonas e desafios de  
> corrida

A violet rounded-square category icon is visible at left.

The icon itself is a small yellow running/person symbol.

A purple `"Entrar"` button appears at the far right.

The rest of this card continues below the screenshot.

---

# 35. Approximate vertical layout map

```text
0       screenshot start

7       Comunidades title
30      member/online count
40      header divider

62      Desafios em destaque heading
84      challenge cards begin
189     challenge cards end

212     Ranking da Semana heading
233     ranking row 1
278     row 1 ends
282     ranking row 2
327     row 2 ends
332     ranking row 3
377     row 3 ends

397     Feed da comunidade heading
417     Pedro Lima card begins
509     Pedro card ends

517     Ana Ferreira card begins
610     Ana card ends

617     Rafael Santos card begins
710     Rafael card ends

729     Descobrir comunidades heading

750     Hipertrofia discovery card begins
817     Hipertrofia card ends

824     Corrida discovery card begins
873     screenshot ends while card continues
```

---

# 36. Approximate horizontal layout map

```text
0       screenshot edge

13–14   common content left edge
239–240 common content right edge

challenge grid:
14–124   Shape de Verão
130–240  30 Dias de Leitura

ranking/feed/discovery:
13–240   full-width cards

search:
215–238  circular search button
```

---

# 37. Spacing system

Useful screenshot-scale values:

```css
--space-xs: 4px;
--space-sm: 6px;
--space-md: 10px;
--space-lg: 14px;
--space-xl: 20px;
```

Typical usage:

- page side inset: `13–14px`
- card-to-card vertical gap: `4–8px`
- section heading to content: `10–12px`
- major section gap: `18–22px`
- card inner padding: `9–11px`

---

# 38. Border-radius system

Recommended:

```css
--radius-card: 11px;
--radius-large: 13px;
--radius-icon: 8px;
--radius-pill: 999px;
```

Use:

- challenge cards: `13px`
- ranking/feed/discovery cards: `10–11px`
- category icon tiles: `8–9px`
- XP and Join buttons: pills

---

# 39. Icon style

Most icons are thin rounded outlines.

Recommended icon libraries:

- Lucide
- Phosphor
- Heroicons Outline

Suggested equivalents:

```text
Search
Users
Clock
Award / Medal
Heart
MessageCircle
Badge / Ribbon
BicepsFlexed or Dumbbell
PersonStanding / Activity
```

Emoji are used directly in section headings and some post content:

```text
🔥
🏆
💪
```

---

# 40. Responsive implementation guidance

The source screenshot width is `249px`, significantly narrower than a standard modern phone viewport.

For a `390px` viewport:

```text
390 / 249 ≈ 1.57
```

Do not literally multiply every dimension. Instead preserve the same proportions.

Recommended shell:

```css
.app-shell {
  width: 100%;
  max-width: 430px;
  min-height: 100vh;
  margin: 0 auto;
  background: #08050e;
}
```

Recommended main content:

```css
.communities-content {
  padding: 0 14px 24px;
}
```

Featured challenges:

```css
.challenge-grid {
  display: grid;
  grid-template-columns: repeat(2, minmax(0, 1fr));
  gap: 8px;
}
```

All ranking/feed/discovery cards should use:

```css
width: 100%;
```

---

# 41. Recommended component hierarchy

```text
CommunitiesPage
├── CommunitiesHeader
│   ├── TitleGroup
│   │   ├── Title
│   │   └── MemberStatus
│   └── SearchButton
│
├── FeaturedChallengesSection
│   ├── SectionHeading
│   └── ChallengeGrid
│       ├── ChallengeCard(Shape de Verão)
│       └── ChallengeCard(30 Dias de Leitura)
│
├── WeeklyRankingSection
│   ├── SectionHeading
│   ├── RankingRow(Carlos Alves)
│   ├── RankingRow(Marina Costa)
│   └── RankingRow(João Silva)
│
├── CommunityFeedSection
│   ├── SectionHeading
│   ├── FeedCard(Pedro Lima)
│   ├── FeedCard(Ana Ferreira)
│   └── FeedCard(Rafael Santos)
│
└── DiscoverCommunitiesSection
    ├── SectionHeading
    ├── CommunityCard(Hipertrofia)
    └── CommunityCard(Corrida, partially visible)
```

---

# 42. Exact visible text inventory

Use these strings exactly:

```text
Comunidades

12.4 mil membros • 1.2 mil online

🔥 Desafios em destaque

+250 XP

Shape de Verão

2.4k

3 dias restantes

+180 XP

30 Dias de Leitura

1.8k

12 dias restantes

🏆 Ranking da Semana

#1

CA

Carlos Alves

2.450 XP

#2

MC

Marina Costa

2.180 XP

#3

JS

João Silva

1.940 XP

Feed da comunidade

PL

Pedro Lima

2h atrás

Finalmente bati meu recorde pessoal no supino! 💪
120kg x 5 reps. Muito feliz com a evolução!

42

8

AF

Ana Ferreira

5h atrás

Dica: aumentar a ingestão de proteína pela manhã
mudou completamente meus resultados. Recomendo!

67

15

RS

Rafael Santos

1d atrás

Alguém mais fazendo o desafio Shape de Verão?
Vamos trocar dicas nos comentários! 🔥

89

23

Descobrir comunidades

Hipertrofia

Técnicas e dicas para ganho de
massa muscular

45.2k membros

Entrar

Corrida

Treinos, maratonas e desafios de
corrida

Entrar
```

---

# 43. Important visual characteristics to preserve

For close visual reproduction, preserve the following:

1. The page uses a **very dark purple-black background**.
2. The title is large and left aligned rather than centered.
3. The member count is directly beneath the title.
4. The search control is a small circular button at the top-right.
5. Featured challenge cards use bright **purple-to-magenta blocks**.
6. XP values appear in dark rounded pills at the upper-right of each challenge.
7. Challenge details occupy a separate dark lower portion.
8. Weekly ranking rows are compact horizontal cards.
9. Rank badges use distinct colors:
   - #1 orange
   - #2 gray
   - #3 burnt orange
10. Ranking avatars use bright magenta/pink circles with initials.
11. Feed cards use blue-violet avatar circles.
12. Feed timestamps sit beneath names rather than at the far-right.
13. Social reaction icons are small and muted.
14. Discover-community cards use icon tiles on the left and a purple `"Entrar"` pill on the right.
15. The interface uses tight spacing; avoid oversized gaps.
16. Section headings are bold but compact.
17. Cards have subtle violet-gray borders, not bright outlines.
18. No visible fixed bottom navigation should be added to this screenshot reconstruction.
19. The bottom of the screenshot intentionally cuts through the second discover-community card.
20. Preserve the vertical scroll-page feeling rather than forcing all content into a fixed-height dashboard.

---

# 44. Visual hierarchy

The strongest visual elements should appear in this order:

```text
Comunidades
↓
bright featured challenge cards
↓
weekly ranking
↓
community feed
↓
community discovery cards
```

Within the content, the eye should be drawn especially to:

```text
magenta challenge panels
→ rank badges
→ colorful avatars
→ purple Entrar buttons
```

The finished screen should feel like a **premium dark social fitness community hub**, combining challenges, leaderboard mechanics, social posts, and discoverable interest groups while remaining fully consistent with the established JOVIS interface.
