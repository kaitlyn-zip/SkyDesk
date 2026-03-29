```markdown
# Design System Specification: Twilight Aviator

## 1. Overview & Creative North Star
The visual identity of this design system is anchored by the **"Nocturnal Cockpit"** Creative North Star. It is designed to evoke the focused, high-stakes environment of a modern flight deck at twilight—where high-density data meets immersive, atmospheric depth.

Rather than relying on the rigid, "boxed-in" layout of traditional SaaS platforms, this system embraces **Atmospheric Layering**. We move away from flat containers and towards a UI that feels like light projected onto glass. By utilizing intentional asymmetry, variable blur intensities, and high-contrast telemetry, we create a signature experience that is both authoritative and ethereal. 

The goal is to provide a sense of "Command and Control" without the visual clutter of legacy systems, using depth and tonal transitions to guide the eye through complex aviation workflows.

---

## 2. Colors & Surface Philosophy
The palette transitions from the deep shadows of the stratosphere to the sharp, energetic glow of instrumentation.

### The Palette
- **Deep Slate (`surface`: #101222):** The base of our universe. A non-black dark mode that provides more depth than a standard neutral.
- **Twilight Purple (`primary_container`: #4B3F72):** Used for structural grounding and primary brand surfaces.
- **Dawn Orange (`secondary`: #FFB68D):** Our "Action" color. High visibility, reserved for critical telemetry and primary CTAs.
- **Signal White (`on_surface`: #E1E1F7):** A crisp, slightly cooled white to ensure maximum legibility against dark backgrounds.

### Semantic Status Colors (Telemetry Specific)
- **In-Flight (Primary):** `primary` (#CDBEFA) — Indicates active, healthy operations.
- **Aborted (Critical):** `error` (#FFB4AB) — Used for immediate stop-actions and failures.
- **Landing (Warning/Transition):** `secondary` (#FFB68D) — Indicates state changes or caution.

### The "No-Line" Rule & Surface Nesting
In this design system, **lines are a failure of imagination.** To separate sections, designers must use background color shifts rather than 1px borders.
- **Nesting Hierarchy:** 
    - **Background:** `surface_container_lowest` (#0B0D1C)
    - **Main Content Area:** `surface` (#101222)
    - **Module/Card:** `surface_container_low` (#181A2A)
    - **Active/Hover State:** `surface_container_high` (#272939)

### The Glass & Gradient Rule
Floating panels (Modals, Popovers, and Command Palettes) must utilize **Glassmorphism**. Apply a `backdrop-blur` of 12px–20px to `surface_container_highest` at 70% opacity. 
To provide "soul," primary action elements should use a linear gradient: `primary` (#CDBEFA) transitioning to `primary_container` (#4B3F72) at a 135-degree angle.

---

## 3. Typography
We utilize a dual-font strategy to balance editorial sophistication with technical precision.

- **Inter (UI & Narrative):** Used for all `body`, `title`, and `label` roles. It provides the human element—clean, highly readable, and professional.
- **JetBrains Mono (Telemetry & Data):** To be used for all `display` scales and technical readouts (altitudes, timestamps, coordinates). The monospaced nature emphasizes the "Command" aspect of the system.

### Scale Application
- **Display (JetBrains Mono):** For hero data points and high-impact telemetry. Use `display-lg` (3.5rem) for primary flight data.
- **Headlines (Inter):** Use `headline-md` (1.75rem) with tighter tracking (-0.02em) for a high-end editorial feel.
- **Body (Inter):** Use `body-md` (0.875rem) for standard text. Never use pure black text; always use `on_surface_variant` (#CAC4D0) for secondary descriptions to maintain tonal depth.

---

## 4. Elevation & Depth
We eschew traditional drop shadows for **Tonal Layering** and **Ambient Glow**.

- **The Layering Principle:** Depth is achieved by stacking the `surface-container` tokens. An "inner" element should always be visually "higher" (lighter) than its parent container.
- **Ambient Shadows:** For floating glass panels, use an extra-diffused shadow: `box-shadow: 0 24px 48px rgba(0, 0, 0, 0.4);`. The shadow should feel like a natural occlusion of light, not a "drop shadow."
- **The Ghost Border:** If a boundary is required for accessibility, use a "Ghost Border": the `outline_variant` token at **15% opacity**. This creates a hint of an edge that catches the "light" without breaking the immersive atmosphere.
- **Signature Detail:** High-priority cards should feature a **Border Gradient**. A 1px stroke that transitions from `primary` at the top-left to `transparent` at the bottom-right.

---

## 5. Components

### Buttons
- **Primary:** `secondary` (#FFB68D) background with `on_secondary` (#532200) text. Rounding: `md` (0.375rem). Apply a subtle outer glow on hover using the `secondary` color at 10% opacity.
- **Tertiary (Ghost):** No background. Use `on_surface` text. On hover, shift background to `surface_variant` at 20% opacity.

### Telemetry Chips
- Used for flight status.
- **In-Flight:** `primary_container` background with `primary` text.
- **Aborted:** `error_container` background with `error` text.
- **Style:** All chips use `full` rounding (9999px) and JetBrains Mono `label-sm` typography.

### Input Fields
- **Base State:** `surface_container_highest` background, no border.
- **Focus State:** 1px "Ghost Border" using `primary`. The label should shift to `primary` color and `label-sm` size.
- **Spacing:** Use spacing scale `4` (0.9rem) for internal padding to maintain high-density data integrity.

### Data Cards (The High-Density Grid)
Forbid the use of divider lines. Instead, use vertical white space (Scale `6`: 1.3rem) to group data. Use `surface_container_low` for the card base and `surface_container_high` for headers within the card to create a clear visual hierarchy.

### The "Heads-Up" Tooltip
Tooltips are treated as micro-glass elements. Use `surface_container_highest` with a 12px blur and `title-sm` typography. They should appear with a slight "spring" micro-interaction (0.2s ease-out).

---

## 6. Do's and Don'ts

### Do
- **Do** use `JetBrains Mono` for any string containing a number or technical unit.
- **Do** use the Spacing Scale `0.5` (0.1rem) and `1` (0.2rem) for micro-adjustments in high-density telemetry views.
- **Do** leverage variable blur. A background panel should have a 4px blur, while a foreground modal should have a 20px blur to simulate depth of field.

### Don't
- **Don't** use 100% opaque solid borders to define layout sections.
- **Don't** use standard "Material Design" blue for primary actions. Use the `primary` (Twilight Purple/Lavender) or `secondary` (Dawn Orange) tokens.
- **Don't** use shadows on nested elements. Shadows are strictly reserved for elements that "float" (Modals, Menus, Tooltips).
- **Don't** crowd the display. Even in high-density data, use the Spacing Scale `24` (5.5rem) to create "breathing rooms" between major functional groups.