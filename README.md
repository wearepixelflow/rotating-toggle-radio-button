<div align="center">

# Rotating Toggle Radio Button

**A pure HTML & CSS wheel-style selector with buttery-smooth rotation, glassmorphism, and zero JavaScript.**

[![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/HTML)
[![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)](https://developer.mozilla.org/en-US/docs/Web/CSS)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg?style=for-the-badge)](#-license)

[![GitHub Repo stars](https://img.shields.io/github/stars/wearepixelflow/rotating-toggle-radio-button?style=flat-square&color=blueviolet)](https://github.com/wearepixelflow/folder-hover-animation/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/wearepixelflow/rotating-toggle-radio-button?style=flat-square&color=blue)](https://github.com/wearepixelflow/folder-hover-animation/network/members)
[![Last commit](https://img.shields.io/github/last-commit/wearepixelflow/rotating-toggle-radio-button?style=flat-square)](https://github.com/wearepixelflow/folder-hover-animation/commits/main)
[![Made with love](https://img.shields.io/badge/Made%20with-%E2%9D%A4-red?style=flat-square)](#-author)

[Preview](#-preview) · [Quick Start](#-quick-start) · [How It Works](#-how-the-wheel-animation-works) · [Customization](#-customization) · [FAQ](#-faq)

</div>

<br />

<div align="center">
  <img src="assets/preview.gif" alt="Rotating Toggle Radio Button demo" width="640" />
</div>

<br />

---

## Overview

Rotating Toggle Radio Button is a self-contained UI component that replaces the traditional radio group with a **rotating wheel selector** — the kind of refined, tactile interaction usually reserved for native apps. It's built entirely with HTML and CSS: no dependencies, no build step, no JavaScript.

Drop it into any project, style it with CSS variables, and get a production-ready selector with glassmorphism surfaces and physically-inspired motion out of the box.

<br />

## ✨ Features

| | |
|---|---|
| **🎡 Smooth Wheel Rotation** | Physically-inspired easing makes every selection feel deliberate, not robotic. |
| **🧊 Glassmorphism Overlay** | Frosted, translucent layers add depth without weighing down the UI. |
| **⚡ Zero JavaScript** | Fully driven by native CSS — radio inputs, transforms, and transitions. |
| **🎨 Themeable by Design** | Every visual property is exposed as a CSS custom property. |
| **📱 Responsive Structure** | Scales cleanly from mobile widths to desktop layouts. |
| **🪶 Lightweight** | A single stylesheet, no external assets required to run. |
| **♿ Accessible Foundation** | Built on native `<input type="radio">` elements, not custom `<div>` fakery. |
| **🚀 Production-Ready** | Clean markup and predictable class names, ready to drop into real products. |

<br />

## 📸 Preview

<div align="center">
  <img src="assets/preview.gif" alt="Wheel selector rotating between options" width="480" />
  <br />
  <sub>Rotating wheel transitioning between three states</sub>
</div>

<br />

<details>
<summary><strong>Static screenshot</strong></summary>
<br />
<div align="center">
  <img src="assets/screenshot.png" alt="Rotating Toggle Radio Button static screenshot" width="480" />
</div>
</details>

<br />

## 🚀 Quick Start

```bash
git clone https://github.com/wearepixelflow/rotating-toggle-radio-button.git
cd rotating-toggle-radio-button
```

Then simply open `index.html` in a browser — there's no build step and no dependencies to install.

```
open index.html        # macOS
start index.html        # Windows
xdg-open index.html     # Linux
```

<br />



## ⚙️ How the Wheel Animation Works

The component is powered by three CSS mechanisms working together — no JavaScript involved:

**1. Native radio state as the source of truth**
Each option is a hidden `<input type="radio">` bound to a `<label>`. The `:checked` pseudo-class is the only "state" the component has, which is what keeps everything CSS-only.

**2. Rotation via `transform`**
The wheel's rotation angle is stored as a CSS custom property (e.g. `--wheel-rotation`) and applied with `transform: rotate(var(--wheel-rotation))`. When a different radio input is checked, a sibling combinator (`~`) or `:has()` selector updates which angle applies to the wheel.

**3. Motion via `transition`**
A `transition: transform var(--duration) var(--easing)` on the wheel interpolates between angles smoothly, rather than snapping. An easing curve close to `cubic-bezier(0.22, 1, 0.36, 1)` gives the rotation its natural, weighted deceleration.

The glassmorphism layer sits above the wheel using `backdrop-filter: blur()` with a semi-transparent background, so the frosted surface reacts to whatever is rotating underneath it.

```css
.wheel {
  transform: rotate(var(--wheel-rotation, 0deg));
  transition: transform 480ms cubic-bezier(0.22, 1, 0.36, 1);
}

input:nth-of-type(2):checked ~ .wheel { --wheel-rotation: 120deg; }
input:nth-of-type(3):checked ~ .wheel { --wheel-rotation: 240deg; }
```

<br />

## 🌐 Browser Compatibility

| Browser | Supported | Notes |
|---|:---:|---|
| Chrome / Edge (Chromium) | ✅ | Full support, including `backdrop-filter`. |
| Firefox | ✅ | Full support since v103+. |
| Safari (macOS & iOS) | ✅ | Requires `-webkit-backdrop-filter` prefix, included. |
| Opera | ✅ | Full support. |
| Internet Explorer | ❌ | Not supported — no CSS custom property or `backdrop-filter` support. |

> `:has()`-based variants require a browser released 2023 or later. A `~` sibling-selector fallback is included for broader coverage.

<br />

## 🎨 Customization

Every visual property is exposed as a CSS custom property on `:root` or the component wrapper, so theming doesn't require touching the core styles.

```css
.rotating-toggle {
  --accent-color: #6366f1;
  --wheel-size: 220px;
  --border-radius: 999px;
  --rotation-duration: 480ms;
  --rotation-easing: cubic-bezier(0.22, 1, 0.36, 1);
  --glass-blur: 12px;
  --glass-opacity: 0.15;
  --shadow: 0 20px 40px rgba(0, 0, 0, 0.25);
  --font-family: "Inter", system-ui, sans-serif;
}
```

| Property | Controls |
|---|---|
| `--accent-color` | Selected-state highlight color |
| `--wheel-size` | Overall diameter of the wheel |
| `--border-radius` | Corner rounding of the wheel and labels |
| `--rotation-duration` | Speed of the rotation transition |
| `--rotation-easing` | Motion curve of the rotation |
| `--glass-blur` | Intensity of the glassmorphism blur |
| `--glass-opacity` | Translucency of the glass overlay |
| `--shadow` | Elevation shadow beneath the wheel |
| `--font-family` | Typography used for option labels |

Adding an option is just another `<input>` / `<label>` pair plus one rotation-angle rule — no JavaScript changes required.

<br />

## ♿ Accessibility

- Built on native `<input type="radio">` elements, so keyboard navigation (<kbd>Tab</kbd>, <kbd>Arrow keys</kbd>, <kbd>Space</kbd>) works without extra code.
- Each option should have an associated `<label>` with descriptive text, or an `aria-label` if the label is visual-only.
- Focus states are styled via `:focus-visible` rather than suppressed — never remove the outline without providing a visible replacement.
- Respects `prefers-reduced-motion`; wheel transitions shorten to a near-instant duration when the user has motion sensitivity enabled.
- Color contrast between the selected state and background meets WCAG AA at default theme values — verify again after customizing `--accent-color`.

<br />

## ⚡ Performance

- **Zero JavaScript** means zero parse/execution cost — the component's interactivity is delivered entirely through the browser's native CSS engine.
- Animations use `transform`, which is GPU-accelerated and avoids triggering layout or paint on every frame.
- No external fonts or icon libraries are required by default, keeping the component's footprint to a single stylesheet.
- `backdrop-filter` is the most expensive property in use; on lower-end devices, consider reducing `--glass-blur` or disabling it via a `prefers-reduced-motion` / capability query.

<br />

## 💡 Use Cases

- Settings panels
- Product configurators
- Pricing plan switchers
- Theme selectors (light / dark / system)
- Dashboard controls
- Interactive landing pages
- Portfolio websites
- Premium UI component libraries

<br />

## 🗺️ Roadmap

- [ ] Vertical wheel orientation variant
- [ ] Optional snap-to-tick haptic-style feedback (CSS-only)
- [ ] Framework wrappers (React, Vue, Svelte) as thin adapters over the same markup
- [ ] Additional prebuilt themes (minimal, neumorphic, high-contrast)
- [ ] RTL layout support
- [ ] Storybook-style interactive docs site

<br />

## 🤝 Contributing

Contributions are welcome and appreciated.

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/my-improvement`
3. Make your changes, keeping the component pure HTML/CSS (no JS dependencies)
4. Test across the browsers listed in [Browser Compatibility](#-browser-compatibility)
5. Commit using clear, conventional messages
6. Open a pull request describing the change and its motivation

Please open an issue first for larger changes so the direction can be discussed before implementation.

<br />

## ❓ FAQ

<details>
<summary><strong>Does this require any JavaScript at all?</strong></summary>
<br />
No. Selection state, rotation, and transitions are handled entirely by native <code>&lt;input type="radio"&gt;</code> elements and CSS. JavaScript is optional and only useful if you want to hook into selection changes for application logic outside the component.
</details>

<details>
<summary><strong>Can I use this with React, Vue, or another framework?</strong></summary>
<br />
Yes. Since it's plain HTML and CSS, you can copy the markup structure directly into a component in any framework. A framework-agnostic core is part of the <a href="#-roadmap">roadmap</a>.
</details>

<details>
<summary><strong>How many options can the wheel support?</strong></summary>
<br />
There's no hard limit — each option is just an additional input/label pair and a corresponding rotation angle. Practically, 3–6 options give the best balance of usability and visual clarity.
</details>

<details>
<summary><strong>Why isn't the glass effect showing in my browser?</strong></summary>
<br />
The glassmorphism overlay relies on <code>backdrop-filter</code>. Confirm your browser is on the supported list in <a href="#-browser-compatibility">Browser Compatibility</a>, and that the element behind the wheel isn't fully opaque.
</details>

<details>
<summary><strong>Can I disable the rotation animation?</strong></summary>
<br />
Yes — set <code>--rotation-duration: 0ms</code>, or rely on the built-in <code>prefers-reduced-motion</code> handling to do it automatically for users who need it.
</details>

<br />

## 📄 License

Released under the [MIT License](./LICENSE).

<br />

<div align="center">

If this project was useful to you, consider giving it a ⭐ — it genuinely helps.

<sub>Built with HTML, CSS, and an unreasonable amount of attention to easing curves.</sub>

</div>
