# 360 Order Fulfilment Analytics Dashboard

An interactive analytics dashboard showing how order fulfilment worked at 360 International Trading — and what changed when order processing was semi-automated.

**Live dashboard:** https://trading360-order-fulfilment-analytics.racingoleander32.chatgpt.site/

## What this is

I was Logistics Officer at 360 International Trading (May–Nov 2026), processing several thousand B2B/B2C orders a month across Shopify, client portals, Cin7, CartonCloud and carriers (EWE, AusPost, DHL). This dashboard presents that work in five pages, following a Summary → Why → So what → How → Evidence story:

1. **Operations Overview** — the headline: 95.6% of 1,403 orders dispatched within 48 hours (Oct 2026 weekly reports: 94.65% → 93.91% → 97.52%).
2. **Logistics Deep Dive** — late orders by reason (mostly stock shortages, not processing delays), plus inbound sea freight: typically 19–22 days from China to Australia.
3. **Business Analysis** — returns analysis by category and reason, and what it suggests (for example, sizing information).
4. **Cin7 Order Push** — the automation: how the manual order push was cut, with a What-if model (65% modelled time saving at 100% automation coverage) and an honest note on what was and wasn't measured.
5. **Data & Definitions** — appendix: definitions, sources, reconciliation and gaps.

## Key results

- **95.6%** of 1,403 orders dispatched within 48 hours (Oct 2026, from weekly fulfilment reports).
- **~60–70% estimated** reduction in order-processing time from the semi-automated order push (my estimate, not a timed measurement — the dashboard says so).
- **65% modelled** time saving at 100% automation coverage (What-if model, based on the 60–70% estimate).
- Late orders in my final week: 14; the week after I left: 100+ (human-caused, not stock). Shown as a comparison, not as a measured before/after of the automation.

## What's in this repo

- `output/index.html` — the dashboard itself (the same page as the live link above; open it in a browser, it works offline).
- `output/powerbi/` — Power BI assets: data model (`data_model.md`), DAX measures (`dax_measures.dax`, including the What-if measures), theme (`theme.json`), CSVs and a step-by-step build guide (`powerbi_build_guide.md`). The `.pbix` itself is built in Power BI Desktop following the guide.
- `output/360-order-fulfilment-dashboard.zip` — the Power BI assets bundle, downloadable in one file.

## Data note

Figures are aggregates from my October 2026 weekly fulfilment reports and working sheets. No customer names, addresses, order numbers or tracking numbers are included. Anything modelled or estimated is labelled as such on the dashboard.
