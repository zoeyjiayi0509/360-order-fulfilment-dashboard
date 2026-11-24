# Build the three report pages


1. Open a blank report in Power BI Desktop. Use **Get data → Text/CSV** for each CSV in the data/ folder. Choose UTF-8 and comma delimiters. In Power Query, set the query names to the exact filenames without extensions and apply the documented data types. Use English (United States) locale for parsing fixed decimals if needed. Keep PO and carton dimensions as Text. Apply the queries.
2. Build the active relationships exactly as shown in [data_model.md](data_model.md). Use the explicit measures in [dax_measures.dax](dax_measures.dax), one definition per Modeling → New measure action. Create the calculated table below before adding scenario measures.
3. Import [theme.json](theme.json) via **View → Themes → Browse for themes**. Use a 1440 × 1050 custom canvas with 32 px outer margins and 16 px gutters. Set the page background to warm cream #F3F1EB, visual panels to #FFFFFF and header/navigation to #152D2B with white text. Use Georgia for page titles and Segoe UI for small labels. Use a page navigator across all three pages with prominent selected state. For KPI cards use small titles, large callouts and white panels with subtle borders. Format unit/carton measures as whole numbers, order amounts as `$#,##0`, return cost as `$#,##0.00` and modelling measures as percentages with up to one decimal. Keep the estimate card title exactly **Zoey's revised estimate (~60–70%)**. Its value may be presented in the title with the numeric callout hidden to avoid repeating the estimate.
4. Duplicate the header, page navigation and **Sources & notes** footer before configuring each page. Footer text for all pages: “Zoey Chao, Logistics Officer, 360 International Trading, May–Nov 2026. Evidence from Zoey’s ChatGPT/Codex chats as supplied, read 24 Nov 2026. real examples from Zoey's chats, Nov 2026. Total order volumes, error rates and measured minutes per order are unavailable.” Add the page-specific notes below.


## What-if parameter


Use **Modeling → New table**. This is a disconnected numeric What-if parameter. The generated values reproduce the slider configuration from the CSV.


```dax
Coverage =
SELECTCOLUMNS(
    GENERATESERIES(
        MAX(automation_parameters[CoverageMinPct]),
        MAX(automation_parameters[CoverageMaxPct]),
        MAX(automation_parameters[CoverageStepPct])
    ),
    "Coverage", [Value]
)
```


Place Coverage[Coverage] in a single-select numeric parameter slicer if supported by your Desktop version. A single-select dropdown is an equivalent fallback. For the native numeric range parameter slider, create it via **Modeling → New parameter → Numeric range**, name it Coverage, use Whole number 0–100, increment 1 and default 100, and use that generated table in place of the calculated table above. Save with 100 selected. The model assumes a linear share of time savings as coverage increases. At 0%, savings are zero. The complement is the share of original processing time remaining.


## 1. Operations Overview


- Place the Channel slicer above the example visuals and sync only to Logistics Deep Dive and Business Analysis. Place the System slicer above the systems coverage table. Set Edit interactions so System only filters that coverage table.
- Put **Costco PO units**, **Original quantity** and **Corrected quantity** in the KPI band. Label the PO card “Costco PO 1991533680 · H60”. Place a clustered bar chart below with Original quantity and Corrected quantity on the value axis, starting at zero. Set the tooltip to show both values. Use the title “Order quantity correction” with the November evidence label. Show a callout on the right for the separate Costco PO and the Cin7 cancellation. For the cancellation use a table filtered to E2 so the Channel slicer applies.
- Add the four intake-to-delivery stages as a compact process strip. Below it place a systems table with Stage, System and Coverage. Add the exception-support scope in Logistics Deep Dive.
- Footer addition: “The correction and the cancellation have no verified link to PO 1991533
