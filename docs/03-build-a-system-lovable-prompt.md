# Solar Builder — Build a System page update prompt

Update only Step 2, “Build a System”, using the supplied screenshots as the reference. This file continues the page-by-page updates for the existing Solar Builder demo. Implement the changes below with simple English and accessible visual explanations.

## 1. Preserve the app and improve readability

Keep the existing logo, green/navy/white design, demo badges, separate navigation tabs, routes, saved household needs, catalog and working calculations. Preserve preset identities internally even when changing their display names.

Make STEP 2 the same visual size as “Build a System”, with green emphasis. Keep Build a System as the main page heading.

Replace the subtitle with:

> Choose the parts for your solar system. We will help you check how they fit together and show the estimated cost as you make changes.

Add a readable secondary note:

> This is a demo. The products, shops, prices and stock shown here are examples.

Use approximately 16–18 px for body text and form values, at least 14 px for secondary information, and comfortable line spacing. Make section headings and choice buttons clearly larger than they are now. Use touch targets at least 44 px high. Avoid pale, tiny text and unexplained abbreviations. Do not make the page wider than the viewport.

## 2. Make starting choices prominent

Replace “Start from a preset” with:

**What matters most to you?**

Supporting text:

> Start with one of these examples. You can change the parts below.

Show three large selectable cards, with a clear selected state:

| Existing preset | New visible title | Description |
| --- | --- | --- |
| Budget | Spend less | Start with the lowest-cost example of these three choices. It may still cost more than your budget. |
| Balanced | Balance cost and power | Start with a middle option for price and solar power. |
| More Solar | Get more solar power | Start with more solar panels. Check the total cost and battery backup below. |

Keep their existing component selections and calculations. Check these relative descriptions against the actual three presets; if their ordering differs, use accurate descriptions rather than changing data to fit the wording. Do not imply that More Solar necessarily gives longer battery backup or that Spend less always meets the household budget.

## 3. Add a visual learning guide before the part selectors

Heading: **Meet the parts of your solar system**

Introduction:

> These three parts work together to bring solar power into your home.

Use three large illustrated cards:

| Part | Exact explanation |
| --- | --- |
| Solar panels | Collect sunlight and turn it into electricity. More panels can collect more energy when there is enough sunlight. |
| Inverter | Changes electricity from the panels and battery into the kind your home appliances use. In this hybrid demo, it also manages power going to and from the battery. |
| Battery | Stores electricity for later, such as at night or during a power cut. Its size and charge affect how long it can run your appliances. |

Below the cards, add a small animated illustration using accessible SVG/CSS or existing project icons. Show sunlight reaching panels, electricity moving through the inverter to a house, and a battery connected to the inverter. Include the electricity company connection to reflect the hybrid demo.

Provide two clearly labeled states:

- **Sunny daytime:** Illustrate panels supplying the home through the inverter and charging the battery when there is spare solar power.
- **During a power cut:** Illustrate the battery supplying selected home appliances through the inverter. Show the electricity-company connection inactive. This example assumes a suitable backup setup; the animation does not establish that the chosen build is approved for backup use.

Use a brief play-once animation or a Play/Pause control. Respect reduced-motion preferences and provide a static equivalent with labeled arrows. Do not rely on movement or color alone to explain the system. This is an educational illustration, not live monitoring, an electrical wiring diagram or an installation tutorial. Do not add fabricated live readings.

Caption:

> A simple example of how a hybrid system works. The parts you choose and the way they are installed affect what your home can use.

## 4. Make “Your parts” understandable

Replace the visible sentence about a series string and an MPPT input with:

> Choose a model and how many you need. We will update the price and check whether the parts can work together in this demo.

Preserve the existing single-string, one-MPPT calculation model internally. Put that technical limitation in an expandable “Technical details” area for users who need it; do not imply that the simplified model checks every possible wiring arrangement.

Keep solar panel model and quantity, inverter model, and battery model and quantity. Use friendly labels:

- Solar panel model
- Number of panels
- Inverter model
- Battery model
- Number of batteries

Show friendly model names and useful sizes first. Move dense specifications such as voltage limits and MPPT ranges into expandable technical details near the component. Keep all underlying values and validation.

### Shop offers for each part

Make the supplier price and stock information larger and easy to scan. Show all existing offers for the selected model, not just the cheapest offer.

Use this layout beneath each selected component:

| Shop | Price for one | Available |
| --- | --- | --- |
| Actual demo shop name from catalog | Actual demo price | Actual stock count, or “Sold out” |

Above the offer table, show the offer actually used in the estimate:

> Price used: {shop name} — ₱{unit price} each

If supported by the existing offer-selection logic, explain it accurately as:

> We use the lowest-priced available offer in the demo catalog.

Keep pricing selection rules consistent with quantity and stock validation. Do not call an offer sufficient for the order when it has fewer units than requested. Show “Only {count} available — you selected {quantity}” when appropriate. Never treat a missing offer as a zero-price offer or silently split orders across shops unless the existing app supports that behavior.

Show Demo Solar Shop B as “Sold out” only if that model’s offer actually has zero stock in the demo data. Do not invent stock counts, prices or shop offers for presentation. If a second offer does not exist, do not fabricate one. For no available offers, show “No stock available for this part” and preserve the relevant failed check.

Keep the distinction between fictional demo shops and any real help providers elsewhere on the page.

### Replace “Allowance”

Section heading: **Other costs to plan for**

Field label: **Extra equipment and installation budget**

Helper text:

> Set aside money for items such as roof supports, cables, safety equipment and installation help. This amount is added to the cost of your panels, inverter and battery.

Small note:

> This is a sample amount, not a quote from an installer. The real cost may be different.

Keep the existing editable peso amount and calculation. Do not count it twice or imply that a complete itemized installation package is included.

## 5. Rewrite the result cards and use useful icons

Keep live calculations. Use simple icons beside labels: peso for cost, wallet for budget, panel for panel size, battery for storage, sun/calendar for monthly energy and clock for backup time. Pair every icon with readable text.

| Existing card | New label | Description |
| --- | --- | --- |
| Total estimated cost | Estimated total cost | The cost of your selected parts, plus the extra amount for equipment and installation. |
| Remaining budget | Money left in your budget | Your budget minus the estimated total cost. |
| Solar capacity | Total solar panel size | The combined rated size of your panels. Actual power changes with sunlight and weather. |
| Nominal battery | Total battery storage | The battery’s stated storage size. Some energy is kept in reserve or lost during use, so you cannot use all of this amount. |
| Est. monthly generation | Solar electricity in a month | An estimate of what these panels could produce in a month using the demo’s sunlight settings. Actual output can be different. |
| Est. backup duration | Estimated battery backup time | About how long the battery could run the appliances you listed in My Household, using the demo’s battery settings. |

For over-budget builds, change the budget card to **Over your budget by** and show a positive currency amount, for example **₱93,000**, rather than only displaying a negative number. For an exact match, show **Matches your budget** and ₱0 left.

Keep units visible and explained: kWp for panel size, kWh for storage and monthly electricity, hours for backup. Include short inline help or refer to the earlier learning guide without forcing users to leave the page.

Replace visible equations with short explanations. Keep equations and assumptions in an optional “How this estimate is calculated” disclosure. For panel size, “6 panels × 450 W each” is useful and may remain as a plain example based on the actual selection.

For backup duration, show a readable goal comparison:

- “About {estimated hours} hours — shorter than your {goal hours}-hour goal.”
- Or “About {estimated hours} hours — meets your {goal hours}-hour goal in this demo.”

A labeled horizontal bar may compare estimated hours with the goal. Keep the numeric values visible. Do not use a battery charge gauge to represent hours or nominal storage size.

Retain the battery calculation assumptions, accessible in the disclosure. For the screenshot’s current model these include 95% starting charge, 20% reserve, 95% discharge efficiency and constant appliance load. Do not promise guaranteed runtime.

Rewrite the household comparison strip:

> Based on your electricity use, the demo suggests about {required size} kWp of panels. You have chosen {selected size} kWp.

Keep a clear **Change my household needs** link to the existing My Household route.

## 6. Make component checks readable

Replace “Preliminary compatibility” with:

**Do these parts fit together?**

Introduction:

> We check a few basic limits to help you spot problems. These demo checks do not replace an installer’s review.

Use **Looks OK in this demo**, **Needs changing**, or **Not checked** as appropriate. Pair status icons with words. Keep the actual pass/fail/unknown logic internally. Do not turn unknown data into a passing result.

Suggested mapping for each existing check:

| Existing check | Simple visible wording |
| --- | --- |
| Component quantities | Do you have the right number of parts? |
| Solar capacity | Can the inverter handle this amount of solar panels? |
| Solar operating voltage | Do the panels work within the inverter’s voltage range? |
| Solar open-circuit voltage | Is the panel voltage below the inverter’s demo limit? |
| Solar current | Is the panel current within the inverter’s limit? |
| MPPT count | Does the inverter have the solar input this demo setup needs? |
| Battery voltage | Does the battery’s voltage match the inverter? |
| Battery communication | Can the battery and inverter communicate in this demo? |
| Battery quantity | Can this inverter support this number of batteries? |
| Stock | Are enough parts available? |

For each item, show a short result and, for failures, a specific corrective action based on the actual failed condition. Keep raw technical values in an expandable details area. Do not invent product compatibility from brand names or use fictional communication-family matches as manufacturer approval.

Show budget separately:

**Does it fit your budget?**

Examples:

- “Within your budget — ₱{amount} left.”
- “Over your budget by ₱{amount}. Try a lower-cost choice, change your parts, or review your budget.”

A budget problem is different from a parts mismatch. If parts checks pass but the budget fails, the overall summary must visibly say both. Do not show one prominent green success that hides an over-budget result.

## 7. Replace the professional-review block with practical help

Heading: **Need help with your next step?**

Copy:

> You can choose and compare parts yourself. Before buying or installing them, ask a qualified solar installer or electrician to check the complete setup for your home.

Supporting text:

> They can check your roof, wiring, safety equipment and whether the battery and inverter are suitable together.

Offer three clear resource areas:

1. **Learn the basics** — Beginner explanations and videos about choosing a system and understanding its parts.
2. **Find local installation help** — A place to find verified installers or electricians serving the selected location.
3. **Community support** — Verified organizations or community programs that offer solar advice, training or assistance.

Use real resource links only when supplied or verified. Do not invent organizations, volunteers, contacts, local coverage, availability or endorsements. This prompt does not supply a verified directory. If there is no verified resource data, show a clearly labeled empty state such as “Local contacts have not been added to this demo yet”, not fictional provider cards presented as real contacts.

When verified contacts become available, show provider name, area served, type of help, source and a working website/contact link. Label any example contact explicitly “Demo contact” and do not make it appear contactable. Do not create a working contact form that silently discards messages. Do not send messages or share household details automatically.

Keep this section useful without turning it into a new marketplace or booking system. Learning resources should explain planning; do not present an unreviewed wiring video as installation approval.

## 8. Put both next-step choices together at the bottom

Remove the small “Compare presets” button from the top-right of the page. Keep the main Compare navigation tab.

After the results, checks and help section, add a full-width section:

**What would you like to do next?**

Place two clearly separated choice panels side by side on desktop and stacked on mobile. Use the same width and readable spacing; make the checklist choice the green primary action.

### Left choice

**Still deciding?**

> Compare the example systems before you choose.

Button: **Compare options**

Action: open the existing Compare page. Preserve the current custom build so returning does not reset it. Do not imply the Compare page compares arbitrary custom builds if it currently compares only presets.

### Right choice

**Happy with this system?**

> Save these parts to your shopping checklist.

Button: **Use this system for my checklist**

On click, show a short confirmation with the actual selected parts, quantities, estimated total and budget status:

**Use these parts for your checklist?**

> You can review the list before buying anything. This does not place an order.

Actions:

- **Keep editing**
- **Yes, create my checklist**

On confirmation, preserve the existing save/selection behavior and open My Checklist with these exact parts and quantities. If an existing checklist will be replaced or statuses reset, state the actual effect before confirmation; do not silently discard progress. Prevent duplicate saves from repeated clicks.

Preserve existing blockers for invalid quantities, unavailable offers or failed component checks. Explain why an action is blocked and how to fix it; never label a failed build as approved. If the existing app permits saving an over-budget draft, show the over-budget amount explicitly in the confirmation rather than treating it as a component failure or silently raising the budget.

## 9. Verification and scope

- Preserve the current calculations, catalog identity and state flow across My Household, Build a System, Compare and My Checklist.
- Verify larger text, touch targets, readable offer tables and a clear mobile flow.
- Verify the educational illustration with reduced motion and without animation.
- Check that every displayed offer and stock status comes from actual demo data.
- Verify unit prices, quantities, stock sufficiency and the equipment/installation amount feed the same total used by the checklist.
- With the screenshot’s unchanged Budget selection and assumptions, results should remain: ₱143,000 total, ₱93,000 over a ₱50,000 budget, 2.70 kWp panels, 5.12 kWh stated battery storage, 291.6 kWh estimated monthly electricity and approximately 7.3 hours of backup. Use this as a regression example, not hardcoded interface content.
- Check at least one failed component condition and an over-budget condition: each must show a clear, different explanation.
- Confirm preset selection and custom changes update the results accurately without silently changing household needs.
- Confirm both bottom actions work, the confirmation can be canceled, and a saved checklist matches the chosen system.
- Keep demo limitations readable. No claim that a passed demo check certifies an installation.
- Do not redesign or update the other pages as part of this task, except shared display-label plumbing strictly needed to preserve existing identities and navigation.
