Here is the design brief for the 2026 showcase SaaS landing page. 

### 1. SECTION ORDER & STRUCTURE
The canonical 2026 layout is ruthless about vertical rhythm and interactive depth. 
*   **Global Nav (Sticky):** Translucent (`backdrop-filter: blur(16px)`), minimal text links, primary CTA.
*   **Hero (100vh):** The hook. Above the fold must be perfectly balanced. No scrolling required to understand the product.
*   **Social Proof / Logo Marquee (20vh):** Monochromatic, low-opacity (`20%`) client logos moving at a slow, continuous mathematical crawl.
*   **The Bento Box / Feature Teaser (80-100vh):** 3-5 asymmetrical grid cards. This replaced the classic "3-column feature list". Each card highlights a micro-interaction or core mechanic.
*   **Scrollytelling Deep Dive (120-150vh):** Sticky left column (text/context), scrolling right column (interactive UI states updating in real-time).
*   **Developer / Performance Proof (60vh):** Darkest section of the page. Massive typography highlighting latency (e.g., "12ms"), uptime, or an interactive API code block.
*   **"Wall of Love" / Testimonials (80vh):** High-density masonry grid of tweets/posts. Heavy blur masks on the top and bottom edges to imply endlessness.
*   **The Terminal CTA (60vh):** Full-bleed gradient mesh background. Massive headline. Final conversion push.
*   **Footer (40vh):** Multi-column, ultra-clean, strict typographic grid.

### 2. HERO ANATOMY
*   **Headline Formula:** 3 to 5 words maximum. The formula: *[High-agency verb] [Outcome].* (e.g., "Ship hardware-accelerated code."). Often features a single italicized or gradient-masked word for visual pacing.
*   **Subhead:** Strictly 1.5 to 2 lines. 18-20px. Color: `#A1A1AA`. Must state exactly what the product *is*, dropping all marketing fluff.
*   **CTA Pair:** 
    *   *Primary:* Glow effect, inset border, high contrast (e.g., pure white background, black text). 
    *   *Secondary:* Ghost button containing a keyboard shortcut hint (e.g., `Book Demo  ⌘K`).
*   **The Visual:** A highly polished, interactive WebGL component or a perfectly isolated "app window" hovering in 3D space. 
*   **Great vs. Generic:** Generic 2024 heroes used a static WebP dashboard screenshot. A great 2026 hero uses an actual, interactive React component that the user can play with before they even scroll.

### 3. VISUAL SYSTEM
*   **Type Scale & Pairings:** 
    *   *Display:* Geist, Inter Display, or PP Mori. Tight tracking (`letter-spacing: -0.04em`).
    *   *Body:* Geist Mono or SF Pro.
*   **Dark-Mode-First Palette:**
    *   Background: `#09090B` (never pure black).
    *   Surface/Cards: `#121214` to `#18181B`.
    *   Primary Accent: Pure White (`#FFFFFF`) for text, or a harsh neon (e.g., `#00FFAA`) for interaction states.
*   **Texture:** 2-4% opacity SVG noise/grain overlaid globally (`pointer-events: none`). It grounds digital elements, making them feel physical.
*   **Borders & Radii:** 
    *   Borders are dead; use 1px inner shadows: `box-shadow: inset 0 0 0 1px rgba(255,255,255,0.08)`.
    *   Radii: Outer containers `24px` or `32px`. Inner elements `16px`. (Nested radius math must be perfect: *Outer Radius - Padding = Inner Radius*).
*   **Elevation:** Drop shadows look muddy in dark mode. Elevation is achieved via layered backgrounds, subtle top-edge highlights, and radial-gradient glows placed *behind* components.

### 4. MOTION
*   **Expected in 2026:** 
    *   *Scroll-driven reveals:* Elements translate Y from `20px` to `0px` and fade from `0` to `1` with a `0.1s` stagger. 
    *   *Spring Easings:* Linear transitions are obsolete. Everything must feel physical (e.g., `framer-motion` springs with `stiffness: 400, damping: 30`).
    *   *Magnetic Buttons:* CTAs that subtly pull toward the cursor when hovering nearby.
    *   *Dynamic lighting:* Radial gradients that track the `x/y` coordinates of the mouse.
*   **Where it becomes tacky:** Scrolljacking (hijacking the native scroll bar). Parallax elements moving at completely disjointed speeds. Heavy Lottie files that drop the frame rate below 120hz. Elements flying in horizontally from off-screen.

### 5. CLICHÉS TO AVOID
*   Midjourney/AI-generated isometric 3D illustrations. Instantly reads as cheap.
*   "Supercharge your workflow" or "Unleash the power" copy.
*   Typewriter text effects in the hero headline.
*   Floating elements without a light source or context.
*   Generic dashboard screenshots featuring meaningless bar charts going "up and to the right."

### 6. FIVE REFERENCE SITES
1.  **Linear:** Steal their absolute precision in typographic hierarchy and nested border radii.
2.  **Vercel:** Steal their flawless use of subtle UI glows and borders to indicate interactivity or state.
3.  **Stripe:** Steal their masterclass in scrollytelling and performant, canvas-driven background animations.
4.  **Raycast:** Steal their integration of developer culture (command palettes, keyboard shortcuts) directly into marketing copy.
5.  **Framer:** Steal their scroll-triggered spring animations that give web elements physical weight and momentum.
