# Hungry Henry — component inventory

Hungry Henry–only pieces. Not the generic library (Button, Input, Badge). Those stay in Figma as the usual variant sets.

This file is what we build in Figma before Home is drawn. If a field is not here, do not invent it on a screen.

Copy in the product says **you**. The person is a Fitness Enthusiast. The product is **Hungry Henry**.

Chrome (nav, buttons, macros, chips) uses Inter. Restaurant names and menu items use **Fraunces**.

Colours come from `brand/tokens.json` v2.0.0 (Muted Olive, Tea Green, White, Blackberry Cream, Rusty Spice). Do not type a hex in Figma. Paint styles are named `muted-olive-700`, `rusty-spice-600`, and so on.

## Figma hierarchy

Property names are `Property=Value`. Icons are never a colour variant — swap them.

| Layer | Component | Types and values |
| --- | --- | --- |
| Glyph | Icon | Name = Heart, Plus, Bookmark, Undo, ArrowBack, ArrowForward, Search, Pin, Person, Utensils, Close, Filters |
| Button | Action button | Size = Sm, Md, Lg. Tone = Muted, Brand. Icon is a swap, not a variant. |
| Button | Nav item | Selected = True, False. Label text. Icon is a swap. |
| Group | Action group | Rear Sm, Save Md, Match Lg Brand, Add Md, Forward Sm |
| Group | Bottom nav | Selected = Match, Map, Filters, Account |
| Other | Button | Variant = Primary, Ghost, Danger. Size = Md. State = Default, Disabled |
| Other | Title pill | State = Unlocked, Locked |
| Other | Macro row | Indicator = Off, Diff, Hit |
| Other | Diet pill | Placement = Plate, Selected |
| Other | Map pin | State = Default, Selected |
| Other | Restaurant drawer | Source = Map, Add |
| Other | Search bar | State = Collapsed, Expanded. On Home and Map; tap opens `/search` |
| Other | Nutrition filter | Enabled = Off, On. Compare = Less, More, Is, Range. Name = Energy, Carbs, Fat, Protein |
| Other | Filter toggle | Kind = Diet, Allergy. State = Off, On |
| Other | Filters nutrition section | The four nutrition rows plus Advanced |
| Other | Filters diets section | Diet toggles |
| Other | Filters allergies section | Allergy toggles |

## Design inspo

Taken from the three Mobbin boards named in `HUNGRY-HENRY.md`. Mobbin itself needs a login; these are the patterns those products are known for, and what we will and will not copy.

### Tripadvisor

[Tripadvisor iOS screens](https://mobbin.com/apps/tripadvisor-ios-ed0940e2-5ae2-4ee4-a983-dc77db6654af/39c453d6-38bd-4fb4-86ed-f12db948d8d9/screens)

Take: restaurant name, stars, and distance in one tight header. Map pins only for places that qualify. A sheet that opens from a pin. Comments sitting with the place, not in a separate app area. Search that highlights the word you typed.

Leave: the giant photo carousel, the review-site chrome, and anything that makes Hungry Henry feel like a guidebook.

### Zip

[Zip iOS screens](https://mobbin.com/apps/zip-ios-9c5e6faf-b117-4e52-97ca-8ab194e9d489/732a21c0-ee06-4f81-83c8-35f81d4a5903/screens)

Take: a short action bar along the bottom of the plate (not a floating heart in the corner). Filter chips for diets and allergies. A menu that comes up as a sheet, not a new page. Dense but calm type.

Leave: checkout, pay, and cart. Hungry Henry stops at Match.

### Blackbird

[Blackbird iOS screens](https://mobbin.com/apps/blackbird-ios-b9cc8195-aa38-4ca6-8d13-8d719bd1b8a4/e45a22c0-6998-4ef3-a499-bbd5e5cbd5e4/screens)

Take: a stacked list of dishes that feels like a plate, not a Tinder deck. A map that is quiet. Saved and recent as collections under Account. A restaurant sheet with a few popular plates you can tap straight onto Home.

Leave: membership, city-guide editorial, and any card-swipe metaphor. Food items bump in and bump out one by one so a locked item can stay put.

---

## Bottom nav

On every main screen except full-page Search (Search is not a tab).

| Item | Opens | Icon | Notes |
| --- | --- | --- | --- |
| Match | `/home` | Utensils | Default. This is the meal-match plate. |
| Map | `/map` | Pin | Only restaurants that currently have a match. |
| Filters | `/filters` | Filters | Nutrition targets, diets, and allergies. Replaces Search in the bar. |
| Account | `/account` | Person | Collections live here (Saved, Recent). |

Selected tab uses Rusty Spice (`primary.600`). Unselected uses Blackberry Cream muted (`surface.textMuted`). Bar sits on white. Icon plus word, same as Tripadvisor and Blackbird — not icon-only.

---

## Search bar

On `/home` and `/map` only. Not a bottom-nav item.

**Collapsed** — compact control (chef mark + search). Sits in Restaurant info on Home; floats at the top of Map.

**Expanded** — the `/search` page. Tap the collapsed bar to open it. Keyword, restaurant, and Ask Henry live here.

| Field | What it is | Token |
| --- | --- | --- |
| Placeholder | “Search” | `surface.textMuted` |
| Ask Henry | Optional prompt under the field | Same as a secondary button, not a third nav item |

Closing Search returns you to the screen you came from (Home or Map). The dock on `/search` keeps that tab selected — never a Search tab.

---

## Filters

`/filters`. The control centre. Three sections, in this order:

1. `filters-nutrition-section`
2. `filters-diets-section`
3. `filters-allergies-section`

You change targets here. The plate only shows the result.

---

## Nutrition filter

The main control on Filters. One row per name: **energy**, **carbs**, **fat**, **protein**.

| Field | What it is | Token |
| --- | --- | --- |
| Name | Energy, carbs, fat, or protein | `surface.text` |
| Toggle | On or off. Off means Henry ignores this macro | Track `neutral.200` / thumb white. On: track `accent.600` |
| Compare | Three-way: **less**, **more**, **is**. Hidden when the toggle is off | Selected: Rusty Spice fill, `primary.on` type. Unselected: `neutral.100` |
| Value | Number plus unit (kcal or g) | `surface.text` |
| Advanced | Dropdown. Closed shows the label and a chevron. Open reveals the range slider | Trigger uses `surface.textMuted`. Open trigger uses Rusty Spice |
| Range slider | Inside the Advanced dropdown. Two handles | Track `neutral.200`, fill and handles `primary.600` |

**Range** — two handles, inside the Advanced dropdown. Henry presents the option bounds for the current match set. You pick a min and a max. Less / more / is stay on the segmented control.

States: Advanced = Closed, Advanced = Open. Off / less / is / more live on the segmented control, not as separate component variants.

---

## Filter toggle

One row. Used for a diet and for an allergy. Same component, different `Kind`.

| Field | What it is | Token |
| --- | --- | --- |
| Name | Diet or allergy name | `surface.text` |
| Toggle | On or off | Same toggle as nutrition |

States: off, on.

---

## I'm looking for

Withdrawn as a screen control. Targets live on `/filters`. The old collapsed chip row is not on Home or Map.

---

## Toggleable title pill

Restaurant name and each food name on Home. Tap to lock. Tap again to unlock.

Locking a food also locks the restaurant. Foods come from one restaurant.

| Field | What it is | Token |
| --- | --- | --- |
| Label | Restaurant name, or food name. Set in Fraunces. | Unlocked: `surface.text`. Locked: `primary.on` on Rusty Spice. |
| Lock mark | Visible when selected | Same as the locked fill, not a new colour |

States: unlocked, locked, pressed (the pill expands, then settles).

Motion: the pill grows on lock. It does not flip like a card.

---

## Restaurant info

Top of Home, and the header of the restaurant drawer.

| Field | What it is | Token |
| --- | --- | --- |
| Name | Toggleable title pill | See above |
| Stars | Google rating | `surface.text` |
| Distance | From you | `surface.textMuted` |
| Comments | Optional. Other people on this match | `surface.textMuted`. Not a Tripadvisor review wall. |

---

## Stacked food list

The plate. Each row is a food. The list feels endless and fades to white above the match-data group.

| Field | What it is | Token |
| --- | --- | --- |
| Food name | Toggleable title pill | See above |
| Category | Optional (starter, main) | `surface.textMuted` |

States: idle, locked (stays in place on the next match), bumping out, bumping in.

Motion: on swipe or rear/forward, unlocked rows leave and new rows arrive one by one. Locked rows do not move. This is not a card stack.

---

## Macro row

One row per macro on the match-data group: energy, protein, carbs, fat.

| Field | What it is | Token |
| --- | --- | --- |
| Name | Energy, protein, carbs, or fat | `surface.textMuted` |
| Icon | Same four, always | `surface.text` |
| Value | Number plus unit (kcal or kJ, g) | `surface.text` |
| Indicator | Shown when you are looking for this macro | `accent.600` Muted Olive — the dark step, so it reads on white. Not the pale wash. |

Indicator values:

- `+` / `-` and the difference, when the plate is off your target
- **Hit**, when it is on target (under or over as you defined it)

A little over or under still counts as a match. The difference goes to the nutrition bank. The row tells you that in the indicator. It does not scold.

---

## Diet and allergy pills

On the match-data group, under the macros. Read-only on the plate. You change them on `/filters`.

| Field | What it is | Token |
| --- | --- | --- |
| Label | Diet or allergy name | Plum on `accent.100`, or `surface.text` on `neutral.100` |

States: on plate (not tappable), selected in I'm looking for, not selected.

---

## Lower action group

Fixed under the plate on Home. Five large circular buttons, Tinder-style: smaller on the ends, Match biggest in the middle. Not a swipe deck — the buttons sit under the plate.

| Control | What it does | Icon | Size | Tone |
| --- | --- | --- | --- | --- |
| Rear | Previous match. For people who will not swipe | ArrowBack | Sm (56) | Muted. White fill, Blackberry Cream icon |
| Save | Puts this match in Saved | Bookmark | Md (64) | Muted |
| Match | You are going to eat this | Heart | Lg (80) | Brand. `primary.600` fill, `primary.on` icon. This is the only loud control |
| Add | Opens the current restaurant's menu as a sheet | Plus | Md (64) | Muted |
| Forward | Next match | ArrowForward | Sm (56) | Muted |

Match is the north star. Nothing else in this bar is Rusty Spice fill.

---

## Restaurant drawer

Sheet from Map (a pin) and from Add on Home (the menu).

From a **map pin**:

| Field | What it is |
| --- | --- |
| Restaurant info | Name, stars, distance |
| Popular meals | A short list. Tap one: open Home with every food on that plate, restaurant locked |

From **Add**:

| Field | What it is |
| --- | --- |
| Menu list | Foods at the current restaurant |
| Food row | Name, optional category |

Pick a food: it locks, the restaurant locks, the sheet closes, you are on Home.

States: closed, open from map, open from Add, empty (no popular meals / no menu).

Tripadvisor sheet, Zip menu sheet, Blackbird restaurant sheet — one pattern, two entry points.

---

## Search result

Two kinds of row, plus an AI path that skips the list.

**Meal match row**

| Field | What it is | Token |
| --- | --- | --- |
| All foods in the match | Names | `surface.text` |
| Keyword | The letters you typed, marked in the names | Highlight fill `accent.100`, type still Blackberry Cream |
| Delta | How far this plate is from your target | `accent.600` |

Tap: Home, that match loaded.

**Restaurant row**

| Field | What it is | Token |
| --- | --- | --- |
| Name | Restaurant | `surface.text` |
| Stars | Rating | `surface.text` |
| Distance | From you | `surface.textMuted` |

Tap: Home, that restaurant already locked, a match already generated.

**AI prompt**: no result list. Straight to Home with a match for what you asked.

---

## What this file does not hold

- Button, input, and other generic variants — Figma primitives.
- Screen-to-requirement names — `screen-inventory.md`, once IDs exist.
- Colours — `brand/tokens.json`.
- B2B restaurant-operator screens — out of MVP.
