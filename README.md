# Karabiner Elements Config

Personal keyboard remapping for macOS using [Karabiner-Elements](https://karabiner-elements.pqrs.org/). All remapping is implemented as complex modifications — no simple modifications used.

## Profile: `Internal`

Single active profile targeting the built-in (ANSI) keyboard. Two external keyboards are explicitly **ignored** (they have their own firmware-level mapping).

---

## Layer System

Two custom layers implemented via `set_variable`:

| Layer | Trigger | Reset |
|-------|---------|-------|
| **nav_layer** | Hold `Space` | Release `Space` |
| **num_layer** | Hold `Right Cmd` while `nav_layer` is active | Release `Space` |

Tapping `Space` alone (within 150 ms) still sends a regular space.

---

## Rules

### 1. F-Key Row — tap vs. hold

Tap sends the media/system action; hold sends the real Fn key.

| Key | Tap | Hold |
|-----|-----|------|
| F1  | Brightness ↓ | F1 |
| F2  | Brightness ↑ | F2 |
| F3  | Mission Control | F3 |
| F4  | F4 | F4 |
| F5  | Dictation | F5 |
| F6  | F6 | F6 |
| F7  | ⏮ Rewind | F7 |
| F8  | ⏯ Play/Pause | F8 |
| F9  | F9 | F9 |
| F10 | 🔇 Mute | F10 |
| F11 | 🔉 Volume ↓ | F11 |
| F12 | 🔊 Volume ↑ | F12 |

Threshold: 135 ms (slightly higher than the global default of 120 ms).

---

### 2. Caps Lock — tap vs. hold

| Action | Result |
|--------|--------|
| Tap alone | Toggle Caps Lock (real toggle via `vk_none` sequence) 
| Hold | Left Shift |
| `Right Cmd` + Caps Lock | Send actual Caps Lock keycode |

When `nav_layer` is active, Caps Lock is remapped (see Navigation Layer below).

---

### 3. Navigation Layer  (hold `Space`)

#### Cursor & Editing

```
  Nav layer active (hold Space)
  ┌───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┐
  │   │   │   │   │   │   │   │ u │ i │ o │ p │   │
  │   │   │   │   │   │   │   │ 7 │ ↑ │ ⌫ │BS │   │
  ├───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
  │CL │ a │ s │ d │ f │ g │ h │ j │ k │ l │ ; │ ' │
  │⌘⇥ │^  │⇧  │⌥  │⌘  │ = │ - │ ← │ ↓ │ → │ : │ " │
  ├───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
  │ z │   │ c │ v │ b │ n │ m │ , │ . │ / │   │   │
  │⇧· │   │ # │ / │   │   │↩  │ ( │   │ , │   │   │
  └───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
              │       Space (held)        │
```

| Key | Action |
|-----|--------|
| `j` | ← Left Arrow |
| `k` | ↓ Down Arrow |
| `l` | → Right Arrow |
| `i` | ↑ Up Arrow |
| `o` | ⌫ Backspace |
| `tab` | Escape |
| `m` | Return/Enter |
| `z` | Sticky Left Shift |

#### Homerow Modifiers (nav_layer)

| Key | Modifier |
|-----|----------|
| `a` | Left Control |
| `s` | Left Shift |
| `d` | Left Option |
| `f` | Left Command |

Combine with arrow keys, e.g. `Space`+`f`+`j` = `Cmd+Left`.

#### App & Tab Switching

| Combo | Action |
|-------|--------|
| `Caps Lock` | Cmd+Tab (next app) |
| `Shift`+`Caps Lock` | Cmd+Tab (same, shift-held for reverse) |
| `Ctrl`+`Caps Lock` | Ctrl+Tab (next tab) |
| `Left Shift` (non-ZMK) | Cmd+\` (prev window same app) |
| `Left Control` (ZMK kb only) | Ctrl+Shift+Tab (prev tab) |

#### Layout-Independent Symbols

These are emitted regardless of whether the OS input source is EN or RU:

| Key | Tap | Hold |
|-----|-----|------|
| `h` | `-` | `_` |
| `g` | `+` | `=` |
| `t` | `` ` `` | `~` |
| `e` | `%` | `&` |
| `w` | `@` | `$` |
| `c` | `#` | `^` |
| `v` (EN) | `/` | `\|` |
| `v` (RU) | `\|` | `\|` |
| `semicolon` (EN) | `:` | `;` |
| `semicolon` (RU) | `:` | `$` |
| `quote` (RU) | `"` | `'` |
| `comma` (EN) | `(` | `<` |
| `slash` (EN) | `,` | `.` |

#### Volume (nav_layer)

Dedicated Vol Up / Vol Down shortcuts mapped within the nav layer.

#### Flycut (clipboard manager)

`Space`+`Shift`+`x` → triggers Flycut (`Cmd+Shift+V`).

#### Dictation

Dedicated dictation shortcut active within the nav layer.

---

### 4. Num Layer  (hold `Space`, then `Right Cmd`)

A numpad-style layer activated on top of the nav layer. Layout matches the right-hand home row:

```
  Num layer active (Space held + Right Cmd held)
  ┌───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┬───┐
  │   │   │   │   │   │   │   │ u │ i │ o │ p │   │
  │   │   │   │   │   │   │   │ 7 │ 8 │ 9 │ BS│   │
  ├───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
  │   │   │   │   │   │   │   │ j │ k │ l │   │   │
  │   │   │   │   │   │   │   │ 4 │ 5 │ 6 │   │   │
  ├───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┼───┤
  │   │   │   │   │   │   │ m │ , │ . │   │   │   │
  │   │   │   │   │   │   │ 1 │ 2 │ 3 │   │   │   │
  └───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┴───┘
                    │ R⌘ │   R⌥  │
                    │  0 │   .   │
```

| Key | Output |
|-----|--------|
| `m` | 1 |
| `,` | 2 |
| `.` | 3 |
| `j` | 4 |
| `k` | 5 |
| `l` | 6 |
| `u` | 7 |
| `i` | 8 |
| `o` | 9 |
| `Right Cmd` | 0 |
| `Right Alt` | . (keypad period) |
| `p` | ⌫ Backspace |

---

### 5. Language & Register Switch

Two always-active rules integrating with [PuntoSwitcher](https://yandex.ru/soft/punto/):

- **Language toggle** — switches between EN and RU input sources.
- **Register switch** — toggles Punto's case-change function.

---

### 6. Yo

A single-key shortcut to type `ё` / `Ё` regardless of the current input layout.

---

### 7. Autoshift  (alphabets)

Hold any alphabetic key slightly longer than the threshold (~120 ms) to produce the shifted (uppercase) version instead. Uses `to_if_held_down` + `to_after_key_up` pattern. Works on both EN and RU layouts, including special handling for comma/period/slash in RU.

---

### 8. Column Key Placement Remap

Device-conditional remap to correct physical key position differences between staggered-row (Apple internal, standard keyboards) and column-stagger (ZMK-based split) keyboards:

- Swaps `m`/`n`, `` ` `` and a few other keys depending on which keyboard is active.
- Uses `device_if` / `device_unless` + `event_changed_if` conditions to avoid double-firing.

---

## Timing Parameters

| Parameter | Global default | Per-rule overrides |
|-----------|---------------|-------------------|
| `to_if_held_down_threshold_milliseconds` | 120 ms | 130–135 ms (F-keys, some symbols) |
| `to_if_alone_timeout_milliseconds` | default | 150 ms (Space), 250 ms (Caps Lock) |
| `simultaneous_threshold_milliseconds` | default | 1 ms (Caps Lock dual-role) |

---

## Devices

| Vendor ID | Product ID | Treatment |
|-----------|-----------|-----------|
| 10205 | 257 | Ignored (handled by its own firmware) |
| 3118 | 4097 | Ignored (handled by its own firmware) |
| 7504 | 24926 | ZMK keyboard — device-specific rules apply |

---

## Assets / Community Presets

Under `assets/complex_modifications/` (not auto-loaded — import manually via Karabiner's UI if needed):

| File | Description |
|------|-------------|
| `1682800185.json` | Swap Cmd↔Ctrl in Microsoft Remote Desktop and Ericom Blaze |
| `1682069287.json` | Full Autoshift preset (community version) |

---

## Repository Layout

```
karabiner/
├── karabiner.json              # Main config (single profile "Internal")
├── assets/
│   └── complex_modifications/  # Optional community presets
│       ├── 1682800185.json     # RDP Cmd/Ctrl swap
│       └── 1682069287.json     # Autoshift preset
└── automatic_backups/          # Date-stamped auto-backups (git-ignored)
```
