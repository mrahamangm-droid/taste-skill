---
name: design-director
description: Use first for any design task (websites, online stores, web or mobile apps, brand assets, Figma, Canva, Stitch, Shopify, WordPress) to pick the lead design skill, settle conflicts and keep one brand spec.
---

# Design Director

The entry point for every design job. It decides which design skill leads, settles conflicts between skills, keeps one portable design spec per brand, and adapts the work to the platform it will live on. It does not replace the specialist skills; it makes them work together.

## 1. Classify the job (always first)

Answer four questions before designing anything:

1. **Surface:** marketing site or landing page / online store / web app or dashboard / mobile app / brand or visual asset / screen or file inside a design platform.
2. **State:** new build, or a change to something that already exists?
3. **Platform:** hand-written code (React, Next.js, HTML), Shopify theme, WordPress, Webflow, Framer, Figma, Canva, Google Stitch or another AI UI generator (v0, Lovable, Figma Make), React Native / Expo, Flutter, native iOS / Android.
4. **Brand:** does a DESIGN.md, brand kit, logo, palette or live site already exist? If yes, it is the starting point, not a suggestion.

Then tell the user one line before designing:

> Design read: [surface] on [platform] for [audience], [new build / redesign], lead skill: [name].

Ask one question only if the answer changes the lead skill or the platform. Otherwise proceed.

## 2. Pick ONE lead skill

| Job | Lead skill | Support |
|---|---|---|
| New landing page, portfolio, marketing or brand site | design-taste-frontend | high-end-visual-design or minimalist-ui for the look, only when the brief asks for that look |
| Improving an existing site or web app | redesign-existing-projects | design-taste-frontend (Section 11 and pre-flight) |
| Online store pages or Shopify / WooCommerce theme work | ecommerce-store-design | design-taste-frontend for campaign and landing-style sections |
| Mobile app screens, flows, components | mobile-app-design | brand tokens from the design spec |
| "Expensive / agency / luxury" look requested | high-end-visual-design | design-taste-frontend checks |
| "Clean / calm / editorial / document-style" look requested | minimalist-ui | design-taste-frontend checks |
| Dashboard, admin panel, data table, internal tool | An official design system (design-taste-frontend Section 2.A: Polaris for Shopify admin apps, Carbon, Fluent, Radix Themes, shadcn/ui) | Section 6 quality floor. Landing-page rules (hero limits, eyebrow counts, marquees) do not apply |
| Slides, documents, social graphics | The platform or format skill for that output | Colors, fonts and voice from the design spec |

One lead skill sets the aesthetic. Support skills add checks, never a second aesthetic. If a named skill is not installed, continue with the ones that are.

## 3. Conflict rules

Precedence, highest first:

1. The user's explicit brief and existing brand assets.
2. Legal, accessibility and platform rules (WCAG 2.2 AA, App Store and Google Play guidelines, Shopify theme requirements, consumer-protection law).
3. The lead skill.
4. Support skills.
5. General defaults.

Known conflicts, already settled:

- **Eyebrow labels.** high-end-visual-design puts a pill label above every major heading; design-taste-frontend allows at most one per three sections. Use the design-taste-frontend limit unless high-end-visual-design is the lead AND the brief asks for that agency style.
- **Serif fonts.** minimalist-ui allows editorial serifs; design-taste-frontend bans serif as a default. When minimalist-ui leads an editorial brief a serif is fine, but choose it for the brand and do not reuse the same serif on consecutive projects.
- **Amount of motion.** Any rule saying "everything animates" yields to "motion must be motivated": every animation needs a one-sentence reason (hierarchy, storytelling, feedback, state change), and all of it collapses to static under reduced-motion settings.
- **Warm off-white backgrounds.** Allowed when minimalist-ui leads. For premium-consumer product brands, apply design-taste-frontend's palette ban and rotate palette families.
- **Button and card shape.** Follow the lead skill, then apply one radius system across the whole product.
- **Placeholders.** Never ship lorem ipsum, invented reviews, invented numbers or fake logos as if real. Labelled image slots are allowed only when no real or generated image exists, and they must be listed for the user.

## 4. One portable design spec per brand

Every brand or product gets a DESIGN.md: in the repository root when there is one, otherwise delivered to the user as a file. Create it on the first design task for that brand, read and follow it on every later task, and update it only when the user approves a change. Never quietly invent a second style for the same brand.

```markdown
# Design Spec: [Brand]
Version, date, owner

## 1. Brand read
Audience, promise, personality in three words, two or three reference products, what this brand is NOT.

## 2. Dials
DESIGN_VARIANCE / MOTION_INTENSITY / VISUAL_DENSITY (definitions in design-taste-frontend).

## 3. Color roles (light and dark)
| Role | Light | Dark | Used for |
background, surface, surface-raised, text-primary, text-secondary, border,
accent, on-accent, success, warning, danger, focus
Contrast verified: text-primary/background, text-secondary/surface, on-accent/accent.

## 4. Typography
Display, body and mono fonts with fallback stacks and license source.
Scale: display, h1, h2, h3, body-lg, body, small, caption (size, line height, tracking).
Arabic / RTL pairing if the brand serves Arabic readers.

## 5. Space, radius, elevation
Spacing scale (4 or 8 base), one radius rule, tinted shadow tokens, max content width.

## 6. Motion
Durations, easing or spring values, what moves and why, reduced-motion behaviour.

## 7. Components
Buttons, inputs, cards, navigation, product card, badges: default, hover, pressed,
focus, disabled, loading, error.

## 8. Imagery and icons
Photo style and aspect ratios, icon family and stroke width, illustration rules.

## 9. Voice
Tone, words we use, words we never use, one CTA label per intent.

## 10. Do not
Brand-specific bans plus the lead skill's AI tells.
```

### Token translation (keep token names identical everywhere)

| Platform | Where the tokens live |
|---|---|
| Tailwind v4 | `@theme` block in the main CSS (`--color-*`, `--font-*`, `--radius-*`, `--spacing`) |
| Plain CSS / any framework | `:root` custom properties; dark values under `prefers-color-scheme` and `[data-theme="dark"]` |
| Shopify theme | `config/settings_schema.json` color schemes and typography settings, output as CSS variables in the layout. Anything a merchant may want to change is a setting, never hardcoded |
| WordPress block theme | `theme.json`: `settings.color.palette`, `settings.typography.fontFamilies` and `fontSizes`, `settings.spacing.spacingSizes` |
| Figma | Variable collections (Color with Light and Dark modes; Number for spacing and radius), text styles, and components that use those variables |
| Canva | Brand Kit (logos, colors, fonts), then templates built from it |
| Webflow / Framer | Variables for color, size and font, with components and classes built on them |
| React Native / Expo | One `theme.ts` consumed by every component; light and dark via `useColorScheme` |
| Flutter | `ThemeData` with light and dark `ColorScheme`, `TextTheme`, and a `ThemeExtension` for brand extras |
| Stitch, v0, Lovable, Figma Make and other AI generators | Paste DESIGN.md sections 3-10 into the prompt or project context, generate one screen at a time, and review every result against the checklists before accepting it |

## 5. Platform notes

- **Shopify storefront.** Online Store 2.0: JSON templates built from sections and blocks so the merchant can rearrange without code; settings instead of hardcoded values; test in the theme editor; keep installed apps lean because each can inject scripts; responsive images through Shopify's image filters with explicit widths. Admin apps use Polaris, never storefront styling.
- **WordPress.** Prefer block themes, `theme.json` and registered block patterns over page-builder lock-in; test in the Site Editor.
- **Webflow / Framer.** Work inside the platform's variable and component system, keep class naming systematic, check every breakpoint, keep interactions compatible with reduced motion.
- **Figma.** Auto layout everywhere, component variants that mirror real code states, variables for tokens, named frames and layers, mobile and desktop frames for each key screen. Hand off with the design spec.
- **Canva.** Set up the Brand Kit first, lock brand elements in templates, export at the correct size for each channel.
- **AI UI generators.** They drift toward generic output. Always supply the spec, name the patterns to avoid, iterate screen by screen, and treat the output as a draft that must pass the checklists, not a finished design.

## 6. Universal quality floor (every surface, every skill)

- **Contrast (WCAG 2.2 AA):** 4.5:1 for body text; 3:1 for large text, UI components and focus indicators.
- **Target size:** at least 24x24 CSS px on the web (WCAG 2.2), 44x44 pt on iOS, 48x48 dp on Android; primary touch actions larger.
- **Operability:** visible keyboard focus, logical order, semantic HTML or native accessibility labels, alt text for meaningful images.
- **Motion and color:** reduced-motion settings respected; no meaning carried by motion or color alone.
- **Themes:** light and dark handled for consumer-facing products unless the brand deliberately chooses one.
- **Mobile first:** check at 360-390 px wide before desktop.
- **Truthful content:** real product data, names and prices; nothing invented presented as fact (reviews, ratings, customer counts, stock levels, awards, press logos).
- **Performance:** responsive optimized images, self-hosted or platform fonts with swap, the LCP element prioritised, no layout shift from late media.
- **RTL:** for Arabic, Urdu or Hebrew readers use CSS logical properties, `dir="rtl"`, mirrored directional icons and carousels, an Arabic-capable font pairing, and test both directions.

## 7. Finish

Before delivering, run the lead skill's checklist, then Section 6. Then tell the user in two to four lines: what was designed, which lead skill and design spec were used, and what is still needed from them (real photos, logo files, copy approval, platform access).
