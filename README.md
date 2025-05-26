# Tailwind Material Symbols

Tailwind CSS v4 utilities for Google's Material Symbols variable font. Compatible with tailwind-merge.

This package brings Google's Material Symbols design system to Tailwind CSS, built on top of the excellent [material-symbols](https://github.com/marella/material-symbols) package by [@marella](https://github.com/marella). The material-symbols package provides the latest variable icon fonts and optimized SVGs, automatically updating from Google's official releases to ensure you always have access to the newest icons.

## Installation

```bash
npm install @spencerwmiles/tailwind-material-symbols
```

This package automatically includes two core dependencies:
- `@spencerwmiles/tailwind-font-variations` - Provides variable font utilities
- `material-symbols` - Provides the actual Material Symbols font files

## Setup

### Full Package (All Variants)

Import in your main CSS file to get all three font variants:

```css
@import '@spencerwmiles/tailwind-material-symbols';
```

### Specific Variants (Smaller Bundle Size)

For better performance, import only the variant you need:

```css
/* Outlined only (most common) */
@import '@spencerwmiles/tailwind-material-symbols/outlined.css';

/* Rounded only */
@import '@spencerwmiles/tailwind-material-symbols/rounded.css';

/* Sharp only */
@import '@spencerwmiles/tailwind-material-symbols/sharp.css';
```

**Recommendation**: Use specific imports in production to minimize bundle size. The outlined variant is the most commonly used.

## How It Works

This package uses a **composition approach** with three core packages:

- **This package** (`tailwind-material-symbols`): Provides Material Symbols font families and the FILL axis
- **Font variations package** (`tailwind-font-variations`): Provides weight, grade, and optical size utilities  
- **Material Symbols package** (`material-symbols`): Provides the actual font files from Google

You combine utilities from these packages to create the exact symbol styling you need.

## Usage

### Basic Symbols

```html
<span class="symbol">home</span>
<span class="symbol">favorite</span>
<span class="symbol">settings</span>
```

### Font Variants

When using the full package import, you can switch between variants:

```html
<span class="symbol symbol-outlined">favorite</span>
<span class="symbol symbol-rounded">favorite</span>
<span class="symbol symbol-sharp">favorite</span>
```

When using specific variant imports, the font is already set:

```html
<!-- With outlined.css import -->
<span class="symbol">favorite</span>

<!-- With rounded.css import -->
<span class="symbol">favorite</span>

<!-- With sharp.css import -->
<span class="symbol">favorite</span>
```

### Fill States (Material Symbols Specific)

```html
<!-- Filled (default) -->
<span class="symbol">star</span>

<!-- Outlined -->
<span class="symbol symbol-fill-0">star</span>

<!-- Explicitly filled -->
<span class="symbol symbol-fill-1">star</span>

<!-- Partially filled -->
<span class="symbol symbol-fill-[0.5]">star</span>
```

### Variable Font Axes (From font-variations package)

```html
<!-- Weight -->
<span class="symbol variation-setting-wght-700">settings</span>

<!-- Grade (emphasis) -->
<span class="symbol variation-setting-GRAD-100">home</span>

<!-- Optical size -->
<span class="symbol variation-setting-opsz-48">close</span>

<!-- Negative values -->
<span class="symbol variation-setting-GRAD--25">home</span>
```

### Combining Everything

```html
<!-- Rounded, filled, bold, high grade -->
<span class="symbol symbol-rounded symbol-fill-1 variation-setting-wght-700 variation-setting-GRAD-100">
  star
</span>

<!-- Sharp, outlined, light weight, optimized for large size -->
<span class="symbol symbol-sharp variation-setting-wght-300 variation-setting-opsz-48">
  home
</span>
```

### Responsive Design

```html
<span class="symbol symbol-fill-0 md:symbol-fill-1 variation-setting-wght-400 md:variation-setting-wght-700">
  favorite
</span>
```

### Transitions

```html
<!-- Smooth fill transition -->
<span class="symbol symbol-fill-0 transition-font-variations duration-300 hover:symbol-fill-1">
  favorite
</span>

<!-- Multiple property transitions -->
<span class="symbol symbol-fill-0 transition-font-variations duration-200 hover:symbol-fill-1 hover:variation-setting-wght-700">
  star
</span>
```

### With Tailwind Utilities

```html
<!-- Size with text utilities -->
<span class="symbol text-2xl text-blue-500">home</span>

<!-- With spacing and colors -->
<span class="symbol symbol-fill-1 variation-setting-wght-600 text-red-500 mr-2">
  error
</span>
```

## Customizing Defaults

Override default symbol behavior using Tailwind v4's `@theme` directive. This works reliably across all import methods:

### When Using Full Package (`all.css`)

```css
@import '@spencerwmiles/tailwind-material-symbols';

@theme {
  /* Change default fill (0 = outlined, 1 = filled) */
  --symbol-fill-default: var(--symbol-fill-0);
  
  /* Change default font variant (applies to base symbol utility) */
  --font-family-material-symbols-default: 'Material Symbols Rounded';
}
```

With this setup:
- `<span class="symbol">home</span>` → Uses Rounded variant (your new default)
- `<span class="symbol symbol-outlined">home</span>` → Forces Outlined variant
- `<span class="symbol symbol-sharp">home</span>` → Forces Sharp variant

### When Using Specific Variants

```css
@import '@spencerwmiles/tailwind-material-symbols/rounded.css';

@theme {
  /* Only fill customization is relevant for specific imports */
  --symbol-fill-default: var(--symbol-fill-0);
}
```

### Available Default Variables

```css
@theme {
  /* Fill defaults */
  --symbol-fill-default: var(--symbol-fill-1); /* 1 = filled, 0 = outlined */
  
  /* Font family defaults (all.css only) */
  --font-family-material-symbols-default: 'Material Symbols Outlined'; /* or Rounded/Sharp */
  
  /* Individual variant references (available in all imports) */
  --font-family-material-symbols-outlined: 'Material Symbols Outlined';
  --font-family-material-symbols-rounded: 'Material Symbols Rounded';
  --font-family-material-symbols-sharp: 'Material Symbols Sharp';
}
```

## Import Options

### Full Package (`@import '@spencerwmiles/tailwind-material-symbols'`)
- **Includes**: All three font variants (Outlined, Rounded, Sharp)
- **Size**: Larger bundle (~3 font files)
- **Use case**: When you need multiple variants or want maximum flexibility
- **Utilities**: `symbol-outlined`, `symbol-rounded`, `symbol-sharp` for switching variants

### Specific Variants (`@import '@spencerwmiles/tailwind-material-symbols/outlined.css'`)
- **Includes**: Only the specified variant
- **Size**: Smaller bundle (~1 font file)
- **Use case**: Production apps where you know which variant you need
- **Utilities**: No variant switching utilities (font is pre-set)

## Package Responsibilities

### This Package Provides:
- `symbol` - Base Material Symbols component (filled by default)
- `symbol-outlined/rounded/sharp` - Font family variants (full package only)
- `symbol-fill-1` - Filled state (explicit)
- `symbol-fill-0` - Outlined state
- `symbol-fill-[value]` - Custom fill values (0-1)

### Font Variations Package Provides:
- `variation-setting-wght-*` - Weight axis (100-900)
- `variation-setting-GRAD-*` - Grade axis (-200 to 300)
- `variation-setting-opsz-*` - Optical size axis (8-144)
- `transition-font-variations` - Transition utility
- Plus support for any custom variable font axes

## Why This Approach?

This **composition pattern** provides several benefits:

1. **No Redundancy**: Each package handles what it does best
2. **Maximum Flexibility**: Combine utilities exactly as needed
3. **Tailwind Philosophy**: Composable building blocks, not opinionated combinations
4. **Future Proof**: Easy to extend with new axes or fonts
5. **Bundle Efficiency**: Only includes utilities you actually use

## Material Symbols Reference

For available symbols, visit the [Material Symbols Library](https://fonts.google.com/icons?icon.set=Material+Symbols).



## License

MIT License - see [LICENSE](./LICENSE) for details. 