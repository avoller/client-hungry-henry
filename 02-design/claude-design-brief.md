# Hungry Henry — product brief for Claude Design

Read this before designing anything for Hungry Henry. It gives the background: who the product is for, what problem it solves, what v1 includes, and the design system it must follow. If this brief and a source file disagree, the source file wins. Sources are listed in section 12.

---

## 1. One line

**Hungry Henry finds your guilt-free cheat meal.** It is an iPhone app that builds a plate from a nearby restaurant to match your remaining calories, protein, carbs and fat. You lock the foods you want, Henry rebuilds the rest, and you tap **Match**.

Tagline: *Find your guilt-free cheat meal.*

## 2. The problem

You've stuck to your nutrition plan all week. On Friday night you eat out, and in 20 minutes a week of careful dieting is undone.

- Restaurants post menus, not nutrition.
- Google Maps, Yelp and delivery apps rank places by rating, distance, cuisine and price. None of them filter by your personal nutrition targets.
- Swapping items and choosing courses is left to mental maths. Restaurant websites don't do it for you.

The result is a long, anxious hunt that often ends in a meal that blows the plan or never gets logged.

| Metric | Today | Goal |
| --- | --- | --- |
| Average meal search time | 23 min | **3 min** |
| Weekly plan completion rate | 30% | 75% |
| Calorie spread on cheat meals (SD) | 500 kcal | 150 kcal |

Size of the problem: about **3.2 billion** restaurant meals a year in the US blow the plan or go untracked. That comes from 81M Fitness Enthusiasts × 72 occasions a year × 55%.

**What the design has to deliver:** cut a 23-minute hunt to about 3 minutes. Every screen should shorten the path to Match.

## 3. Who it's for

**The Fitness Enthusiast**: someone actively following a fitness or nutrition plan who still wants to eat restaurant meals. They are the person most likely to give up on the plan when a menu doesn't show how a meal fits their targets.

- **Beachhead: Macro-Tracking Dine-Out Regulars**, about 9.1M people in the US. They log macros daily in apps such as MyFitnessPal, Lose It! or Cronometer, and they mostly eat at sit-down restaurants.
- **First use case: Dine-Out.** Delivery and takeout come later.
- A second customer, the **Restaurant Operator**, pays for B2B listing tiers. Operator screens are **out of MVP scope**.

### How they find a meal today (current-state journey)

| Stage | What they do | How they feel |
| --- | --- | --- |
| Choose dining mode | Check the macros they have left and pick an occasion | Hopeful |
| Search nearby venues | Open Maps or Yelp and compare stars and distance. There is no goal filter | Overwhelmed |
| Inspect posted menus | Scroll PDF menus looking for calorie labels | Frustrated |
| Estimate remaining fit | Look items up in a tracker and guess the missing macros | Anxious |
| Compose mixed plate | Work out swaps by hand, re-total, give up on combos | Resigned |
| Confirm chosen meal | Choose the venue and items, then go | Relieved |

Hungry Henry collapses the middle four stages into a single screen.

## 4. Positioning

**Position to own:** *a restaurant meal matched to your target, without the 23-minute hunt.* That means strong nutrition-goal filtering and a short time to a decision, supported by plate customisation.

| | Goal filtering | Time to decide (lower is better) | Restaurant coverage | Plate customisation |
| --- | --- | --- | --- | --- |
| Google Maps | 1 | 7 | 10 | 2 |
| Calorie counter apps | 7 | 8 | 6 | 3 |
| Manual (read the menu, guess) | 3 | 9 | 3 | 6 |
| **Hungry Henry** | **9** | **2** | **10** | **9** |

Scores are assumptions, not survey results. Maps finds a venue, not a plate. Trackers log a dish after you've chosen it. Henry builds the plate **before** you order.

## 5. Business model (context only)

- The app is **free** for the Fitness Enthusiast. There is no checkout, cart or payment: Hungry Henry stops at Match.
- Restaurants pay for SaaS tiers:
  - **Free**: standard matching; the restaurant can update its menu.
  - **Pro Silver**: more visibility, plus short-term boosts for a meal.
  - **Pro Gold**: featured matches for popular target profiles, and chef-curated pairings.
  - Prices are unconfirmed. The working assumption is $149/mo for Silver and $399/mo for Gold.
- North-star metric: **Meals Matched**, the moment someone taps Match on a meal they intend to eat.

## 6. The MVP happy path (Dine-Out)

1. Open Hungry Henry on an iPhone. It opens on **Filters**, with every macro turned off.
2. Set the remaining target. For example: energy *less than* 1,000 kcal, protein *more than* 30 g, one diet or allergy on (pescatarian, shellfish).
3. Go to **Home (Match)**. Henry shows a plate from a nearby restaurant: the restaurant name, stars and distance; a stack of foods; energy, protein, carbs and fat, each showing **Hit** or a ± difference; and diet or allergy pills.
4. **Lock** a food you already want by tapping its name. This also locks the restaurant, and that food's nutrition is held constant.
5. Tap **Forward**. Unlocked foods bump out and new ones bump in, **one at a time**. The locked food stays where it is and the macros update.
6. Tap **Match**. A confirmation screen shows the chosen foods and final macros, with a **Share** control. The job is done.

## 7. Screens and key components

App routes: `/home` (Match), `/map`, `/filters`, `/account`, and `/search` (full page, not a tab).

### Home (Match tab): the core screen
- **Restaurant info**: the restaurant name as a toggleable title pill (Fraunces), ★ rating, and distance in muted text. There is a collapsed search control (chef mark + magnifier) at the top right. Optional comments on the match.
- **Stacked food list**: one row per food. Each name is a toggleable pill, with an optional course label (Entrée / Main / Dessert), kcal and protein, and a one-line description. The list fades to white above the macro group.
- **Macro group**: energy, protein, carbs and fat, each with a label, a value and an indicator. The indicator reads `−80` or `+12 g`, or **Hit**, in olive `#50663C`. A small miss still counts as a match. It never scolds. Diet and allergy pills sit below, read-only.
- **Action bar**: five circular buttons. Rear (56, ←), Save (64, bookmark), **Match (80, heart, solid Rusty Spice)**, Add (64, +), Forward (56, →). Match is the only filled, loud control.
- **Add** opens the current restaurant's menu as a bottom sheet. Picking a food locks it (and the restaurant) and closes the sheet.

### Filters: the control centre (page title "I'm looking for..")
- Three sections, in this order: **Nutrition**, **Diets**, **Allergies**.
- Nutrition has a row each for energy, protein, fat and carbs. Each row has a segmented control (off / less / is / more), a value with its unit shown in large Fraunces numerals, and an **Advanced** disclosure that reveals a two-handle range slider. The slider's bounds come from the current set of matches ("Henry shows the options he can match").
- Diets and Allergies: one toggle row per item.

### Map
- A quiet, washed-out map. It pins **only restaurants that currently have a match**. The selected pin is larger and Rusty Spice.
- Tapping a pin opens the **restaurant drawer**: name, stars, distance, and 2–4 *Popular matches*, each with a kcal delta. Tapping a match opens Home with that plate loaded and the restaurant locked.

### Search (full page, opened from the collapsed search bar on Home or Map)
- **Meal match rows**: all foods in the match, with the typed keyword highlighted on Tea Green and the delta to target in olive. Tapping one opens Home with that plate.
- **Restaurant rows**: name, stars and distance. Tapping one opens Home with the restaurant locked and a fresh match.
- **Ask Henry**: a natural-language prompt ("something spicy under 800 kcal") that skips the results list and goes straight to a plate on Home.
- Closing Search returns you to the screen you came from.

### Account
- Collections: **Saved** (from the Save button) and **Recent** (meals you've matched).

### Bottom nav (every main screen)
Match (utensils) · Map (pin) · Filters (sliders) · Account (person). Each tab has an icon and a label. The selected tab is Rusty Spice and unselected tabs are muted plum. Search is **not** a tab.

### Component list (already in Figma)
Icon, Action button (Sm/Md/Lg × Muted/Brand), Action group, Nav item, Bottom nav, Button (Primary/Ghost/Danger), Title pill (Unlocked/Locked), Macro row (Off/Diff/Hit), Diet pill, Map pin (Default/Selected), Food row, Restaurant drawer (Source = Map/Add), Search bar (Collapsed/Expanded), Nutrition filter, Filter toggle, and the three Filters sections.

Figma file: https://www.figma.com/design/KgGqrjgtSA4Zh5hiI7yUiM (pages: Foundations, Primitives, Screens, Icons).

## 8. Design system

### Feel
The feel is calm, dense and editorial, like a good restaurant menu rather than a fitness dashboard or a review site. Use white space and thin plum dividers, not heavy cards. There is **light mode only**.

### Colour (from `brand/tokens.json` v2.0.0)

| Role | Name | Hex |
| --- | --- | --- |
| Primary: Match button, selected tab, locked pills, selected segment, sliders, focus ring | Rusty Spice | `#B43B1F` |
| Body ink, icons, text on green | Blackberry Cream | `#503047` |
| Muted text (distance, captions, unselected nav) | Plum 500 | `#8E6A83` |
| Borders and dividers | Plum 400 | `#AA859F` |
| Chip / unselected segment background | Plum 100 | `#F0DAE9` |
| Toggle and slider track | Plum 200 | `#DFC0D5` |
| Sunken background | Plum 50 | `#FFF0FA` |
| Macro indicators, success, olive text | Olive 600 | `#50663C` |
| Large decorative fills only | Muted Olive | `#ADC698` |
| Pill background, keyword highlight | Tea Green | `#D0E3C4` |
| Olive tint background | Olive 50 | `#EFF9E8` |
| Primary tint background | Spice 50 | `#FFF2EE` |
| Page and cards | White | `#FFFFFF` |
| Error (kept distinct from Match) | Crimson | `#A4192C` on `#FBE9EC` |
| Warning | Amber | `#8A5A00` on `#FDF3DC` |

Colour rules:
- Rusty Spice is the **only** loud colour. On Home, only the Match button has a solid Rusty Spice fill.
- Never set Muted Olive or Tea Green text on white. Text on those colours is Blackberry Cream.
- Every text colour must meet WCAG AA contrast.
- No gradients, except the fade to white at the bottom of the food list.

### Type
- **Fraunces** (serif) for restaurant names, food and menu item names, and big numerals. Food names on the plate are 20–24 px.
- **Inter** for all chrome: nav, buttons, macro labels, chips, body text.
- **JetBrains Mono** is available for data if it's ever needed.
- Scale: 12 / 14 / 16 / 18 / 20 / 24 / 30 / 36 px. Weights: 400, 500, 600, 700. Line height: 1.2 for headings, 1.5 for body.

### Shape, space and elevation
- Spacing is on a 4 px grid, with 16 px screen gutters.
- Radius: 2 px (small), 6 px (inputs and cards), 12 px (sheets), fully round for pills and circular buttons.
- Use one soft shadow, only for bottom sheets and the action bar. Everything else is flat.
- Icons are Lucide-style line icons with a 1.5 px stroke.
- Target device: iPhone, 390 × 844. Design for touch: large targets, primary actions within thumb reach.

### Motion
- Food rows **bump out and bump in individually**, in crisp sequences. Locked rows don't move. **This is not a Tinder card stack.**
- A title pill grows slightly when it locks, then settles. It never flips.
- Use 150–250 ms ease-out timing. Bottom sheets slide up.

### Brand character
Chef Henry is a small illustrated chef in a red coat (`01-discovery/visuals/chef-red-coat.png`). He appears in the collapsed search control and can lead the Ask Henry prompt.

## 9. Voice and copy

- The person is a **Fitness Enthusiast**. In the UI, address them as **"you"**. Never write *user*, *diner*, *customer* or *consumer*.
- The name is **Hungry Henry**: two words, both capitalised, no *the*. Never *HH* or *HungryHenry*.
- Tone:
  - **Direct**: say plainly whether it's a match. Don't soften a miss.
  - **Appetising**: write as if Friday night is allowed. Mains, sides and dessert, not rations.
  - **Unashamed**: don't apologise for eating out and don't lecture.
- Never use: *guilty pleasure*, *diet-friendly*, *sin-free*, *swipe right*, *Tinder for food*.
- Sample copy: "This plate's a match." · "3 g over on fat. Still a match." · "Nothing here fits yet. Try loosening carbs."
- No emoji in the UI.

## 10. Do not

- Add checkout, cart, payment or delivery ordering.
- Add photo carousels, review walls, or city-guide editorial. Hungry Henry is not Tripadvisor.
- Use card-swipe or Tinder metaphors: no PASS/MATCH stamps, no restaurant swiper.
- Add a second bright colour that competes with Rusty Spice.
- Design restaurant-operator (B2B) screens. They are out of MVP.
- Use features that prototyping dropped:
  - **Pin throughout**, which kept a restaurant pin on screen after the place was chosen.
  - A **restaurant swiper**; movement stays at the food level.
  - A **heavy or technical theme**.

### Inspiration (take the pattern, leave the rest)
- **Tripadvisor**: take the tight name/stars/distance header, pins only for qualifying places, a sheet that opens from a pin, and keyword highlighting. Leave the photo carousels and review-site chrome.
- **Zip**: take the short action bar under the content, filter chips, and the menu as a sheet. Leave checkout.
- **Blackbird**: take a dish stack that feels like a plate, a quiet map, collections under Account, and a restaurant sheet with popular plates. Leave membership and editorial.

## 11. Open questions and known inconsistencies

Resolve these with Alex before treating a design as final:

1. **Nutrition bank.** `HUNGRY-HENRY.md` and the component inventory say a small over or under "goes to the nutrition bank". The prototyping round dropped *calorie banking* as a standing balance. For now, show only the difference on the current plate, with no ledger or counter.
2. **Nav labels in the current mockups.** The Home mockup's first tab reads "Eat" and the Map mockups show "Match" twice. The spec is Match · Map · Filters · Account.
3. **Earlier AI Studio draft.** The draft notes at the bottom of `HUNGRY-HENRY.md` describe cream `#FAF6F0`, sage green, Plus Jakarta Sans, PASS/MATCH stamps, a Nutrition Bank counter, an occasion selector and an Operator Portal. **They are superseded** by `brand/tokens.json` and `02-design/ai-studio-style-guide.md`.
4. **Match confirmation screen.** This is the completion point, with the chosen foods, final macros and Share. It is described in the workbook but not yet drawn in Figma.
5. **Empty and edge states** are not designed yet: no match found, no menu, a restaurant drawer with no popular meals, and loading. There is an existing `loading.png` mockup.
6. **Comments on a match** are in the notes but have no designed component.
7. **Nutrition provenance.** Menu data may be listed by the restaurant or estimated from USDA FoodData Central. It's still open whether the UI should show which.

## 12. Sources in this repo

| File | What it holds |
| --- | --- |
| `brief.md` | Approved config: actor, JTBD, outcomes, beachhead, pricing |
| `01-discovery/hungry-henry-workbook.md` | Full product workbook: problem, market, positioning, MVP, prototyping lessons |
| `HUNGRY-HENRY.md` | Founder notes: screens, flows, data model, analytics |
| `brand/tokens.json` | Design tokens (source of truth for colour, type, space) |
| `brand/voice.md` | Voice and naming rules |
| `02-design/ai-studio-style-guide.md` | A condensed style guide for generative UI tools |
| `02-design/component-inventory.md` | Hungry Henry–specific components, fields, states and tokens |
| `01-discovery/visuals/screens/*.png` | Current mockups: Home, Filters, Map + drawer, Search, Account, Add menu, Loading |
| `01-discovery/visuals/customer-journey-map.png` | Current-state journey |
| `decisions/assumptions.md` | Every unsourced number, with confidence and owner |
