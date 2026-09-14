# Solar Builder — Step 5 Monitoring update prompt

Update the Monitoring page using the supplied screenshots. Preserve the existing demo dataset, calculations, playback behavior and routes. Change the presentation into an accessible learning experience with simple English, large text, illustrations and clear stories about the numbers. This is a prompt for implementation, not a request to replace the data with invented readings.

## 1. Heading and introduction

Make STEP 5 the same visual size as Monitoring, with green emphasis. Keep Monitoring as the main heading. Preserve navigation and the demo badge.

Replace the technical introduction with:

> See how a solar system powers a home through the day.

Use three short bullets below:

- This example uses **Balance cost and power — Component choice 2**.
- The readings are made up for learning. Choosing different parts in your shopping list will not change this example.
- All times shown are Philippine time.

Remove SYS001, C2, seeded, telemetry and the Asia/Manila identifier from the main user-facing description. Keep identifiers and the actual Asia/Manila time-zone handling internally. Do not refer to this as the visitor's installed system or promise that their chosen equipment will produce these readings. Do not imply United Nations endorsement or affiliation.

## 2. Readable design throughout

Use body text around 16–18 pixels, secondary text at least 14 pixels and touch targets at least 44 pixels high. Keep the existing green, navy and white design. Give every icon a text label; do not use color as the only status cue. Stack cards naturally on mobile.

Use full words first: power, electricity used, battery charge and electricity company. Explain units alongside values rather than hiding all explanations in tooltips. Kilowatts measure power at a time; kilowatt-hours measure energy over time. Never write “kilowatts per hour”. Do not display unexplained SOC, DC, AC, bus, load, yield, import or export as primary labels.

Use progressive disclosure: visible plain-English explanations first, optional technical details for people who want them. Keep meaningful limitations short and close to the relevant result.

## 3. Explain the example equipment in practical terms

Heading: **Meet the system in this example**

Use three large illustrated cards with the actual fixed installation values:

| Card | Main value | Plain-English explanation |
| --- | --- | --- |
| Solar panels | 8 panels · 4.4 kilowatts-peak in total | These panels collect sunlight and turn it into electricity. This is their rated size, not the power they produce all day. |
| Inverter | 5 kilowatts | Changes electricity from the panels and battery into the kind home appliances use. This rating describes power it can handle, not how much electricity it makes each day. |
| Battery storage | 10.24 kilowatt-hours | Stores electricity to use later. How long it lasts depends on its charge and the appliances running. |

Keep model names and exact specifications in **See the equipment details**. Explain kilowatts-peak as the panel rating under test conditions.

Add short **What does this mean at home?** examples:

- Panels: **More sunlight usually means more solar power. After sunset, the panels stop producing power.** Use sun/panel illustrations.
- Inverter: **Several appliances can run together only if their combined power and starting needs fit the equipment's limits.** Do not imply every 5-kilowatt combination is approved; retain the actual catalog restrictions.
- Battery: **Like a phone battery, its charge goes up when it stores electricity and down when it supplies electricity.** Use a large labeled battery graphic driven by the actual displayed charge.

An optional energy-only illustration may say: **Using 1 kilowatt for 1 hour uses 1 kilowatt-hour.** Do not divide the full 10.24 storage rating by an appliance load and promise that runtime. The demo keeps a reserve, limits maximum charge and includes losses. If displaying a runtime example, use the existing usable-energy model and clearly label its assumed load, starting charge and limitations. Do not substitute that hypothetical runtime for the recorded demo behavior.

Use lightweight SVG/CSS animation rather than requiring a video download. Add Play/Pause or short one-time motion, respect reduced-motion preferences and provide the same explanation without movement. Never invent a real video source or autoplay external videos.

## 4. Day selector and playback

Rename the tabs:

- **Watch one day**
- **See the week**

Date label: **Choose a day**. Keep only dates available in the dataset. Do not label September 9 as “Today” unless it actually is today in Philippine time. A historical demo date should be shown honestly.

Replace “Replay simulated readings” with:

**Watch the example day unfold**

Optional single-line description:

> Press Play to see how electricity moves through this home. The example runs faster than real time.

Controls: **Play**, **Pause**, **Start again**. Start again replaces the visible Reset label while retaining its reset action. Keep a readable progress bar and **Showing the day up to {time}**.

Keep the existing pace internally: each second reveals the next five-minute record. Users do not need to see “row”, “interval count” or “cards use revealed rows”. All selected-day totals and charts must continue to use only the revealed records.

Before playback starts, show **Press Play to begin**, accumulated energy values of zero and **Not shown yet** for battery charge and power-flow values without a revealed record. Do not invent a 0% battery or display final-day values as though playback had started.

Pause freezes the record pointer, flow, chart and totals. Start again clears revealed data and returns to the initial state. Date changes must reset the selected-day replay coherently and never mix records across days. Preserve existing full-week behavior separately from partial-day playback.

## 5. Rewrite the selected-day summary cards

Heading: **What has happened so far?**

| Old label | New label | Description |
| --- | --- | --- |
| Solar energy so far / solar bus yield | Electricity from the solar panels | Solar electricity available after conversion, during the part of the day shown so far. |
| Household energy so far / load | Electricity used by the home | Electricity the home's appliances have used so far. |
| Grid import so far | Electricity taken from the power company | Extra electricity the home needed from its electricity supplier. |
| Battery SOC / battery charge | How full is the battery? | The battery's charge at the latest time shown. |

Show energy units as **kilowatt-hours** beneath the main numbers if the full label does not fit inline. Show charge with a large percentage and a battery-fill illustration. Do not rename imported electricity “money spent” or solar generation “savings”.

Show **Electricity sent to the power company** as a readable secondary card or line, based on actual export energy. Explain: **Electricity sent out of the home instead of being used or stored here.** Do not claim it earned money or bill credits.

Use a small reminder: **A 100-watt appliance running for 10 hours uses 1 kilowatt-hour.** Label this a unit example rather than an appliance guarantee.

## 6. Replace the cross-shaped technical flow with a visual journey

Heading: **Where is the electricity going?**

Use illustrated stations with clear names: sunshine and solar panels, inverter, home, battery and electricity company. Main visual path on desktop: panels → inverter → home. Position battery on a clearly labeled lower storage path connected to the inverter, and the electricity company on its own side/lower connection. On mobile, use a top-to-bottom layout with short labeled branches. Avoid a dense cross-shaped engineering diagram.

Do not draw a mandatory series route panels → inverter → battery → home. Solar can power the home without first charging the battery. The battery and electricity-company connections must support both directions when the data warrants them.

Use these labels:

- **Solar panels:** “Turns sunlight into electricity.”
- **Inverter:** “Makes the electricity suitable for home appliances.”
- **Home:** “Electricity your appliances are using.”
- **Battery:** “Stores electricity for later.”
- **Electricity company:** “Supplies extra electricity when needed.”

The panels already produce electricity; do not say the inverter turns sunlight into electricity or use “magic” as the technical explanation.

Animate arrows only on active paths, at the actual replay time:

- Solar supplying the home.
- Battery storing electricity or supplying electricity.
- Electricity company supplying electricity or receiving electricity.

Drive arrow directions and labels from the existing source values, not from time of day alone. Connected does not mean power is flowing. At zero flow, show a quiet line and **No electricity moving on this connection**. Use **Power company connection unavailable** only if the dataset actually records that state.

If the data does not distinguish which source charges the battery or supplies the home when sources overlap, show measured connections to the inverter and avoid attributing exact source-to-destination amounts. Do not invent source allocation.

Offer a short automatically generated sentence based only on the current data, for example:

- “The panels are producing electricity and the battery is charging.”
- “The battery is supplying electricity while the panels are not producing power.”
- “The home is taking extra electricity from the power company.”

Do not infer weather, faults, appliance identity or causes absent from the data. Do not label zero solar output a fault.

Show **Around {time}** and a small **Average power for the five minutes shown** note. These are interval averages, not live instantaneous readings. Use watts for small values where helpful, such as 300 watts instead of 0.30 kilowatts, with consistent conversion. Keep energy totals separate from these power values.

Hide raw bus equations, signed battery conventions and energy-balance residuals from the main view. Preserve them in optional **Technical details** and keep the existing balance checks working. The diagram is an educational illustration, not wiring instructions.

## 7. Replace the crowded chart with two simple views

Keep charts, but separate different quantities. Do not combine battery percentage and power on dual axes in the default view.

### Chart A: Electricity through the day

Default to two labeled lines:

- **Power from solar panels**.
- **Power used by the home**.

Time runs left to right with readable morning/noon/evening labels where useful. Axis label: **Power in kilowatts**. Use distinct line styles as well as colors and direct labels or a readable legend. Provide optional switches for **Power from the electricity company** and **Power sent to the electricity company**. Put advanced battery power traces in details rather than displaying a signed negative series to beginners.

Description:

> Compare when the panels produce power with when the home uses it.

### Chart B: Battery through the day

A separate single-axis chart from 0% to 100%, titled **How full was the battery?**

Description:

> The line rises when the battery charges and falls when it supplies electricity.

Keep the measured battery state values. Explain the demo's 20% reserve and 95% upper setting in optional details; do not suggest these percentages are the physical limits of every battery.

Both charts respect playback and stop at the revealed time. Do not draw unrevealed future values or drop the line to zero after the last revealed point. Show missing readings as gaps rather than zeros. Tooltips and an accessible text view must use the same plain-English labels.

## 8. Turn the weekly table into a visual weekly story

Heading: **Your example week at a glance**

Show the exact date range and **Example readings · Philippine time**. This is the fixed demo home's week, not the visitor's own system history.

Summary cards:

- **Solar electricity this week**.
- **Electricity used by the home**.
- **Electricity taken from the power company**.
- **Battery charge during the week**, for example “Lowest 20% · Highest 95%”.

Show **Electricity sent to the power company** visibly as well. Explain that a charge range is not energy and not an average.

Replace the default wide seven-day numerical table with one card per day, or a compact chart plus expandable daily cards. Each day has:

- A clear date.
- Two comparable bars on the same energy scale: **From solar panels** and **Used by the home**.
- A labeled amount **From the power company**.
- A short optional **Sent to the power company** line.
- An expandable **Battery activity** section showing **Electricity stored in the battery** and **Electricity supplied by the battery**.

Always show the numeric amount with its unit beside the bar. Do not stretch each bar to its own arbitrary maximum or rely on colors without labels. Do not add solar generation and battery discharge together and label the sum “solar produced”; storage reuses energy already counted.

Under Battery activity explain:

> The battery stores electricity at one time and supplies it later. Some energy is lost during storage and use.

Important distinction: **Electricity stored in the battery** is energy over a day; **How full is the battery?** is a percentage at a time. Never substitute one for the other.

Generate at most one short factual daily insight, such as **The home also needed {amount} kilowatt-hours from the power company.** Use actual values. Do not infer which appliances ran or claim financial savings. More total daily solar energy than household use does not mean there was no need for the power company: timing and storage matter.

Keep **Show all daily numbers** as an optional accessible table for users who want detail. Rename columns using the same plain wording. Move “vs. summary”, “matches”, formulas, record counts and reconciliation internals to technical details. Preserve the validation internally and count each energy source once, not once from readings plus again from the summary file.

The full-week view may show all seven completed demo days independently of the one-day replay. Clearly label this **Full example week**, so users do not confuse it with “so far” totals.

## 9. Simplify the estimate comparison

Move “Expected vs. simulated solar energy” below the weekly story inside an optional **Why can an estimate look different?** disclosure. It should not compete with the main household information.

Use:

- **Simple planning estimate**.
- **Solar electricity in this example week**.
- **Difference**.

Explanation:

> A planning estimate uses simple assumptions. This example uses a different set of made-up readings, so the totals can differ. This comparison does not prove that equipment is working well or badly.

If the existing reference comparison still uses the same seven days and original assumptions, the screenshot's rounded values are 110.9 kilowatt-hours for the estimate, 176.3 for the example and 65.4 more in the example. Calculate from actual active reference inputs; never hardcode the screenshot values or silently replace the reference with edited household assumptions.

Show an optional two-bar comparison with the same scale, or three simple numbers. Do not use profit arrows, success badges or fault warnings. This is not a money-savings calculation, a measured forecast accuracy score or an investment promise. Put the underlying formula in technical details only.

## 10. Preserve the data meaning and demo boundaries

- Keep the fixed installation behind Component choice 2, including its 4.4 kilowatts-peak panels, 5-kilowatt inverter and 10.24-kilowatt-hour battery, unless the actual fixed dataset says otherwise.
- Changing My Household, a custom build or a checklist must not change these monitoring readings.
- Use the existing post-conversion solar series for the primary solar-energy cards, flow and charts consistently. Keep pre-conversion energy separate in details; do not silently relabel or add both together.
- Preserve actual interval durations, date bucketing and energy integration. Explain units simply without changing their calculation.
- Treat the final 24:00 boundary carefully: display “End of day” or the correct midnight boundary while retaining the original local-day aggregation. Do not move the final interval to the wrong day.
- Keep technical assumptions accessible but out of the main educational journey.
- No unverified claims about bill savings, bill credits, poverty thresholds, real equipment health or the visitor's future output.

## 11. Acceptance checks

- STEP 5 is as prominent as Monitoring; no SYS001, C2, SOC or bus appears as unexplained main copy.
- Equipment cards explain practical meaning and preserve units.
- Playback, pause, start again and date changes stay coherent across totals, battery state, flow and both charts. The initial battery state is unknown until a reading is revealed.
- Flow arrows reflect actual direction and activity; solar can reach the home without passing through the battery. Zero-flow and unavailable states are distinct.
- Default charts separate power from battery percentage and do not reveal future records.
- Weekly cards and the optional table agree with the existing daily summaries. No energy is double-counted.
- For the same seven-day dataset in the screenshots, rounded full-week values remain 176.30 kilowatt-hours solar, 124.99 household use, 10.19 taken from the electricity company and 59.64 sent out; battery range remains 20–95%. Treat these as regression examples, not interface constants.
- The optional comparison remains correctly scoped to seven full days and the reference assumptions; it does not imply money saved.
- Unit conversion, negative/positive battery direction, midnight boundaries and missing readings remain correct.
- Check keyboard navigation, readable mobile layouts, reduced-motion mode, color-independent labels and chart text alternatives.
- Keep the selected shopping system and all other page behavior intact. This is a standalone Monitoring prompt following the updated 04 Compare/My Checklist file.
