---
name: mobile-app-design
description: "Use when designing or building mobile app screens, flows or components for iOS, Android, React Native/Expo or Flutter: native navigation, states, accessibility, onboarding and store assets."
---

# Mobile App Design

For app screens, flows and components. Web landing-page rules (hero limits, eyebrow counts, marquees, scroll-jacking) do not apply inside an app. A marketing page ABOUT the app is web work and goes to design-taste-frontend. Brand tokens come from the brand's DESIGN.md (see design-director); create one first if none exists.

## 1. App read

State before designing:

> App read: [app type] for [user] on [iOS / Android / both], built with [stack], core job: [the one task people open it for].

Find the core loop: the one to three actions people repeat every session. Design those screens first and best; settings and edge screens come last.

## 2. Native feel, brand expression

Rule: the brand lives in color, typography, imagery, illustration, icon style and voice. Navigation, system controls, gestures and sheets follow the platform. People already know how their phone works; do not make them learn a new back button.

### iOS (Apple Human Interface Guidelines)
- Tab bar for 2-5 top-level destinations; navigation bar with back; large titles on scrolling top-level screens.
- Sheets (with detents) for focused sub-tasks, menus for choices, alerts only for decisions that truly need interruption.
- SF Symbols or one matching icon set; Dynamic Type supported so text scales and layouts reflow; 44x44 pt minimum hit targets; safe areas and the home indicator respected.
- System materials (Liquid Glass on iOS 26) come from native components. Use them rather than faking glass with custom blur.
- Edge swipe goes back. Never block it.

### Android (Material 3)
- Navigation bar for 3-5 destinations on phones, navigation rail on tablets and foldables; top app bar; a FAB only for the single primary action of a screen.
- Draw edge-to-edge (enforced for apps targeting Android 15 / API 35) and handle status-bar and navigation-bar insets.
- Support predictive back; do not intercept system back without a reason.
- 48x48 dp minimum touch targets; Material type roles mapped to the brand fonts; dynamic color only when the brand allows it, otherwise a fixed brand ColorScheme.
- Adaptive app icon with a monochrome layer for themed icons.

### Cross-platform stacks
- **React Native / Expo:** `react-native-safe-area-context` for insets; React Navigation or Expo Router with the native stack for native transitions; Reanimated and Gesture Handler so motion runs on the UI thread; FlashList or FlatList for long lists; one `theme.ts` generated from the design spec.
- **Flutter:** Material 3 widgets with a custom `ColorScheme` and `TextTheme` from the spec; adaptive constructors or Cupertino widgets where the iOS feel matters; `SafeArea`; builder-based lists for long content.
- **Default approach: platform-adaptive** (native controls on each platform, shared brand). Fully custom UI only for games, media or products where the interface is the product, and even then back navigation, text scaling and screen readers must work.

## 3. Screen layout

- One primary action per screen, in thumb reach (lower half), visible without scrolling.
- Compact headers; controls sit next to the content they affect.
- Hierarchy through size, weight and spacing on an 8-point grid with 16-20 pt/dp side margins.
- Lists: consistent row heights, whole row tappable, swipe actions only as shortcuts to actions that also exist elsewhere.
- No hamburger menu for primary navigation.
- Tablets and foldables: two panes (list and detail) at wide sizes instead of stretched phone layouts.
- Landscape: support it or lock it deliberately, never by accident.

## 4. States every screen needs

Loading (skeleton matching the layout; show cached content first), empty (what goes here and how to add it), error (plain language plus retry), offline (cached data, queued actions, a clear notice), slow network, permission denied, and first run. Design these with the same care as the happy path.

## 5. Onboarding, permissions, accounts

- Let people see value before signing up wherever the product allows; ask for an account at the moment it is needed.
- Onboarding: zero to three skippable screens; teach in context rather than with tours.
- Permissions: request at the moment of need, after a one-line in-app explanation; handle denial gracefully with a path to Settings.
- Sign-in: passkeys and platform sign-in where available, one-time-code autofill, password-manager support. If the app offers third-party login on iOS, check App Store Review Guideline 4.8.
- If accounts can be created, account deletion must be available (required by both the App Store and Google Play).

## 6. Forms and input

- Correct keyboard for each field (email, number, phone, URL).
- Autofill hints: iOS `textContentType`, Android `autofillHints`, React Native `autoComplete`.
- Visible labels, never placeholder-only; validate when the field loses focus, not on every keystroke.
- The keyboard must never cover the active field or the submit button.
- Segmented controls, steppers or chips for small choice sets instead of long pickers.

## 7. Motion and feedback

- Platform transitions for push, modal and sheet. Custom motion is spring-based, about 150-350 ms for UI feedback, and shows cause and effect.
- Light haptics for confirmations and selections, never constant.
- Respect Reduce Motion (iOS) and Remove animations (Android): swap movement for fades or instant changes.
- Hold 60 fps (120 on high-refresh screens): animate transform and opacity, keep animation work off the JavaScript thread in React Native.

## 8. Accessibility

- VoiceOver and TalkBack: every control has a label, role and state; related elements grouped; logical focus order; custom components expose their actions.
- Text scales to at least 200% without cutting off key information; test the largest sizes.
- WCAG AA contrast; never color alone for status.
- Targets 44 pt (iOS) / 48 dp (Android).

## 9. Visual system

- Tokens from DESIGN.md: color roles for light and dark, type scale mapped to Dynamic Type styles and Material type roles, one radius system, elevation.
- Icons: one family at one weight (SF Symbols on iOS, Material Symbols on Android, or one custom set on both).
- Imagery and sample data: realistic app content, never lorem ipsum or invented statistics.
- App icon: a simple silhouette readable at small sizes, no text or screenshots inside; iOS light, dark and tinted variants; Android adaptive icon plus monochrome layer.

## 10. Store listing

Screenshots show real screens of the core loop, one benefit per screenshot with a caption of six words or fewer, in one consistent style; the first two or three carry the pitch. Icon and screenshots follow the design spec. No claims the app cannot back up.

## 11. Security, privacy and rights

- **No private keys in the app.** App bundles can be decompiled, so anything shipped inside is public. Keys with write, admin or billing power stay on your backend; the app calls the backend.
- **Secure storage:** tokens and credentials in the Keychain (iOS) or Keystore-backed storage (Android); `expo-secure-store` or `flutter_secure_storage` on cross-platform stacks. Never AsyncStorage, SharedPreferences or plain files for secrets.
- **Network:** HTTPS only (keep App Transport Security on for iOS; cleartext traffic off for Android).
- **Disclosures match reality:** the iOS privacy details (and the privacy manifest for the app and its SDKs) and the Google Play Data safety form must describe what the app and every third-party SDK actually collect. Ask the App Tracking Transparency prompt before any cross-app tracking on iOS.
- **Minimum permissions**, each explained at the moment of need.
- **Sensitive screens** (finance, health, private messages): hide content in the app-switcher snapshot and offer a biometric lock where it makes sense.
- **Third-party SDKs:** only from official sources, only what is needed, kept updated.
- **Rights:** fonts licensed for app embedding (some foundries license apps separately from web), icons and images licensed for commercial use, no other brands' logos without permission.

## 12. Pre-flight check

- [ ] App read stated; core loop screens designed first?
- [ ] Navigation, back behaviour, sheets and controls follow each platform?
- [ ] Safe areas, edge-to-edge insets and the keyboard handled on every screen?
- [ ] One primary action per screen, in thumb reach?
- [ ] Loading, empty, error, offline, permission and first-run states designed?
- [ ] Targets at least 44 pt / 48 dp; contrast WCAG AA; screen-reader labels, roles and states present?
- [ ] Layout survives 200% text size, tablets and landscape (or orientation locked on purpose)?
- [ ] Light and dark themes both checked?
- [ ] Motion motivated, spring-based, smooth, and off under reduced-motion settings?
- [ ] Permissions asked in context; sign-up deferred; account deletion available?
- [ ] Correct keyboards and autofill hints on every input?
- [ ] Tokens match DESIGN.md; one icon family; no lorem ipsum or invented data?
- [ ] No private keys in the app; tokens in secure storage; HTTPS only?
- [ ] Store privacy disclosures match what the app and its SDKs collect; tracking prompt shown before tracking on iOS?
- [ ] Fonts, icons and images licensed for commercial app use?

---

Copyright (c) 2026 Mohammad Habibur Rahaman. Released under the MIT License. Part of the mrahamangm-droid/taste-skill fork of taste-skill by Leonxlnx (MIT License).
