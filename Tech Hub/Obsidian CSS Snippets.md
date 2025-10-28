# Obsidian CSS Snippets
[[Tech Hub]] #hub/tech #category/notes
```css
/* Remove the title bar completely */
.titlebar {
    display: none !important;
}

/* Remove any leftover padding or margin */
body,
.workspace,
.workspace-split,
.workspace-tabs,
.workspace-tab-container {
    margin-top: 0 !important;
    padding-top: 0 !important;
}

/* Ensure the main content fills the entire height */
.workspace {
    height: 100vh !important;
}


body {
    background: #121212 !important;
    color: #e0e0e0 !important;
    font-family: "Segoe UI", sans-serif !important;
}

.workspace-leaf-content {
    background: rgba(30, 30, 30, 0.6) !important;
    backdrop-filter: blur(14px) !important;
    border-radius: 12px !important;
    box-shadow: 0 4px 20px rgba(255, 255, 255, 0.05) !important;
}

@keyframes liquid-drip {
    0% { transform: translateY(-10px); opacity: 0.7; }
    50% { transform: translateY(5px); opacity: 1; }
    100% { transform: translateY(0); opacity: 0.8; }
}

.callout {
    background: rgba(28, 28, 28, 0.95) !important; /* Slightly lighter than #121212 */
    backdrop-filter: blur(12px) !important;
    border-radius: 12px !important;
    padding: 14px !important;
    font-weight: bold !important;
    position: relative !important;
}

.callout::after {
    content: '' !important;
    display: block !important;
    width: 8px !important;
    height: 8px !important;
    background: rgba(255, 255, 255, 0.2) !important;
    border-radius: 50% !important;
    position: absolute !important;
    bottom: -10px !important;
    left: 20px !important;
    animation: liquid-drip 2s infinite ease-in-out !important;
}

.callout[data-callout="info"] {
    border-left: 4px solid #b0c4de !important;
    color: #b0c4de !important;
}
.callout[data-callout="example"] {
    border-left: 4px solid #d8bfd8 !important;
    color: #d8bfd8 !important;
}
.callout[data-callout="tip"] {
    border-left: 4px solid #c3e6cb !important;
    color: #c3e6cb !important;
}
.callout[data-callout="quote"] {
    border-left: 4
```

```css
/* ✅ Softer blur and lighter background */
.modal-container {
    backdrop-filter: blur(8px);
    background-color: rgba(0, 0, 0, 0.08);
    transform-origin: center center;
}

/* ✅ Force animation every time modal opens */
.modal-container.is-open {
    animation: liquidBounceBig 1.2s cubic-bezier(0.22, 1.61, 0.36, 1);
}

/* ✅ Bounce for tabs (slightly faster) */
.workspace-leaf.is-active {
    animation: liquidBounceBig 1s cubic-bezier(0.22, 1.61, 0.36, 1);
}

/* Keyframes for BIG bounce with multiple phases */
@keyframes liquidBounceBig {
    0% {
        opacity: 0.8;
        transform: scale(0.7); /* start very small */
    }
    30% {
        transform: scale(1.25); /* huge overshoot */
    }
    55% {
        transform: scale(0.85); /* shrink back */
    }
    75% {
        transform: scale(1.1); /* bounce up */
    }
    90% {
        transform: scale(0.98); /* tiny settle */
    }
    100% {
        opacity: 1;
        transform: scale(1);
    }
}
```


```css
/* Windows 11 Liquid Glass Theme */
body {
  background: url('your-background-image.jpg') center/cover no-repeat fixed;
  backdrop-filter: blur(20px);
}

.markdown-preview-view {
  background: rgba(255, 255, 255, 0.08);
  border-radius: 16px;
  box-shadow: 0 8px 32px rgba(0, 0, 0, 0.3);
  padding: 20px;
}

table {
  width: 100%;
  border-collapse: collapse;
  backdrop-filter: blur(10px);
  background: rgba(255, 255, 255, 0.05);
  border-radius: 12px;
}

th, td {
  padding: 12px;
  text-align: left;
  color: #fff;
}

h1, h2, h3 {
  font-family: 'Segoe UI', sans-serif;
  color: #ffffff;
}

a {
  color: #00aaff;
}

.callout {
  background: rgba(255, 255, 255, 0.08);
  border-left: 4px solid #00aaff;
  border-radius: 8px;
}
```