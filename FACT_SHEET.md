# VWAVS — Fact Sheet

**Site:** [vwavs.com](https://vwavs.com)
**Brand:** VWAVS · TickSense
**Status:** Live · public · auto-updated every 5 minutes

---

## What VWAVS is

VWAVS is a real-time monitoring system for small-cap equity moves. It watches the market continuously for **eruptions** — sudden directional moves backed by the volume and conviction of real institutional flow — and routes those detections to a set of specialist **responders** that decide whether to act.

The website is the public face of that system, running in the open.

---

## What the website shows

Three things, presented as they happen:

1. **Eruptions surfaced** — tickers crossing into the eruption zone, with timestamp, direction, and a label for whether the move is healthy or showing signs of exhaustion (back-side, fading, incoherent).
2. **Responder activity** — when a specialist responder enters or exits a position, the row shows ticker, entry price, hold time, P&L, and current state (open / closed).
3. **The handoff between the two** — every responder row has a marker showing whether the eruption layer flagged the same ticker in the same window. That marker is the architecture made visible.

Every row carries a timestamp. The reader can verify any event against any free chart service.

---

## What the website does NOT do

- Make P&L claims
- Show backtest results
- Sell anything
- Require a subscription, account, or email
- Recommend trades
- Advertise

The page is a demonstration, not a sales page. A visitor either sees something meaningful in the activity or doesn't. There's no further ask.

---

## How to use it

Visit. Watch. Verify any timestamp against any chart. Come back another day. Watch again.

The page auto-refreshes every 5 minutes. Activity accumulates over the trading day; on weekends and overnight, it shows the most recent active window.

---

## The responders

Each responder is a specialist — built for a specific kind of move, with its own discipline for entries and exits. The system runs multiple responders simultaneously because no single rule wins on every kind of equity behavior. Letting specialists disagree, and watching which one is right on which kind of move, is part of how the system works.

Current responders (named publicly on the site as they fire):

- **Tenacity A / B / (paper)** — the original responders, built on patience and structural discipline
- **Renko / Renko Pure / Trend** — substrate-pure responders for distinct chart shapes
- **Velocity** — continuity-driven, for sustained directional flow

Internal architecture is intentionally not detailed on the public page. What's visible is what each responder did, when, and with what outcome.

---

## Verification

Every event the site shows has:

- A timestamp (UTC)
- A ticker symbol
- A price
- An outcome (P&L when closed, current state when open)

Any of these can be verified against TradingView, Webull, or any free chart. If the timestamp shows TickSense flagged a ticker at 10:14, and the chart shows that ticker erupting at 10:14, the eye saw it. If a responder entered at 10:14:08, the entry is independently verifiable from time-and-sales.

There's no way to fake a live page with a continuously verifiable timestamp stream. That's the credibility model.

---

## What's proprietary

The site shows the outcomes. It does not show:

- The substrate (how price is internally represented)
- The entry rules
- The threshold values
- The phase logic
- The filtering layers
- The radar's grading math
- Any parameters

The architecture (eruption detection → responder reaction) is conveyed conceptually. The mechanism is the work of the apparatus and stays with the apparatus.

---

## Frequently observed questions

**Q: Are these real trades?**
Real shadow trades — the responders evaluate every entry and exit against live market data as if they were trading, and the outcomes shown reflect what would have happened on those entries/exits. The system is in a public-validation phase prior to live capital deployment.

**Q: Why show losses?**
Showing only wins would be marketing. Showing wins AND losses is how a system establishes that it's a system, not a curated stream of highlights. Anyone watching for a few sessions will see both.

**Q: Why so many responders?**
Different kinds of equity moves reward different kinds of patience. A responder that wins on sustained climbers will whipsaw on choppy peakers. Running multiple specialists is the system's answer to "no single rule works on everything."

**Q: Is this for trading or for watching?**
For watching. The site is a demonstration of the apparatus, not a tool. The responders run for the operator's own paper validation; the public surface exists so anyone can verify what the system does.

**Q: Can I get the signals?**
Not currently. The site is a public-validation phase. The signals are not yet distributed.

---

## Architecture (at the visible level only)

```
                    ┌─────────────────────────┐
                    │   Equity universe       │
                    │   (small-cap, US)       │
                    └──────────┬──────────────┘
                               │
                               ▼
                    ┌─────────────────────────┐
                    │  Eruption detection     │
                    │  ("the volcano")        │
                    │                         │
                    │  Continuous, agnostic   │
                    └──────────┬──────────────┘
                               │ surfaces
                               ▼
            ┌──────────────────────────────────────┐
            │  Specialist responders               │
            │                                      │
            │  Each acts on its own rule           │
            │  Each exits on its own rule          │
            │  They can disagree (by design)       │
            └──────────┬───────────────────────────┘
                       │ outcomes
                       ▼
                    ┌─────────────────────────┐
                    │   Public site           │
                    │   (this page)           │
                    └─────────────────────────┘
```

What's shown publicly is the bottom row, with provenance markers (✓ / —) connecting back to the layer above.

---

## Pages on the site

- **`/`** — the live page (this is the main view)
- **`/last24h.html`** — full event stream for the last 24 hours
- **`/references.html`** — curated reference cases from earlier in the system's history

---

## Operator note

The system is operated by a single individual in active development. The website is auto-generated from the system's running logs every 5 minutes. The volcano metaphor is operational shorthand for the perception layer's job: surface what's about to erupt, label what's already done. The "responders" are technical bots, named publicly to avoid the connotations of high-frequency trading or algorithmic black boxes — these are patient, structurally disciplined position-takers, not scalpers.

---

*Updated: 2026-05-17*
