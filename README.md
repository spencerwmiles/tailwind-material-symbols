# Tailwind Material Symbols

Tailwind CSS v4 utilities for Google's Material Symbols variable font. Compatible with tailwind-merge.

## Installation

```bash
npm install @spencerwmiles/tailwind-material-symbols
```

This package automatically includes `@spencerwmiles/tailwind-font-variations` as a dependency.

## Setup

Import in your main CSS file:

```css
@import '@spencerwmiles/tailwind-material-symbols';
```

## How It Works

This package uses a **composition approach** with two complementary packages:

- **This package** (`tailwind-material-symbols`): Provides Material Symbols font families and the FILL axis
- **Font variations package** (`tailwind-font-variations`): Provides weight, grade, and optical size utilities

You combine utilities from both packages to create the exact symbol styling you need.

## Usage

### Basic Symbols

```html
<span class="symbol">home</span>
<span class="symbol">favorite</span>
<span class="symbol">settings</span>
```

### Font Variants

```html
<span class="symbol symbol-outlined">favorite</span>
<span class="symbol symbol-rounded">favorite</span>
<span class="symbol symbol-sharp">favorite</span>
```

### Fill States (Material Symbols Specific)

```html
<!-- Outlined (default) -->
<span class="symbol">star</span>

<!-- Filled -->
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
<span class="symbol transition-font-variations duration-300 hover:symbol-fill-1">
  favorite
</span>

<!-- Multiple property transitions -->
<span class="symbol transition-font-variations duration-200 hover:symbol-fill-1 hover:variation-setting-wght-700">
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

## Package Responsibilities

### This Package Provides:
- `symbol` - Base Material Symbols component
- `symbol-outlined/rounded/sharp` - Font family variants
- `symbol-fill-*` - FILL axis (0-1, filled vs outlined)

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