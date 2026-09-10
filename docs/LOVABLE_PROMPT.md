# Solar Builder — Lovable Prototype Instructions

## 1. Project overview

Build a working hackathon prototype called **Solar Builder** for **one Philippine household**.

This is **Part 2 of a wider clean-energy project**. Build only this part.

The app helps a household:

1. Enter its electricity needs and budget.
2. Choose and customize solar equipment.
3. Compare different setups.
4. Create a shopping checklist.
5. Explore simulated monitoring after installation.

Think of a custom PC builder, where users select compatible parts, but use original solar-focused branding and interface design.

## 2. Demo data

Use **`demo_seed.json`** as the main source of data.

If the matching CSV files are supplied instead, use those. These are alternative ways to import the same dataset; do not import both as additional records.

### Data rules

* Use the supplied catalog prices and monitoring readings.
* Do not invent replacement prices or dashboard numbers.
* All products, suppliers, prices and readings are fictional.
* Display a compact **“Demo · synthetic data”** label throughout the app.
* Do not use personal names, addresses or account details from reference screenshots.

### Supplied tables

| Table               | Purpose                                |
| ------------------- | -------------------------------------- |
| `households`        | Household needs and budget             |
| `panels`            | Solar panel models                     |
| `inverters`         | Inverter models                        |
| `batteries`         | Battery models                         |
| `suppliers`         | Fictional suppliers                    |
| `listings`          | Supplier prices and availability       |
| `configurations`    | Proposed solar setups                  |
| `installed_systems` | Fixed demo installation                |
| `telemetry`         | Five-minute monitoring readings        |
| `daily_summary`     | Daily totals calculated from telemetry |

Read **`START_HERE.md`**, if attached, for the full data definitions and calculation rules.

### Units and timestamps

* `_kw` means power in kilowatts.
* `_kwh` means energy in kilowatt-hours.
* `_php` means Philippine pesos.
* Store timestamps using UTC.
* Display and group dates using **Asia/Manila**.
* Each telemetry row is uniquely identified by `(system_id, timestamp_utc)`.
* `daily_summary` contains totals derived from telemetry. Do not add these totals to telemetry totals again.

## 3. Design and navigation

Create a responsive app for desktop and mobile.

### Visual style

| Element        | Style                                   |
| -------------- | --------------------------------------- |
| Background     | Clean white                             |
| Main text      | Dark navy                               |
| Main accents   | Solar green                             |
| Household load | Warm yellow                             |
| Battery status | Blue                                    |
| Layout         | Readable cards with comfortable spacing |

Use plain English. Include short explanations of:

* **kW:** How much power is being produced or used.
* **kWh:** How much electricity is produced or used over time.
* **Battery SOC:** The battery’s estimated charge percentage.

### Main navigation

1. My Household
2. Build a System
3. Compare
4. My Checklist
5. Monitoring

## 4. Backend and saved progress

Implement the frontend and the simplest managed backend/database available in this project.

### Required behaviour

* Import the seed data using the supplied IDs.
* Repeated imports must not create duplicate records.
* Store saved builds and shopping checklist progress.
* Keep each visitor’s changes separate by browser or session.
* Do not allow public visitors to overwrite one shared household record.
* Build working interactions connected to the supplied data.

If a backend cannot be provisioned, a **localStorage demo fallback** is acceptable. State this limitation in the completion message.

No paid APIs or real hardware connections are needed.

## 5. Page: My Household

Preload household **HH001** with these values:

| Setting                         | Default             | Editable?           |
| ------------------------------- | ------------------- | ------------------- |
| Location                        | Laguna, Philippines | Fixed for this demo |
| Monthly electricity consumption | 450 kWh             | Yes                 |
| Budget                          | ₱250,000            | Yes                 |
| System type                     | Hybrid              | Hybrid only         |
| Critical load                   | 0.5 kW              | Yes                 |
| Backup goal                     | 8 hours             | Yes                 |

Explain **critical load** as the combined power needed by essential appliances during backup.

On-grid and Off-grid may appear as **“future option”**, but must not behave as working features.

### Editable estimate assumptions

| Assumption             | Default |
| ---------------------- | ------: |
| Peak sun hours per day |     4.5 |
| Performance ratio      |     0.8 |
| Electricity tariff     | ₱12/kWh |

Label these as illustrative demo assumptions.

## 6. Page: Build a System

Allow the user to choose:

* Solar panel model and quantity.
* Inverter model.
* Battery model and quantity.
* Allowance for other equipment and installation.

Use the supplied catalog models and supplier offers.

### Show these results

Update results immediately when selections change:

* Total estimated cost.
* Solar capacity in kWp.
* Nominal battery capacity in kWh.
* Remaining budget.
* Estimated monthly generation.
* Estimated backup hours.
* Preliminary compatibility results with explanations.

Do not include actual checkout.

### Pricing rules

For each component, choose the lowest-priced seeded offer that is in stock and has enough units.

**Total cost =**

* Panel quantity × panel offer price
* Plus inverter offer price
* Plus battery quantity × battery offer price
* Plus other equipment/installation allowance

The original seeded configurations must have these totals:

| Configuration |    Total |
| ------------- | -------: |
| Budget        | ₱143,000 |
| Balanced      | ₱227,000 |
| More Solar    | ₱245,000 |

Keep the allowance visible and editable. Explain that it is an illustrative amount, not a supplier quote or an itemized equipment list.

### Estimate formulas

**Required solar capacity in kWp**

`(monthly consumption in kWh / 30) / (peak sun hours × performance ratio)`

**Estimated monthly generation in kWh**

`selected solar kWp × peak sun hours × performance ratio × 30`

**Estimated backup duration in hours**

`nominal battery kWh × 0.75 × 0.95 / critical load kW`

The backup formula assumes:

* Battery starts at 95% charge.
* 20% remains as reserve.
* Discharge efficiency is 95%.
* Critical load remains constant.

Explain the assumptions and reject nonpositive calculation inputs.

Do not promise bill savings, ROI, off-grid independence or guaranteed backup time.

### Preliminary compatibility checks

Run all of these checks:

| Check                      | Rule                                                                                          |
| -------------------------- | --------------------------------------------------------------------------------------------- |
| Component quantities       | Positive whole numbers                                                                        |
| Solar capacity             | PV kWp ≤ inverter maximum PV capacity                                                         |
| Solar operating voltage    | `series_count × Vmp` is within the MPPT range                                                 |
| Solar open-circuit voltage | `series_count × Voc` is below maximum DC voltage                                              |
| Solar current              | `parallel_strings × Imp` and `parallel_strings × Isc` are within the relevant inverter limits |
| MPPT count                 | Used MPPTs do not exceed available MPPTs                                                      |
| Battery voltage            | Battery operating range fits inside the inverter battery range                                |
| Battery communication      | Fictional `bms_family` values match                                                           |
| Battery quantity           | Parallel battery count is supported                                                           |
| Stock                      | Enough units are available                                                                    |
| Budget                     | Total is within the user’s budget                                                             |

For this demo, all panels form **one series string connected to one MPPT**.

Show a warning that temperature-adjusted voltage checks and professional design review are still required, especially near voltage limits.

**Demo High Voltage 10** must fail the battery voltage and BMS checks against both seeded inverters.

Use the wording:

**“Passes preliminary demo checks.”**

Never describe a build as **“certified safe.”**

A failed feasibility check must exclude the build from eligible recommendations. A low price or high ranking score cannot override a failed check.

## 7. Page: Compare

Compare the three seeded configurations side by side.

Show:

* Total cost.
* Solar capacity in kWp.
* Nominal battery capacity in kWh.
* Estimated monthly generation.
* Estimated backup hours at the selected critical load.
* Whether the build is within budget.
* Preliminary compatibility results.

Make the trade-offs easy to understand.

Selecting a configuration should open its shopping checklist.

If no eligible build fits the user’s constraints, say so clearly. Do not silently increase or change the budget.

## 8. Page: My Checklist

Generate a shopping checklist for the selected build.

### Include

* Component names.
* Required quantities.
* Selected fictional suppliers.
* Supplier prices.

Allow each item to have one of these statuses:

* Not purchased
* Ordered
* Received

Save progress for the current browser/session.

Provide a **downloadable shopping CSV**.

### Additional equipment and installation

Show these items as **“scope and quote to confirm”**:

* Mounting.
* Protection equipment.
* Cabling.
* Professional installation.

These are covered only by the illustrative allowance.

Do not invent cable sizes, breaker ratings or real supplier URLs.

### Installation handoff

Provide a summary containing:

* The selected components.
* The quantities.
* Any unresolved design checks.

Do not include electrical wiring tutorials, hardware controls, real bookings, payments or email submissions.

Add a button:

**“Explore demo installed system”**

This opens monitoring for **SYS001**, the seeded Balanced installation.

Marking checklist items as “Received” must not claim that a real system has been installed or commissioned.

## 9. Page: Monitoring

### Fixed demo installation

Monitoring belongs only to **SYS001**, linked to **C2 — Balanced**:

| Equipment    |  Capacity |
| ------------ | --------: |
| Solar panels |   4.4 kWp |
| Inverter     |      5 kW |
| Battery      | 10.24 kWh |

Changing a shopping build must not change which installation these historical readings belong to.

### Dates and data

Use the supplied telemetry:

* September 3–9, 2026.
* 2,016 five-minute intervals.
* Asia/Manila timezone.

Default to **September 9**, at the latest available completed interval.

Provide:

* A local date picker.
* A seven-day view.

Do not default to the current real date and display an empty chart.

Weather data is not supplied, so omit it. Do not show a fake live badge.

### Main dashboard cards

| Card             | Value                                     |
| ---------------- | ----------------------------------------- |
| Solar energy     | Selected-day solar bus yield in kWh       |
| Household energy | Selected-day household consumption in kWh |
| Grid import      | Selected-day imported energy in kWh       |
| Battery charge   | Selected interval-end SOC percentage      |

### Power-flow diagram

Connect:

* Solar.
* Inverter/bus.
* Battery.
* Grid.
* Home.

Use the reference screenshots as inspiration for the information shown.

Use `solar_bus_power_kw` in the diagram so the displayed power flows balance.

Show `solar_dc_power_kw` separately as a clearly labelled detail.

Power values represent the **average during the selected five-minute interval**, not an instantaneous physical reading.

### Charts

Include:

* Solar bus power.
* Household load.
* Grid import and export.
* Battery charging and discharging.
* Battery SOC.

Use:

* A kW axis for power.
* A separate 0–100% axis for SOC.
* Series toggles.
* Readable tooltips.

If using one signed battery series, calculate:

`battery_discharge_bus_kw − battery_charge_bus_kw`

Explain:

* Positive = discharging.
* Negative = charging.

The source data keeps charging and discharging as separate nonnegative values.

### Monitoring calculations

Calculate energy using:

`SUM(power_kw × interval_minutes / 60)`

Group daily results by **Asia/Manila date**.

Rules:

* Never sum kW values and label them as kWh.
* Do not sum SOC percentages.
* Show `battery_soc_end_pct` for the selected interval.
* Read grid status from the selected telemetry row.
* The supplied data has no simultaneous grid import/export or battery charge/discharge.

## 10. Replay simulated readings

Add **Play**, **Pause** and **Reset** controls.

Label this feature:

**“Replay simulated readings.”**

### Playback behaviour

* Advance one five-minute row every second on the selected day.
* Reveal readings progressively.
* Calculate cards using only the rows already revealed.
* Display the interval’s end time as the data coverage time.
* Remember that each row’s timestamp marks the interval’s start.
* Pause freezes playback and totals.
* Reset clears the selected-day replay totals.
* Stop playback at the end of the day.

Do not show full-day energy totals while replay has only revealed part of the day.

## 11. Optional: Expected versus simulated energy

You may add a small comparison card for completed days.

**Rough estimated bus yield in kWh**

`number of full selected days × 4.4 × 4.5 × 0.8`

Compare this with the simulated solar bus energy for exactly the same completed days.

Label it clearly as a **demo estimate**.

Do not:

* Compare seven days of readings with a monthly forecast.
* Diagnose hardware faults.
* Add ROI or financial forecasts.

## 12. Simulation assumptions

The displayed power flows must satisfy:

`solar_bus + battery_discharge_bus + grid_import = load + battery_charge_bus + grid_export`

The supplied simulation assumes:

* Solar DC-to-bus conversion efficiency: 96%.
* Battery charging efficiency: 95%.
* Battery discharging efficiency: 95%.

These battery efficiencies affect changes in stored energy.

Provide a small **“Simulation assumptions”** disclosure. Keep detailed engineering explanations out of the main user journey.

## 13. Acceptance checklist

Before completing the app, verify that:

* [ ] Repeated seed imports do not duplicate rows.
* [ ] The Balanced configuration costs ₱227,000.
* [ ] Balanced monthly generation is 475.2 kWh using default assumptions.
* [ ] Changing quantities updates prices and estimates.
* [ ] Reducing the budget marks affected builds as over budget.
* [ ] Selecting the high-voltage battery shows the explicit mismatch.
* [ ] Selecting a build creates the correct supplier and quantity checklist.
* [ ] Reloading preserves the current session’s choices.
* [ ] Monitoring cards and charts use the supplied telemetry.
* [ ] Full-day calculations match `daily_summary` within rounding tolerance.
* [ ] Replay totals exclude readings that have not yet been revealed.
* [ ] Battery SOC stays within the supplied 20–95% range.
* [ ] Dates use Asia/Manila.
* [ ] Monitoring opens on the latest demo date.
* [ ] The app does not claim real brands, real prices, live hardware connections, actual purchases or safety certification.

## 14. Build priorities and completion response

Implement the complete core journey:

**My Household → Build a System → Compare → My Checklist → Monitoring**

If time or token limits require prioritisation:

1. Complete household inputs, builder, comparison and checklist.
2. Complete the monitoring page using the supplied data.
3. Add optional features only after the core journey works.

In your completion response, state:

* What works.
* Any remaining limitations.
* Whether saved progress uses the managed backend or the localStorage fallback.
