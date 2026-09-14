# Solar Builder — My Household page update prompt

Update only Step 1, “My Household”, in the existing Solar Builder app. Use the supplied My Household screenshot as the layout reference. Preserve the existing green, navy and white design, navigation tabs, demo badges, routes and working calculations. Apply the exact user-facing copy below.

## 1. Page heading

Make “STEP 1” much larger: approximately 80–90% of the “My Household” title size, with clear green emphasis. Keep “My Household” as the main page heading and maintain a sensible heading hierarchy. On small screens, allow the text to wrap without crowding.

Replace the current technical subtitle with:

> Tell us about your home and what you need. We will help you plan a solar system that suits your electricity use and budget.

Keep “Reset to defaults” and “Next: Build a System” and their existing actions.

## 2. Add an easy guide before the form

Place this section after the page introduction and before the Household profile and summary cards. It must be visible by default, so users can learn the basics before filling in the form.

Heading: **A few words to help you start**

Introduction:

> New to solar? These simple explanations will help you fill in the form.

Use this two-column table on desktop. On mobile, stack each term and explanation into a readable card without horizontal scrolling.

| Word | What it means |
| --- | --- |
| kW — power | How much power your appliances use at one time. 1 kW equals 1,000 watts. For example, ten 10-watt lights use 100 watts, or 0.1 kW, together. |
| kWh — electricity used | How much electricity you use over time. A 100-watt appliance running for 10 hours uses 1 kWh. Your electricity bill shows your use in kWh. |
| kWp — solar panel size | The rated power of your solar panels under test conditions. The power they produce at home changes with sunlight, shade and weather. |
| Battery charge — SOC | How full your battery is, like the battery percentage on a phone. 100% means full; 50% means about half full. |
| Hybrid | Uses solar panels, a battery and power from your electricity company. With the right equipment and setup, the battery can power selected appliances during a power cut. |
| On-grid | Uses solar panels and connects to your electricity company. A usual system without a battery stops supplying power during a power cut. |
| Off-grid | Works without a connection to an electricity company. It needs enough solar panels and battery storage for the appliances you want to use. |

Do not call kWh “kilowatts per hour”. Keep examples short and avoid turning this section into a technical manual.

## 3. Household profile: labels and helper text

Keep the existing form structure, but give every helper text enough room to read. Use plain English, short sentences and visible units. Do not describe users by education or income level in the interface.

### Location

Keep the demo location fixed to Laguna, Philippines.

Helper text:

> We are using Laguna, Philippines for this demo.

### System type

Keep Hybrid selected. Preserve the current demo restriction: On-grid and Off-grid remain unavailable. Label them “Coming later” rather than suggesting they work now.

Helper text:

> This demo plans a system with solar panels and a battery, connected to your electricity company.

### Monthly electricity consumption

Keep this label and the kWh unit. Keep the existing 370 kWh demo value for a new or reset profile; do not overwrite a returning user’s saved input.

Helper introduction:

> How much electricity does your home use in one month? Here are two ways to find out:

- **Check your bill:** Look for “kWh” or “consumption”. Enter the electricity used, not the amount you pay in pesos. For a more typical month, add the kWh from your last three monthly bills and divide by three.
- **Check your meter:** If your meter shows total kWh used, write down the reading and date. Read it again about 30 days later. Subtract the first reading from the second. One meter reading alone does not show your monthly use.

Additional short helper:

> Not sure yet, or no electricity bill? You can try the demo number and change it later. Your results will be examples until you enter your own use.

Keep the meter guidance about reading the display only; do not instruct users to open or touch electrical equipment. Do not infer household monthly use from a shared meter without household-specific information.

### Budget

Change the label to:

**How much would you like to spend?**

Keep the input in Philippine pesos (₱).

Helper text:

> Enter your budget for your solar system. We will show you which options are within this amount and which cost more.

Small note underneath:

> ₱50,000 is a sample budget for this demo, not a price quote. Your final cost depends on the parts, delivery and installation.

Default: **₱50,000**, preserving the current screenshot’s demo default. Retain returning users’ saved budgets. Do not increase someone’s budget automatically to fit a build. If no build fits, say so clearly.

Do not claim this amount buys a complete hybrid system, powers an entire home, or is the cheapest setup available in the Philippines. The research note at the end explains why no verified market minimum is supplied.

### Essential appliances during a power cut

Replace “Critical load” with:

**What do you want to keep running during a power cut?**

Keep the existing numerical field and calculation meaning, but display the input in **watts (W)** to make appliance labels easier to use. Show **500 W** for the existing **0.5 kW** default. Convert watts to kW internally wherever the existing calculations expect kW; do not change downstream units accidentally.

Helper text:

> Think about the appliances you need most, such as lights, a fan, your fridge or a TV. Add the watts (W) of the appliances you want to use at the same time. You can usually find the watts on the appliance label or in its manual.

Example:

> Example: two 10 W lights + one 50 W fan + one 10 W Wi-Fi router = 80 W.

Small note:

> Some appliances, such as fridges, need extra power when they start. This number is a starting estimate.

Do not describe this field as the electricity needed for the entire home or as daily energy use. It is the combined power of selected appliances running together during an outage. Do not add a new appliance-picker feature in this update.

### Backup goal

Change the label to:

**How many hours do you want backup power?**

Keep the existing hours input and 8-hour demo default.

Helper text:

> During a power cut, how long would you like your battery to run the appliances you listed above?

Small note:

> This is your goal. How long the battery actually lasts depends on its size, charge and the appliances you use.

## 4. Remove the visible “Estimate assumptions” section

Remove the entire section from this page, including its explanatory text and editable controls for peak sun hours, performance ratio and electricity tariff.

This is a presentation change: retain the underlying assumptions needed by existing calculations. Preserve the current stored assumptions and reset behavior; use the existing defaults for a fresh profile. The screenshot’s defaults are 4.5 peak sun hours, 0.8 performance ratio and ₱12/kWh. These are demo inputs, not verified local rates or forecasts.

Do not delete calculation dependencies, silently substitute researched values, or imply that the estimates are professionally assessed. Keep a simple visible note near the summary:

> These are rough estimates using demo information. Real results depend on your home, equipment and sunlight.

## 5. Make the summary cards easy to understand

Keep the current layout on the right on desktop and stack it naturally below the form on mobile. Keep the live updates when inputs change. Replace the current card labels and technical helper text as follows.

| Current card | New label | Description beneath the number |
| --- | --- | --- |
| Required solar capacity | Suggested solar panel size | A rough guide to the total panel size needed for your electricity use. Your roof and sunlight affect what you will need. |
| Average daily use | Electricity you use in a day | Your monthly electricity use divided by 30. Some days you may use more or less. |
| Budget | Your budget | The amount you would like to spend. We will compare it with the estimated cost of each option. |
| Critical load | Appliances to keep running | The total power of the appliances you want to use together during a power cut. |
| Backup goal | Your backup goal | You would like your selected appliances to run for {hours} hours during a power cut. The battery you choose must be checked against this goal. |

Display the appliance-power summary in watts to match the revised input, for example **500 W**. Keep panel size in kWp, daily use in kWh, budget in ₱ and backup goal in hours.

For Suggested solar panel size, remove the visible formula and replace it with:

> We estimate this from your monthly electricity use and the demo’s sunlight settings.

Retain the calculation internally: monthly consumption ÷ 30 ÷ (peak sun hours × performance ratio). With the screenshot’s demo inputs, the panel-size estimate should remain approximately **3.43 kWp**, and daily use approximately **12.3 kWh**.

Do not write “You will have electricity for 8 hours a day”. The card is a desired outage-backup duration, not a guarantee or a daily schedule. Do not imply a selected build exists on this page if none has been selected.

## 6. Remove “How the numbers connect”

Remove that heading, explanatory paragraph and the entire blue box. The short descriptions on the summary cards replace it.

If retaining the existing saved-state indicator, use:

> Your answers are saved in this browser.

Do not claim account-based saving or guaranteed privacy.

## 7. Completion checks

- STEP 1 is prominent and nearly the size of the main title.
- The educational guide appears before users enter their needs.
- All user-facing labels and explanations match the simple copy above.
- Hybrid remains the supported demo option; future system types remain unavailable.
- The monthly consumption helper explains both bills and two meter readings accurately.
- The budget is editable and clearly labeled as a demo amount, with no unsupported cheapest-system claim.
- Watts displayed in the appliance field convert correctly to the existing kW model: 500 W must remain 0.5 kW internally. Saved profiles must convert for display without multiplying or dividing twice.
- Existing validation continues to reject invalid or negative inputs and avoid division errors.
- Backup hours are a target, not a promise.
- Estimate assumptions and How the numbers connect are absent from the visible page; underlying calculations still work.
- Changing a household need continues to update the relevant summary and downstream comparisons. It must not change the physical output of an unchanged panel build.
- Saved answers, reset behavior, navigation and the next-step button continue to work.
- Desktop and mobile layouts remain readable, with no clipped text or horizontal table scrolling.
- Other pages and the landing-page prompt remain unchanged.

## Research note for the project owner — not website copy

Research date: 11 September 2026.

A defensible lowest price for a complete Philippine DIY home solar system could not be verified from the accessible results. Listings found were a mixture of partial equipment, installed packages and limited social-media material; they do not establish an equivalent complete starter system or a market minimum. Therefore, keep the existing ₱50,000 only as an explicitly illustrative default, rather than writing “according to research, this is the cheapest setup”.

Before replacing this with a sourced budget, verify a dated seller listing that identifies panel wattage, inverter type and rating, battery capacity, included wiring/protection/mounting, and whether delivery and installation are included. Describe it as “one listed starter package”, with its source and date; do not call it the cheapest nationwide. A small lights-and-phone kit is not equivalent to this hybrid household demo.

Optional electricity-use learning resource: [Meralco — Understanding Your Electric Consumption](https://corporatepartners.meralco.com.ph/videos/understanding-your-electric-consumption). This is not a source for solar equipment prices.
