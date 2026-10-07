# Hungry Henry — design style guide for AI Studio

Paste this whole file into AI Studio (System instructions, or at the top of the build prompt). Source of truth: `brand/tokens.json` v2.0.0, `brand/voice.md`, `02-design/component-inventory.md`.

## 1. Product

- Name: Hungry Henry (two words, both capitalised; never "HH", "HungryHenry" or "the Hungry Henry").
- What it is: a mobile app (iPhone first, 390×844) that builds a restaurant plate matching the person's remaining calories, protein, carbs and fat.
- The person is a Fitness Enthusiast. Address them as "you" in UI copy. Never say "user", "diner", "customer" or "consumer".
- Light mode only. No dark mode.

## 2. Colour palette (use these hex values only)

Brand colours:
- Rusty Spice `#B43B1F`: primary. Used for the Match button, the selected nav tab, locked pills, selected segments, sliders and the focus ring.
- Blackberry Cream `#503047`: body text, icons, ink on green washes.
- Muted Olive `#ADC698`: large decorative fills only. Never text on white.
- Tea Green `#D0E3C4`: pale wash for pill backgrounds and search-keyword highlights. Never text.
- White `#FFFFFF`: page and card background.

Supporting steps:
- Olive text / success / macro indicators: `#50663C`
- Muted text (distance, captions, placeholders, unselected nav): `#8E6A83`
- Borders and dividers: `#AA859F`
- Sunken background: `#FFF0FA`
- Neutral chip or segment background: `#F0DAE9`
- Toggle track (off) and slider track: `#DFC0D5`
- Primary tint background: `#FFF2EE`
- Deep red for links and small emphasis: `#860200`
- Olive tint background: `#EFF9E8`

Semantic:
- Error: `#A4192C` on `#FBE9EC`. Keep it distinct from Rusty Spice so an error never reads as Match.
- Warning: `#8A5A00` on `#FDF3DC`.
- Success: `#50663C` on `#EFF9E8`.

Rules:
- Rusty Spice is the only loud colour. On Home, only the Match button uses a solid Rusty Spice fill.
- Text on white is `#503047` (body) or `#8E6A83` (muted). Text on Rusty Spice is white. Text on Olive or Tea Green is `#503047`.
- Keep every text colour at WCAG AA contrast (4.5:1 for body text).
- No gradients. The only exception: the food list fades to white above the macro group.

## 3. Typography

- UI chrome (nav, buttons, macros, chips, labels): Inter, loaded from Google Fonts.
- Restaurant names and food or menu item names: Fraunces (Google Fonts), a serif that makes the food feel appetising.
- Scale in px: 12 / 14 / 16 / 18 / 20 / 24 / 30 / 36.
- Weights: 400 regular, 500 medium, 600 semibold, 700 bold.
- Line height: 1.2 for headings, 1.5 for body text.
- Food names on the plate: Fraunces at 20–24px. Macro values: Inter semibold, 16px.

## 4. Spacing, shape and elevation

- 4px spacing grid: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64.
- Screen side padding: 16px.
- Corner radius: 2px (small), 6px (inputs and cards), 12px (sheets and large cards), fully round for pills and circular buttons.
- Keep shadows minimal: one soft shadow for bottom sheets and the action bar. Flat everywhere else.
- Style: calm, dense, editorial. White space and thin plum dividers rather than heavy cards.

## 5. Layout and navigation

- Bottom navigation on every main screen, with four tabs, each an icon plus a label: Match (utensils icon), Map (pin), Filters (sliders), Account (person).
  - Selected tab: Rusty Spice. Unselected: `#8E6A83`. The bar sits on white.
- Search is not a tab. A collapsed search bar sits on Home and Map; tapping it opens a full Search page. Closing Search returns you to where you came from.
- Use Lucide-style line icons (1.5px stroke).

## 6. Screens

1. Home (Match tab)
   - Restaurant info header: restaurant name as a pill (Fraunces), star rating, distance in muted text.
   - Stacked food list: one row per food, each name a tappable pill. The list fades to white at the bottom.
   - Macro group: four rows (energy, protein, carbs, fat), each with an icon, a value and an indicator. Diet and allergy pills sit underneath.
   - Action bar with five circular buttons: Rear (56px, arrow-left), Save (64px, bookmark), Match (80px, heart, solid Rusty Spice, white icon), Add (64px, plus), Forward (56px, arrow-right). All buttons except Match have a white fill and a `#503047` icon.
2. Filters
   - Three sections, in this order: Nutrition, Diets, Allergies.
   - Nutrition: one row each for Energy, Carbs, Fat and Protein. Each row has a toggle and a three-way segmented control (less / is / more), shown only when the toggle is on, plus a value with its unit (kcal or g). An "Advanced" dropdown reveals a two-handle range slider.
   - Diets and Allergies: one row per item, each with a name and a toggle.
3. Map
   - A quiet, muted map. It pins only restaurants that currently have a match.
   - The selected pin is Rusty Spice.
   - Tapping a pin opens a restaurant bottom sheet: name, stars, distance and 2–4 popular meals. Tapping a meal opens Home with that plate loaded.
4. Search
   - A search field with the placeholder "Search", and an "Ask Henry" prompt below it.
   - Meal-match rows: the food names, with the typed keyword highlighted on a Tea Green background, and the difference from target in `#50663C`.
   - Restaurant rows: name, stars and distance.
5. Account
   - Collections: Saved and Recent.
6. Add sheet
   - A bottom sheet listing the current restaurant's menu. Picking a food locks it and closes the sheet.

## 7. Component states

- Title pill (restaurant or food), unlocked: `#503047` text, no fill.
- Title pill, locked: white text on Rusty Spice with a small lock icon. The pill grows slightly when it locks; it does not flip.
- Toggle: off has a `#DFC0D5` track and a white thumb. On has a `#50663C` track.
- Segmented control: the selected segment is Rusty Spice with white text. Unselected segments are `#F0DAE9` with `#503047` text.
- Macro indicator, off target: "+12 g" or "−40 kcal" in `#50663C`.
- Macro indicator, on target: "Hit" in `#50663C`. It never scolds, and a small miss still counts as a match.
- Diet pill: `#503047` text on Tea Green `#D0E3C4`, fully rounded, read-only on the plate.
- Map pin: the default is `#503047`; the selected pin is Rusty Spice and larger.

## 8. Motion

- Food rows bump out and bump in one at a time. Locked rows stay put. This is NOT a Tinder card stack, so avoid swipe-card metaphors.
- Transitions: 150–250ms, ease-out.
- Bottom sheets slide up.

## 9. Voice and copy

- Tone: direct, appetising, unashamed. Say plainly whether a meal is a match; don't soften a miss.
- Write like Friday night is allowed: mains, sides and dessert, not rations.
- Never use: "guilty pleasure", "diet-friendly", "sin-free", "swipe right", "Tinder for food", "user".
- Tagline: "Find your guilt-free cheat meal."
- Sample copy: "This plate's a match." "3 g over on fat. Still a match." "Nothing here fits yet. Try loosening carbs."

## 10. Do not

- No checkout, cart or payment. Hungry Henry stops at Match.
- No photo carousels, review walls or guidebook-style editorial.
- No second bright colour competing with Rusty Spice.
- No pale olive or tea-green text on white.
- No emoji in the UI.
