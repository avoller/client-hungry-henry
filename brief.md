---
client: Hungry Henry
product_name: Hungry Henry
output_basename: hungry-henry-workbook
status: draft
phase: P1
signatory: Alexander Voller
consulted: []
exemplar_permission: pending

config:
  tagline: Find your guilt-free cheat meal.
  fertile_land: Resturants
  actor: Fitness Enthusiast
  actor_definition: >
    A Fitness Enthusiast is a person actively pursuing a fitness or nutrition
    plan who still wants to eat restaurant meals, and who is at risk of
    abandoning that plan when menus do not show how a meal fits their targets.
  actor_role: >
    The Fitness Enthusiast is Initiator, Primary User, Decider, and Buyer of
    the consumer product. A second customer concept — the Restaurant Operator —
    is Buyer of the B2B listing tiers, and is not developed as the course Actor.
  jtbd: find a restaurant meal
  jtbd_statement: To find a restaurant meal.
  beachhead: Macro-Tracking Dine-Out Regulars
  beachhead_rationale: >
    Macro-Tracking Dine-Out Regulars feel the gap on every sit-down occasion,
    already pay for a nutrition tracker, and can be reached where they already
    log food — so the pain is frequent, they have shown willingness to pay for
    adjacent tools, and access is cheap.
  price_point: Free $0 per member; Paid $14.40 per member per year. Restaurant visibility fees are primary revenue and are excluded from the workbook.
  north_star: Meals Matched
  north_star_definition: >
    The moment a Fitness Enthusiast presses Match on a restaurant meal they
    intend to eat.
  problem: >
    Cheat-Meal Guilt Problem — 3.2 billion blow-out or untracked restaurant
    meals per year in America, because restaurants post menus rather than
    nutrition, discovery products do not filter by personal goals, and
    substitutions are left to mental math.
  desired_outcome_summary: >
    The Ave. Meal Search Time will be 3 minutes. The Ave. Plan Completion
    Rate will be 75%. The Ave. Cheat-Meal Calorie SD will be 150 kcal.
  actual_outcome_summary: >
    The Ave. Meal Search Time is 23 minutes. The Ave. Plan Completion Rate
    is 30%. The Ave. Cheat-Meal Calorie SD is 500 kcal.
  outcome_ideas:
    - Faster meal find
    - Broken mundane nutrition cycle
    - Less next-day guilt
  outcome_current_states:
    - The Ave. Meal Search Time is 23 minutes.
    - The Ave. Plan Completion Rate is 30%.
    - The Ave. Cheat-Meal Calorie SD is 500 kcal.
  outcome_desired_states:
    - The Ave. Meal Search Time will be 3 minutes.
    - The Ave. Plan Completion Rate will be 75%.
    - The Ave. Cheat-Meal Calorie SD will be 150 kcal.
  outcome_metrics:
    - Ave. Meal Search Time
    - Ave. Plan Completion Rate
    - Ave. Cheat-Meal Calorie SD
  outcome_metric_definitions:
    - >
      Calculation: minutes from the trigger (decide to eat a restaurant meal)
      to a confirmed item selection, averaged across occasions. Units: minutes
      per occasion. Actual combines US Foods venue-selection time (14 min) and
      seated order-decision time (9 min).
    - >
      Calculation: (weekly cycles finished ÷ weekly cycles started) × 100.
      A cycle is finished if the Actor logs through the week's last planned
      day without abandoning the plan. Units: percent. Actual 30% informed
      by Helander et al. 2020. Desired 75%.
    - >
      Calculation: sample SD of caloric deviation on cheat meals,
      SD = sqrt(Σ(d_i − d̄)² / (n − 1)), where d_i = calories of cheat
      meal i − the Actor's remaining calorie target for that meal.
      Units: kcal. Actual 500 kcal and desired 150 kcal are assumption:.
  journey_trigger: Decide to eat a restaurant meal
  journey_use_cases:
    - Dine-Out
    - Delivery
    - Takeout
  journey_stages:
    - Choose Dining Mode
    - Search Nearby Venues
    - Inspect Posted Menus
    - Estimate Remaining Fit
    - Compose Mixed Plate
    - Confirm Chosen Meal
  problem_causes:
    - Restaurants post menus, not nutrition.
    - Google Search and other food products do not filter by a user's personal nutrition goals.
    - Meal substitutions and course selection require logic not implemented on restaurant websites.
  problem_category: Meal Search Problem
  positioning_axes:
    - nutrition-goal filtering
    - time to a decision
  position_to_own: a restaurant meal matched to your target, without the 23-minute hunt
  consumer_price: $0 on Free; $14.40 per member per year on Paid
  pricing_strategy: segmented
  pricing_metric: per member
  pricing_price_paid: $14.40 per member per year
  pricing_payment: >
    Free: frequency none, timing none, no charge. Paid: once per year,
    at the start of the term, charged to the Fitness Enthusiast by card
    or app-store purchase.
  product_category: Restaurant and meal discovery
  hungry_henry_match: >
    Recommendations curated from meals already liked. One plate is gifted
    with the paid plan and may include a discount at a participating
    restaurant. No discount amount is set.
  ask_henry: Rate limited on Free. Unlimited on Paid. The free cap is not numbered.
  restaurant_tiers:
    - Free
    - Pro Silver
    - Pro Gold
  mvp_focus: Fitness Enthusiasts finding a meal
---

# Hungry Henry — brief

## The idea

Hungry Henry Meal and restaurant search.

Henry finds and builds your next guilt-free cheat meal. For nutrition-conscious humans who love to eat.

You've been strict on your nutrition plan all week. It's Friday night, and now in the space of 20 minutes you've reverted a week of meticulous dieting. We match you to your guilt-free cheat meal. Hungry Henry curates meals and courses from restaurants nearby that meet, or are close enough to, your nutrition goals. Swipe through mains, add sides, substitute, and explore. Be as picky as you want with sacred cheat night — or let Henry find you the right option.

The service is free to the consumer. Businesses pay for SaaS to get more views of their meals, and pay for features, courses, and meal badges.

## Given facts and constraints

- Fertile Land named in the notes as Restaurants; Dining Out also appears as the area of life.
- Actor: Fitness Enthusiast.
- JTBD named in the notes as "Find a meal."
- Causes the client named: restaurants post menus, not nutrition; Google Search and other food products do not filter by a user's personal nutrition goals; meal substitutions and course selection require logic not implemented on restaurant websites.
- Problem category named: Meal and restaurant search.
- Segmentation variable named: "goto meal", values dine-out and delivery (third value unfinished).
- Consumer product is free. Restaurant tiers: Free, Pro Silver, Pro Gold.
- MVP focus: users finding a meal.
- Pitch statistic supplied by the client: 55% of restaurant patrons trying to lose weight feel guilty the next day.
- V1 screens described: Home (meal match swipe), Map, Search, Collections; control centre "I'm looking for"; restaurant drawer; bottom nav.

## Refinements applied

- **Fertile Land** — restored to **Resturants**, the label in the client's notes. Dining Out is withdrawn.
- **JTBD** — raw idea said "Find a meal." Accurate as a task, but too general for Dining Out (it also covers home cooking). Changed to **find a restaurant meal** / **To find a restaurant meal.** No outcome word was added.
- **Problem Category** — raw idea said "Meal and restaurant search". Tightened to **Meal Search Problem** so it labels the problem, not the product category.
- **Use cases** — notes named dine-out and delivery and left a third value blank. **Takeout** was added so the go-to-meal scheme has three distinct, important cases.
- **Consumer price** — the notes said the service is free to the consumer. Kept as the Free tier ($0 per member, unlimited swipes, calorie and protein range only). A Paid tier at $14.40 per member per year unlocks fat, carbohydrate, and micronutrient filters and the operators is / less / more. Restaurant visibility fees stay the primary revenue and are not priced in the workbook.
- **Hungry Henry Match** — the paid plan includes recommendations curated from meals already liked, and one gifted plate, which may also carry a discount at a participating restaurant. No discount amount was stated, so none is used in the price or the benefit-to-cost ratio.
- **Category** — Hungry Henry is restaurant and meal discovery, not a calorie counter. Ask Henry is rate limited on Free and unlimited on Paid. The free cap is not numbered.

## Open questions

- Restaurant tier prices (Pro Silver / Pro Gold) were never stated. They are excluded from this workbook's pricing model. The Fitness Enthusiast price is the one in §4.
- Signatory beyond the engagement author is unset.
- Exemplar reuse is still `pending`.
