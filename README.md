# Endless Logo Loader

A lightweight, endless loading animation built with pure HTML, CSS and a few lines of JavaScript. A logo pulses inside a spinning ring and keeps "loading" until the visitor presses **Stop loading** and then **Continue** to enter the site.

No libraries, no build step. Just open `index.html`.

## Features

- Endless loop: the logo pulse, ring spin and animated dots repeat forever
- **Stop loading** button that freezes the animation
- **Continue** button that fades the loader out and reveals the page
- Fully customizable logo (SVG or image), colors and speed
- Responsive and centered on any screen size
- Keyboard accessible, with focus styles and an `aria-live` status message
- Respects the `prefers-reduced-motion` setting
- Zero dependencies

## Demo

Open `index.html` in any modern browser:

```bash
git clone https://github.com/<your-username>/endless-logo-loader.git
cd endless-logo-loader
```

Then double-click `index.html`, or serve it locally:

```bash
npx serve .
```

## How it works

| Part | What it does |
| --- | --- |
| `#loader` | Full-screen fixed overlay that covers the page |
| `.ring` | Circle with colored borders, rotated forever with `@keyframes spin` |
| `.logo` | Logo that scales and fades forever with `@keyframes pulse` |
| `.dots span` | Three dots that blink with staggered `animation-delay` |
| Stop button | Adds a `stopped` class, which sets `animation-play-state: paused` |
| Continue button | Adds a `hidden` class (fade out), then removes the loader from the DOM |

## Customization

**Use your own logo**

Replace the placeholder `<svg class="logo">…</svg>` in `index.html` with:

```html
<img class="logo" src="your-logo.png" alt="Your brand">
```

**Change colors**

Edit the CSS variables at the top of the `<style>` block:

```css
:root {
  --bg: #0f1115;
  --accent: #4cc9f0;
  --accent-2: #7b61ff;
  --text: #e8eaf0;
}
```

**Change speed**

- Ring speed: change `1.4s` in `animation: spin 1.4s linear infinite;`
- Logo pulse speed: change `1.8s` in `animation: pulse 1.8s ease-in-out infinite;`

**Hide automatically instead of using buttons**

Remove the buttons and use the page `load` event:

```js
window.addEventListener("load", () => {
  document.getElementById("loader").classList.add("hidden");
});
```

## Project structure

```
endless-logo-loader/
├── index.html   # markup, styles and script in one file
└── README.md
```

## Browser support

Works in all modern browsers (Chrome, Edge, Firefox, Safari). Uses CSS custom properties, `inset` and CSS animations.

## License

Released under the [MIT License](LICENSE). Free to use, modify and share.
