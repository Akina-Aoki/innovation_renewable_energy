# Solar Builder — Project Context and Design Direction

Use this context alongside `LOVABLE_PROMPT.md`.

The technical prompt defines the features, data and calculations. This prompt explains the project’s purpose and the experience we want to create. Keep the existing technical requirements and prototype scope.

## 1. Why we are building this

We are developing a hackathon project for **Innovate for Humanity**, organised by Innovation Pioneers with Machine Learning Open Stockholm.

Our theme is **SDG 7: Affordable and Clean Energy**.

Our goal is to help households and communities make informed decisions about solar energy, especially where affordability and reliable electricity are important concerns.

For our first prototype, we are focusing on **one fictional household in the Philippines**.

The broader vision includes communities, but the current app demonstrates the household journey only.

## 2. The problem we want to explore

Buying a solar setup involves more than choosing panels.

A household may need help understanding:

* How much electricity it uses.
* What equipment it needs.
* Whether the components work together.
* What fits its budget.
* Where to source the components.
* What still needs professional review.
* How to understand system performance after installation.

Our working hypothesis is that bringing this information together can make solar planning easier and more transparent.

Treat this as a problem we are investigating through a prototype and interviews. Do not present it as a proven market finding or claim that no similar platforms exist.

## 3. The wider project has four parts

| Part                                  | Planned purpose                                                                                                                                               |
| ------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **1. Identify potential communities** | Use open data to help identify places where local solar projects could be explored. Population density is one possible input, not a complete site assessment. |
| **2. Solar Builder — this prototype** | Help households plan, customise, compare and source solar equipment, then explore simulated monitoring.                                                       |
| **3. Fair energy distribution**       | Explore how a shared system could allocate available electricity fairly, considering household needs and essential services.                                  |
| **4. Funding and partnerships**       | Explore project costs and potential NGOs, investors and implementation partners.                                                                              |

Build **Part 2 only**.

The other parts may appear in a small “Our wider vision” section, clearly labelled as planned work. Do not create working community maps, energy allocation controls or funding tools.

## 4. Who we are designing for

Our main user is a household member who wants to explore solar but may not understand technical equipment specifications.

They might know:

* Their monthly electricity use.
* Their available budget.
* Which appliances matter most during an outage.
* How much backup time they would like.

They may not understand:

* Inverter sizing.
* Battery capacity.
* Electrical compatibility.
* The difference between power and energy.

The interface should help them learn as they make decisions.

Use practical explanations such as:

**“Which essential appliances would you want to keep running?”**

Explain technical terms close to where they appear. Keep detailed specifications available through expandable sections.

## 5. Our product concept

**Solar Builder helps households plan and compare solar setups based on their electricity needs and budget.**

The interaction is inspired by custom PC builders:

* Select components.
* See how selections affect the total.
* Check preliminary compatibility.
* Compare alternatives.
* Save a complete shopping checklist.

For solar, the main components are panels, an inverter and batteries.

DIY means giving users more involvement in planning and sourcing their equipment. The app must still provide a professional installation handoff and explain unresolved design checks.

## 6. Our data engineering contribution

We are building the information layer that connects:

* Household needs.
* Equipment specifications.
* Supplier offers.
* Preliminary compatibility rules.
* Estimated performance.
* Monitoring readings.

For this prototype, all of these use the supplied synthetic datasets.

The monitoring page demonstrates how readings could become understandable charts after installation. It does not connect to real equipment.

Do not add AI simply for presentation value. The prototype uses the calculations and rules defined in the technical prompt.

## 7. Reference: Green Empowerment

Green Empowerment’s renewable-energy work highlights community-owned systems, locally appropriate technology, and training that helps people manage and maintain equipment. It also connects energy access with everyday needs in homes, schools and clinics. [Green Empowerment — Renewable Energy](https://greenempowerment.org/our-work/renewable-energy/)

### Our design interpretation

Translate that inspiration into:

* A people-focused introduction.
* Clear explanations of how equipment choices relate to household needs.
* Visible installation handoff and maintenance awareness.
* A short explanation of the longer-term community vision.

These are our proposed design choices, not claims about features on Green Empowerment’s website.

Do not copy its branding, photographs, logo or wording. Do not imply partnership or endorsement.

## 8. Reference: Empower a Billion Lives

The linked document describes the **2023 Global Final and Energy Access Workshop**. It emphasises economically viable, environmentally sustainable energy-access solutions, alongside consumer education, inclusion and productive uses of electricity. Use it as historical mission context. [Empower a Billion Lives — Workshop PDF](https://empowerabillionlives.org/wp-content/uploads/031522Global-Final-and-Energy-Access-Workshop-6.pdf)

### Our design interpretation

Help users understand:

* Whether a proposed setup fits their budget.
* What assumptions sit behind estimates.
* What trade-offs different configurations involve.
* What still needs confirmation before installation.

Use this reference for purpose and messaging. It is not a solar product catalog, current statistics source or interface template.

Do not claim that our prototype has been field-tested, won an award or demonstrated real-world impact.

## 9. Visual direction

The app should feel **approachable, practical and trustworthy**.

Keep the visual style from the technical prompt:

* White background.
* Dark navy text.
* Green accents.
* Warm yellow for household load.
* Blue for battery information.
* Comfortable spacing and readable cards.

Use simple solar, home and battery illustrations where helpful.

Make the main actions easy to find on mobile. Keep pages lightweight, avoid autoplay video and avoid animations that distract from choosing or comparing equipment.

Explain the social purpose through clear copy and practical examples. Do not invent testimonials, customer counts, savings figures or impact statistics.

## 10. Suggested introduction

Add a compact introduction above the existing app journey.

**Headline**

Plan a solar setup that fits your household.

**Supporting text**

Explore equipment, compare estimated costs and understand your options based on your electricity needs and budget.

**Primary action**

Start my solar plan

**Secondary action**

Explore demo monitoring

**Small context note**

A hackathon prototype exploring more accessible solar planning for households, with a longer-term community energy vision.

Keep the “Demo · synthetic data” label visible.

Do not require users to read a long project explanation before entering the builder.

## 11. What the experience should communicate

By the end of the journey, the user should understand:

1. What equipment is included in their selected setup.
2. How its estimated cost compares with their budget.
3. What its generation and backup estimates mean.
4. Which checks are preliminary.
5. What they need to source and confirm.
6. How monitoring could help them understand an installed system.

Keep the distinction clear between:

* **Working prototype features.**
* **Simulated data and estimates.**
* **Future community ambitions.**

## 12. Apply this context

Use this context to improve the app’s introduction, explanations, visual hierarchy and overall tone.

Preserve the supplied data, formulas, navigation and core journey from `LOVABLE_PROMPT.md`.

If the app already exists, refine it without resetting saved progress or replacing working features.
