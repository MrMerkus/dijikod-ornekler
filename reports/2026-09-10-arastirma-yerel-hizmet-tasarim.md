# 2026 Local Service Website Design Brief (Turkey)

## 1. Section Order & Content
A high-converting local service site flows from immediate value to social proof to logistics. 

1. **Hero (Above the Fold):**
   * **Visual:** Full-bleed cinematic looping background video (subtle, dark-tinted to ensure text contrast) or an extreme high-res macro shot of the core offering (e.g., espresso extraction, stylist cutting hair, signature dish).
   * **Copy:** H1 is the primary value prop + location (e.g., "Kadıköy'ün Yeni Nesil Kahvecisi" or "Nişantaşı'nda İmza Kesimler").
   * **Action:** Primary CTA (e.g., "Rezervasyon Yap", "Randevu Al") and Secondary CTA (e.g., "Menüyü İncele").
2. **The "Vibe" / Introduction (The 5-Second Pitch):**
   * **Content:** 2-3 sentences max on the philosophy or atmosphere. High-contrast, large-scale typography.
   * **Visual:** Asymmetric grid of 2-3 lifestyle images showing people enjoying the space.
3. **Core Services / Menu Highlights (Bento Box Layout):**
   * **Structure:** Do NOT list everything. Use a bento box grid for the top 3-4 categories (e.g., "Saç Kesimi", "Renklendirme", "Bakım"). 
   * **Interaction:** Hover reveals price range or short description. Clicking opens a full-screen modern modal or slide-out drawer (no jarring page reloads).
4. **Social Proof / Vibe Check:**
   * **Content:** A horizontal, infinitely scrolling marquee or masonry grid pulling curated, high-quality Instagram/TikTok video snippets. Avoid blocky text testimonials; prioritize visual proof of quality.
5. **Logistics & Footer (The Conversion Hub):**
   * **Content:** Dynamic Google Maps embed.
   * **Text:** Plain-text address with a high-contrast "Yol Tarifi Al" (Get Directions) button.
   * **Hours:** Current day highlighted, using JS to dynamically note "Şu an Açık" (Open) or "Kapalı" (Closed) based on user's local time.

## 2. Conversion Elements (Turkish Market)
* **WhatsApp is Non-Negotiable:** A persistent, floating WhatsApp icon (bottom right). It should *not* be the generic green circle; use a custom SVG styled to the brand palette (or monochrome), expanding on hover to "WhatsApp'tan Ulaşın".
* **Sticky Mobile CTA:** On mobile, the bottom 60px of the screen must be a fixed glassmorphic bar with two distinct actions: "Ara" (Call) and "Yol Tarifi" (Directions).
* **Map Styling:** Do not use default Google Maps colors. Use Snazzy Maps or Google Cloud Console to apply a dark/light minimalist theme matching the site's aesthetic.
* **Frictionless Booking:** If integrating a booking engine (like Fresha or a local alternative), embed the widget directly via an elegant slide-out drawer. Do not link out to a third-party domain immediately.

## 3. Visual Language (2026 Modern)
* **Type Scale:** Extreme contrast. Display headings in massive, tight-tracked elegant serifs (e.g., *Ogg*, *PP Editorial New*) or brutalist geometric sans-serifs (e.g., *Neue Montreal*). Body text must be highly legible, slightly larger than standard (18px-20px), with loose line-height (1.6).
* **Spacing Rhythm:** Expansive whitespace. Use `clamp()` for fluid typography and padding. If you think there is enough padding between sections, add 30% more.
* **Imagery Treatment:** Zero stock photos. Images should share a consistent color grade (e.g., slightly desaturated, warm undertones). Implement subtle parallax on scroll (max 5-10% speed difference) and edge-to-edge bleed for hero images. Soft corner radii (4px-8px) on cards; avoid harsh sharp squares unless intentionally brutalist.
* **Motion:** Scroll-triggered micro-animations. Elements should fade in and translate slightly upward (`translateY(20px) -> 0`) as they enter the viewport. Staggered reveals for lists/grids. Use custom cursors (e.g., an inverted dot) that expand over clickable elements.
* **Cliches to AVOID:**
  * "Hakkımızda" (About Us) text walls.
  * Generic Font Awesome icons (use custom SVGs or Lucide icons with 1px stroke weights).
  * Pop-ups on page load.
  * The standard Bootstrap 3-column feature card layout.

## 4. Mobile Priorities
* **Navigation:** Ditch the standard top hamburger menu. Use a bottom tab bar (Home, Menu, Booking, Contact) OR a full-screen blur overlay menu that focuses purely on massive conversion actions.
* **Gestures:** Implement horizontal swiping for galleries and menu categories. Users expect native app-like interactions in 2026.
* **Speed & Weight:** Above-the-fold content must load instantly. Compress hero videos to under 2MB (use WebM/mp4 fallbacks) and aggressively lazy-load everything below the fold.
* **Tap Targets:** Minimum 48x48px for all interactive elements to prevent misclicks.

## 5. Reference Sites (What to Steal)
1. **Maaemo (or similar Awwwards dining sites):** Steal their pre-loader transitions and the cinematic, full-bleed imagery masking that makes the product look like high art.
2. **Blank Street Coffee:** Steal their frictionless, app-like mobile interface and incredibly clean, bento-box style layout for menu items.
3. **Blind Barber (or modern DTC salons):** Steal the stark, high-contrast typography hierarchy and the seamless integration of their booking widget via slide-out drawers.
