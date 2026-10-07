# PRODUCT DESCRIPTION 

Hungry Henry Meal and restaurant search.

Henry finds and builds your next guilt-free cheat meal. For nutrition-conscious humans who love to eat.

---

### Fertile Land 

Resturants

### Dining Out

### Actor

Fitness Enthusiast

### Job To Be Done

Find a meal.

### Outcomes

#### Break the mundane nutrition cycle

- **Metric:** Number of nutrition plans not completed (%)
- **Features:** Range of options

#### Save time

- **Metric:** Search time

#### No guilt

- **Metrics:**
  - Number of cheat meals at restaurants per year
  - Number of meals per user per week
  - Compare against statistics

### Causes

- Restaurants post menus, not nutrition.
- Google Search and other food products do not filter by a user's personal nutrition goals.
- Meal substitutions and course selection require logic not implemented on restaurant websites.


### Problem Category

Meal and restaurant search

---

# GO TO MARKET

### MVP

Users focused on finding a meal.

## Market Segmentation 

Segmentation variable 1: "goto meal", values: "dine-out", "delivery", "

### Go to Market

- Service is free to the consumer.
- B2B: businesses pay for SaaS to get more views of their meals, and pay for features, courses, and meal badges.

### Consumer Tiers

- **Free:** Meal matches from venue follow Hungry Henry default matching algorithm. Abilty to update menu.  
- **Pro Silver:** Meal mathes from paid resturants have higher visibitly.  Ability to boost a particular meal match for a short period of time. 
- **Pro Gold** Achieve competitive edge by setting featured matches for popular user types viewing your resturant. Higher match conversion rates through manual fine tune your meal and food pairings so matches appear like personally crafted chef suggestions. 
---



---

## Pitch

### You Know How

You've been strict on your nutrition plan all week. It's Friday night, and now in the space of 20 minutes you've reverted a week of meticulous dieting.

### In Fact

Every year there are 81 million restaurant patrons in America. 55% of them are guilty the next day because they're trying to lose weight.

That's 45 million Americans trying to find meals that fit their goals.

### So What We Do

We match you to your guilt-free cheat meal. Hungry Henry curates meals and courses from restaurants nearby that meet, or are close enough to, your nutrition goals.

Swipe through mains, add sides, substitute, and explore. Be as picky as you want with sacred cheat night — or let Henry find you the right option.

We are B2B, and we reward restaurants who take the extra time to list their nutrition details with us, and who take the extra time to curate meals and courses for the 88 million of us who are nutrition conscious.


### To Get Started

As a business, create an account and start advertising your meals and courses to the world.

For you and me who just want a meal: tell Henry your goals and start swiping for a match — for free.

### Vision

Hungry Henry is linking the XX billion fitness and nutrition industry with the XX billion restaurant scene.

Our vision is guilt-free, sustainable eating — and it would be my pleasure to share that with you.

# Design

### Screens

#### Home (meal match)
**Page Description**
- A user clicks through meal matches until they find their match. A meal match is a combination of food items that are within the user's nutrition target. The differnence is added the users nutition bank if the meal match is a little under or over. Swiping left is essentially using Henry's auto meal match algorithm. 
- A user can select the resturant by tapping on the resturant name which toggles the resturant to selction. Futher swiping will only show meal matches from within the selected resturant. 
- A user can select particular food items by tapping on them which toggles them to selected. Further swipping will KEEP the selected food items in future matches. Consequently the matching algorithm must treat te nutrition values of the selected items as constant, and the other food items in the match must factor the target, and the constant values of selected food. Selecting a food item will also select the resturant; as food items come from a single resturant.  
- Swiping left presents the last generated option. 
- A user add a specific food item to the meal by pressing the add button. This will bring up the menu of the current resturant menu for the user to add a food item. Selecting a food item will cause it to be selected, and select the resturnat too.
-A match may have comments from users.
- The swiping animation is not like a typical card swiper. As food items are required to stay in place when locked, food items are required to bump in and bump out induviually which nice crisp animated sequences when swiped.  

**Page Components**
Top Meal Info Group
-Resturant Info: resturatn name, stars, distance from you  
-comments

Stacked List
- Food items each with: food name 
- the stacked list as in infinte list that fades to white at the bottom for the Match Data Group 

Match Data Group
-Macro Info: energy (cal/kJ), pro (g), carbs (g), fat(g). Each maco has text, icon, value, and indicator is the user is looking for that macro.
 The indicator is +/- diff if set, hit if less than or greater than. The indicator shoud be in the accent colour.   
-Pills (diets, alerges)

Lower action group
- rear button (for users who don't want to swipe) 
- save
- match (main CTA, indicates the user is going to eat the meal)
- add (brings up resturnant menu drawer)
- forward button (for users who don't want to swipe) 



### Map

-A user can find resturants by map. 
-Only resturants that have meal matches show on the map
-Clicking the resturant opens up the resurant drawer, where the user can either: select one of their popular meals (where clicking it would open up /home will all food items), 

### Search 

- Full mult-catalog search.
- Meal matches with the seach keyword are presented in the search results, with the search key word highlighted. 
-The search results contain all food items in the meal match and the delta to the user's target. 
-selecting the search result will open up /home with the meal match.  
-The search bar multi-catlog, and is able to return results for resturants options as well. 
-Resturant search resuls show: rating, distantce. Clicking a resturant search result will open up /home with resturant selected and a random meal match.   
-The user can also search with AI will open up directly to a meal match based on the prompt.  

### Collections
-Accessed under Account
-Collections enble the user to view meals matches they've already created. 
-The two collecitons offered by default are saved (user clicks save button whilst swiping) and recent (recently eaten meals)

## UI Elements

### I'm looking for..  
- The contol centre where the user selects their nutrition targets, alergies, diets and any other thing Henry needs to know to whilst finding meal matches.
- This is show in a collapsed view in both /home and /map so the user can quickly see their targets. 

### Resturant Drawer 

### Bottom Nav
Bottom footer for all pages
- Match (home)
- Map (/map) 
- Search (/home)
- Account  

### Toggleable title pills 
- Resturant title and food item titles are able be selected induvidually in the /home page. 
- THe animation should expand the pill 


## Flows

### Saving a meal
-As the user swipes through meal matches they can save for later. 

### Finish a meal
- users selects match from /home. 
- The user 

# Implementation

### Key Data and Terms

#### Restaurant

- Distance (from Google)
- Rating (from Google)
- Restaurant badges (internal)
- Additional fields from Google

#### Food

- Category (optional, from menu — e.g. entree / main)
- Title (from menu)
- Nutrition: calories, protein, fat, carbs, allergen
- Badges (internal — e.g. popular, satisfying)

#### Meal

- One or more foods
- Save

### Key Signals and Analytics (PostHog)

- **Average time to find a meal:** Time from a user opening a meal to pressing the Eat button
- **Number of meals found:** Total meals found
- **User search targets** what nutrition targets users are searching for. What the nutrition targets where for customers who viewed your resturant.
- **Conversion Rate** Number swipes before a user selects a meal. Key metric used to distinguish between Pro Silver and Pro Gold users.    

### Feedback Board

Allow users to give feature requests and upvote others.

---




DRAFT

System Overview & Core Philosophy
Value proposition for the 81M fitness enthusiast market (resolving 23-minute meal paralysis down to < 3 minutes).
Mobile-first touch ergonomics (
 touch targets, thumb-reach layout).
Warm editorial aesthetic (Fraunces serif, Plus Jakarta Sans, JetBrains Mono, warm cream #FAF6F0, Rusty Spice #B43B1F, Herb Sage #4E6B38).
Screen & Page-Based Views
HomePlateView.tsx (Home Plate): Tinder-style plate swiper, card drag gestures with PASS/MATCH visual stamps, 5 circular action buttons, and stacked dish pinning.
FiltersView.tsx (Targets): Calorie & macro tolerance sliders, comparison modes (is, less, more, off), fitness presets (e.g. Lean Gains, Keto, Endurance), and dietary exclusions.
MapView.tsx (Map): Geospatial map pinning venues with confirmed macro matches, bottom sheet plate preview, and single-tap plate loader.
SearchView.tsx (Ask Henry): Natural language query engine ("What are you craving?") paired with real-time dish and restaurant catalog search.
AccountView.tsx (Collections): Value dashboard (search time saved, adherence rate), Saved Plates collection, Recent Matches, and rolling Nutrition Bank ledger.
OperatorPortalView.tsx (Operator Portal): B2B venue claiming flow, neighborhood fitness search demand analytics, and dish macro management (Restaurant Listed vs. USDA FoodData est.).
Global & Shared Components
TopNav.tsx: Chef Henry avatar, occasion selector (Dine-Out, Takeout, Delivery), rolling Nutrition Bank counter, and operator portal toggle.
BottomTabBar.tsx: Docked bottom navigation with live match counters.
MacroRow.tsx: Differential grid comparing plate totals vs. user targets with color-coded delta tolerances and live banking notices.
AddMenuDrawer.tsx: Course-based restaurant menu drawer for manual item additions.
MatchCelebrationModal.tsx: Match confirmation modal with Google Maps navigation handoff and time saved metrics.
Key Features & Mechanics
"Select Throughout" Pinning & Rebuild: Lock a venue or individual dish while regenerating unpinned sides to hit remaining macros.
Tinder-Style Swiper Action Bar: Rewind (Amber), Pass (Rose), Pin Venue (Cyan), Rebuild Unselected (Purple), and Match (Rusty Spice Heart).
Rolling Nutrition Bank: Automatic rollover of daily surpluses/deficits to eliminate cheat-meal guilt.
Multi-Source Nutrition Provenance: Distinguishing verified restaurant data from USDA FoodData estimates.
Key User Flows
Flow 1: 3-Minute Quick Match (The North Star Path).
Flow 2: "Select Throughout" Dish Pinning & Rebuild.
Flow 3: Natural Language Craving Match ("Ask Henry").
Flow 4: Restaurant Operator Free Claiming & Macro Ingestion.
Data Architecture & State Contracts
Core data models (Plate, MacroTargets, NutritionBank, MatchRecord, Restaurant, MenuItem).