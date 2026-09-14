# Solar Builder — Compare and My Checklist update prompt

Update Step 3, Compare, using the supplied screenshots. Preserve the visual identity and existing catalog, household inputs, calculations and internal choice identifiers. Implement the wording, presentation and budget-enforcement changes below. Cover both Scenario A (no eligible choices) and Scenario B (an eligible choice proceeds to Step 4). Include the My Checklist changes and proposed help-application window below in this same file, as requested.

## 1. Larger heading and simple introduction

Make STEP 3 as visually large as Compare, with green emphasis. Keep Compare as the main heading.

Subtitle:

> Compare these three solar systems. See the parts, price and estimated electricity from each one, then choose an option that fits your budget.

Use readable body text around 16–18 pixels, secondary text at least 14 pixels, comfortable spacing and large buttons. Keep the top navigation and demo badge.

## 2. Explain when none of the choices work

Replace “No seeded setup fits your current constraints” and its paragraph with a prominent bordered message, a large X icon and text. Do not say the user's entire solar plan is impossible just because these three examples do not fit.

If all three are over budget, show:

**These choices cost more than your budget.**

> Your budget is ₱{budget}. None of these three choices fits it yet. Try changing the parts to lower the cost, or review your budget if you want to.

Buttons: **Change the parts** → Build a System; **Review my budget** → the budget field on My Household.

If none are eligible for mixed reasons, show:

**These choices need changes before you can continue.**

> Check the messages below each choice. You may need to change the parts or review your budget.

If at least one qualifies, show:

**{count} choice(s) can be added to your checklist.**

Use correct singular/plural grammar. The count must come from the same eligibility logic as the buttons. Explain each choice's actual blockers, including unavailable stock, missing data and failed component checks. Use words as well as icons and colors.

## 3. Clear choice names without internal codes

Use these display names consistently with the revised Build a System page:

| Internal identifier — never display | Visible title | Visible subtitle |
| --- | --- | --- |
| C1 / Budget | Spend less | Component choice 1 |
| C2 / Balanced | Balance cost and power | Component choice 2 |
| C3 / More Solar | Get more solar power | Component choice 3 |

Do not rename model identifiers in storage or break existing saved selections. Update shared user-facing choice labels wherever these choices appear, including checklist headings. Do not show C1, C2 or C3 as names.

Avoid unexplained abbreviations throughout the platform. Use “estimated” rather than “Est.” and “battery charge” rather than “SOC”. For values, write out watts, kilowatt-hours and hours where space allows; if using a standard unit symbol, pair it with its full name or a visible explanation. Do not corrupt real model names or internal identifiers to remove abbreviations. Do not describe kilowatt-hours as kilowatts per hour. The Step 4 redesign below is also in scope; keep unrelated page redesigns out of scope.

## 4. Make the comparison easy to scan

Keep an aligned comparison on desktop, with a clearly separated column for each system. On mobile, show stacked cards containing the same rows and actions without horizontal scrolling. Show a small panel/inverter/battery illustration with each parts list. Images are explanatory, not new product photographs or invented products.

| Current wording | Replacement | Visible explanation |
| --- | --- | --- |
| Setup | Your choices | Compare the three example systems below. |
| Parts | What is included? | List panels, inverter and batteries on separate lines with their quantities. |
| Total cost | Estimated total cost | Parts plus the extra budget for equipment and installation. |
| Within budget? | Does it fit your budget? | Your budget: ₱{budget}. |
| Solar capacity | Total solar panel size | The combined rated size of the panels. Actual power changes with sunlight and weather. |
| Nominal battery | Total battery storage | The stated battery size. Not all of this energy is available to use. |
| Est. monthly generation | Solar electricity in one month | An estimate using the demo's sunlight settings. Actual results may be different. |
| Est. backup at 0.5 kW | How long could the battery run your appliances? | Based on the appliances you entered in My Household: {watts} watts used together. |
| Preliminary checks | Do the parts fit together? | Basic demo checks, not approval for installation. |
| Allowance | Extra equipment and installation budget | Money set aside for supports, cables, safety equipment and installation help. Already included in the total. |

All displayed values must come from existing calculations. Do not show raw formulas as the main explanation; retain them in an optional details disclosure.

Budget states:

- Below budget: **Within your budget — ₱{difference} left.**
- Equal to budget: **Matches your budget.**
- Above budget: **Over your budget by ₱{difference}.**

Backup states:

- **About {hours} hours — shorter than your {goal}-hour goal.**
- **About {hours} hours — meets your {goal}-hour goal in this demo.**

Do not promise this many hours every day. Keep existing runtime assumptions available in expandable details. Treat backup-goal and solar-size shortfalls as clearly displayed goal comparisons; preserve their existing classification rather than silently introducing new hard gates.

Under the component checks use **Looks OK in this demo**, **Needs changing**, or **Not checked**, based on actual results. Keep specific failure reasons visible and technical numbers in details. Retain professional-review warnings and explain them in plain language. For example, the existing temperature-adjusted voltage warning can read: **An installer needs to check the panel voltage in cold weather.** Do not convert a warning to approval or hide it behind a green success message.

Add a small visible educational reminder near the comparison:

**A quick reminder**

> Kilowatt-hours measure electricity used or stored over time. For example, a 100-watt appliance running for 10 hours uses 1 kilowatt-hour.

Include a light-bulb icon and **See everyday appliance examples** linking to the new guide on My Household. Preserve any current selection when navigating there. Do not insert unsupported claims about poverty thresholds or average household requirements.

## 5. Make choosing a system an obvious action

Replace the tiny “Choose” table row with a distinct action panel at the bottom of each choice column/card. Align panels on desktop and keep each attached to its choice on mobile.

For an eligible choice:

**Ready to choose this system?**

> Add these parts to your shopping checklist.

Large green button: **Choose component choice {number}**

For an over-budget choice:

**Over your budget by ₱{difference}**

Disabled selection button: **Over budget — cannot choose yet**

Show a working **Change parts** action and a **Review budget** link. Do not make users click a disabled button to discover the reason.

For other blocked choices, use a disabled **Fix the issues to continue** button, with specific visible reasons and a working edit action. If multiple blockers apply, show them all without flooding the page with raw technical details.

Eligible selections use a short confirmation consistent with Build a System:

**Add component choice {number} to your checklist?**

Show actual parts, quantities, full estimated total and budget status. Explain any replacement of an existing checklist before it occurs.

Buttons: **Keep comparing** and **Yes, create my checklist**.

On successful confirmation, save the exact choice and open My Checklist. This does not place an order.

## 6. Fix the over-budget checklist bug across all entry points

This is a required behavior change, not only a disabled-button style.

A choice passes the budget gate when its full estimated total is less than or equal to the saved household budget. Over budget must block selection. Under budget is allowed, subject to the other existing required checks.

Use one shared eligibility calculation for banners, choice buttons, confirmations and the action that saves the checklist. Apply it to Compare AND Build a System so users cannot bypass the rule by changing pages. Include the equipment/installation amount in the total exactly once. Recheck current prices, quantities, stock, total and budget when the user confirms, not only when the page first loads.

Reject invalid or missing inputs and failed required component/stock checks. Do not count unknown prices as zero or assume unknown checks pass. Do not silently increase the budget, lower quantities, switch parts or save the cheapest option instead.

If a stale click or changed budget invalidates a choice at confirmation time, keep the user on the current page, preserve their edits and show:

> This system is now ₱{difference} over your budget. Please change the parts or review your budget before creating your checklist.

No new checklist should be saved for the blocked selection.

For previously saved over-budget checklists, do not erase ordered/received progress. Keep them viewable with a prominent **This saved plan is over your current budget** notice and a route to fix it. Viewing old saved data is not permission to create or replace a checklist with a newly invalid choice. Navigating directly to My Checklist must not auto-create a rejected choice.

This explicitly supersedes the older Build a System instruction that allowed an over-budget draft to be saved. The revised Step 2 prompt now uses this same stricter rule.

## 7. Acceptance checks

Using the screenshot's current totals, with component and stock checks otherwise passing:

| Household budget | Budget-gate result |
| --- | --- |
| ₱50,000 | All three blocked: over by ₱93,000, ₱177,000 and ₱195,000. |
| ₱143,000 | Component choice 1 meets the budget exactly; choices 2 and 3 blocked. |
| ₱200,000 | Component choice 1 below budget; choices 2 and 3 blocked. |
| ₱227,000 | Choices 1 and 2 pass the budget gate; choice 3 blocked. |
| ₱250,000 | All three pass the budget gate. |

These are regression examples, not hardcoded business logic. Full eligibility also includes the existing required checks.

Verify that a below-budget choice with a required component failure is still blocked. Verify a budget change while a confirmation is open is caught before saving. Verify the same rules in Build a System, no blocked click creates a checklist, and an eligible confirmation opens the correct checklist with matching quantities and total. Verify reloads preserve choices and existing checklist progress appropriately.

Check desktop/mobile readability, keyboard operation, disabled-state explanations, prominent selection controls, and removal of visible internal choice codes. Apply the Step 4 requirements below. Keep Monitoring calculations and its fixed demo dataset unchanged.


## 8. Scenario B — choosing an affordable system

With a ₱150,000 household budget, the ₱143,000 Component choice 1 may proceed if required checks pass. Show **₱7,000 left in your budget**. This is not ₱7,000 over budget. Choices 2 and 3 remain blocked at their current prices.

After the existing confirmation, open the actual Step 4 My Checklist route with the selected system. Preserve household inputs and all active estimate assumptions. Do not reset them when navigating or copy numbers from screenshots into the interface.

The latest screenshot uses different assumptions from earlier screenshots: 9 demo sunlight hours and a 600-watt appliance load. Those inputs explain 583.2 kilowatt-hours per month and about 6.1 backup hours for Component choice 1. They are not newly verified local sunlight values. With earlier settings, different results are expected. Keep the assumptions visible in optional technical details and label estimates as demo estimates.

## 9. Step 4 heading, navigation and plain English

Make STEP 4 as visually large as My Checklist, with green emphasis. Keep My Checklist as the main heading. Apply the same large, readable text and spacing as Steps 2 and 3.

Subtitle:

> Here are the parts for your chosen solar system. Save your list, check where to find the parts, or ask someone to help you plan the installation.

Below it show **Your choice: Spend less — Component choice 1**, or the actual selected display name. Use **Your custom system** for a custom build; never mislabel it as a preset.

Replace the top controls:

- **Download CSV** → **Download my shopping list (PDF)**.
- **Change build** → **Change my parts**. Return to Build a System with this selection loaded for editing. Going back must not immediately overwrite the saved checklist; commit replacement only when the user confirms a valid revised system.

Optional saved-state text: **Your list is saved in this browser.** Do not imply account storage.

## 10. Step 4 summary cards

Use icons plus full labels and short explanations. Preserve calculated values:

| Label | Explanation |
| --- | --- |
| Estimated total cost | Your selected parts plus the money set aside for extra equipment and installation. |
| Money left in your budget | What remains after the estimated cost of this system. |
| Total solar panel size | The combined rated power of your panels. Sunlight and weather affect actual output. |
| Total battery storage | The battery's stated storage size. Some energy is kept in reserve or lost during use. |
| Solar electricity in one month | What these panels might produce using the demo's sunlight settings. Real results can differ. |
| How long your battery could last | An estimate for the appliances you entered in My Household. Actual time depends on their use and the battery's charge. |

For a legacy saved plan that is now over budget, change the second card to **Over your current budget by** and show the positive difference. Preserve the budget gate for new saves.

Write out units where practical and explain any symbols. Panel rated power is in kilowatts-peak, not kilowatt-hours; battery storage and monthly energy use kilowatt-hours; backup duration uses hours. Avoid EST, SOC and other unexplained abbreviations.

## 11. Add a visual everyday-appliance estimate

Heading: **What could this battery power?**

Introduction:

> Here is an example using everyday appliances. Your appliances may use more or less electricity. These estimates are not a promise of how long your whole home will have power.

Show recognizable fridge, light-bulb and washing-machine illustrations. Reuse the explicitly hypothetical appliance assumptions from My Household: a fridge with a 365-kilowatt-hour yearly energy label (about 1 per day), four 10-watt bulbs used for 5 evening hours (0.2 per evening), and a washing machine assumed to use 0.5 per wash. Label these as **Example values**, not Philippine averages or a poverty threshold. These appliances do not define what lifts a family out of poverty.

Make this section respond to the selected battery's usable energy, not just its stated capacity. With the current demo model, usable delivered energy equals stated storage × (starting charge minus reserve) × discharge efficiency, with percentages represented as fractions. Reuse the existing calculation rather than introducing inconsistent battery accounting. For the screenshot's 5.12-kilowatt-hour battery, 95% starting charge, 20% reserve and 95% efficiency, this is 3.648 kilowatt-hours.

Show a table headed **If the battery powered only this example appliance**:

- Fridge: illustrative energy-only hours = usable energy ÷ (1 kilowatt-hour / 24 hours).
- Four bulbs together: hours = usable energy ÷ 0.04 kilowatts; optionally show how many five-hour evenings that represents.
- Washing machine: complete example washes = floor(usable energy ÷ 0.5 kilowatt-hours). Do not invent a cycle duration to convert washes into hours.

Make clear: **These are separate examples. You cannot add these times together. Using appliances together uses the battery faster.** Do not truncate numbers without explaining the time horizon or imply the battery recharges automatically every day.

Also show **One example day together**: fridge for 24 hours, four bulbs for 5 hours and one wash require about 1.7 kilowatt-hours under these assumed values. Compare this with the selected usable battery energy as **Enough energy for this example** or **Not enough energy for this example**, followed by **Appliance power and starting needs still need checking**. This is an energy comparison, not a compatibility verdict.

The current catalog does not establish the actual fridge/washing-machine running and starting power. Do not label them confirmed supported. State **Ask your installer to check whether the inverter can start and run your actual appliances.** If relevant appliance specifications are missing, retain an explicit unverified status. Never replace the household's entered load with this illustration or change the existing backup card to match it.

Keep monthly solar generation separate from battery-only runtime; do not divide monthly generation by an appliance's power to claim outage backup hours. Make assumptions readable in a disclosure and include them in the PDF if the example is exported.

## 12. Shopping list focused on finding parts

Remove Not purchased / Ordered / Received dropdowns and the received-count progress text. This app is not ordering products. Existing status data can remain in storage for compatibility, but should not be displayed or exported as purchase tracking in this updated flow.

Heading: **Your shopping list**

Introduction:

> Take this list to a shop or share it with someone helping you. Check the current price and availability before buying.

For each component show, in large readable text:

- Part type and model.
- Number needed.
- Price for one and total for that line.
- **Where to find it**, with the selected supplier name prominently displayed.
- A verified website, address/service area or phone number only if available in the supplier data.

For the current fictional catalog, show **Example shop — contact details are not available in this demo**. Do not invent websites or numbers for Demo Solar Shop A/B. Do not map a fictional component to an actual seller without evidence. When real supplier data is supplied later, use visible **Visit shop website**, **View location** or **Call shop** links with actual verified destinations. Never automatically contact anyone.

Replace obscure installation rows with:

| Old wording | New wording | Explanation |
| --- | --- | --- |
| Mounting | Supports for your solar panels | Holds the panels in place. Ask an installer which supports your roof needs. |
| Protection equipment | Electrical safety equipment | Safety parts for the system. An installer must choose the correct types and sizes. |
| Cabling | Cables and connectors | Connects the parts. The correct sizes and lengths depend on your setup. |
| Professional installation | Installation help | A qualified person checks and installs the system. Ask what work is included and what it costs. |
| Scope and quote to confirm | Ask an installer what you need and what it costs | The exact items and prices have not been confirmed. |
| Covered by allowance | Included in your extra-cost estimate | Money is set aside, but this is not a confirmed price. |

Show one **Extra equipment and installation budget** amount, counted only once in the total. Do not invent individual prices for these rows or label them paid/included in a purchased package. Preserve the estimate even if someone applies for free help; no support has been awarded yet.

## 13. Replace spreadsheet export with a readable PDF

Implement a genuine PDF download from **Download my shopping list (PDF)**. Remove the main CSV download control. Do not rename CSV bytes as .pdf. Use the supplied receipt screenshot as a simple layout reference: clear heading, neat item table and totals. Create an original Solar Builder design with the app's colors; omit the template vendor branding.

Title: **Solar shopping list**

Subtitle: **Planning estimate — not a receipt or proof of payment**

No purchase has occurred. Do not include Amount paid, Payment method, Tax owed, Paid stamps or fabricated invoice information. Use a generated date and plan reference instead of receipt/payment fields.

Create a clear A4 portrait PDF with two sections/pages as needed:

### Household-friendly shopping list

- Solar Builder name and clear Demo / example prices label.
- Choice name, generated date and plan reference.
- Household location at the existing demo level, budget, total and remaining amount.
- Table columns: **Part and model**, **Quantity**, **Price for one**, **Line total**. Put **Where to find it** on a readable second line for each item or in a dedicated supplier section to avoid squeezing too many columns.
- Parts subtotal, one extra-equipment/installation estimate, and estimated total.
- The plain-language explanation that supports, cables, safety equipment and installation costs must be confirmed.
- Verified supplier contacts if supplied; otherwise honest demo placeholders.

### Information for the person helping you

Use a second page when needed instead of tiny text:

- Component models, quantities and available technical specifications with units.
- Household monthly consumption, selected appliance load and backup goal.
- Panel configuration used by the demo, inverter limits, battery voltage and communication assumptions when present in the actual catalog.
- Actual passed, failed, unknown and professional-review findings. Do not omit unresolved warnings.
- Estimate assumptions, including sunlight settings, battery starting charge, reserve and efficiency.
- Explain that the document supports a professional review; it is not an approved electrical design or wiring instruction.

Do not invent missing specifications. Do not include household income, precise address or application answers in this default shopping PDF. Those belong to the separate support-application flow and require explicit sharing choices.

Use selectable text, readable type, wrapping model names, repeated table headers on overflow, clear totals and no clipped rows. Embed a font that supports the peso symbol or use a readable “Philippine pesos” fallback. Suggested filename: solar-shopping-list-{plan-reference}.pdf.

Verify an actual downloaded PDF opens, matches the selected system and on-screen totals, and is readable on phone and printed A4. Render and inspect the generated PDF during implementation, including long product names and multiple-page cases.

## 14. Turn installation handoff into a clear help route

Replace “Installation handoff” with **Share your plan with someone who can help**.

Copy:

> An installer or trained volunteer can review your parts and help you work out what your home needs. Your shopping list includes details they can check before speaking with you.

Keep a brief plain-language plan summary. Put technical specifications in expandable **Details for your installer**, and include them in the PDF. Preserve warnings but replace “Professional design review still required” with:

**Ask a qualified person to check your plan before installation.**

Large button: **Find installation help**.

Open a separate accessible dialog or dedicated view. Keep the shopping list intact when users close it or return. Title the new view **Find help with your solar system**.

This is a proposed hackathon feature with a demonstrable interface, not an already-connected worldwide volunteer network.

### Help choices

- **Apply for free help** — “See whether an organization or volunteer program can help with your installation. Availability and eligibility depend on the program.”
- **Explore lower-cost help** — “Find providers offering reduced-cost support. Check the price and what is included.”

Put free help first. Do not promise free support, worldwide coverage, eligibility, the lowest price or a volunteer assignment. Only display organizations, service areas, charges and application links that have been verified or supplied. With no verified directory, show **No verified programs have been added for your area yet** and allow a clearly labeled sample application preview. Do not fabricate real-looking recipients.

### Application prototype

Use a short, step-by-step form with simple labels for:

- Name and preferred contact method.
- Location/address needed to check the service area.
- Number of people living in the home.
- Monthly household income, preferably a range and with “Prefer not to say” for the demo.
- A short description of the living situation and help needed.
- Selected organization/program when a real recipient exists.
- The shopping checklist attachment and plan reference, visible before submission.

Avoid asking for identity documents or bank details. Clearly state why each sensitive field is requested. In demo mode, encourage fictional answers and keep application data in memory rather than persisting precise addresses/income in browser storage or analytics. Keep the household's normal planning data separate.

Add **Review my application** before the final action. Show the exact named recipient, the answers to be shared and a preview of the attached shopping list. Require an explicit unticked consent checkbox:

> I agree to share these application details and my shopping list with {organization name} so they can contact me about help.

A real **Send application** action is enabled only when there is a configured, authorized recipient and a working secure submission service. It must send the selected plan snapshot/PDF and technical details to that recipient, not just show a success animation. Record a reference and a truthful submission status; handle failure without claiming delivery or losing the user's in-memory draft. Prevent duplicate sends.

Without a configured service, implement **Preview sample application** and show **Demo only — nothing has been sent**. Do not use fake “Submitted” states, active fake contact buttons or automatically email anyone. Connecting real organizations and their secure receiving workflow is a separate integration dependency, not something to pretend exists in this page update.

For the proposed receiving side, specify that an authorized organization sees the application, shared plan snapshot, PDF and contact preference together so a qualified reviewer can prepare before contacting the household. Access must be restricted to the selected recipient's authorized staff; do not expose applicant income/address publicly or broadcast applications worldwide. A full organization portal, matching algorithm or scholarship decision engine is not required for this prototype.

## 15. Make the Monitoring invitation clear

Replace the current invitation with:

**Want to see how solar monitoring works?**

> Explore an example of solar power, home electricity use and battery charge over time. This demo uses a separate example system, so its readings will not change to match your shopping list.

Button: **See the solar monitoring demo**.

Use the existing Monitoring route and preserve the current shopping plan. Do not label the fixed demo as “your system” or imply that these are predictions for the selected build. Keep the monitoring data and calculations unchanged in this update.

## 16. Additional Scenario B and Step 4 acceptance checks

- ₱150,000 budget with the ₱143,000 valid choice proceeds to Step 4 and shows ₱7,000 remaining. Other over-budget choices remain blocked.
- Active assumptions survive navigation: with the latest screenshot's 9-hour sunlight assumption and 600-watt load, the same example shows 583.2 kilowatt-hours per month and approximately 6.1 hours of backup. Label the sunlight input as a demo assumption, not a local forecast.
- The 8-hour backup goal shortfall remains visible; do not call the system a complete match to all household goals merely because it is within budget.
- No purchase-status dropdowns or received-count progress appear. Selected parts and legacy data are not silently erased.
- Change my parts opens the selected system for editing; canceling does not corrupt the saved plan.
- PDF download produces a valid, legible PDF with matching totals, actual specifications and warnings; it is labeled a planning estimate rather than a paid receipt.
- Appliance illustrations use explicit example assumptions and the correct usable-energy calculation; each appliance-alone estimate is labeled as separate. Missing starting-power data remains unverified.
- Shop contacts are either verified working links or honest demo empty states.
- Find installation help opens and closes accessibly, preserving the plan. Demo application preview never sends or claims to send anything.
- A future connected submission requires recipient selection, explicit consent and successful delivery before a sent confirmation; its plan snapshot matches the reviewed attachment.
- Monitoring opens the existing fixed demo and clearly distinguishes it from the chosen shopping system.

This revision expands the scope of this same 04 file to include Step 4 and the support-application prototype; it supersedes earlier wording that excluded a checklist redesign. It requests implementation instructions only here, not sending applications or contacting providers during prompt preparation.
