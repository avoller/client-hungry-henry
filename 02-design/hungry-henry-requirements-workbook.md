# Requirements Workbook

**Product:** Hungry Henry - Restaurant Discovery App
**Prepared by:** Alexander Voller
**Course:** 17-627 Requirements for Embedded Systems
**Document version:** 0.2
**Date:** 3 November 2026

## Version History

| Version | Date | Change |
| --- | --- | --- |
| 0.1 | 30 Oct 2026 | Checkpoint 2. Main Document: product description, conceptual and system diagrams, personas, and functional and non-functional requirements. |
| 0.2 | 3 Nov 2026 | Requirements review. Eighteen high-level requirements covering every v1 feature and actor, with 60 derived functional requirements in ISO/IEC/IEEE 29148 wording and SOPHIST sentence structure. Quality attributes defined and tied to quality requirements, with a timing and dependability analysis. Design constraints moved into their own ID-bearing table. New system concept, annotated Home HMI and vendor portal wireframe. Usability and availability targets aligned with the Product Idea Workbook. NFR-01 moved from the ultra-low to the low latency class, because no display renders a screen in under 2 ms. |

## Table of Contents

Word builds this from the headings below. The field refreshes on open, so the
section and page numbers are accurate in the submitted file.

## Main Document

### 1. Introduction

#### 1.1 Purpose

This Software Requirements Specification (SRS) defines the requirements for version 1.0 of the Hungry Henry restaurant discovery application. It is written for the Hungry Henry product and engineering team, and for the requirements review that baselines it before design. Section 3 is the part a designer builds from and a tester tests against.

#### 1.2 Scope

Hungry Henry finds a restaurant meal that fits a fitness enthusiast's nutrition targets.

In scope, across the MVP and its subsequent features: the mobile app, the web vendor portal, wearable integration, and the cloud-hosted infrastructure. Version 1.0 is the iOS app, the vendor portal and the cloud service. Wearable integration is post-MVP, and Section 3 writes it with "will" under the convention stated there.

Out of scope: a general nutrition and exercise platform, food delivery, and home cooking.

#### 1.3 Abbreviations

The project glossary. Every term a requirement in Section 3 leans on is defined here, and each is used with this one meaning throughout.

| Term | Meaning |
| --- | --- |
| Account | The fitness enthusiast's Hungry Henry identity. It holds matched meals, collections, reviews and the membership. |
| Allergen-unverified | A food item whose restaurant posts no allergen information. It carries a warning and is never presented as free of an allergen. |
| Ask Henry | The Paid feature that turns a typed sentence into a generated meal. |
| Collection | A named list of meals the fitness enthusiast has saved. |
| Deviance | A meal total minus the matching bound of the remaining nutrition target, shown as a signed number, or as "hit" when the total is inside tolerance. |
| Diet | A dietary pattern, such as pescatarian or vegetarian, that excludes food items. The supported diet list is not yet fixed. Alexander Voller owns it, and it is set before the design review, because FR-01.2 and FR-02.2 cannot be tested without it. |
| Estimated value | A nutrient value derived from reference nutrient values because the menu does not post it. |
| Fit | A meal fits when every total that is turned on lies inside tolerance of its bound. |
| Fitness enthusiast | A person actively pursuing a fitness or nutrition plan who still wants to eat restaurant meals. The consumer actor. |
| Food item | One menu line: title, optional course, energy, protein, carbohydrate, fat and allergens. |
| Generated meal | A set of food items from one restaurant that the system assembles to fit the remaining nutrition target. |
| Happy path | The app opens with location permission granted, a remaining nutrition target already set, and a network connection. |
| Listing tier | The restaurant's plan: Free, Pro Silver or Pro Gold. |
| Lock | Hold a food item, and with it the restaurant, constant while the other food items are replaced. |
| Match | Confirm the meal the fitness enthusiast intends to eat. Meals Matched is the product's north star metric. |
| Membership | Free, at $0, or Paid, at $10 a month, which adds target templates and Ask Henry. |
| Nine major food allergens | Milk, eggs, fish, crustacean shellfish, tree nuts, peanuts, wheat, soybeans and sesame [19]. See C-011. |
| Operational fault condition | Any of the conditions in FR-17.1, FR-17.2 or FR-17.3. |
| Posted value | A nutrient or allergen value the restaurant publishes. |
| Remaining nutrition target | The bounds on energy, protein, carbohydrate and fat, together with the diets and allergens turned on, that a meal is judged against. |
| Restaurant drawer | The panel that shows the venue behind a generated meal. |
| Restaurant owner | The person who lists a restaurant's menu and buys its listing tier. The B2B actor. |
| Search radius | The distance from the fitness enthusiast's GPS location inside which restaurants are considered. Default 5 miles (assumption: ASM-032). |
| Smallest total deviance | The lowest sum, across the bounds turned on, of each total's absolute deviance as a percentage of its bound. |
| System administrator | The person who operates the production service. |
| Target template | A remaining nutrition target saved under a name. Paid. |
| Tolerance | The allowed deviation from each bound before a total stops being a hit. 10% by default (assumption: ASM-031). |
| Display (verb) | Render on the screen of the actor named in the requirement. |
| Exclude (verb) | Leave out of every generated meal, search result and Ask Henry result. |
| Generate (verb) | Assemble a meal from one restaurant's food items. |
| Mark (verb) | Attach a visible label to a value or food item. |
| Notify (verb) | Deliver a message to a mobile device without the recipient opening the product. |
| Record (verb) | Store on the account so that a later session can retrieve it. |
| ASVS | OWASP Application Security Verification Standard |
| C | Constraint (Section 3.3) |
| CCPA / CPRA | California Consumer Privacy Act, as amended by the California Privacy Rights Act |
| EOY | End of year, counted from introduction in January 2028 |
| FR | Functional requirement (Section 3.1) |
| GenAI | Generative artificial intelligence |
| GPS | Global Positioning System |
| HLR | High-level requirement (Section 3.1.1) |
| HMI | Human-machine interface |
| MASVS | OWASP Mobile Application Security Verification Standard |
| MTTF | Mean time to failure |
| MTTR | Mean time to restore |
| MVP | Minimum viable product |
| NFR | Non-functional (quality) requirement (Section 3.2) |
| p90 | 90th percentile: 90% of measured cases are at or under the stated value |
| QA | Quality attribute (Section 3.2) |
| SRS | Software Requirements Specification |
| USDA | United States Department of Agriculture |

#### 1.4 References

[1] Towers, S. et al. "How long do people stick to a diet resolution? A digital epidemiological estimation of weight loss diet persistence." *Public Health Nutrition*, published online 14 December 2020. New January dieters: South Beach about 3.12 weeks, Paleo about 5.32 weeks. https://doi.org/10.1017/S1368980020001597

[2] International Food Information Council. *2025 Food & Health Survey*. Online survey of 3,000 Americans aged 18 to 80, fielded 13–27 March 2025. In the past year, 57% followed a specific eating pattern or diet. The most common was high protein (23%), then mindful eating (19%), then calorie counting (15%). 70% said they try to consume protein. "Good source of protein" was the top definition of a healthy food (38%). https://ific.org/wp-content/uploads/2025-IFIC-Food-Health-Survey-Full-Report.pdf

[3] Business of Apps. "MyFitnessPal Revenue and Usage Statistics (2026)." Aggregates company data: 220 million registered users in 2024, and more than 30 million monthly active users. https://www.businessofapps.com/data/myfitnesspal-statistics/

[4] FDA. Menu labeling requirements, and 21 CFR 101.11. Calorie disclosure applies to a restaurant chain with 20 or more locations doing business under the same name and offering substantially the same menu items. An independent restaurant is not covered unless it volunteers. https://www.fda.gov/food/nutrition-food-labeling-and-critical-foods/menu-labeling-requirements

[5] Nation's Restaurant News and Restaurant Business. *2025 Restaurant Technology Outlook*. Online survey of 562 operators, January 2025. 53% of independent operators said they would definitely or probably invest in new technology in the next 12 months, against 79% of chain operators. https://5868902.fs1.hubspotusercontent-na1.net/hubfs/5868902/Resource%20Center/2025-restaurant-technology-outlook.pdf

[6] Restaurant Technology News, reporting a Paysafe survey of small and medium restaurants, 22 July 2025. 92% accept credit cards and 83% still take cash. https://restauranttechnologynews.com/2025/07/how-small-restaurants-are-serving-up-success-with-payments-technology-and-online-ordering/

[7] Alexander Voller, product outline, 29 October 2026. Source of the version 0.1 top-level requirements that Section 3.1.1 refines.

[8] Hungry Henry prototype, P1/P2 design phase screens, 2026. Source of the prototype screenshots in Section 2.2 and the base screen of the annotated Home HMI.

[9] Hungry Henry studio engagement, context-diagram skill output, 2026. Source of the context view and the deployment view in Section 2.2.

[10] Hungry Henry Product Idea Workbook, 2026. Solution Space, Section 1 (MVP Product Concept Outline) and Customer Value Space, Section 1 (Product Features and Benefits) are the source of the main attributes in Section 2.3, and carry the detail behind each one. Solution Space, Section 3 (Functional Requirements, user stories 1 to 22) is the source of the derived functional requirements in Section 3.1. Solution Space, Section 5 is the source of the quality requirements in Section 3.2. Product Strategy Space, Sections 6 and 7 (development dates, load, latency and data profiles) are the source of the capacity, data-refresh and schedule content in Sections 3.1 to 3.3.

[11] Jain, A., Berardone, J., and Grinberg, D. 17-627 Product Management Essentials course materials, Carnegie Mellon University, 2026. Source of the four-tier latency taxonomy (Ultra-Low, Low, Medium, High) used in Section 3.2.

[12] OWASP Foundation. *Application Security Verification Standard*, v5.0.0, May 2025. https://owasp.org/www-project-application-security-verification-standard/. Source of C-008.

[13] OWASP Foundation. *Mobile Application Security Verification Standard*, v2.1.0, January 2024. https://mas.owasp.org/MASVS/. Source of C-009.

[14] ISO/IEC/IEEE 29148:2018. *Systems and software engineering — Life cycle processes — Requirements engineering*. Source of the keyword convention and requirement-wording rules in Section 3.

[15] Rupp, C. and the SOPHISTen. *Requirements-Engineering und -Management*, Carl Hanser Verlag. Source of the SOPHIST requirement templates and the reading of "will" used in Section 3.

[16] IEEE Std 830-1998. *IEEE Recommended Practice for Software Requirements Specifications*. Source of the document outline, the organizing scheme in Section 3.1 and the priority scale.

[17] ISO/IEC 25010:2023. *Systems and software engineering — Systems and software Quality Requirements and Evaluation (SQuaRE) — Product quality model*. Source of the quality attribute names in Section 3.2.

[18] Kopetz, H. *Real-Time Systems: Design Principles for Distributed Embedded Applications*, 2nd ed., Springer, 2011. Source of the deadline classes and the dependability split in Section 3.2.

[19] FDA. "FASTER Act: Sesame is the Ninth Major Food Allergen." Sesame joined the eight FALCPA allergens on 1 January 2023. https://www.fda.gov/food/food-allergies/faster-act-sesame-ninth-major-food-allergen. Source of the allergen list in Section 1.3 and C-011.

[20] California Civil Code §1798.130 (CCPA, as amended by CPRA). A business delivers its response to a verifiable consumer request within 45 days of receipt, extendable once by 45 days with notice. https://leginfo.legislature.ca.gov/faces/codes_displaySection.xhtml?lawCode=CIV&sectionNum=1798.130. Source of NFR-13 and C-010.

[21] Apple. *App Store Review Guidelines*, Section 3.1.1, In-App Purchase. https://developer.apple.com/app-store/review/guidelines/. Source of C-007.

[22] Hungry Henry assumption log, `decisions/assumptions.md`, 2026. ASM-031 to ASM-039 are the source of every figure in Section 3 labelled assumption.

[23] Hungry Henry studio engagement, system concept and wireframes, `02-design/visuals`, 3 November 2026. Source of the system concept, the annotated Home HMI and the vendor portal wireframe in Section 2.2.

<!-- page-break -->

### 2. Overall Description

#### 2.1 Product Perspective

Hungry Henry is a restaurant discovery app which enables sustainable and flexible dieting practices by finding goal-compliant restaurant meals. The core problem for fitness enthusiasts is that a goal-compliant cheat meal is too hard, or impossible, to find, leading to untracked guilty meals, a loss of confidence, and diet abandonment. Today, to find a meal, a fitness enthusiast has to:

- Check individual restaurants, because common apps such as Google Maps and DoorDash do not have nutritional filters.
- Conduct a separate nutritional lookup, because most restaurants do not post nutritional values.
- Perform mental mathematics to find the best fit across the combinations of menu items and the nutrition target.

The magnitude of this problem, that rigid and inflexible eating is unsustainable for the average person, has no single honest percentage behind it: there is no reliable figure for "diet plans in America fail." What is published is how fast a new diet drops off. New January dieters in the United States held the South Beach diet for about 3.1 weeks and the Paleo diet for about 5.3 weeks before dropping off [1]. Hungry Henry's answer is that a compliant meal should be found just as quickly as any other meal, with smart substitutions and replacements, and a gamified experience that reminds the fitness enthusiast they are still hitting their goals while eating ice cream.

The market strategy is to target the find-a-restaurant-meal vertical first, before expanding into the food-delivery and home-cooking segments in later products. Swiping and finding meals is free for fitness enthusiasts; instead, Hungry Henry takes a B2B approach, with restaurants paying for increased visibility and exposure. Hungry Henry uses social media distribution channels to pursue a viral network effect on initial market entry, to capitalize on the first-mover advantage. Search history and lifetime data used in suggestions raise the switching cost, and the lovable UI and gamified experience aim to keep Hungry Henry the original and dominant product in the market.

#### 2.2 Conceptual Diagram

The pictures below are the current prototype. The set has no vendor-portal screen; the vendor portal wireframe further down stands in for it until one is designed.

| Filters | Home | Restaurant drawer |
| --- | --- | --- |
| ![Prototype, Filters: the fitness enthusiast sets energy, protein, carbohydrate and fat targets, plus diet and allergy constraints](visuals/filters.png) | ![Prototype, Home: a generated meal from one nearby restaurant, with the macro row showing a hit or a plus/minus against the remaining target](visuals/home.png) | ![Prototype, Restaurant drawer: the venue behind the meal, with its rating and distance](visuals/restaurant-drawer.png) |

The system concept is the cartoon of the whole product: the physical pieces each actor holds, the functions Hungry Henry runs in the cloud, and the external systems it depends on. Every piece carries the high-level requirement and constraint IDs from Section 3 that it serves, so the picture traces into the tables. Against version 0.1 it adds the hardware the fitness enthusiast carries (the touchscreen, the GPS receiver, the buttons and the post-MVP wearable), the restaurant owner's and the system administrator's devices, and the on-device hand-offs to Google Maps and Instagram. The cloud blocks are functions, not modules; how the service is divided is left to design.

![System concept. The devices each actor uses, the functions Hungry Henry runs in the cloud, and the external systems, labelled with their HLR and constraint IDs. [23]](visuals/system-concept.png)

The two wireframes map the HMI onto the functional requirements. The Home wireframe annotates the prototype's primary screen with the FR or NFR ID behind each control. The vendor portal wireframe is new in this version and fills the gap named above: the restaurant owner's menu, listing tier and per-item results in one desktop view.

![Home HMI, annotated. Each control on the primary screen, labelled with the requirement behind it. [23]](visuals/hmi-home-annotated.png)

![Vendor portal wireframe. The restaurant owner's menu table, import, listing tier and per-item results, keyed to their requirements. [23]](visuals/vendor-portal-wireframe.png)

The context view is the boundary. Hungry Henry is one box. Nothing inside it is drawn there. The deployment view is where the iOS client, the web client, the server, and the database sit. The two are separate on purpose. Wearables are on both, marked post-MVP. The wire protocol between the wearable and the server, and between the server and the database, is not named.

![Context view. Hungry Henry and the actors and external systems that exchange data with it. [9]](visuals/context-view.png)

![Deployment view. The mobile client, the web client, the server, and the database. [9]](visuals/deployment-view.png)

#### 2.3 Product Functions

In summary, and without the detail of Section 3:

- A fitness enthusiast sets a remaining nutrition target, gets a generated meal from a nearby restaurant or searches by restaurant, food or map, changes items on the meal and sees the deviance, widens the tolerance, matches the meal and opens directions, saves, shares and reviews, and looks back at previous matches. On the Paid membership the fitness enthusiast also uses target templates and Ask Henry.
- A restaurant owner adds, edits and deletes food items or imports a menu, chooses a listing tier for increased visibility to fitness enthusiasts nearby, and sees how often each food item was shown and matched.
- A system administrator is told, on a mobile device, when capacity is critical and when user-facing behaviour looks wrong.

The product's main attributes, as defined in the Product Idea Workbook [10]. One or two lines each here; that workbook carries the full description of each feature and the benefit behind it.

- **Search and Discovery.** The primary feature. Returns meals from nearby restaurants that sit inside the remaining energy, protein, carbohydrate, and fat target, searchable by food, by restaurant name, or on the map. Diet and allergy requirements exclude everything that does not qualify, and every meal carries its venue, rating, and distance.
- **Edit meals.** Swaps, adds, and removes items across starters, mains, and desserts, scoring the running total against the target as each change is made.
- **Get directions.** Opens directions to the venue in Google from a matched meal.
- **Match.** Confirms the meal the fitness enthusiast intends to eat and saves it to the fitness enthusiast's list.
- **Save for later.** Curates collections of pre-selected meals, so a known-good meal is reachable on the next occasion.
- **Share.** Produces a summary graphic for a matched meal, sized to be overlaid onto an Instagram story.
- **Review.** Leaves a star rating and notes on a restaurant for other fitness enthusiasts.
- **Target templates.** Saves preset nutrition values as named templates and starts a search from one of them. Paid.
- **Ask Henry.** Standard GenAI: turns a typed sentence into a meal, with *try something new* and *in-season* toggles. Paid.

#### 2.4 User Personas

Three personas, each a composite rather than an actor name.

**Chad**, the **tolerant, proactive tracker** (Fitness Enthusiast), meal-preps most of the week, keeps a calorie and protein target, and wants a plate that respects both without the guilt of a 300 kcal miss; he represents the smaller but real tracking population, who favour high-protein patterns and logging apps such as MyFitnessPal [2][3].

**Sam**, the **casual healthy eater** (Fitness Enthusiast), keeps no calorie goal and types a rough target into a form, reflecting the larger population who follow a qualitative rule such as mindful eating rather than a number [2], and needs a plate that looks like a fit without doing nutrition homework first.

**Bruce**, the **entrenched restaurant owner** (Restaurant Owner), does not know his menu's calorie values, is not comfortable on a computer, and still runs a cash-and-card register; independents like Bruce are slower to adopt new technology than chains, though cash-only is the tail of that population, not its average [4][5][6]. The vendor portal has to work for Bruce without assuming a structured menu or a card reader.

#### 2.5 Conceptual System Model and HMI

Hungry Henry has one point of contact per actor, all three shown in the system concept in Section 2.2.

- **The fitness enthusiast's iPhone is the primary HMI.** The touchscreen carries every control: the Filters rows that set the remaining nutrition target; the generated meal, whose food titles are tapped to lock them; the macro row with its deviance; and five buttons under the meal (previous meal, save, Match, add, Forward), with Eat, Map, Filters and Account in the bottom navigation. The GPS receiver sets the point the search radius is measured from.
- **The restaurant owner uses the vendor portal** in a desktop web browser, for the larger viewport a menu table needs. The same functions are available on the mobile application.
- **The system administrator receives alerts** on a mobile device. There is no administrator screen in version 1.0.

Behind those, a cloud-hosted service generates and scores meals, keeps accounts, matches and menus, and watches its own health. Cloud hosting is chosen so that Hungry Henry spends developer resources on product iteration, rather than on self-hosted infrastructure and maintenance (C-002). How the service is divided internally is left to design.

#### 2.6 Sensing Capabilities

Version 1.0 senses two things, both through the iPhone: the fitness enthusiast's location, from the GPS receiver, which sets the point the search radius is measured from; and touch input on the display. It reads no other sensor.

For advanced features, post-MVP, there is scope to implement automatic calorie banking and exercise compensation: the ability to compensate for a restaurant meal through increased exercise. This requires sensing a user's baseline and current active calories through a wearable such as a Garmin or an Apple Watch (HLR-18). The sampling period for active calories is not set; it is a design decision for the release that carries HLR-18.

#### 2.7 Environment Conditions

**Typical.** The fitness enthusiast uses Hungry Henry one-handed on an iPhone, outdoors or at the restaurant table, mostly on Friday to Sunday evenings between 17:00 and 21:00 [10], over a cellular or venue Wi-Fi connection. The restaurant owner uses a desktop browser, at the venue or at home, outside service hours. The service runs in a commercial public-cloud data centre with conditioned power and cooling.

**Exceptional and hazards.**

- Weak or no signal inside a venue, where a search can stall. NFR-18 sets what happens when a data source does not answer.
- Low light and glare at the table, which make small text and low-contrast state hard to read.
- Peak demand. About 13 evening windows a month carry most of the load, so capacity is sized on the EOY 3 peak, not the average (NFR-04).
- An outage at Google Places or USDA FoodData Central, which Hungry Henry does not control.
- Allergen exposure. A meal shown as safe for an allergy when it is not is the one failure in this product that can injure someone. The Product Idea Workbook rates safety High for this reason [10]. NFR-05, NFR-06, FR-02.3 and FR-02.4 address it.

How much physical compute the service requires is not yet known. It is sized from NFR-04 in design.

#### 2.8 Constraints

TBA.

### 3. Specific Requirements

Every requirement in this section follows the ISO/IEC/IEEE 29148 wording rules [14] in the SOPHIST requirement-template structure [15]. Each takes one of three forms:

| Form | Template |
| --- | --- |
| Independent system activity | [When condition,] the system shall [process verb] [object] [constraint]. |
| User interaction | [When condition,] the system shall provide [actor] with the ability to [process verb] [object] [constraint]. |
| Interface | [When condition,] the system shall be able to [process verb] [object] [constraint]. |

Conventions for this document:

- **Shall** is binding. **Should** is a recommendation and **may** is permitted; neither is used for a requirement in this version.
- **Will** takes the SOPHIST reading: a requirement planned for a later release, which the design leaves room for and which is not verified in version 1.0. Only HLR-18 and its children use it.
- **The system** is Hungry Henry: the iOS app, the vendor portal and the cloud service together.
- **Priority** is the IEEE 830 scale [16]. Essential: version 1.0 is unacceptable without it. Conditional: it enhances version 1.0 but does not block it. Optional: post-MVP, or may not be worthwhile.
- **IDs** are local to this document, not permanent requirement IDs. HLR-NN is a high-level requirement. FR-NN.M is the M-th functional requirement derived from HLR-NN, so every functional requirement traces to its parent by its ID. QA-NN is a quality attribute, NFR-NN a quality requirement and C-NNN a constraint.
- A figure labelled **assumption** is logged in the assumption log [22] with an owner and the test that would settle it.

#### 3.1 Functional Requirements

Section 3.1 is organized by user class, then by feature within each class [16]: the fitness enthusiast first (3.1.2 to 3.1.5), then the restaurant owner (3.1.6), the system's own data work (3.1.7), the system administrator (3.1.8), and post-MVP (3.1.9). Section 3.1.1 states the high-level requirements. Every group after it holds the functional requirements derived from them, drawn from the Product Idea Workbook's user stories [10] and from the version 0.1 requirements [7].

##### 3.1.1 High-Level Requirements

Version 0.1 had eleven top-level requirements. They covered search, the restaurant dashboard and alerts, but not Match, directions, saving, sharing, reviews, membership, menu data or either paid feature. The set below covers every feature in Section 2.3 and every actor.

| ID | Priority | Requirement |
| --- | --- | --- |
| HLR-01 | Essential | The system shall provide the fitness enthusiast with the ability to set a remaining nutrition target. |
| HLR-02 | Essential | When a remaining nutrition target is set, the system shall generate meals that fit that target from restaurants inside the search radius. |
| HLR-03 | Essential | The system shall provide the fitness enthusiast with the ability to search for meals. |
| HLR-04 | Essential | The system shall provide the fitness enthusiast with the ability to edit the food items on a generated meal. |
| HLR-05 | Essential | The system shall provide the fitness enthusiast with the ability to match a meal. |
| HLR-06 | Conditional | When the fitness enthusiast has matched a meal, the system shall provide the fitness enthusiast with the ability to open directions to that meal's restaurant. |
| HLR-07 | Conditional | The system shall provide the fitness enthusiast with the ability to keep meals for a later occasion. |
| HLR-08 | Conditional | The system shall provide the fitness enthusiast with the ability to share a matched meal. |
| HLR-09 | Conditional | The system shall provide the fitness enthusiast with the ability to review a restaurant. |
| HLR-10 | Conditional | The system shall provide a fitness enthusiast holding a Paid membership with the ability to save a remaining nutrition target as a target template. |
| HLR-11 | Conditional | The system shall provide a fitness enthusiast holding a Paid membership with the ability to describe a meal in a typed sentence. |
| HLR-12 | Essential | The system shall provide the fitness enthusiast with the ability to hold a Free or a Paid membership. |
| HLR-13 | Essential | The system shall provide the restaurant owner with the ability to list that restaurant's menu. |
| HLR-14 | Essential | The system shall provide the restaurant owner with the ability to buy increased visibility for that restaurant's meals. |
| HLR-15 | Essential | The system shall provide the restaurant owner with the ability to see how often that restaurant's food items are shown and matched. |
| HLR-16 | Essential | The system shall assign energy, protein, carbohydrate and fat values to every food item it presents. |
| HLR-17 | Essential | When an operational fault condition is met, the system shall notify the system administrator on a mobile device. |
| HLR-18 | Optional | The system will adjust the remaining energy target by the active calories a connected wearable reports. |

Where each version 0.1 requirement went:

| Version 0.1 | Now | What changed |
| --- | --- | --- |
| FE-01 | HLR-01; FR-01.1 to FR-01.4 | "Accept targets" named no target and no test. Raised to a high-level requirement and split into the four bounds, diets, allergens and restore. |
| FE-02 | FR-03.1 | Rewritten as a user-interaction requirement under HLR-03. |
| FE-03 | FR-03.2 | Rewritten as a user-interaction requirement under HLR-03. |
| FE-04 | FR-02.6, FR-04.7 | Compound. Displaying the deviance and recalculating it after a change are two functions. |
| FE-05 | FR-02.7 | The tolerance now has a default and a ceiling. |
| FE-06 | FR-07.3 | "Previous selections" now means previously matched meals, most recent first. |
| RO-01 | FR-13.1 to FR-13.3 | Compound (add, edit and delete), and the subject was wrong: the owner adds a food item, the system does not. |
| RO-02 | HLR-14; FR-14.1, FR-14.2 | "Increase visibility" now names the tiers and what ranking ahead means, without breaking fit. |
| RO-03 | FR-15.1 | Now per food item, per day, over 30 days. |
| SA-01 | FR-17.1 | "Critical capacity" now has a threshold (assumption). |
| SA-02 | FR-17.2, FR-17.3 | "Abnormal user-facing symptoms" split into error rate and latency, each with a threshold (assumption). |

##### 3.1.2 Fitness Enthusiast: Targets, Discovery and Search

Derived from HLR-01, HLR-02 and HLR-03. Search and Discovery feature.

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-01.1 | Essential | The system shall provide the fitness enthusiast with the ability to set each of energy, protein, carbohydrate and fat to off, less than, equal to, or more than a value, in kilocalories for energy and in grams for the others. |
| FR-01.2 | Essential | The system shall provide the fitness enthusiast with the ability to turn on any diet in the supported diet list. |
| FR-01.3 | Essential | The system shall provide the fitness enthusiast with the ability to turn on any of the nine major food allergens. |
| FR-01.4 | Conditional | When the fitness enthusiast reopens the app, the system shall restore the remaining nutrition target last set on that device. |
| FR-02.1 | Essential | When the fitness enthusiast leaves Filters, the system shall generate a meal from one restaurant inside the search radius whose energy, protein, carbohydrate and fat totals fit the remaining nutrition target. |
| FR-02.2 | Essential | When a diet is turned on, the system shall exclude every food item that breaks that diet. |
| FR-02.3 | Essential | When an allergen is turned on, the system shall exclude every food item that posts that allergen. |
| FR-02.4 | Essential | When an allergen is turned on and a food item posts no allergen information, the system shall mark that food item as allergen-unverified. |
| FR-02.5 | Essential | The system shall display the restaurant name, star rating and distance on every generated meal. |
| FR-02.6 | Essential | The system shall display, on every generated meal, the energy, protein, carbohydrate and fat totals, each with its deviance from the remaining nutrition target. |
| FR-02.7 | Conditional | The system shall provide the fitness enthusiast with the ability to widen the tolerance from 10% to at most 25% (assumption: ASM-031). |
| FR-02.8 | Essential | When no meal inside the search radius fits the remaining nutrition target, the system shall display the meal with the smallest total deviance, marked as outside tolerance. |
| FR-03.1 | Essential | The system shall provide the fitness enthusiast with the ability to search for meals by restaurant name. |
| FR-03.2 | Essential | The system shall provide the fitness enthusiast with the ability to search for meals by food-item name. |
| FR-03.3 | Conditional | The system shall display the restaurants of generated meals as locations on a map. |
| FR-03.4 | Conditional | The system shall provide the fitness enthusiast with the ability to set the search radius from 1 to 25 miles (assumption: ASM-032). |

##### 3.1.3 Fitness Enthusiast: Edit Meals, Match and Directions

Derived from HLR-04, HLR-05 and HLR-06. Edit meals, Match and Get directions features.

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-04.1 | Essential | The system shall display each food item on a generated meal with its title, course, energy and protein. |
| FR-04.2 | Essential | The system shall provide the fitness enthusiast with the ability to lock a food item on a generated meal. |
| FR-04.3 | Essential | When the fitness enthusiast locks a food item, the system shall lock the meal's restaurant. |
| FR-04.4 | Essential | When the fitness enthusiast requests the next meal, the system shall replace every unlocked food item, leaving every locked food item unchanged. |
| FR-04.5 | Essential | The system shall provide the fitness enthusiast with the ability to add a food item from the meal's restaurant to the meal. |
| FR-04.6 | Essential | The system shall provide the fitness enthusiast with the ability to remove a food item from the meal. |
| FR-04.7 | Essential | When a food item is added, removed or replaced, the system shall recalculate each total's deviance from the remaining nutrition target. |
| FR-04.8 | Conditional | The system shall provide the fitness enthusiast with the ability to return to the previously generated meal. |
| FR-05.1 | Essential | When the fitness enthusiast matches a meal, the system shall record the meal, its restaurant and the match time on the fitness enthusiast's account. |
| FR-05.2 | Essential | When the fitness enthusiast matches a meal, the system shall display the chosen food items and the final totals. |
| FR-06.1 | Conditional | When the fitness enthusiast requests directions from a matched meal, the system shall open directions from the fitness enthusiast's location to that meal's restaurant (C-005). |

##### 3.1.4 Fitness Enthusiast: Save, Share and Review

Derived from HLR-07, HLR-08 and HLR-09. Save for later, Share and Review features.

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-07.1 | Conditional | The system shall provide the fitness enthusiast with the ability to save a meal into a collection. |
| FR-07.2 | Conditional | The system shall provide the fitness enthusiast with the ability to create a named collection. |
| FR-07.3 | Essential | When the fitness enthusiast opens search, the system shall display that fitness enthusiast's previously matched meals, most recent first. |
| FR-08.1 | Conditional | When the fitness enthusiast shares a matched meal, the system shall produce a summary graphic of that meal in the Instagram story format (C-006). |
| FR-08.2 | Conditional | The system shall be able to pass the summary graphic to the device's share function. |
| FR-09.1 | Conditional | The system shall provide the fitness enthusiast with the ability to rate a restaurant from 1 to 5 stars, with an optional text note. |
| FR-09.2 | Conditional | The system shall display a restaurant's Hungry Henry rating, with the number of reviews behind it, in the restaurant drawer. |

##### 3.1.5 Fitness Enthusiast: Membership and Paid Features

Derived from HLR-10, HLR-11 and HLR-12. Target templates and Ask Henry features, and the membership that gates them.

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-10.1 | Conditional | The system shall provide a fitness enthusiast holding a Paid membership with the ability to save the current remaining nutrition target under a name. |
| FR-10.2 | Conditional | The system shall provide a fitness enthusiast holding a Paid membership with the ability to start a search from a saved target template. |
| FR-11.1 | Conditional | When a fitness enthusiast holding a Paid membership submits a typed sentence, the system shall generate a meal that fits both the sentence and the remaining nutrition target. |
| FR-11.2 | Optional | When *try something new* is on, the system shall exclude from Ask Henry meals every food item the fitness enthusiast has previously matched. |
| FR-11.3 | Optional | When *in-season* is on, the system shall restrict Ask Henry meals to food items the restaurant marks as in season. |
| FR-12.1 | Essential | The system shall provide the fitness enthusiast with the ability to create an account. |
| FR-12.2 | Essential | The system shall provide the fitness enthusiast with the ability to subscribe to the Paid membership (C-007). |
| FR-12.3 | Essential | The system shall provide the fitness enthusiast with the ability to cancel the Paid membership (C-007). |
| FR-12.4 | Essential | When a fitness enthusiast without a Paid membership opens Target templates or Ask Henry, the system shall offer the Paid membership in place of the feature. |

##### 3.1.6 Restaurant Owner: Menu, Visibility and Insights

Derived from HLR-13, HLR-14 and HLR-15. The vendor portal.

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-13.1 | Essential | The system shall provide the restaurant owner with the ability to add a food item with its title, course, energy, protein, carbohydrate, fat and allergens. |
| FR-13.2 | Essential | The system shall provide the restaurant owner with the ability to edit a food item. |
| FR-13.3 | Essential | The system shall provide the restaurant owner with the ability to delete a food item. |
| FR-13.4 | Conditional | The system shall provide the restaurant owner with the ability to submit a menu web page or file for import. |
| FR-14.1 | Essential | The system shall provide the restaurant owner with the ability to choose the Free, Pro Silver or Pro Gold listing tier. |
| FR-14.2 | Essential | When two meals fit the remaining nutrition target with equal total deviance, the system shall rank first the meal from the restaurant on the higher listing tier. |
| FR-15.1 | Essential | The system shall display to the restaurant owner, for each food item, the number of matches that included it on each of the last 30 days. |
| FR-15.2 | Conditional | The system shall display to the restaurant owner, for each food item, the number of generated meals that showed it on each of the last 30 days. |

##### 3.1.7 System: Menu Nutrition Data

Derived from HLR-16. The content processing and data integration pipelines in the Product Idea Workbook [10].

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-16.1 | Essential | The system shall extract the title, course, posted energy and posted allergens of each food item from a restaurant's published menu. |
| FR-16.2 | Essential | When a food item has no posted value for energy, protein, carbohydrate or fat, the system shall estimate that value from reference nutrient values (C-004). |
| FR-16.3 | Essential | The system shall refresh every imported menu at least once every 24 hours. |
| FR-16.4 | Essential | When the restaurant owner saves a change to a food item, the system shall use the changed values in every meal generated after the save. |

##### 3.1.8 System Administrator: Operational Alerts

Derived from HLR-17.

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-17.1 | Essential | When utilization of any production compute, memory or storage resource stays above 80% for 5 consecutive minutes, the system shall notify the system administrator on a mobile device (assumption: ASM-033). |
| FR-17.2 | Essential | When more than 1% of user-facing requests fail over 5 consecutive minutes, the system shall notify the system administrator on a mobile device (assumption: ASM-034). |
| FR-17.3 | Essential | When any of NFR-01 to NFR-03 is missed at the 90th percentile for 5 consecutive minutes, the system shall notify the system administrator on a mobile device (assumption: ASM-034). |

##### 3.1.9 Post-MVP: Wearable Calorie Banking

Derived from HLR-18. Written with "will": planned for a later release and not verified in version 1.0.

| ID | Priority | Requirement |
| --- | --- | --- |
| FR-18.1 | Optional | The system will read the active calories a connected wearable reports. |
| FR-18.2 | Optional | When a connected wearable reports active calories burned since the remaining nutrition target was set, the system will raise the remaining energy target by that amount. |

#### 3.2 Non-Functional Requirements

The quality requirements below are drawn from the Product Idea Workbook's Solution Space and Technology Drivers [10]. Each is filed under a quality attribute named from ISO/IEC 25010 [17], with this product's own definition of what that attribute means and how it is measured. The attributes are categories; the NFR rows under them are the requirements. None has been measured on a build.

NFR IDs are reissued in this version. Version 0.1's interoperability rows, which named Google Places and USDA FoodData Central, are now constraints C-003 and C-004, because each names a mandated system rather than a quality. Its testability rows NFR-14 and NFR-16 described how the project is run, and are now process constraints C-012 and C-013.

Latency classes, per the course materials [11]:

| Class | Target |
| --- | --- |
| Ultra-Low | Less than 2 ms |
| Low | 2 ms to 200 ms |
| Medium | 200 ms to 1 second |
| High | 1 second to 4 seconds |

Quality attributes, as this document defines them:

| ID | Quality attribute | Definition for Hungry Henry | Measured by | Requirements |
| --- | --- | --- | --- | --- |
| QA-01 | Time behaviour | The time from an actor's action to the system's visible response. | 90th-percentile latency on a production build, from on-device instrumentation across a full evening window. | NFR-01, NFR-02, NFR-03, NFR-19 |
| QA-02 | Capacity | The number of concurrent sessions the system serves while still meeting every QA-01 requirement. | Load test at the stated concurrency. | NFR-04 |
| QA-03 | Reliability | How long the user-facing service runs between failures, and how it behaves when a dependency fails. | Incident log, MTTF over the trailing 12 months; fault-injection test. | NFR-16, NFR-18 |
| QA-04 | Availability | The share of a calendar year the user-facing service answers requests: MTTF / (MTTF + MTTR) [18]. | External uptime probe at a 1-minute interval. | NFR-15 |
| QA-05 | Maintainability | How fast the service is restored after a failure (MTTR). | Incident log, time from first alert to restored service. | NFR-17 |
| QA-06 | Safety | Freedom from the one malign failure: a meal presented as safe for an allergy when it is not. | Test against a seeded menu set covering all nine major food allergens. | NFR-05, NFR-06 |
| QA-07 | Functional correctness | Displayed nutrition equals its source value, and every estimate says so. | Comparison against a seeded menu set with known posted values. | NFR-07, NFR-08, NFR-09 |
| QA-08 | Usability | Whether a first-time fitness enthusiast finishes the core job unaided, and how fast. | Moderated usability test with at least 10 first-time participants. | NFR-10 |
| QA-09 | Security | Personal information and accounts stay confidential and unaltered by anyone not entitled to them. | Penetration test, and the verification checklists of C-008 and C-009. | NFR-11, NFR-12 |
| QA-10 | Privacy | The fitness enthusiast's control over their own personal information. | Timed deletion request on a test account. | NFR-13 |
| QA-11 | Compatibility | The range of iPhone and iOS versions the app runs on. | Test-device matrix. | NFR-14 |
| QA-12 | Testability | How easily a test shows the system meets a requirement, without calling external services. | The automated suite run with network access to external services blocked. | NFR-20 |

Categories walked and carried elsewhere: interoperability is carried by the interface constraints C-003 to C-007 and C-015, because each names a mandated external system; regulatory compliance by C-007 to C-011; and operational requirements by HLR-17 and NFR-19. Portability is empty by design, because C-001 limits version 1.0 to iOS.

| ID | Category | Priority | Requirement |
| --- | --- | --- | --- |
| NFR-01 | QA-01 Time behaviour | Essential | When the fitness enthusiast opens the app on the happy path, the system shall display the first generated meal within the low latency class, at most 200 ms, at the 90th percentile. |
| NFR-02 | QA-01 Time behaviour | Essential | When the fitness enthusiast submits a search, the system shall display the first results within the medium latency class, at most 1 second, at the 90th percentile. |
| NFR-03 | QA-01 Time behaviour | Essential | When the fitness enthusiast requests the next meal or changes a food item, the system shall display the updated meal and its deviance within the low latency class, at most 200 ms, at the 90th percentile. |
| NFR-04 | QA-02 Capacity | Essential | The system shall meet NFR-01 to NFR-03 with 1,590 concurrent sessions, the EOY 3 design concurrency at the 5-minute session ceiling [10]. |
| NFR-05 | QA-06 Safety | Essential | When a food item posts an allergen, the system shall display that allergen on every generated meal that contains the food item. |
| NFR-06 | QA-06 Safety | Essential | The system shall display, on every generated meal, a notice that allergen information comes from the restaurant and is to be confirmed with restaurant staff. |
| NFR-07 | QA-07 Functional correctness | Essential | When a food item posts an energy value, the system shall display that posted value, not an estimate, for 100% of such food items. |
| NFR-08 | QA-07 Functional correctness | Essential | When a value is estimated from reference nutrient values, the system shall mark it as estimated, for 100% of estimated values. |
| NFR-09 | QA-07 Functional correctness | Essential | The system shall display each meal total as the sum of its food items' values, rounded to the nearest whole kilocalorie or gram. |
| NFR-10 | QA-08 Usability | Essential | The system shall enable 90% of first-time fitness enthusiasts to match a meal within 1 minute of opening the app, without prior instruction. |
| NFR-11 | QA-09 Security | Essential | The system shall render stored personal information unreadable to unauthorized individuals, at rest and in transit. |
| NFR-12 | QA-09 Security | Essential | The system shall restrict access to a fitness enthusiast's account data to that fitness enthusiast's authenticated session. |
| NFR-13 | QA-10 Privacy | Essential | When a fitness enthusiast submits a verified request to delete their account, the system shall delete that fitness enthusiast's personal information within 45 days [20]. |
| NFR-14 | QA-11 Compatibility | Essential | The iOS app shall run on an iPhone with the current iOS release or either of the two previous major releases. |

##### Timing and Dependability

Hungry Henry has no hard real-time component: no control loop and no actuator. Its timing requirements are soft deadlines in Kopetz's sense [18], where a late result still has value. A meal shown at 3 seconds is worse than one shown at 1 second, but it is still a meal. Missing a deadline costs the position-to-own, a low time to a decision, not safety. The one malign failure in the product, an allergen shown as absent when it is present, is not a timing failure, and is covered by NFR-05, NFR-06, FR-02.3 and FR-02.4 rather than by a deadline.

| Requirement | Deadline class | What a late result costs |
| --- | --- | --- |
| NFR-01 | Soft | The fitness enthusiast waits at the table on a blank screen, the experience the product replaces. |
| NFR-02 | Soft | Search feels slower than Google Maps; the results are still valid. |
| NFR-03 | Soft | Swiping feels sluggish; the next meal is still valid. |
| NFR-19 | Soft | An outage runs longer before anyone acts. |
| FR-16.3 | Soft | A stale menu can show a food item the restaurant no longer serves. |

Dependability is split into its three measurable parts, and they agree arithmetically: availability = MTTF / (MTTF + MTTR) [18]. With an MTTR of 1 hour (assumption: ASM-035), 99.9% availability requires an MTTF of at least 999 hours, about 42 days between user-facing failures.

| ID | Category | Priority | Requirement |
| --- | --- | --- | --- |
| NFR-15 | QA-04 Availability | Essential | The system shall keep the user-facing service available for 99.9% of each calendar year, at most 8.76 hours of downtime [10]. |
| NFR-16 | QA-03 Reliability | Essential | The system shall run the user-facing service for a mean of at least 999 hours between user-facing failures. |
| NFR-17 | QA-05 Maintainability | Essential | The system shall restore the user-facing service within a mean of 1 hour from the first alert (assumption: ASM-035). |
| NFR-18 | QA-03 Reliability | Essential | When an external data source does not respond within 1 second, the system shall generate meals from that source's last stored data, provided it is no older than 24 hours (assumption: ASM-039). |
| NFR-19 | QA-01 Time behaviour | Essential | When an operational fault condition is met, the system shall deliver the alert to the system administrator's mobile device within 60 seconds (assumption: ASM-036). |

##### Testability

ISO/IEC 25010 places testability under maintainability [17]: how easily a test can be designed and run to show the system meets its requirements. Hungry Henry's two live external data sources, Google Places and USDA FoodData Central, make this concrete rather than abstract, since a test that calls either service directly is slow, flaky, and outside the author's control.

| ID | Category | Priority | Requirement |
| --- | --- | --- | --- |
| NFR-20 | QA-12 Testability | Essential | The system shall run every essential user flow in an automated test with every external data source substituted (C-003, C-004), with no live call to either service. |

#### 3.3 Design Constraints

A constraint limits the solution space; a quality requirement limits how well a behaviour performs. Every row below passes the first test. IDs use the C-NNN series, distinct from the requirement IDs, and the notes name the type and what each constraint bounds.

| ID | Constraint | Source | Notes |
| --- | --- | --- | --- |
| C-001 | The mobile client shall be built for iOS on iPhone. | [10] Solution Space, Section 1 | Business. Android is out of scope for version 1.0. Bounds HLR-01 to HLR-12. |
| C-002 | The system shall run on public cloud infrastructure. | [10] Solution Space, Section 1; Section 2.5 | Business. No self-hosted or on-premises hardware. |
| C-003 | The system shall obtain venue identity, star rating and distance from Google Places, under the Google Maps Platform terms. | [10] Solution Space, Section 1 | Interface. Bounds FR-02.5 and FR-03.3. |
| C-004 | The system shall obtain reference nutrient values from USDA FoodData Central, with the attribution USDA requests. | [10] Solution Space, Section 1 | Interface. Public domain. Bounds FR-16.2. |
| C-005 | The system shall open directions in Google Maps. | [10] Solution Space, Section 1, Get directions | Interface. Bounds FR-06.1. |
| C-006 | The share graphic shall be 1080 × 1920 pixels, the 9:16 Instagram story format. | [10] Solution Space, Section 1, Share | Interface format. The pixel size is assumption: ASM-038; Meta's own specification was not confirmed. Bounds FR-08.1. |
| C-007 | The Paid membership shall be sold through Apple in-app purchase. | [21] Section 3.1.1 | Regulatory (platform). The guideline requires in-app purchase to unlock features or functionality, subscriptions included. Bounds FR-12.2 and FR-12.3. |
| C-008 | The backend and API shall satisfy OWASP ASVS v5.0.0 Level 2. | [12] | Standards compliance. Sized to the risk of an organized hacker group, not a nation-state actor [10]. Verifies NFR-11 and NFR-12. |
| C-009 | The iOS client shall satisfy OWASP MASVS v2.1.0. | [13] | Standards compliance. Verifies NFR-11. |
| C-010 | The system shall classify location, nutrition targets, diet and allergy data as personal information under CCPA/CPRA. | [10] Solution Space, Section 5; [20] | Regulatory. Whether the statutory business thresholds apply at EOY 1 to 3 is not settled; the consumer rights are applied to every user regardless (assumption: ASM-037). Bounds NFR-13. |
| C-011 | The allergen list shall be the nine major food allergens. | [19] | Regulatory. FALCPA (2004) set eight; the FASTER Act added sesame from 1 January 2023. Bounds FR-01.3 and FR-02.3. |
| C-012 | Every essential user flow shall be tested before a version is deployed. | Version 0.1, NFR-14 | Process. |
| C-013 | Every version shall pass a human approval gate before release. | Version 0.1, NFR-16 | Process. |
| C-014 | Development shall start on 1 January 2027, with introduction in January 2028. | [10] Product Strategy Space, Section 6 | Business (time). 12.8 months, from the EstiMate output. |
| C-015 | Ask Henry shall use a general-purpose generative AI model on pre-trained public data, with no training pipeline at version 1.0. | [10] Product Strategy Space, Section 7 | Design. Bounds HLR-11. |

#### 3.4 External Interface Requirements

TBA.

### Appendixes

TBA.

### Index

TBA.
