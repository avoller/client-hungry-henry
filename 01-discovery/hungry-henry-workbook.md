# Product Idea Workbook
By Alex Voller

## Product Idea Brief

TBA

## 1. Customer Problem Space

### 1. Fertile Land

Resturants

### 2. Actor

**Fitness Enthusiast**

A Fitness Enthusiast is a person actively pursuing a fitness or nutrition plan who still wants to eat restaurant meals, and who is at risk of abandoning that plan when menus do not show how a meal fits their targets.

The Fitness Enthusiast is Initiator, Primary User, Decider, and Buyer of the consumer product. A second customer concept — the Restaurant Operator — is Buyer of the B2B listing tiers, and is not developed as the course Actor.

### 3. Job To Be Done

To find a restaurant meal.

<!-- landscape -->

### 4. Outcomes

| Outcome idea | Metric | Actual Outcome | Desired Outcome | Measurement Method |
| --- | --- | --- | --- | --- |
| Faster meal find | Ave. Meal Search Time | The Ave. Meal Search Time is 23 minutes. | The Ave. Meal Search Time will be 3 minutes. | **Calculate:** minutes from the trigger (decide to eat a restaurant meal) to a confirmed item selection, averaged across occasions. Actual = 14 minutes selecting a restaurant + 9 minutes deciding what to order once seated.[1] Units: minutes per occasion. |
| Broken mundane nutrition cycle | Ave. Plan Completion Rate | The Ave. Plan Completion Rate is 30%. | The Ave. Plan Completion Rate will be 75%. | **Calculate:** `(weekly cycles finished ÷ weekly cycles started) × 100`. A cycle is finished if the Actor logs through the week's last planned day without abandoning the plan. Units: percent. *(assumption: actual 30% is informed by Helander et al. 2020 — new January dieters persist about 3.1–5.3 weeks, so most intended weekly cycles in a longer plan are not finished;[6] desired 75% is 45 percentage points above that DIY baseline.)* |
| Less next-day guilt | Ave. Cheat-Meal Calorie SD | The Ave. Cheat-Meal Calorie SD is 500 kcal. | The Ave. Cheat-Meal Calorie SD will be 150 kcal. | **Calculate:** sample SD of caloric deviation on cheat meals, `SD = sqrt(Σ(d_i − d̄)² / (n − 1))`, then averaged across Actors. `d_i` = calories of cheat meal *i* − the Actor's remaining calorie target for that meal. Units: kcal. Actual 500 kcal is the spread when the plate is guessed from a posted menu *(assumption)*. Desired 150 kcal is a tight enough band around the intended cheat that the meal reads as guilt-free. |

**Outcome 1 — Faster meal find** (`Ave. Meal Search Time`)
- Actual Outcome Statement: The Ave. Meal Search Time is 23 minutes.
- Desired Outcome Statement: The Ave. Meal Search Time will be 3 minutes.
- Measurement Method: minutes from trigger to confirmed item selection, averaged across occasions. Units: minutes per occasion. Source: US Foods.[1]

**Outcome 2 — Broken mundane nutrition cycle** (`Ave. Plan Completion Rate`)
- Actual Outcome Statement: The Ave. Plan Completion Rate is 30%.
- Desired Outcome Statement: The Ave. Plan Completion Rate will be 75%.
- Measurement Method: `(weekly cycles finished ÷ weekly cycles started) × 100`. Units: percent. Source: Helander et al. 2020.[6]

**Outcome 3 — Less next-day guilt** (`Ave. Cheat-Meal Calorie SD`)
- Actual Outcome Statement: The Ave. Cheat-Meal Calorie SD is 500 kcal.
- Desired Outcome Statement: The Ave. Cheat-Meal Calorie SD will be 150 kcal.
- Measurement Method: `SD = sqrt(Σ(d_i − d̄)² / (n − 1))` of cheat-meal caloric deviations from the remaining target. Units: kcal. *(assumption: actual 500 kcal; desired 150 kcal.)*

<!-- portrait -->

### 5. Customer Journey Map

Current-state journey: how a Fitness Enthusiast finds a restaurant meal today, without Hungry Henry. The journey starts after the trigger and ends when the meal is chosen.

<!-- landscape -->

![Current-state Customer Journey Map](visuals/customer-journey-map.png)

<!-- portrait -->

| Layer | Choose Dining Mode | Search Nearby Venues | Inspect Posted Menus | Estimate Remaining Fit | Compose Mixed Plate | Confirm Chosen Meal |
| --- | --- | --- | --- | --- | --- | --- |
| Tasks | Check remaining macros; Pick dining occasion; Select dine-out mode; Gather companion input; Set location context | Open nearby maps; Scan nearby venues; Compare star ratings; Compare walking distance; Filter without goals ★ | Open restaurant site; Scroll posted menu; Hunt calorie labels ★; Screenshot candidate items; Switch candidate venue | Search item calories; Open tracker database; Guess missing macros ★; Subtract remaining budget; Reject oversized mains | Pick candidate main; Add possible sides; Calculate swaps by hand ★; Retotal combined plate; Abandon failed combo | Choose final venue; Lock chosen items; Place order or go; Save selected meal |
| Experiences | Hopeful | Overwhelmed | Frustrated | Anxious | Resigned | Relieved |
| Information | Macros remaining; Weeknight or cheat | Rating, distance; No goal filter | Names and prices; Nutrition missing | Partial calories; Daily budget left | Running total; Sides and swaps | Chosen items; Order confirm |
| Touchpoints | Nutrition tracker; Calendar; Companions | Google Maps; Yelp; Apple Maps | Restaurant site; PDF menu; Phone browser | MyFitnessPal; Web search; Calculator | Notes app; Companions; Server or cart | Maps; Delivery app; Host stand |

★ Causes — starred tasks are the contributing causes in §1.6.

### 6. Problem

#### Gap

| Metric | Desired | Actual | Gap (Desired − Actual) |
| --- | --- | --- | --- |
| Ave. Meal Search Time | 3 minutes | 23 minutes | 20 minutes extra per occasion |
| Ave. Plan Completion Rate | 75% | 30% | 45 percentage points |
| Ave. Cheat-Meal Calorie SD | 150 kcal | 500 kcal | 350 kcal wider spread |

Fitness Enthusiasts cannot find a restaurant meal that fits their nutrition targets without a long manual search, because restaurants post menus rather than nutrition, discovery products do not filter by personal goals, and substitutions are left to mental math.

#### Causes

**Root cause.** No product treats the Actor's personal nutrition targets as a filter on restaurant meal discovery, so the matching step between "what is on this menu" and "what I should eat" is left to the Actor.

**Contributing causes** (each starred on the current-state map):

1. **Filter without goals** (Search Nearby Venues). Google Search and other food products do not filter by a user's personal nutrition goals.
2. **Hunt calorie labels** (Inspect Posted Menus). Restaurants post menus, not nutrition.
3. **Guess missing macros** (Estimate Remaining Fit). Where a calorie figure exists it is often incomplete; protein, carbs, fat and allergens are missing, so the Actor guesses.
4. **Calculate swaps by hand** (Compose Mixed Plate). Meal substitutions and course selection require logic not implemented on restaurant websites.

### 7. Use Cases

1. **Dine-Out** — The Actor sits down at a restaurant and must choose a venue and a plate before ordering.
2. **Delivery** — The Actor orders a restaurant meal to a home or gym and must choose from marketplace menus without seeing the food.
3. **Takeout** — The Actor picks up a restaurant meal and must choose items that will travel, still inside the nutrition target.

### 8. Problem Sizing

Selected problem: **Cheat-Meal Guilt Problem** — restaurant meals that blow the nutrition plan or go untracked. The size is the number of those meals.

Frequency of the JTBD: 72 restaurant-meal occasions per Actor per year (`assumption:` 6 occasions per month, slightly below the US Foods preference of about 8 restaurant occasions per month).[1] Number of Actors: 81 million Fitness Enthusiasts in the United States, using 2025 US fitness-facility membership as the aligned published proxy.[2] Share of those occasions that are a blow-out or untracked meal: 55%, from the client's pitch that 55% of restaurant patrons trying to lose weight feel guilty the next day.[13] (`assumption:` one guilty occasion = one blow-out or untracked meal.)

**Per instance**

`1 restaurant occasion × 0.55 = 0.55 blow-out or untracked meals per occasion`

**Annualized per actor**

`0.55 meals/occasion × 72 occasions/year = 39.6 blow-out or untracked meals/year per Fitness Enthusiast`

**Total impact, annually (America)**

`39.6 meals/year × 81,000,000 Fitness Enthusiasts = 3,207,600,000 blow-out or untracked meals/year`

That is **3.2 billion blow-out or untracked restaurant meals per year in America.**

The other gaps, for completeness:

- Search time: `23 minutes − 3 minutes = 20 minutes` extra per occasion; `20 × 72 = 1,440 minutes` (24 hours) per Actor per year; `24 × 81,000,000 = 1.944 billion hours/year`.[1][2]
- Plan completion: `75% − 30% = 45 percentage points` each weekly cycle. `52 × 30% = 15.6` weeks finished today; `52 × 75% = 39` weeks at the desired rate. The gap is 23.4 unfinished weeks per Actor per year (`assumption:` weekly cycle).[6]
- Cheat-meal calorie SD: `500 kcal − 150 kcal = 350 kcal` wider spread per cheat occasion (`assumption:`).

### 9. Problem Category

Meal Search Problem

### 10. Problem Statement

Fitness Enthusiasts want restaurant meals that stay on their nutrition plan, but restaurants post menus rather than nutrition and discovery tools do not filter by personal goals. Consequently 55% of restaurant occasions blow the plan or go untracked — 39.6 such meals per Actor per year, **3.2 billion blow-out or untracked meals per year in America** across the 81 million people who match the Actor.

## 2. Market Space

### 1. Overall Market

**US Fitness Enthusiast Dining-Out Market** — everyone who matches the Actor and does the JTBD.

Number of Actors: **81 million** in the United States (2025 fitness-facility members). The published figure is membership, not a self-label of "Fitness Enthusiast"; it is the closest aligned count for people in a structured fitness practice. Total facility users, including non-members, exceeded 100 million in 2025.[2]

Trend: **growing.** Membership rose 5.2% from 2024 to 2025, and 20% from 2019 to 2024, as fitness facilities moved from amenity to health infrastructure.[2][3] More people in a plan means more occasions on which a restaurant meal can break that plan.

### 2. Total Addressable Market (TAM)

Course note: do not complete until the last Product Assignment.

### 3. Market Segmentation

Scheme 1 uses the go-to-meal variable. The same variable is applied across every segment. Sizes are a partition of the 81 million Actors (`assumption:` primary mode, so each Actor is counted once).

| Segmentation Variable | Segment Values | Segment Name | Segment Size |
| --- | --- | --- | --- |
| Go-to meal | Dine-Out | Dine-Out Regulars | 36.45 million (45%) |
| Go-to meal | Delivery | Delivery Regulars | 22.68 million (28%) |
| Go-to meal | Takeout | Takeout Regulars | 21.87 million (27%) |

Notes: 45% dine-out as primary mode follows the US Foods finding that dining out holds a slight preference edge (55% vs 45% takeout/delivery) and is then pulled down so the three values sum to the market.[1] The 28% / 27% split of the remaining 55% is `assumption:`.

A second scheme, used to name the beachhead, cuts on nutrition-tracking behaviour:

| Segmentation Variable | Segment Values | Segment Name | Segment Size |
| --- | --- | --- | --- |
| Nutrition-tracking intensity | Daily macro log | Macro Trackers | 20.25 million (25%) |
| Nutrition-tracking intensity | Has a plan, does not log daily | Goal-Aware | 36.45 million (45%) |
| Nutrition-tracking intensity | Trains, loose nutrition | Fitness-Only | 24.30 million (30%) |

Shares in scheme 2 are `assumption:`. The schemes are not multiplied in the market total; the beachhead below is the overlap used for entry, not a fourth segment added to 81 million.

### 4. Target Market Profiles

**Dine-Out Regulars**

| Field | Value |
| --- | --- |
| Segment name | Dine-Out Regulars |
| Variables | Go-to meal |
| Values | Dine-Out |
| No. Actors | 36.45 million |
| Growth | Growing with sit-down recovery; dine-in preference rose versus 2023 in the US Foods diner study.[1] |

Homogeneous (same primary occasion), distinctive from delivery and takeout, measurable from diner studies, substantial, actionable (swipe + restaurant lock), accessible (maps, reviews, gym catchments).

**Delivery Regulars**

| Field | Value |
| --- | --- |
| Segment name | Delivery Regulars |
| Variables | Go-to meal |
| Values | Delivery |
| No. Actors | 22.68 million |
| Growth | Takeout and delivery weekly use has risen versus 2022 (43% ordering takeout weekly or more).[4] |

Same six tests. Product difference: marketplace menus and no server; the Match still ends the JTBD.

**Macro Trackers**

| Field | Value |
| --- | --- |
| Segment name | Macro Trackers |
| Variables | Nutrition-tracking intensity |
| Values | Daily macro log |
| No. Actors | 20.25 million (`assumption:` 25% of 81 million) |
| Growth | Tracker use rides the same fitness-membership trend.[2] |

This is the behaviour that makes nutrition-goal filtering a purchasing criterion. Accessible where they already log food.

### 5. Competition

Frame: a Fitness Enthusiast trying to find a restaurant meal. Options the Actor already perceives.

| Kind | Option | Category |
| --- | --- | --- |
| Indirect | Google Maps (Google LLC) | Local search / maps |
| Indirect | Calorie counter apps (category) | Food logging |
| Indirect | Manual method | Substitute |

None of the three sit in the same product category. There is no widely used product in *nutrition-goal-filtered restaurant meal matching*. That is the white space on the current-state map.

**1. Google Maps (specific product)**

| Field | Value |
| --- | --- |
| Brand name | Google Maps |
| Company | Google LLC |
| Competitive positioning | The complete local map: ratings, distance, photos, and hours for nearly every restaurant, now with Ask Maps conversational discovery. Claimed differentiator is place coverage plus getting the Actor from search to directions without leaving the map.[7] |

Maps finds a venue, not a plate that fits a nutrition target.

**2. Calorie counter apps (product category)**

| Field | Value |
| --- | --- |
| Product category | Calorie counter apps |
| Examples | MyFitnessPal — MyFitnessPal, Inc. (Francisco Partners).[8] Lose It! — FitNow, Inc.[9] Cronometer — Cronometer Software Inc.[10] |
| Evidence the category exists | Apple lists the product as *MyFitnessPal: Calorie Counter App* in Health & Fitness.[8] MyFitnessPal's site answers "Is MyFitnessPal a free calorie tracker app?" with "If you're looking for a free calorie counter app, you're in the right place."[11] Capterra lists the same class as *Calorie Tracking Software*.[12] |

The Actor uses this category to look up a dish after they have already picked a venue. It logs food; it does not assemble a restaurant plate to a remaining target.

**3. Manual method**

Walk in (or open the PDF menu), read item names and prices, and guess the macros. No brand. Most economical. Still a real choice the Actor treats as a way to finish the job.

### 6. Positioning Analysis

Customer evaluation criteria, scored 0–10. **Higher means the option offers more of that criterion. High is not "good."** Calorie counter apps are plotted as the median product in that category.

| Criterion | What it means | Google Maps | Calorie counter apps | Manual method | Hungry Henry (future only) |
| --- | --- | --- | --- | --- | --- |
| Nutrition-goal filtering | How much the option uses the Actor's personal calorie/macro target as a filter | 1 | 7 | 3 | 9 |
| Time to a decision | How much of the Actor's time the option consumes to reach a chosen meal. Higher = slower. | 7 | 8 | 9 | 2 |
| Restaurant coverage | How many nearby venues the option can show | 10 | 6 | 3 | 10 |
| Meal customization | How far the Actor can lock, swap, and rebuild a plate | 2 | 3 | 6 | 9 |
| Price paid | How much money the option charges the Actor. Higher = more expensive. | 0 | 2 | 0 | 0 |

Scores are `assumption:` from the customer's point of view, not a survey.

*Time to a decision* and *Price paid* are not "quality" axes. A high score means the option offers more time-cost or more price, which some Actors accept and this product will not.

#### Current State Positioning Map

Without Hungry Henry. Green ovals mark significant white space — positions none of the three noteworthy options occupy.

![Current-state positioning map — three noteworthy options, white space marked](visuals/current-state-positioning-map.png)

White space called out on the map:

1. **High nutrition-goal filtering** (about 8–10). Calorie counter apps reach 7 by looking up a logged item. Nothing filters the restaurant search itself by the remaining target.
2. **Low time to a decision** (about 1–3). Every current option consumes a long search. The 23-minute actual sits here.
3. **High meal customization** (about 8–10). The manual method can swap sides by hand (6). Nothing locks an item and rebuilds the rest of the plate to the leftover macros.

#### Future State Positioning Map

The current-state map copied, with Hungry Henry plotted. White-space ovals are removed. No new evaluation criterion is added — the Actor already uses these five when they choose how to find a restaurant meal.

![Future-state positioning map — Hungry Henry on the positions to own](visuals/future-state-positioning-map.png)

Hungry Henry is placed at 9 on nutrition-goal filtering, 2 on time to a decision, and 9 on meal customization. Those are the three white-space ovals from the current-state map. Restaurant coverage is **10, the same as Google Maps**, because Hungry Henry uses Google place data for distance, rating, and venue identity. Price paid stays 0, same as Maps and the manual method; that is not a position to differentiate on.

#### Position-to-Own

**A restaurant meal matched to your target, without the 23-minute hunt.**

The first product owns two places on the future-state map: **high nutrition-goal filtering** and **low time to a decision**, with meal customization as the supporting move that makes a match picky without restarting the search.

**Tagline:** Find your guilt-free cheat meal.

### 7. Market Focus Decision

**Market coverage strategy.** Differentiated. Go-to meal and tracking intensity change the product. An undifferentiated mass-market restaurant app would recreate Google Maps.

**Market entry strategy.** First segment: **Dine-Out Regulars** (36.45 million) — largest go-to-meal segment, growing with sit-down recovery, and a low entry barrier because the Actor already opens Maps at the table.[1] First niche: **Macro-Tracking Dine-Out Regulars** (~9.1 million if the 25% tracker share is applied to the dine-out segment; `assumption:` independence) — they already pay for a calorie counter app, so nutrition-goal filtering is a criterion they use today, and they can be reached where they already log. First use case: **Dine-Out** — highest pain on the current-state journey. First problem: **Cheat-Meal Guilt Problem** — 3.2 billion blow-out or untracked restaurant meals per year in America. First position-to-own: high nutrition-goal filtering and low time to a decision. People outside this focus can still open the free consumer product; v1 design decisions are made for this group only.

**Market growth strategy.** TBA.

## 3. Solution Space

### 1. MVP Product Concept Outline

TBA

### 2. User Views

TBA

### 3. Functional Requirements

TBA

### 4. Context View

TBA

### 5. Non-Functional Requirements

TBA

## 4. Customer Value Space

### 1. Product Features and Benefits

TBA

### 2. Pricing Model

TBA

### 3. Customer Cost Items

TBA

### 4. Customer Value Proposition Evaluation

TBA

## Appendix

### Sources

1. US Foods, "New Survey Reveals Menu and Ordering Choices of Americans" — Americans spend 14 minutes selecting a restaurant and 9 minutes deciding what to order once seated; about 5 preferred dine-in occasions and 3 takeout/delivery occasions per month; 55% vs 45% dine-out vs takeout/delivery preference. https://www.usfoods.com/tools-tips-and-ideas/articles-and-publications/articles/american-menu-choices
2. Health & Fitness Association, "81 Million Americans Were Members of a Fitness Facility in 2025" — 81 million members, +5.2% versus 2024; more than 100 million total users. https://www.healthandfitness.org/81-million-americans-were-members-of-a-fitness-facility-in-2025-new-hfa-report-finds/
3. Health & Fitness Association / PR Newswire, "One in Four Americans Belonged to a Gym in 2024" — 77 million members in 2024; +20% membership from 2019 to 2024. https://www.healthandfitness.org/one-in-four-americans-belonged-to-a-gym-in-2024/
4. TouchBistro, *2024 American Diner Trends Report* — 39% of Americans dine out weekly or more; 43% order takeout or delivery weekly or more. https://www.touchbistro.com/wp-content/uploads/2022/09/American_Diner_Report_2024_Final.pdf
5. Finlayson, G. et al., "Retention rates and weight loss in a commercial weight loss program," *International Journal of Obesity* — 6.6% retained at 52 weeks (annual program context; weekly completion uses [6]). https://www.nature.com/articles/0803395
6. Helander, E. E., Vuorinen, A.-L., Wansink, B., and Korhonen, I. K. J., "How long do people stick to a diet resolution? A digital epidemiological estimation of weight loss diet persistence," *Public Health Nutrition* (2020) — new January dieters persist about 3.1–5.3 weeks. https://pmc.ncbi.nlm.nih.gov/articles/PMC10200480/
7. Google, "Ask Maps and Immersive Navigation: New AI features in Google Maps" — Ask Maps conversational discovery on Google Maps. https://blog.google/products-and-platforms/products/maps/ask-maps-immersive-navigation/
8. Apple App Store, *MyFitnessPal: Calorie Counter App* — listed in Health & Fitness as a calorie counter. https://apps.apple.com/us/app/myfitnesspal-calorie-counter/id341232718
9. Apple App Store, *Lose It! – Calorie Counter* — FitNow, Inc. https://apps.apple.com/us/app/lose-it-calorie-counter/id297368629
10. Apple App Store, *Cronometer: Nutrition Tracker* — Cronometer Software Inc. https://apps.apple.com/us/app/cronometer-nutrition-tracker/id1145935738
11. MyFitnessPal, homepage — "If you're looking for a free calorie counter app, you're in the right place." https://www.myfitnesspal.com/
12. Capterra, *Calorie Tracking Software* — product-category listing that names this class of tools. https://www.capterra.com/calorie-tracking-software/
13. Client pitch, Hungry Henry notes — "55% of them are guilty the next day because they're trying to lose weight." Used as the share of restaurant occasions that are a blow-out or untracked meal.

### Five Whys (Cheat-Meal Guilt Problem)

1. Why are 3.2 billion restaurant meals a year blow-outs or untracked? The Actor leaves the table without a plate that fits the remaining target.
2. Why no fitting plate? The search is not filtered by personal calories or macros.
3. Why don't discovery products filter that way? They rank on rating, distance, cuisine and price.
4. Why can't the menu close the gap? Restaurants post item names and prices, not a complete nutrition record.
5. Why is the plate still rebuilt by hand? Substitutions and course logic are not implemented on restaurant sites. → Root: no personal-goal filter on restaurant meal discovery.

### Population and segment math

```
Actors (US Fitness Enthusiasts) = 81,000,000          [2]
Dine-Out Regulars = 81,000,000 × 0.45 = 36,450,000    assumption: on [1]
Delivery Regulars = 81,000,000 × 0.28 = 22,680,000    assumption:
Takeout Regulars  = 81,000,000 × 0.27 = 21,870,000    assumption:
Sum = 81,000,000

Macro Trackers = 81,000,000 × 0.25 = 20,250,000       assumption:
Beachhead (Dine-Out ∩ Macro Tracker, independence) =
  36,450,000 × 0.25 = 9,112,500                       assumption:

Blow-out or untracked meals (Cheat-Meal Guilt Problem)
  Rate per occasion = 0.55                            [13]
  Per instance = 0.55 meals
  Per Actor / year = 0.55 × 72 = 39.6 meals
  America / year = 39.6 × 81,000,000 = 3,207,600,000 meals
```

### Competitor scores (0–10)

See the table in §2.6. All scores are `assumption:`.

### Familiarity

The fertile land is Resturants. The Actor and JTBD are taken from the client's notes and from first-hand use of Maps, restaurant sites and a nutrition tracker to find a meal that does not blow a plan.
