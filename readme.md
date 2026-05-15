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
- Out-of-town surcharge: +1 crew for unloading, multiplied food cost
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

When the **Out of Town** checkbox is enabled:

- **+1 crew member** is added to the manpower cost (one person travels with the truck to unload at the destination)
- **Food cost is multiplied** by the number of meals per person (default: 3 — covers multiple meals for the travel day)

| Scenario | Manpower | Food |
|---|---|---|
| In town | `crewCount × costPerCrew` | `crewCount × foodPerCrew × 1` |
| Out of town | `(crewCount + 1) × costPerCrew` | `(crewCount + 1) × foodPerCrew × mealsCount` |

> Example: 3 crew → 4 paid (3 base + 1 unloader); food calculated for 4 people × 3 meals.

---

## Margin Tiers

| Adjusted Cost | Margin |
|---|---|
| < 1M | 55% |
| 1M–3M | 45% |
| 3M–7M | 35% |
| 7M–15M | 25% |
| > 15M | 20% |

---

## Minimum Profit Floors

| Adjusted Cost | Minimum Profit |
|---|---|
| < 1M | 450K |
| 1M–3M | 900K |
| 3M–7M | 1.400M |
| 7M–15M | 2.300M |
| > 15M | 3.8M |

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