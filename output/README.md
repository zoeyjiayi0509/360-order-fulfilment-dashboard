# 360 International Trading · Order Fulfilment Analytics

Open `index.html` directly in a browser. All styles, data and interactions are embedded and work offline. The Power BI assets are in `powerbi/`. Start with `powerbi_build_guide.md`.

**No real .pbix was produced.** Power BI Desktop was unavailable in the Linux build environment. The import CSVs, model specification, DAX, theme and page guide are supplied for building the report in Desktop.

This is a separate build based on the verified facts supplied in the task. The sample rows come from Zoey Chao’s November 2026 chats as summarized in the brief. The coverage slider is hypothetical and starts at full coverage. Blank example metrics indicate that the selected filter excludes their evidence.

## Real Data (added 24 Nov 2026)

The dashboard's fifth tab, Real Data, shows aggregated counts read (read-only) from Zoey's working Google Sheets on 24 Nov 2026: online order inquiries (254 items), Costco/Amazon deliveries (135 orders in transit / 23,461 units; 194 of 246 listed as delivered), ILS returns (681 records / 1,284 units) and Hohem Amazon orders (34). Aggregates only — no customer names, addresses, phone numbers, emails, order IDs or tracking numbers. See `powerbi/real_data_aggregates.csv` and `powerbi/real_data_dictionary.md`. The What-if 65% figure is modelled (midpoint of the revised 60–70% estimate), not measured. The downloadable ZIP bundle is rebuilt separately after each update.
