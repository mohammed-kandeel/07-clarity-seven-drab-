<div align="center">

# 🔷 Clarity — Digital Solutions Platform

**Transforming Digital Experiences**

[![Live Demo](https://img.shields.io/badge/🌐_Live_Demo-View_Project-ea580c?style=for-the-badge&labelColor=fff7ed)](https://mohammed-kandeel.github.io/07-clarity-seven-drab-/)
[![GitHub](https://img.shields.io/badge/GitHub-Source_Code-181717?style=for-the-badge&logo=github)](https://github.com/mohammed-kandeel/07-clarity-seven-drab-)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)
![Bootstrap](https://img.shields.io/badge/Bootstrap_5-7952B3?style=for-the-badge&logo=bootstrap&logoColor=white)

</div>

---

## 📌 About

**Clarity** is a fully responsive digital solutions landing page — the **Bootstrap Exam** of my Frontend learning journey. The challenge was to produce a pixel-perfect implementation of a given design mockup using Bootstrap 5, extended with a hand-built utility and design token system, all within a strict deadline.

---

## ✨ Technical Highlights

### 1. OKLCH Color System — Modern CSS Color Space

Unlike the previous projects that used `rgb()`, Clarity's design system is built entirely on **OKLCH** — the perceptually uniform color space that produces more consistent and accessible color scales.

```css
:root {
  --blue-500: 62.3% 0.214 259.815;
  --orange-500: 70.5% 0.213 47.604;
}

/* Usage */
.bg-blue-500 {
  background-color: oklch(var(--blue-500) / var(--bs-bg-opacity));
}
```

This approach separates the color channel values from the `oklch()` function, making every color opacity-controllable via a single `--bs-bg-opacity` variable.

---

### 2. Fully Custom Utility System — No Tailwind

Rather than relying on Tailwind or Bootstrap alone, the project includes a hand-crafted `utilities.css` that defines every spacing, sizing, typography, and color utility class used — all mapped to CSS custom properties.

```css
/* Font size with matching line-height — both in one token */
--font-size-18: 1.125rem;
--font-size-18--line-height: calc(1.75 / 1.125);

.fs-18 {
  font-size: var(--font-size-18);
  line-height: var(--font-size-18--line-height);
}
```

Every `fs-*` class carries its mathematically correct line-height — no guessing, no overrides.

---

### 3. Multi-Level Gradient System

The brand uses a three-color gradient identity (primary → secondary → accent). A full set of named gradient utility classes handles every combination directionally.

```css
.linear-gradient-br-primary-secondary {
  background-image: linear-gradient(
    to bottom right,
    rgba(var(--primary), var(--bs-bg-opacity)),
    rgba(var(--secondary), var(--bs-bg-opacity))
  );
}
.linear-gradient-r-primary-secondary-accent {
  background-image: linear-gradient(
    to right,
    rgba(var(--primary)),
    rgba(var(--secondary)),
    rgba(var(--accent))
  );
}
```

Combined with `.text-clip`, this powers the gradient text effect on headings across the page.

---

### 4. Animated Mega Dropdown Navigation

The Services nav item opens a full-width mega menu with three grouped columns — each with an icon, title, and description. The layout switches between 1, 2, and 3 columns based on viewport, and adapts its "Need help?" card placement accordingly.

```css
.dropdown-menu {
  animation: 0.5s ease-out fadeInUp;
}
.inner {
  grid-template-columns: repeat(1, minmax(0, 1fr)); /* mobile */
}
@media (min-width: 768px)  { grid-template-columns: repeat(2, 1fr); }
@media (min-width: 1280px) { grid-template-columns: repeat(3, 1fr); }
```

The dropdown arrow rotates 180° on open via a CSS transition tied to Bootstrap's `.show` class.

---

### 5. Bootstrap Tabs — Technology Stack Section

The Technology section uses Bootstrap's Pills Tab component to switch between Frontend, Backend, Mobile, Cloud & DevOps, and Database stacks — each tab rendering a 3-column card grid with a `fadeInUp` animation on activation.

```css
.tab-content .active {
  animation: 0.5s ease-out fadeInUp;
}
```

Each technology card has a unique gradient background and color-coded badges — all built from the utility system.

---

### 6. Bootstrap Accordion — FAQ Section

The FAQ uses Bootstrap's Accordion with a single-open constraint (`data-bs-parent`). Custom CSS overrides the default styling: the toggle icon rotates on expand, the item border changes color on hover, and the background shifts subtly.

```css
button[aria-expanded='true'] span:last-child {
  transform: rotate(180deg);
}
.item:hover {
  border-color: rgba(234, 90, 12, 0.3);
}
```

---

### 7. Bootstrap Carousel — Testimonials

The testimonials section uses Bootstrap's auto-advancing Carousel with custom dot indicators that expand on hover and fill with the brand color when active.

```css
.carousel-indicators [data-bs-target] {
  width: 7px;
  border-radius: 14px;
  transition: all 0.3s;
}
.carousel-indicators [data-bs-target]:hover {
  width: 28px;
  background-color: rgba(234, 90, 12, 0.5);
}
.carousel-indicators [data-bs-target].active {
  background-color: var(--color-primary);
}
```

---

### 8. Bootstrap Modal — Contact Form Confirmation

Submitting the contact form triggers a Bootstrap Modal for confirmation feedback — styled to match the page's dark aesthetic, overriding Bootstrap's default light modal appearance.

```css
.modal-content {
  background-color: #1f1f1f;
  max-width: 460px;
  margin-inline: auto;
}
```

---

### 9. Radio Button Budget Selector — CSS-Only

The budget range selector in the contact form is built with hidden `<input type="radio">` elements styled via the adjacent sibling combinator — no JavaScript needed.

```css
.radio { display: none; }

.radio:checked + .form-control {
  border-color: var(--color-primary);
  background-color: rgba(234, 90, 12, 0.1);
}
```

Clicking the label selects it visually with a brand-colored border and tinted background.

---

### 10. Custom Container Breakpoint System

Bootstrap's default container widths were replaced with a custom responsive system that more closely follows the design mockup's layout at each breakpoint.

```css
@media (min-width: 640px)  { .container { max-width: 560px; } }
@media (min-width: 768px)  { .container { max-width: 672px; } }
@media (min-width: 1024px) { .container { max-width: 896px; } }
@media (min-width: 1280px) { .container { max-width: 1280px; } }
```

---

## 🧩 Sections

| Section | Description |
|---|---|
| **Navbar** | Fixed nav with mega dropdown, ScrollSpy, responsive collapse |
| **Hero** | Full-viewport gradient background, rotated image card with floating icons |
| **Services** | 3-column card grid with lift-on-hover and icon scale effect |
| **Technology** | Bootstrap Pills Tabs — 5 stacks, animated card grids per tab |
| **Testimonials** | Auto-playing Bootstrap Carousel with custom expandable dot indicators |
| **FAQ** | Bootstrap Accordion with rotating arrow toggle |
| **Contact** | Split-panel form with CSS-only radio selector and modal confirmation |
| **Footer** | Social links with hover color fill, copyright bar |

---

## 🛠️ Built With

- **HTML5** — Semantic markup, accessibility attributes (`aria-*`, `role`)
- **CSS3** — OKLCH color space · Custom Properties · Grid · Transitions · `@keyframes`
- **Bootstrap 5** — Navbar · Dropdown · Tabs · Carousel · Accordion · Modal · ScrollSpy
- **Font Awesome 6** — Icon library
- **Inter** — Google Fonts typeface

---

## 🚀 Getting Started

```bash
git clone https://github.com/mohammed-kandeel/07-clarity-seven-drab-.git
cd 07-clarity-seven-drab-
# Open index.html in your browser
```

Or visit the [Live Demo](https://mohammed-kandeel.github.io/07-clarity-seven-drab-/) directly.

---

<div align="center">
  Built with ❤️ by <strong>Mohammed Kandeel</strong>
</div>
