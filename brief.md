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
  price_point: >
    Free $0 per member; Paid $14.40 per member per year. Restaurant listing
    fees are excluded from this workbook.
  pricing_strategy: segmented
  pricing_metric: per member
  consumer_price: $0 Free per member; $14.40 Paid per member per year
  paid_price: $14.40 per member per year
  paid_price_basis: >
    Free includes every macro, so the 20-minute search saving ($480 a year)
    is on Free. Paid is one-tenth of an assumed $144 a year for the extras
    (recommendations, micronutrient targets, unlimited Ask Henry): 6/60 × 72
    × $20 = $144, and 0.10 × $144 = $14.40. Those 6 minutes are not a slice
    of the 23-to-3 gap. Google Maps costs $0, so there is no paid reference
    price.
  product_goals: >
    Modeling targets, not a forecast. EOY 3 total users = 1% of 9,112,500
    Macro-Tracking Dine-Out Regulars = 91,125. Constant progression:
    EOY 1 = 30,375; EOY 2 = 60,750. Free-to-paid 30:1. Units sold are Paid
    memberships: 980, 1,960, and 2,940.
  vision_statement: >
    Hungry Henry will make dieting fun, flexible, and achievable. Ten years
    from now a Fitness Enthusiast wants the carbonara at the local Italian,
    the late delivery, or Tuesday night at their own stove, and they get it —
    delicious, satisfying, and still on the goal — because the meal was built
    for their taste and for whatever the day has left.
  vision_horizon: 10 years
  tam_revenue: $1,166,400,000 per year
  tam_units: 81,000,000 memberships per year
  hourly_value: $20 per hour
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
  restaurant_tiers:
    - Free
    - Pro Silver
    - Pro Gold
  mvp_focus: Fitness Enthusiasts finding a meal
  requirements_workbook_title: "Requirements Workbook"
  requirements_workbook_basename: hungry-henry-requirements-workbook
  requirements_workbook_version: "0.2"
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
- **Consumer price** — raw idea said the service is free. The workbook now uses segmented pricing: Free at $0 per member, Paid at $14.40 per member per year. Free includes every macro. Restaurant listing fees stay out of this workbook.

## Open questions

- Restaurant tier prices (Pro Silver / Pro Gold) were never stated. Marked assumption in the workbook.
- Signatory beyond the engagement author is unset.
- Exemplar reuse is still `pending`.
