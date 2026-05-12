# MarginCalc

Simple service pricing calculator with:
- operational buffer
- tiered profit margin
- minimum profit floor
- negotiation buffer

Built as a lightweight static HTML tool that can be hosted anywhere.

---

## Features

- Automatic price calculation
- Tiered margin system
- Minimum profit protection
- Negotiation buffer support
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
+ Negotiation Buffer
= Initial Offer Price
```

The calculator uses:
- dynamic margin tiers
- minimum profit floors
- customer negotiation profiles

to create more realistic and sustainable pricing.

---

## Customer Types

| Type | Buffer |
|---|---|
| Price-sensitive | +15% |
| Standard | +10% |
| Corporate / VIP | +5% |
| Repeat Customer | +3% |

---

## Margin Tiers

| Adjusted Cost | Margin |
|---|---|
| < 1M | 70% |
| 1M–3M | 50% |
| 3M–7M | 35% |
| 7M–15M | 25% |
| > 15M | 20% |

---

## Minimum Profit Floors

| Adjusted Cost | Minimum Profit |
|---|---|
| < 1M | 475K |
| 1M–3M | 950K |
| 3M–7M | 1.425M |
| 7M–15M | 2.375M |
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