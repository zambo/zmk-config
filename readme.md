# zambo's zmk-config

Fork of [urob's zmk-config](https://github.com/urob/zmk-config) adapted for the
**Eyelash Corne** keyboard with 42 keys + joystick + encoder.

## Eyelash Corne Features

- **5-way joystick**: Mouse movement, click, and smooth scrolling with 4K
  display optimization
- **Rotary encoder**: Volume control with RGB brightness on alternate mode
- **MEH keys**: Shift+Ctrl+Alt combinations for app shortcuts
- **Smart pointing**: Context-aware mouse precision and warp modes
- **Power optimized**: 1-hour sleep timeout, optimized debounce (8ms)
- **Enhanced HID**: NKRO support for gaming and productivity

## Notable Improvements

- **Unicode support**: Greek, German, and currency symbols via zmk-unicode
  module
- **Custom mouse tuning**: 600px movement, 20px scroll for 4K displays
- **RGB underglow**: Purple theme (160° hue), auto-off on idle
- **Layer-aware joystick**: Different sensitivities on Nav/Fn layers

See the [original repo](https://github.com/urob/zmk-config) for documentation of
timeless homerow mods, combos, smart layers, and build environment.

![](draw/base.svg)

things to add...

why a numpad and a number layer? well, I rely heavily on shortcuts. I use the
numpad to type numpers, and there are some software I use that needs both for
shortcuts... Blender for example, where numpad changes the camera while regular
numpers select between vertices, edges and faces in edit mode. I've faced issues
like this in other apps, but can't remember which ones at the time of writing
this.

some of urobs keymaps are windows specific. mine, macos specific. I dind't care
about extendability, this is for my use case, and if that helps anyone else,
great.

ive removed some of urobs features, like the space dot thing. macos has this by
default

also, added some common macos shortcuts, show open windows and so on. rarely use
those, but sometimes it's useful to find windows lost in aerospace
