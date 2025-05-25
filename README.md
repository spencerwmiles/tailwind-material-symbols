# Material Symbols Tailwind CSS v4 Plugin

Material Symbols specific Tailwind CSS v4 utilities for Google's Material Symbols variable font. This package builds on [`@spencerwmiles/tailwind-font-variations`](https://github.com/spencerwmiles/tailwind-font-variations) to provide icon-optimized utilities and Material Symbols specific features.

The Material Symbols fonts are included via the `material-symbols` dependency and automatically available.

## Installation

```bash
npm install @spencerwmiles/tailwind-material-symbols
```

## Setup

Import in your main CSS file:

```css
@import '@spencerwmiles/tailwind-material-symbols';
```

## Usage

### Basic Material Symbols

```html
<span class="font-ms">home</span>
```

### Font Style Variants

```html
<span class="font-ms font-ms-outlined">favorite</span>
<span class="font-ms font-ms-rounded">favorite</span>
<span class="font-ms font-ms-sharp">favorite</span>
```

### Fill States

```html
<span class="font-ms font-ms-outline">star</span>
<span class="font-ms font-ms-fill">star</span>
<span class="font-ms font-ms-fill-[0.5]">star</span>
```

### Icon Sizes

```html
<span class="font-ms font-ms-xs">close</span>    <!-- 16px -->
<span class="font-ms font-ms-sm">close</span>    <!-- 20px -->
<span class="font-ms font-ms-base">close</span>  <!-- 24px -->
<span class="font-ms font-ms-xl">close</span>    <!-- 32px -->
<span class="font-ms font-ms-5xl">close</span>   <!-- 48px -->
```

### Transitions & Hover States

```html
<span class="font-ms transition-fonts hover:font-ms-fill">favorite</span>
<span class="font-ms font-ms-rounded transition-fonts hover:font-ms-fill hover:font-var-bold">star</span>
```

### With Variable Font Utilities

```html
<span class="font-ms font-var-bold font-var-GRAD-100">settings</span>
<span class="font-ms font-ms-xl font-var-wght-[550]">home</span>
```

## API Reference

### Material Symbols Utilities

- `font-ms` - Base Material Symbols component (defaults to Outlined)
- `font-ms-{outlined|rounded|sharp}` - Font family variants
- `font-ms-{fill|outline}` - Fill states
- `font-ms-fill-*` - Arbitrary fill values
- `font-ms-{xs|sm|base|lg|xl|2xl|3xl|4xl|5xl|6xl|7xl|8xl|9xl}` - Icon sizes
- `transition-fonts` - Transitions for font-variation-settings

### Variable Font Utilities

Includes all utilities from `@spencerwmiles/tailwind-font-variations` for weight, grade, optical size, and other variable font axes.

## Material Symbols Reference

For available symbols, visit the [Material Symbols Library](https://fonts.google.com/icons?icon.set=Material+Symbols).

## License

MIT License - see [LICENSE](./LICENSE) for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request. 