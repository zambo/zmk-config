# Keymap-Drawer Customization Guide

## 📋 Table of Contents

1. [Font Customization](#fonts)
2. [Adding Symbols & Icons](#symbols)
3. [Color Schemes & Styling](#colors)
4. [Layout & Spacing](#layout)
5. [Key Legend Mapping](#legends)
6. [Advanced Styling](#advanced)

---

## 🔤 Font Customization {#fonts}

### Basic Font Changes

```yaml
draw_config:
  svg_extra_style: |
    svg.keymap {
      font-family: 'Fira Code', 'Cascadia Code', monospace;
      font-size: 18px;
      font-weight: 500;
    }
```

### Different Fonts for Different Elements

```yaml
draw_config:
  svg_extra_style: |
    /* Layer headers */
    text.label {
      font-family: 'Inter', sans-serif;
      font-size: 32px;
      font-weight: 700;
    }

    /* Key legends */
    .tap {
      font-family: 'SF Mono', monospace;
      font-weight: 600;
    }

    /* Hold/shifted legends */
    .hold, .shifted {
      font-family: 'Inter', sans-serif;
      font-size: 14px;
    }
```

### Font Size Control

```yaml
draw_config:
  # Auto-shrink long legends
  shrink_wide_legends: 5  # chars threshold

  # Control line spacing for multi-line text
  line_spacing: 1.3

  svg_extra_style: |
    /* Responsive font sizing */
    .tap { font-size: 20px; }
    .hold { font-size: 16px; }
    .shifted { font-size: 14px; }
```

---

## 🎨 Adding Symbols & Icons {#symbols}

### Material Design Icons (Recommended)

```yaml
# Use built-in icon sources
zmk_keycode_map:
  # Navigation
  UP: $$mdi:arrow-up-bold$$
  DOWN: $$mdi:arrow-down-bold$$
  LEFT: $$mdi:arrow-left-bold$$
  RIGHT: $$mdi:arrow-right-bold$$

  # Media controls
  C_MUTE: $$mdi:volume-off$$
  C_VOL_UP: $$mdi:volume-high$$
  C_VOL_DN: $$mdi:volume-low$$
  C_NEXT: $$mdi:skip-next$$
  C_PREV: $$mdi:skip-previous$$
  C_PP: $$mdi:play-pause$$

  # System
  ENTER: $$mdi:keyboard-return$$
  BSPC: $$mdi:backspace$$
  TAB: $$mdi:keyboard-tab$$
  SPACE: $$mdi:keyboard-space$$
  ESC: $$mdi:keyboard-esc$$

  # Modifiers
  LCTRL: $$mdi:apple-keyboard-control$$
  LSHIFT: $$mdi:apple-keyboard-shift$$
  LALT: $$mdi:apple-keyboard-option$$
  LGUI: $$mdi:apple-keyboard-command$$
```

### Icon Sources Available

• `$$mdi:icon-name$$` - Material Design Icons
• `$$mdil:icon-name$$` - Material Design Icons Light
• `$$material:icon-name$$` - Google Material Symbols
• `$$tabler:icon-name$$` - Tabler Icons
• `$$phosphor:weight/name$$` - Phosphor Icons
• `$$fa:type/name$$` - Font Awesome

### Custom SVG Glyphs

```yaml
draw_config:
  glyphs:
    vol_up: |
      <svg viewBox="2 3 34 33">
        <path style="stroke: black; fill: black;" d="M23.41,25.25a1,1,0,0,1-.54-1.85..."/>
      </svg>
    bluetooth: |
      <svg viewBox="0 0 24 24">
        <path d="M17.71 7.71L12 2h-1v7.59L6.41 5 5 6.41 10.59 12 5 17.59..."/>
      </svg>

# Use custom glyphs
zmk_keycode_map:
  C_VOL_UP: $$vol_up$$
  BT_CLR: $$bluetooth$$
```

### Icon Sizing

```yaml
draw_config:
  glyph_tap_size: 22     # Main legend icons
  glyph_hold_size: 16    # Hold legend icons
  glyph_shifted_size: 14 # Shifted legend icons
```

---

## 🌈 Color Schemes & Styling {#colors}

### Material Design Color Palette

```yaml
draw_config:
  svg_extra_style: |
    svg.keymap {
      /* Define color variables */
      --color-bg: #fafafa;
      --color-text: #37474f;
      --color-key-bg: #ffffff;
      --color-key-border: #e0e0e0;
      --color-accent: #2196f3;

      /* Layer-specific colors */
      --color-nav-bg: #e8f5e8;
      --color-fn-bg: #fff3e0;
      --color-num-bg: #f3e5f5;
      --color-sys-bg: #ffebee;
    }

    /* Apply colors */
    rect.key {
      fill: var(--color-key-bg);
      stroke: var(--color-key-border);
      stroke-width: 1;
    }

    /* Layer-specific styling */
    .layer-Nav rect.key {
      fill: var(--color-nav-bg);
    }

    .layer-Fn rect.key {
      fill: var(--color-fn-bg);
    }
```

### Dark Mode Support

```yaml
draw_config:
  dark_mode: auto  # or true/false

  svg_extra_style: |
    /* Light mode colors */
    svg.keymap {
      --color-bg: #ffffff;
      --color-text: #2e3440;
    }

    /* Dark mode overrides */
    @media (prefers-color-scheme: dark) {
      svg.keymap {
        --color-bg: #2e3440;
        --color-text: #d8dee9;
      }
    }
```

### Key Type Styling

```yaml
draw_config:
  svg_extra_style: |
    /* Modifier keys */
    .held rect.key {
      fill: #e3f2fd;
      stroke: #bbdefb;
    }

    /* Transparent keys */
    .trans rect.key {
      opacity: 0.4;
    }

    /* Special key types */
    .bootloader rect.key {
      fill: #ffebee;
      stroke: #ffcdd2;
    }

    /* Home row modifiers */
    .keypos-13 rect.key,
    .keypos-14 rect.key,
    .keypos-15 rect.key,
    .keypos-16 rect.key {
      fill: #f3e5f5;
    }
```

---

## 📐 Layout & Spacing {#layout}

### Key Dimensions & Spacing

```yaml
draw_config:
  # Key size
  key_h: 60
  key_w: 60  # For non-ortho layouts

  # Rounded corners
  key_rx: 6
  key_ry: 6

  # Spacing
  inner_pad_w: 2    # Between keys
  inner_pad_h: 2
  outer_pad_w: 30   # Between layers
  outer_pad_h: 56

  # Split keyboard gap
  split_gap: 30
```

### Multi-Column Layouts

```yaml
draw_config:
  n_columns: 2  # Show 2 layers side-by-side
```

### Combo Styling

```yaml
draw_config:
  # Combo box size
  combo_w: 28
  combo_h: 26

  # Separate combo diagrams
  separate_combo_diagrams: false
  combo_diagrams_scale: 2

  svg_extra_style: |
    /* Combo styling */
    rect.combo {
      fill: #f5f5f5;
      stroke: #e0e0e0;
      opacity: 0.8;
    }

    path.combo {
      stroke: #9e9e9e;
      stroke-width: 1;
    }
```

---

## 🏷️ Key Legend Mapping {#legends}

### Basic Key Mapping

```yaml
parse_config:
  zmk_keycode_map:
    # Simple text replacement
    BSPC: Bksp
    DEL: Del
    ESC: Esc

    # Multi-character legends
    CAPSLOCK: Caps

    # Number keys with shift symbols
    N1:
      tap: "1"
      shifted: "!"
    N2:
      tap: "2"
      shifted: "@"
```

### Complex Key Behaviors

```yaml
parse_config:
  raw_binding_map:
    # Hold-tap behaviors
    "&mt LSHIFT A":
      tap: A
      hold: $$mdi:apple-keyboard-shift$$

    # Layer tap
    "&lt NUM ESC":
      tap: $$mdi:keyboard-esc$$
      hold: Num

    # Custom behaviors
    "&magic_shift":
      tap: Magic
      hold: $$mdi:apple-keyboard-shift$$
      shifted: $$mdi:alpha-w-box$$
```

### Layer Names

```yaml
parse_config:
  layer_legend_map:
    "Base": "⌂"
    "Navigation": "⇅"
    "Numbers": "123"
    "Function": "Fn"
```

---

## 🎨 Advanced Styling {#advanced}

### Custom CSS Classes

```yaml
draw_config:
  svg_extra_style: |
    /* Create custom key classes */
    .keypos-0 rect.key,
    .keypos-11 rect.key {
      fill: #ffeb3b; /* Highlight specific keys */
    }

    /* Style specific glyphs */
    .glyph.mdi-bluetooth {
      fill: #2196f3;
    }

    /* Layer-specific text colors */
    .layer-Nav .tap {
      fill: #1b5e20;
    }
```

### Animation & Effects

```yaml
draw_config:
  svg_extra_style: |
    /* Hover effects */
    rect.key:hover {
      filter: brightness(1.1);
      transition: filter 0.2s;
    }

    /* Gradient fills */
    .special rect.key {
      fill: url(#gradient);
    }

    /* Add gradients in defs */
    svg {
      background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
    }
```

### Typography Fine-Tuning

```yaml
draw_config:
  svg_extra_style: |
    /* Precise text positioning */
    .shifted {
      translate: 26px 2px;
      font-size: 16px;
    }

    .hold {
      translate: 26px 4px;
      font-size: 16px;
    }

    /* Text rendering quality */
    text {
      text-rendering: optimizeLegibility;
      font-kerning: normal;
    }
```

---

## 💡 Best Practices Summary

### ✅ Do's

• Start with `keymap dump-config` to get the default settings
• Use Material Design Icons for consistency and variety
• Define color variables for easy theme maintenance
• Test incremental changes - add one feature at a time
• Use the web interface for quick testing and iteration
• Cache is your friend - icons are cached locally for performance

### ❌ Don'ts

• Don't modify `svg_style` directly - use `svg_extra_style` instead
• Don't hardcode colors - use CSS variables for maintainability
• Don't forget `viewBox` when creating custom SVG glyphs
• Don't mix text and glyphs in the same legend field
• Don't make legends too long - use `shrink_wide_legends`

### 🔧 Debugging Tips

• Use browser dev tools to inspect generated SVG
• Test your config with `keymap -c config.yaml draw keymap.yaml`
• Check the [examples](https://github.com/caksoylar/keymap-drawer/tree/main/examples) for inspiration
• Join the [discussions](https://github.com/caksoylar/keymap-drawer/discussions) for community help

This comprehensive approach will give you professional-looking keymap diagrams with consistent styling and excellent readability!