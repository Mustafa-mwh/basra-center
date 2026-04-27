# Design System — Basra Center Style

A reference guide for replicating this app's design language in other projects.

---

## Stack

- **CSS Framework**: Tailwind CSS (CDN)
- **Icons**: Lucide Icons (CDN)
- **Font**: Cairo (Google Fonts)
- **Direction**: RTL (`<html lang="ar" dir="rtl">`)
- **Architecture**: Single-page, multi-view (vanilla JS view controller)

---

## Color Tokens

```js
tailwind.config = {
  theme: {
    extend: {
      colors: {
        primary: "#26b559",      // main green — CTAs, active states, badges
        secondary: "#F58220",    // orange — highlights, sales tags, delivery
        background: "#fff",
        surface: "#FFFFFF",
        accent: "#F2F9F8",       // very light green tint — empty states, icon bg
        cardBg: "#FFFFFF",
      },
    },
  },
};
```

### Usage Rules

| Token       | Use For |
|-------------|---------|
| `#26b559` primary   | Buttons, active nav, price text, focus rings, icon accents |
| `#F58220` secondary | Sale badges, delivery cost, promo tags |
| `#F2F9F8` accent    | Card backgrounds, empty state icons, input tint |
| `#1e293b` slate-900 | Primary headings |
| `#94a3b8` slate-400 | Subtext, placeholders, disabled icons |
| `#f1f5f9` slate-100 | Borders, dividers |
| rose tones  | Destructive actions (delete, logout) |
| amber tones | Favorites / saved items |

---

## Typography

```html
<link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />
```

```css
body { font-family: "Cairo", sans-serif; }
```

### Scale

| Role             | Font Size | Font Weight | Color |
|------------------|-----------|-------------|-------|
| Page title       | 24px      | 900         | `#1e293b` |
| Section heading  | 18px      | 900         | `#1e293b` |
| Card title       | 14px      | 900         | `#1e293b` |
| Body             | 14px      | 700         | `#475569` |
| Caption / meta   | 12px      | 700         | `#94a3b8` |
| Micro label      | 10px      | 700         | `#94a3b8` |
| Price            | 14px      | 400 — currency suffix at 10px, opacity 40% | `#1e293b` |
| Badge / tag text | 9px–10px  | 900         | white |

**Rule:** Weight 900 for all interactive labels and headings; 700 for secondary text; never lighter in UI.

---

## Spacing & Layout

### Page Wrapper
```html
<body style="padding-bottom: 128px; color: #1e293b; background: #fff; min-height: 100vh;">
  <main style="background: #fbfbfb; max-width: 1024px; margin: 0 auto;">
```
- `padding-bottom: 128px` — clears floating bottom nav
- `max-width: 1024px; margin: 0 auto` — constrains and centers on desktop

### Section Padding
```html
<section style="padding: 0 20px; margin-bottom: 32px;">  <!-- standard -->
<section style="padding: 0 20px; margin-bottom: 40px;">  <!-- spacious -->
```
- Horizontal padding: always `20px`
- Section bottom margin: `32px` (standard), `40px` (breathable), `48px` (major breaks)

### View Padding
```html
<div style="padding: 32px 20px 0; min-height: 100vh;">
```

---

## Border Radius

| Value  | Use |
|--------|-----|
| 8px    | Small chips, tags (`rounded-lg`) |
| 12px   | Inputs, small icon buttons (`rounded-xl`) |
| 16px   | Standard buttons, inputs (`rounded-2xl`) |
| 24px   | Medium cards, banners (`rounded-3xl`) |
| 26px   | Active nav item inner pill |
| 28px   | Product cards |
| 32px   | Large cards, sheets, bottom nav |
| 9999px | Pill filters, subcategory tags |

### Per-Component

| Component         | Border Radius |
|-------------------|---------------|
| Banner cards      | 32px |
| Product cards     | 28px |
| Cart summary card | 28px |
| Account cards     | 32px |
| Nav bar           | 32px |
| Buttons (primary) | 16px |
| Buttons (small)   | 12px |
| Icon buttons      | 12px |
| Tags / badges     | 8px |
| Pills / subcats   | 9999px |
| Inputs            | 16px |

---

## Shadows

```js
boxShadow: {
  premium: "0 10px 20px -5px rgba(0, 0, 0, 0.05)",
  nav: "0 -10px 40px -10px rgba(0, 132, 119, 0.15)",
}
```

| Shadow                                     | Use |
|--------------------------------------------|-----|
| `0 10px 20px -5px rgba(0,0,0,0.05)`        | Empty state cards, feature cards |
| `0 -10px 40px -10px rgba(0,132,119,0.15)`  | Bottom navigation bar |
| `0 10px 15px -3px rgba(38,181,89,0.2)`     | Primary CTA buttons |
| `0 20px 25px -5px rgba(245,130,32,0.25)`   | Cart badge |
| `0 1px 3px rgba(0,0,0,0.05)`               | Icon buttons, qty selectors |

---

## Glass Effect

```css
.glass {
  background: rgba(255, 255, 255, 0.85);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  border: 1px solid rgba(255, 255, 255, 0.5);
}
```

Used on: bottom nav, floating overlays, like buttons on product images.

---

## Component Patterns

### Primary Button
```html
<button style="
  background: #26b559;
  color: white;
  padding: 16px 40px;
  border-radius: 16px;
  font-size: 14px;
  font-weight: 900;
  box-shadow: 0 10px 15px -3px rgba(38,181,89,0.2);
  transition: transform 0.15s;
">
  Label
</button>
```

### Dark Button (Full-width, 56px tall)
```html
<button style="
  width: 100%;
  background: #0f172a;
  color: white;
  height: 56px;
  border-radius: 16px;
  font-size: 14px;
  font-weight: 900;
  box-shadow: 0 20px 25px -5px rgba(0,0,0,0.15);
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  transition: transform 0.15s;
">
  Label
  <i data-lucide="arrow-left" style="width: 16px; height: 16px;"></i>
</button>
```

### Destructive Button (Full-width, 64px tall)
```html
<button style="
  width: 100%;
  background: #fff1f2;
  color: #e11d48;
  height: 64px;
  border-radius: 24px;
  font-weight: 900;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 12px;
  transition: transform 0.15s;
">
  <i data-lucide="log-out" style="width: 20px; height: 20px;"></i>
  Label
</button>
```

### Icon Button (44px)
```html
<button style="
  width: 44px;
  height: 44px;
  background: white;
  border-radius: 12px;
  border: 1px solid #f1f5f9;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: transform 0.15s;
">
  <i data-lucide="bell" style="width: 20px; height: 20px; color: #475569;"></i>
</button>
```

### Text Input (56px tall)
```html
<div style="position: relative;">
  <i data-lucide="search" style="
    position: absolute;
    right: 16px;
    top: 50%;
    transform: translateY(-50%);
    width: 20px;
    height: 20px;
    color: #94a3b8;
  "></i>
  <input
    type="text"
    placeholder="..."
    style="
      width: 100%;
      height: 56px;
      background: white;
      border-radius: 16px;
      padding: 0 48px 0 16px;
      border: 1px solid #f1f5f9;
      font-size: 14px;
      font-weight: 700;
      outline: none;
    "
  />
</div>
```
- Height: 56px
- Right padding: 48px to clear icon (RTL layout)
- Focus ring: `box-shadow: 0 0 0 4px rgba(38,181,89,0.05)` — ultra-subtle

### Card (Standard)
```html
<div style="
  background: white;
  border-radius: 32px;
  border: 1px solid #f1f5f9;
  overflow: hidden;
">
  <!-- content -->
</div>
```

### Card Row (Menu Item)
```html
<button style="
  width: 100%;
  padding: 20px 24px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  border-bottom: 1px solid #f8fafc;
  transition: background 0.15s;
">
  <div style="display: flex; align-items: center; gap: 16px;">
    <div style="
      width: 40px;
      height: 40px;
      background: rgba(38,181,89,0.1);
      border-radius: 12px;
      display: flex;
      align-items: center;
      justify-content: center;
      color: #26b559;
    ">
      <i data-lucide="package" style="width: 20px; height: 20px;"></i>
    </div>
    <span style="font-weight: 900; color: #1e293b; font-size: 14px;">Label</span>
  </div>
  <i data-lucide="chevron-left" style="width: 20px; height: 20px; color: #cbd5e1;"></i>
</button>
```

Icon bg tints:
- Primary: `background: rgba(38,181,89,0.1); color: #26b559`
- Secondary: `background: rgba(245,130,32,0.1); color: #F58220`
- Amber: `background: #fef3c7; color: #d97706`
- Neutral: `background: #f1f5f9; color: #64748b`

### Section Header
```html
<div style="padding: 0 20px; margin-bottom: 20px; display: flex; align-items: center; justify-content: space-between;">
  <div style="display: flex; flex-direction: column;">
    <h3 style="font-size: 18px; font-weight: 900; color: #1e293b; line-height: 1; margin-bottom: 4px;">Title</h3>
    <span style="font-size: 10px; font-weight: 700; color: #26b559;">Subtitle</span>
  </div>
  <button style="
    color: #26b559;
    font-size: 14px;
    font-weight: 900;
    background: rgba(38,181,89,0.05);
    padding: 6px 12px;
    border-radius: 8px;
  ">عرض الكل</button>
</div>
```

### Badge / Tag

```html
<!-- Sale badge -->
<span style="background: #F58220; color: white; font-size: 9px; font-weight: 900; padding: 4px 8px; border-radius: 8px;">خصم 20%</span>

<!-- Status badge — success -->
<span style="background: #ecfdf5; color: #059669; padding: 8px 16px; border-radius: 12px; font-size: 10px; font-weight: 900;">نشط</span>

<!-- Status badge — warning -->
<span style="background: #fffbeb; color: #d97706; padding: 8px 16px; border-radius: 12px; font-size: 10px; font-weight: 900;">قيد المعالجة</span>

<!-- Status badge — error -->
<span style="background: #fff1f2; color: #e11d48; padding: 8px 16px; border-radius: 12px; font-size: 10px; font-weight: 900;">ملغي</span>

<!-- Pill filter — active -->
<div style="padding: 6px 16px; border-radius: 9999px; background: #26b559; color: white; font-size: 12px; font-weight: 700; box-shadow: 0 1px 3px rgba(38,181,89,0.2);">الكل</div>

<!-- Pill filter — inactive -->
<div style="padding: 6px 16px; border-radius: 9999px; background: white; border: 1px solid #f1f5f9; color: #475569; font-size: 12px; font-weight: 700;">فئة</div>
```

### Header (Sticky Page Header)
```html
<header style="
  padding: 32px 20px 16px;
  display: flex;
  align-items: center;
  justify-content: space-between;
  position: sticky;
  top: 0;
  background: rgba(255,255,255,0.8);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  z-index: 50;
">
  <!-- left: logo + location | right: action buttons -->
</header>
```

### Banner Card (180px mobile / 240px desktop)
```html
<div style="
  position: relative;
  border-radius: 32px;
  overflow: hidden;
  background: #0A2E2A;
  height: 180px;        /* 240px on desktop (≥1024px) */
  flex-shrink: 0;
  min-width: 90%;       /* auto on desktop */
">
  <img src="..." style="position: absolute; inset: 0; width: 100%; height: 100%; object-fit: cover; opacity: 0.6;" />
  <div style="position: absolute; inset: 0; background: linear-gradient(to left, rgba(0,0,0,0.4), transparent);"></div>
  <div style="position: relative; height: 100%; padding: 28px; display: flex; flex-direction: column; justify-content: center; color: white;">
    <span style="background: #F58220; color: white; padding: 4px 12px; border-radius: 8px; font-size: 10px; font-weight: 900; width: fit-content; margin-bottom: 12px;">Tag</span>
    <h2 style="font-size: 18px; font-weight: 900; line-height: 1.3; margin-bottom: 16px;">Title<br/>Line two</h2>
    <button style="background: white; color: #26b559; width: fit-content; padding: 10px 24px; border-radius: 12px; font-weight: 700; font-size: 14px; box-shadow: 0 20px 25px -5px rgba(0,0,0,0.1);">CTA</button>
  </div>
</div>
```

### Empty State
```html
<div style="padding: 80px 0; display: flex; flex-direction: column; align-items: center; text-align: center;">
  <div style="
    width: 96px; height: 96px;
    background: #F2F9F8;
    border-radius: 9999px;
    display: flex; align-items: center; justify-content: center;
    color: rgba(38,181,89,0.3);
    margin-bottom: 24px;
    box-shadow: 0 10px 20px -5px rgba(0,0,0,0.05);
  ">
    <i data-lucide="package-search" style="width: 48px; height: 48px;"></i>
  </div>
  <h3 style="font-size: 20px; font-weight: 900; color: #1e293b; margin-bottom: 8px;">عنوان الحالة</h3>
  <p style="font-size: 14px; color: #94a3b8; max-width: 260px; line-height: 1.6;">نص توضيحي مختصر.</p>
  <button style="
    margin-top: 32px;
    padding: 14px 40px;
    background: #26b559;
    color: white;
    border-radius: 16px;
    font-weight: 900;
    font-size: 14px;
    box-shadow: 0 10px 15px -3px rgba(38,181,89,0.2);
    display: flex; align-items: center; gap: 8px;
  ">
    <i data-lucide="layout-grid" style="width: 16px; height: 16px;"></i>
    إجراء
  </button>
</div>
```

---

## Bottom Navigation

```html
<!-- Outer wrapper — pointer-events trick lets taps pass through the padding zone -->
<div style="
  position: fixed;
  bottom: 0; left: 0;
  width: 100%;
  padding: 8px 20px 32px;
  pointer-events: none;
  z-index: 50;
">
  <nav style="
    max-width: 448px;      /* 672px on desktop (≥1024px) */
    margin: 0 auto;
    background: rgba(255,255,255,0.85);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    border: 1px solid rgba(255,255,255,0.6);
    border-radius: 32px;
    padding: 8px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    box-shadow: 0 -10px 40px -10px rgba(0,132,119,0.15);
    pointer-events: auto;
  ">

    <!-- Active tab -->
    <button style="
      display: flex; flex-direction: column; align-items: center; gap: 4px;
      min-width: 70px; padding: 12px 8px;
      color: #26b559;
      background: rgba(38,181,89,0.08);
      border-radius: 26px;
      transition: all 0.3s;
    ">
      <i data-lucide="home" style="width: 20px; height: 20px;"></i>
      <span style="font-size: 10px; font-weight: 900;">الرئيسية</span>
    </button>

    <!-- Inactive tab -->
    <button style="
      display: flex; flex-direction: column; align-items: center; gap: 4px;
      min-width: 70px; padding: 12px 8px;
      color: #94a3b8;
      border-radius: 16px;
      transition: all 0.3s;
    ">
      <i data-lucide="layout-grid" style="width: 20px; height: 20px;"></i>
      <span style="font-size: 10px; font-weight: 700;">الفئات</span>
    </button>

  </nav>
</div>
```

Active tab: `color: #26b559; background: rgba(38,181,89,0.08); border-radius: 26px; font-weight: 900`
Inactive tab: `color: #94a3b8; font-weight: 700`

---

## Animation

```css
@keyframes fadeIn {
  from { opacity: 0; transform: translateY(12px); }
  to   { opacity: 1; transform: translateY(0); }
}
.animate-fade-in {
  animation: fadeIn 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards;
}
```

Stagger list items: `animation-delay: 0.05s` increments per item.

Interactive press states:
- Buttons: `transform: scale(0.95)` on `:active`
- Icon buttons: `transform: scale(0.90)` on `:active`

---

## SPA View Controller Pattern

```js
const VIEWS = ["home", "browse", "category", "cart", "account", "orders"];
const NAV_MAP = { home: "nav-home", browse: "nav-browse", cart: "nav-cart", account: "nav-account" };

function switchView(viewId) {
  VIEWS.forEach(v => document.getElementById(`${v}-view`)?.classList.add("hidden"));
  document.getElementById(`${viewId}-view`)?.classList.remove("hidden");

  // Reset all nav buttons
  Object.values(NAV_MAP).forEach(id => {
    const el = document.getElementById(id);
    if (!el) return;
    el.classList.remove("active", "text-primary");
    el.classList.add("text-slate-400");
    el.querySelector("span").classList.replace("font-black", "font-bold");
  });

  // Activate relevant nav button
  const navId = viewId === "category" ? NAV_MAP.browse : NAV_MAP[viewId];
  if (navId) {
    const el = document.getElementById(navId);
    el.classList.add("active");
    el.classList.remove("text-slate-400");
    el.classList.add("text-primary");
    el.querySelector("span").classList.replace("font-bold", "font-black");
  }

  lucide.createIcons();
  window.scrollTo(0, 0);
}
```

Each view is a `<div id="{name}-view" class="hidden ...">`. The active view removes `hidden`.

---

## Scrollable Horizontal Row

```html
<div style="display: flex; overflow-x: auto; padding: 0 20px; gap: 16px; scrollbar-width: none; -ms-overflow-style: none;">
  <!-- cards -->
</div>
```

```css
div::-webkit-scrollbar { display: none; }
```

On desktop (≥1024px): switch to `display: grid; grid-template-columns: repeat(4, 1fr); gap: 12px`.

---

## Product Image Container

```css
.product-image-container {
  width: 100%;
  height: 52.09vw;   /* scales with viewport on mobile */
  max-height: 224px;
}
@media (min-width: 1024px) {
  .product-image-container { height: 224px; }
}

.product-image {
  object-fit: contain;
  width: 100%;
  height: 100%;
  padding: 8px;
}
```

---

## Desktop Background (Decorative Gradients)

```css
@media (min-width: 1024px) {
  body {
    background-image:
      radial-gradient(at 0% 0%,    rgba(0, 132, 119, 0.068) 0px, transparent 50%),
      radial-gradient(at 100% 0%,  rgba(225, 105, 36, 0.089) 0px, transparent 50%),
      radial-gradient(at 100% 100%, rgba(0, 132, 119, 0.05)  0px, transparent 50%),
      radial-gradient(at 0% 100%,  rgba(225, 105, 36, 0.158) 0px, transparent 50%);
    background-attachment: fixed;
  }
}
```

---

## HTML Boilerplate

```html
<!doctype html>
<html lang="ar" dir="rtl">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />
  <title>App Name</title>
  <script src="https://cdn.tailwindcss.com"></script>
  <link href="https://fonts.googleapis.com/css2?family=Cairo:wght@300;400;500;600;700;800&display=swap" rel="stylesheet" />
  <script src="https://unpkg.com/lucide@latest"></script>
  <script>
    tailwind.config = {
      theme: {
        extend: {
          colors: {
            primary: "#26b559",
            secondary: "#F58220",
            background: "#fff",
            surface: "#FFFFFF",
            accent: "#F2F9F8",
            cardBg: "#FFFFFF",
          },
          fontFamily: { cairo: ["Cairo", "sans-serif"] },
          borderRadius: { xs: "8px", md: "16px", lg: "24px", xl: "32px" },
          boxShadow: {
            premium: "0 10px 20px -5px rgba(0, 0, 0, 0.05)",
            nav: "0 -10px 40px -10px rgba(0, 132, 119, 0.15)",
          },
        },
      },
    };
  </script>
  <style>
    body {
      font-family: "Cairo", sans-serif;
      background-color: #fff;
      -webkit-tap-highlight-color: transparent;
      overflow-x: hidden;
    }
    .hide-scrollbar::-webkit-scrollbar { display: none; }
    .hide-scrollbar { -ms-overflow-style: none; scrollbar-width: none; }
    .glass {
      background: rgba(255,255,255,0.85);
      backdrop-filter: blur(24px);
      -webkit-backdrop-filter: blur(24px);
      border: 1px solid rgba(255,255,255,0.5);
    }
    @keyframes fadeIn {
      from { opacity: 0; transform: translateY(12px); }
      to   { opacity: 1; transform: translateY(0); }
    }
    .animate-fade-in { animation: fadeIn 0.6s cubic-bezier(0.16, 1, 0.3, 1) forwards; }
    .nav-item.active { color: #26b559; background: rgba(38, 181, 89, 0.08); }
  </style>
</head>
<body style="padding-bottom: 128px;">
  <main style="background: #fbfbfb; max-width: 1024px; margin: 0 auto;">
    <!-- views here -->
  </main>
  <!-- bottom nav here -->
  <script>
    window.onload = function() { lucide.createIcons(); };
  </script>
</body>
</html>
```

---

## Quick Rules Summary

1. **Round everything aggressively** — minimum 12px, prefer 28px–32px for cards.
2. **Font weight 900 for all interactive text**, 700 for meta/captions, never lighter in UI.
3. **Active states always scale**: `scale(0.95)` buttons, `scale(0.90)` icon buttons.
4. **No hard outlines** — borders are `1px solid #f1f5f9`, focus is a soft `0 0 0 4px rgba(38,181,89,0.05)`.
5. **Shadows are subtle** — `0 10px 20px -5px rgba(0,0,0,0.05)` for depth, colored glows at `0.2` opacity for CTAs.
6. **Horizontal scroll on mobile → grid on desktop** at 1024px breakpoint.
7. **All views hidden except active** — `hidden` class toggled by `switchView()`.
8. **`lucide.createIcons()`** must be called after every dynamic HTML injection.
9. **Body needs 128px bottom padding** to prevent content hiding behind the floating nav.
10. **Stagger fade-ins** with `animation-delay` increments of 50ms–100ms on list items.
