---
name: ecommerce-store-design
description: Use when designing or improving online store pages (home, collection, product, cart, search) or Shopify/WooCommerce themes: real product data, honest conversion design, RTL and GCC markets, speed.
---

# E-commerce Store Design

For storefronts: home, collection, product, search and cart pages, campaign landing pages, and Shopify or WooCommerce theme work. The goal is to help shoppers find, trust and buy, honestly. Brand tokens come from the store's DESIGN.md (see design-director). Landing-style sections can borrow design-taste-frontend's rules; its premium-consumer palette ban applies to product brands.

## 0. Store read

State before designing:

> Store read: [category] store for [shopper], [budget / mid / premium] price point, on [Shopify / WooCommerce / custom], main traffic from [social ads / search / direct / marketplaces], top goal: [first purchase / order value / repeat purchase].

Traffic source changes the design. Social-ad traffic lands on product pages on phones, so for those stores the product page matters more than the homepage.

## 1. Real data first

- When the Shopify connector or a store export is available, pull real products, prices, variants, collections and images before designing.
- Never invent reviews, ratings, units sold, stock levels, discounts, compare-at prices, "as seen in" logos or customer counts.
- Placeholder content must be visibly marked and listed for replacement before launch.

## 2. Page blueprints

### Home
- First screen: what the store sells and why buy here (one line), a clear way in (shop a category or the hero product), and real product imagery.
- Then: category entry points (image plus name), real bestsellers or new arrivals, true value props with specifics (shipping threshold, return window, warranty), real reviews or customer photos, a short brand story, and a newsletter with an honest incentive.
- Mobile: search and cart always reachable; the menu opens on categories.

### Collection
- Filters matching how shoppers choose (size, color, price, type, availability): a drawer on mobile with removable applied-filter chips, plus sort and a result count.
- Product cards: one aspect ratio across the grid (1:1 or 4:5), second image on hover on desktop, title, price (sale price only against a genuine previous price), swatches for variants, badges only when true.
- Two columns on mobile, three or four on desktop. Returning from a product page restores the scroll position.

### Product page (the most important page)
- Above the fold on mobile: swipeable gallery, title, price, main variant pickers, add to cart, and a rating summary only if real reviews exist.
- Gallery of five to eight images: hero on a clean background, angles, detail or texture, scale or in use, lifestyle; video when available; zoom.
- Variants as buttons or swatches rather than dropdowns when there are few options; sold-out variants shown disabled with a notify option; the selected variant updates image, price and URL.
- Next to add to cart: delivery estimate or shipping cost, a returns summary, express payment options, and stock status only if real.
- Below: key benefits, details and specs (grouped; see design-taste-frontend's spec-sheet rules), size or fit guide, materials and care, FAQs, reviews with photos, related products.
- Sticky add-to-cart bar on mobile once the main button scrolls away.
- One primary CTA ("Add to cart"); express wallet buttons are secondary.

### Cart and checkout
- Cart drawer for quick adds plus a full cart page; quantity, variant and remove editable inline.
- Free-shipping progress bar only for a real threshold; show estimated shipping and taxes early so there are no surprises later.
- At most one to three relevant add-ons; express checkout; guest checkout kept.
- Checkout is platform-managed (Shopify Checkout): brand it through checkout settings (logo, colors, fonts) and do not add friction.

### Search and trust
- Predictive search covering products and collections, tolerant of typos, with a helpful no-results page.
- Real contact details, shipping, returns, privacy and terms pages, and a clear business identity. Payment badges only for methods actually offered.

## 3. Honest persuasion (non-negotiable)

Banned dark patterns: countdown timers that reset, fake "X people viewing", fake low stock, pre-ticked add-ons, fees revealed only at checkout, confirmshaming ("No thanks, I hate saving money"), fabricated or undisclosed incentivised reviews, and invented compare-at prices.

Legal context (general information, not legal advice; confirm for each market):
- US: the FTC rule banning fake reviews and testimonials, in force since October 2024.
- EU: an announced price reduction must reference the lowest price of the previous 30 days; the European Accessibility Act has applied to many e-commerce services for EU consumers since 28 June 2025.
- UAE: consumer protection rules (Federal Law No. 15 of 2020) cover pricing, advertising and returns.

## 4. Visual direction for stores

- Product photography IS the design: same background, lighting, angle set and aspect ratio across the catalog, high resolution (around 2048 px on the long side).
- The interface recedes: neutral surfaces, one accent for CTAs and sale states, type chosen for legible prices.
- Prices: tabular numbers, a clear sale versus regular distinction, currency formatted per market.
- Premium-consumer categories: apply design-taste-frontend's palette ban and rotate palette families.

## 5. Running several stores

- Each store has its own DESIGN.md. Share one theme or code base where possible, and tell stores apart through tokens, photography, voice and hero composition.
- Stores selling to the same audience must not share identical homepage layouts.
- Reuse what converts as structure, not as look. Record which layouts win in each store's spec.

## 6. Markets, language and RTL (UAE and GCC)

- Shopify Markets (or equivalent) for currency and language; local currency formatting (for example AED).
- Arabic storefronts: full RTL layout (logical CSS properties, `dir="rtl"`, mirrored arrows and carousels), an Arabic-capable font pairing (for example IBM Plex Sans Arabic, Noto Kufi Arabic, Cairo or Tajawal), one numeral style used consistently, and human-reviewed translation.
- Show local payment options that are actually enabled (cash on delivery, buy-now-pay-later providers common in the region) and realistic delivery times.

## 7. Performance and SEO

- Mobile Core Web Vitals: LCP under 2.5 s (hero or first product image prioritised, never lazy-loaded), CLS under 0.1 (image space reserved), INP under 200 ms.
- Audit installed apps and remove unused ones; each can add scripts to every page.
- Responsive images through the platform image CDN with srcset.
- SEO: unique titles and meta descriptions per product and collection, descriptive handles, Product structured data (price and availability; review markup only for real reviews), breadcrumbs, descriptive alt text, no thin duplicate collection pages.

## 8. Shopify implementation notes

- Online Store 2.0: JSON templates built from sections and blocks; every merchant-editable value is a setting; use color schemes; keep Liquid logic simple; test in the theme editor.
- Start from a maintained theme (Shopify's free reference themes such as Dawn or Horizon, or a reputable paid theme) and customise through settings and sections before writing custom code.
- Specs, size guides and care instructions live in metafields and render consistently, not as pasted HTML in descriptions.
- Test with long product titles, many variants, sold-out variants, products without images, sale and non-sale prices, and Arabic or other long translations.

## 9. Pre-flight check

- [ ] Store read stated; the page the traffic lands on got the most attention?
- [ ] Real products, prices and images used; every placeholder marked and listed?
- [ ] Product page: gallery, price, variants and add to cart above the fold on mobile; sticky add-to-cart bar?
- [ ] Shipping, returns and delivery info next to add to cart?
- [ ] Every badge, timer, stock notice, review and compare-at price is true?
- [ ] No dark patterns from Section 3?
- [ ] Filters and sort usable on mobile; grid aspect ratio consistent?
- [ ] Cart shows costs early; guest and express checkout available?
- [ ] Contrast, target sizes and focus meet the design-director quality floor?
- [ ] LCP image prioritised; unused apps removed; image space reserved?
- [ ] Titles, meta, structured data and alt text in place?
- [ ] RTL and local currency correct for each market served?
- [ ] Tokens match the store's DESIGN.md, and the store is visibly distinct from its sister stores?
