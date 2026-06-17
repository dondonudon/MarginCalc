# MarginCalc

Simple service pricing calculator with:
- operational buffer
- tiered profit margin
- minimum profit floor
- fixed 3% negotiation buffer (repeat customer)
- out-of-town surcharge logic

Built as a lightweight static HTML tool that can be hosted anywhere.

---

## Features

- Automatic price calculation
- Tiered margin system
- Minimum profit protection
- Fixed 3% negotiation buffer (repeat customer default)
- Out-of-town multi-day support with spot hire crew at separate rates
- Crew-based cost calculation
- Thousand separator formatting
- EN/ID language toggle
- Mobile-friendly UI
- No backend required

---

## Pricing Logic

```text
Job Cost
+ Operational Buffer (10%)
+ Profit Margin
+ Fixed Negotiation Buffer (3%)
= Initial Offer Price
```

The calculator uses:
- dynamic margin tiers
- minimum profit floors
- fixed 3% negotiation buffer (repeat customer)

to create more realistic and sustainable pricing.

---

## Out-of-Town Calculation

When the **Out of Town** checkbox is enabled, six additional fields appear:

| Field | Description | Default |
|---|---|---|
| **Crew Going to Destination** | How many of the origin crew travel with the truck | 0 |
| **Cost per Traveling Crew** | Day rate for traveling crew (typically higher than stay crew) | 250,000 |
| **Days** | Number of days the job spans | 1 |
| **Meals per Day** | Meals per traveling crew member per day | 3 |
| **Spot Hire Count** | Local helpers hired at the destination | 0 |
| **Cost per Spot Hire** | Day rate for each spot hire | 100,000 |

The origin crew splits into **stay crew** (load at origin, paid 1 day at `costPerCrew`) and **travel crew** (ride with the truck, paid for all days at the higher `travelCostPerCrew`).

**Formulas:**

| Component | Formula |
|---|---|
| Stay crew manpower | `(crewCount − travelCrewCount) × costPerCrew` |
| Travel crew manpower | `travelCrewCount × travelCostPerCrew × days` |
| Spot hire manpower | `spotHireCount × spotHireCost` |
| Stay crew food | `(crewCount − travelCrewCount) × foodPerCrew` |
| Travel crew food | `travelCrewCount × foodPerCrew × mealsPerDay × days` |

Spot hire crew receive no food allowance.

> Example: 4 origin crew, 2 travel (at 250K/day), 1 spot hire (at 100K), 2 days —
> stay cost = 2×175K, travel cost = 2×250K×2, spot hire = 1×100K.

---

## Margin Tiers

| Adjusted Cost | Margin |
|---|---|
| < 1M | 45% |
| 1M–3M | 35% |
| 3M–7M | 25% |
| 7M–15M | 20% |
| > 15M | 15% |

---

## Minimum Profit Floors

| Adjusted Cost | Minimum Profit |
|---|---|
| < 1M | 300K |
| 1M–3M | 500K |
| 3M–7M | 750K |
| 7M–15M | 1.300M |
| > 15M | 2.100M |

---

## Project Structure

```
index.html      — markup
styles.css      — all styles
calculator.js   — pricing logic and number formatting
i18n.js         — translation strings and language toggle
```

---

## Local Development

Simply open:

```bash
index.html
```

No build step required.

---

## Tech Stack

- HTML
- CSS
- Vanilla JavaScript

---

## License

MIT