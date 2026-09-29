---
name: Multiorder Culinary Engine
colors:
  surface: '#fcf8ff'
  surface-dim: '#dbd8e8'
  surface-bright: '#fcf8ff'
  surface-container-lowest: '#ffffff'
  surface-container-low: '#f5f2ff'
  surface-container: '#efecfc'
  surface-container-high: '#e9e6f6'
  surface-container-highest: '#e3e1f0'
  on-surface: '#1b1b26'
  on-surface-variant: '#5b403f'
  inverse-surface: '#302f3b'
  inverse-on-surface: '#f2efff'
  outline: '#8f6f6e'
  outline-variant: '#e4bebc'
  surface-tint: '#bb162c'
  primary: '#b7122a'
  on-primary: '#ffffff'
  primary-container: '#db313f'
  on-primary-container: '#fffbff'
  inverse-primary: '#ffb3b1'
  secondary: '#006d2f'
  on-secondary: '#ffffff'
  secondary-container: '#81f899'
  on-secondary-container: '#007232'
  tertiary: '#8b4c00'
  on-tertiary: '#ffffff'
  tertiary-container: '#af6100'
  on-tertiary-container: '#fffbff'
  error: '#ba1a1a'
  on-error: '#ffffff'
  error-container: '#ffdad6'
  on-error-container: '#93000a'
  primary-fixed: '#ffdad8'
  primary-fixed-dim: '#ffb3b1'
  on-primary-fixed: '#410007'
  on-primary-fixed-variant: '#92001c'
  secondary-fixed: '#84fb9c'
  secondary-fixed-dim: '#67de82'
  on-secondary-fixed: '#002109'
  on-secondary-fixed-variant: '#005322'
  tertiary-fixed: '#ffdcc1'
  tertiary-fixed-dim: '#ffb77a'
  on-tertiary-fixed: '#2e1500'
  on-tertiary-fixed-variant: '#6c3a00'
  background: '#fcf8ff'
  on-background: '#1b1b26'
  surface-variant: '#e3e1f0'
typography:
  headline-xl:
    fontFamily: Plus Jakarta Sans
    fontSize: 36px
    fontWeight: '800'
    lineHeight: 44px
  headline-xl-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 28px
    fontWeight: '800'
    lineHeight: 36px
  headline-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 28px
    fontWeight: '700'
    lineHeight: 36px
  headline-lg-mobile:
    fontFamily: Plus Jakarta Sans
    fontSize: 22px
    fontWeight: '700'
    lineHeight: 30px
  headline-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 20px
    fontWeight: '700'
    lineHeight: 28px
  headline-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 16px
    fontWeight: '600'
    lineHeight: 24px
  body-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 16px
    fontWeight: '400'
    lineHeight: 24px
  body-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '400'
    lineHeight: 20px
  body-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '400'
    lineHeight: 18px
  label-lg:
    fontFamily: Plus Jakarta Sans
    fontSize: 14px
    fontWeight: '600'
    lineHeight: 20px
  label-md:
    fontFamily: Plus Jakarta Sans
    fontSize: 12px
    fontWeight: '600'
    lineHeight: 16px
  label-sm:
    fontFamily: Plus Jakarta Sans
    fontSize: 10px
    fontWeight: '700'
    lineHeight: 14px
rounded:
  sm: 0.25rem
  DEFAULT: 0.5rem
  md: 0.75rem
  lg: 1rem
  xl: 1.5rem
  full: 9999px
spacing:
  gutter: 1rem
  gutter-mobile: 0.75rem
  margin: 2rem
  margin-mobile: 1rem
  space-xs: 0.25rem
  space-sm: 0.5rem
  space-md: 1rem
  space-lg: 1.5rem
  space-xl: 2rem
---

## Brand & Style
The design system powers an advanced multi-restaurant ordering flow for modern food delivery, engineered to handle synchronous order state, disparate restaurant cart items, and parallel delivery timelines with clarity and culinary appeal.

### Brand Personality & Tone
- **Appetizing & Vital:** Vibrant, warm culinary touches that celebrate food culture while maintaining frictionless utility.
- **Reliable & Transparent:** Absolute clarity on pricing splits, multi-stop tracking, kitchen prep states, and parallel rider assignments.
- **Modern & Effortless:** Clean typographic hierarchy, generous breathing room, and soft visual boundaries that avoid cognitive overload during complex checkout flows.

### Design Movement: Modern Tactile Fluidity
A balance of modern neutral minimalism with subtle ambient depth. High surface legibility using crisp boundaries, delicate low-contrast outlines (`#EAEBED`), and soft warm base tones prevents multi-merchant carts from appearing cluttered. Micro-interactions and synchronized status trackers use high-contrast status colors to anchor temporal urgency without inducing anxiety.

## Colors
The color architecture establishes immediate recognition, regulatory compliance (such as vegetarian/non-vegetarian food markers), and multi-order state tracking.

### Primary Accent (`#E23744`)
- Used for high-intent conversion actions (e.g., "Place Multiorder", "Add to Order"), active tab indicators, and critical brand anchors.
- Light tint variant (`#FDF1F2`) provides subtle highlights for multi-order badge backgrounds and merchant sync pills.

### Secondary Emerald (`#1B9E4B`)
- Anchors the universal Indian vegetarian indicator ("Green Dot in Square"), positive confirmations, delivery milestone completion, and total savings callouts.
- Light tint variant (`#E8F7EE`) serves as the surface for positive badges, multi-restaurant discount tags, and active rider milestones.

### Tertiary Warm Amber (`#E5820D`)
- Communicates time-sensitive preparation delays, synchronous rider wait times, multi-kitchen prep offset alerts, and multi-stop logistics status.
- Light tint variant (`#FEF5EA`) cushions alert banners and temporal notices.

### Neutrals & Background Surfaces
- **Canvas Base:** `#F8F9FA` gives warmth and reduces eye fatigue compared to pure harsh white.
- **Surface Elevation (Cards & Modals):** `#FFFFFF` pure white ensures sharp contrast against the base canvas.
- **Deep Slate Text:** `#1C1C27` replaces pure black for rich, high-contrast, fatigue-free readability.
- **Muted Subtitles / Metadata:** `#686B78` for restaurant tags, ETAs, and secondary instructions.
- **Structural Outlines:** `#EAEBED` for clear card separations, item dividers, and segmented status rails.

## Typography
Plus Jakarta Sans provides high legibility at dense tabular scales (such as split delivery fees and modifier lists) while lending warm geometric character to bold headline branding.

- **Numerics & Currency:** Render prices, countdown timers, and sync indices with `font-variant-numeric: tabular-nums` to ensure synchronized multi-cart values align accurately.
- **Hierarchy Rules:** Headline tokens are strictly reserved for merchant banners and screen titles. Item descriptions stick to `body-sm`, and operational notifications use `label-md` for punchy scanability.

## Layout & Spacing
A fluid 4-column layout is utilized on mobile devices (width < 600px), transitioning to an 8-column layout for tablets and a constrained 12-column layout maxing out at 1120px for desktop ordering.

### Grid Rhythm & Rules
- **Multi-Merchant Separation:** Visual cards representing individual restaurants maintain a mandatory `space-lg` (24px) gap to isolate line items clearly.
- **Internal Dish Spacing:** Nested dish line items within a merchant card adhere to `space-md` (16px) vertical stack gaps, bounded by a 1px `#EAEBED` horizontal rule.
- **Persistent Bottom Bar:** On mobile, checkout summaries and sticky actions retain a 16px lateral margin and an integrated safe-area padding at the base.

## Elevation & Depth
Depth is articulated through tinted layered surfaces, faint ambient shadows, and crisp 1px borders rather than heavy drop shadows.

- **Level 0 (Canvas):** `#F8F9FA`. Base neutral floor for scrollable lists.
- **Level 1 (Cards & Groups):** `#FFFFFF` surface with a subtle 1px border (`#EAEBED`) and an ambient shadow: `box-shadow: 0 2px 8px -2px rgba(28, 28, 39, 0.04), 0 1px 4px -1px rgba(28, 28, 39, 0.02)`.
- **Level 2 (Floating Action Bars / Active Cart Summary):** `#FFFFFF` surface with `box-shadow: 0 8px 24px -4px rgba(28, 28, 39, 0.08), 0 2px 6px -1px rgba(28, 28, 39, 0.04)`.
- **Level 3 (Modals & Bottom Sheets):** `#FFFFFF` surface with backdrop blur (`backdrop-filter: blur(8px)`, background `rgba(28, 28, 39, 0.4)`), elevated with `box-shadow: 0 16px 32px -8px rgba(28, 28, 39, 0.16)`.

## Shapes
A roundedness value of `2` provides balanced, modern curvature that feels friendly and ergonomic on mobile touchscreens without consuming excess screen real estate.

- **Standard Elements (0.5rem / 8px):** Input fields, secondary buttons, food type icons, and synchronized progress track segments.
- **Container Elements (1rem / 16px - `rounded-lg`):** Restaurant merchant group cards, bottom sheet containers, delivery estimate banners, and map overlays.
- **Pill Badges & Steppers (`rounded-full`):** Category filter chips, "Multiorder Eligible" status badges, veg/non-veg indicator chips, and stepper quantity controls.

## Components

### Buttons
- **Primary Order CTA:** Background `#E23744`, text `#FFFFFF`, font `label-lg`, height 48px, radius 8px (`space-sm` * 2). Hover/active state deepens to `#C92C38`.
- **Add / Stepper Button:** Bordered container `#EAEBED` with white fill; active state features `#E23744` text and interactive increment/decrement counters.
- **Secondary Action:** Ghost style, 1px border `#EAEBED`, text `#1C1C27`, background `#FFFFFF`.

### Chips & Eligibility Badges
- **"Multiorder Eligible" Chip:** Pill shape, background `#FDF1F2`, text `#E23744`, border 1px solid `rgba(226, 55, 68, 0.2)`. Features a dual-bag or link icon at 14px size.
- **Veg / Non-Veg Indicator:** 14px square with 2px radius, 1px solid border matching content type. Veg uses `#1B9E4B` with a solid 6px center circle; non-veg uses `#E23744` with a solid center triangle.

### Merchant Group Card Containers
- Nested wrapper encapsulating distinct restaurants within the master checkout.
- Top section holds merchant name, branch, distance, and preparation sync ETA pill (e.g., "Kitchen 1: Ready in 15m").
- Separated internally by 1px `#EAEBED` hairline dividers between individual food items.

### Synchronized Status Trackers
- A multi-track progress component showing parallel statuses:
  - Timeline split into parallel lanes for Restaurant A and Restaurant B.
  - Completed stages: Filled `#1B9E4B`.
  - In-progress prep: Filled `#E5820D` with gentle pulse.
  - Pending rider handover: Outlined neutral `#EAEBED`.

### Transparent Fee Breakdown Table
- Modular collapsible card showing itemized bill splits:
  - Base food items per merchant.
  - Combined delivery fee showing individual savings banner (`#E8F7EE` background, `#1B9E4B` text).
  - Explicit platform fees and tax breakdowns (GST/Restaurant packaging) tagged per establishment.