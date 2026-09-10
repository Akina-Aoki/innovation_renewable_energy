Build a working hackathon prototype called “Solar Builder” for one Philippine household. This is Part 2 of a wider clean-energy project. Its main purpose is helping a household plan, customize, compare and source a solar setup, with simulated post-installation monitoring. Think of selecting parts in a custom PC builder, but use original solar-focused branding and interface design. Do not build the other project parts.

Use the attached demo_seed.json as canonical data, or the matching CSV tables if supplied instead. Do not fabricate different catalog prices or dashboard numbers. All products, suppliers, prices and readings are fictional. Show a compact “Demo · synthetic data” label throughout. Do not use names, addresses or account details from reference screenshots.

Deliver a responsive app with a clean white background, dark navy text, solar-green accents, warm yellow for household load and blue for battery status. Use readable cards and spacing. Desktop navigation: My Household, Build a System, Compare, My Checklist, Monitoring. Provide a mobile layout. Use plain English and short definitions of kW, kWh and battery SOC.

Implement the frontend and the simplest managed backend/database available in this project. Seed idempotently using the supplied IDs. Store saved builds and checklist progress; for a public demo, keep changes isolated per browser/session, with no publicly writable shared household. A localStorage demo fallback is acceptable if backend provisioning is unavailable; explicitly describe that implementation limitation in your completion message. No paid APIs or real hardware integration are needed. Use actual data-backed UI interactions, not static screens.

Data tables supplied: households, panels, inverters, batteries, suppliers, listings, configurations, installed_systems, telemetry, daily_summary. Read START_HERE.md if attached for the full data contract. Fields ending _kw are power, _kwh energy, _php currency. Timestamp UTC is canonical; group/render dates in Asia/Manila. telemetry's key is (system_id,timestamp_utc); daily_summary is derived, not extra energy.

1. MY HOUSEHOLD
Preload HH001: monthly consumption 450 kWh, budget ₱250,000, Hybrid, critical load 0.5 kW, backup goal 8 hours. Editable consumption, budget, critical load and backup goal. Keep Hybrid as the supported prototype type; On-grid and Off-grid may appear labeled “future option” and must not pretend to work. Location is Laguna Philippines. Editable estimate assumptions: 4.5 peak sun hours/day, performance ratio 0.8, tariff ₱12/kWh (illustrative).

2. BUILD A SYSTEM
Show rows for panel model and quantity, inverter, battery model and quantity, plus other equipment/installation allowance. Browse seeded catalog models and supplier offers, update total immediately, show solar kWp, nominal battery kWh, remaining budget and explanatory preliminary compatibility results. No actual checkout.

Use lowest-price seeded in-stock offers with sufficient quantity for each selected component. Price = panel quantity × panel offer + inverter offer + battery quantity × battery offer + other allowance. Configuration seed totals must be Budget ₱143,000; Balanced ₱227,000; More Solar ₱245,000. Keep allowance visible and editable; do not present it as a supplier quote or itemized equipment list.

Show required PV estimate = (monthly kWh / 30)/(peak sun hours × performance ratio). Monthly generation = selected PV kWp × peak sun hours × performance ratio × 30. Backup estimate = battery nominal kWh × 0.75 × 0.95 / critical load kW, assuming 95% starting SOC and 20% reserve. Explain assumptions; reject nonpositive inputs. Do not promise bill savings, ROI, off-grid independence or guaranteed runtime from these estimates.

Run preliminary checks: positive integer quantities; PV kWp <= inverter maximum PV; series_count × Vmp within MPPT range; series_count × Voc below max DC voltage; parallel_strings × Imp and Isc within inverter current limits; MPPT count; battery operating voltage range within inverter battery range; fictional bms_family match; supported parallel battery count; stock; budget. In this demo all panels form one series string on one MPPT. Warn that temperature-adjusted voltage and professional design review are still needed, particularly near voltage limits. Demo High Voltage 10 must fail battery voltage and BMS checks against both seeded inverters. Use “passes preliminary demo checks,” never “certified safe.” Failed feasibility checks exclude a build from eligible recommendations; they cannot be outweighed by price or a ranking score.

3. COMPARE
Compare three seeded configurations side by side: total cost, PV kWp, nominal battery kWh, estimated monthly generation, estimated backup hours at the selected critical load, budget and preliminary check results. Make trade-offs readable. Selecting a build takes the user to its shopping checklist. If no eligible build fits input constraints, say so honestly. Do not silently change budget.

4. CHECKLIST AND INSTALLATION HANDOFF
Generate the selected build's item quantities, chosen fictional supplier and prices. Track Not purchased / Ordered / Received; persist per session. Show mounting, protection, cabling and professional installation as “scope and quote to confirm,” covered only by an illustrative allowance. Do not invent cable sizes, breaker ratings or real supplier URLs. Provide a downloadable shopping CSV.
Offer a handoff summary with the chosen components and unresolved design checks. No electrical wiring tutorial, hardware control, real booking, payment or email submission. Button “Explore demo installed system” opens monitoring of SYS001, explicitly the seeded Balanced system. Merely checking items as received must not claim a system has actually been installed or commissioned.

5. MONITORING
Only SYS001 corresponds to the fixed Balanced system C2: 4.4 kWp PV, 5 kW inverter and 10.24 kWh battery. Historical data must remain attached to this system even when a different shopping build is selected.

Use telemetry for September 3–9, 2026 (2,016 five-minute intervals). Default to September 9, latest available completed interval. Provide local date picker and 7-day view. Do not default to today's actual date and show an empty chart. Weather information is not supplied; omit it. No fake live badge.

Top cards: selected-day solar yield at bus in kWh, household energy in kWh, grid import in kWh, and interval-end battery SOC %. Add a power-flow diagram connecting solar, inverter/bus, battery, grid and home, inspired by the functional content of the provided screenshots. Use solar_bus_power_kw in the diagram so the flow balances. Make solar_dc_power_kw available as a separately labeled detail. Power cards show the selected interval average, not an instantaneous physical reading.

Charts: solar bus power, household load, grid import/export, battery charging/discharging and battery SOC. Power on a kW axis; SOC on a separate 0–100% axis. For a signed battery series only, use discharge_bus_kw − charge_bus_kw; explain positive means discharging and negative means charging. The data itself stores separate nonnegative flows. Offer toggles and readable tooltips.

Energy = SUM(power_kw × interval_minutes / 60), grouped by local date. Never sum kW as energy. Do not sum SOC. At a selected interval show battery_soc_end_pct. Grid status comes from the row. No simultaneous import/export or charge/discharge is present in this seed.

Add Play / Pause / Reset for “Replay simulated readings.” Advance one five-minute row every second on the selected day. Display the interval's end time as data coverage; each row's timestamp is its start. Reveal rows progressively and calculate cards only from revealed rows. Reset clears the selected-day replay totals; pause freezes them. End playback stops. Do not use full-day totals while only showing a partial replay.

Optional small expected-versus-simulated card: full selected days × 4.4 × 4.5 × 0.8 as rough estimated bus yield, compared with solar_bus energy for those same completed days. Clearly name this a demo estimate. Do not compare seven days to a monthly forecast or diagnose hardware faults. Skip ROI and financial forecasts.

AC-equivalent bus balance must hold in the display: solar_bus + battery_discharge_bus + grid_import = load + battery_charge_bus + grid_export. Solar DC is converted to bus at 96% in the seed. Battery stored-energy change includes 95% charge efficiency and 95% discharge efficiency. Show a small “simulation assumptions” disclosure, without exposing engineering details throughout the user journey.

Acceptance checks before completion:
- Seed imports do not duplicate rows.
- Balanced total is ₱227,000 and its monthly generation estimate is 475.2 kWh at the default assumptions.
- Changing quantities updates total and estimates; reducing budget marks over-budget builds.
- Selecting high-voltage battery shows the explicit mismatch.
- Choosing a build generates the correct supplier/quantity checklist; reload preserves this session's choices.
- Monitoring charts and cards derive from supplied telemetry and match daily_summary for full days within rounding tolerance.
- Replay cards do not reveal future interval energy; SOC remains 20–95%.
- Dates use Asia/Manila and latest demo date, not browser timezone or current real date.
- No real brands, real prices, actual live-device connections, purchases, or safety certification are claimed.

Implement the complete core journey. If token/time constraints force prioritization, finish household → builder → compare → checklist first, then the seeded monitoring page. In your completion response state what works and any remaining limitations.
