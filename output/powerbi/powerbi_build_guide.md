# Build the three report pages

1. Open a blank report in Power BI Desktop. Use **Get data → Text/CSV** for each CSV next to this guide. Choose UTF-8 and comma delimiters. In Power Query, set the query names to the exact filenames without extensions and apply the documented data types. Use English (United States) locale for parsing fixed decimals if needed. Keep PO and carton dimensions as Text. Apply the queries.
2. Build the active relationships exactly as shown in [data_model.md](data_model.md). Use the explicit measures in [dax_measures.dax](dax_measures.dax), one definition per Modeling → New measure action. Create the calculated table below before adding scenario measures.
3. Import [theme.json](theme.json) via **View → Themes → Browse for themes**. Use a 1440 × 1050 custom canvas with 32 px outer margins and 16 px gutters. Set the page background to warm cream #F3F1EB, visual panels to #FFFFFF and header/navigation to #152D2B with white text. Use Georgia for page titles and Segoe UI for small labels. Use a page navigator across all three pages with prominent selected state. For KPI cards use small titles, large callouts and white panels with subtle borders. Format unit/carton measures as whole numbers, order amounts as `$#,##0`, return cost as `$#,##0.00` and modelling measures as percentages with up to one decimal. Keep the estimate card title exactly **Zoey's estimate (~80%)**. Its value may be presented in the title with the numeric callout hidden to avoid repeating the estimate.
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
- Footer addition: “The correction and the cancellation have no verified link to PO 1991533680.”

## 2. Logistics Deep Dive

- Pin **Returned cartons** and **Return cost** above a return example panel. Use a single-bar chart for Returned cartons, with Return cost in Tooltips. Label it “Damaged-goods return” and place “360 paid the freight” beside it. Keep the November evidence label visible.
- Add a Freight mode slicer above a mode and coverage table. Use a second System slicer restricted to Tracking / delivery, with a table for EWE, AusPost and DHL. Give each slicer interactions only with its associated table. Add a narrow carton examples table with Dimensions and the November evidence label.
- List Costco RA, shortages, PO errors, cross-state transfers, invoice reissue, returns, LIT, warehouse inventory allocation and order follow-up in a compact two-column coverage panel.
- Footer addition: “Air-sea freight sheet and EWE tracking numbers were unavailable in the readable chats. Carton dimension units were unspecified.”

## 3. Business Analysis

- Place **Order value example**, **Split order value** and the estimate card across the top. Chart the standalone order value and the two split components in a bar chart using the three corresponding measures. Add Split order value to Tooltips or show the components and total together in a detail table. Keep the November evidence label visible.
- Put the coverage parameter slicer and **Modelled time saved** and **Modelled time remaining** cards in an adjacent What-if panel. Use a 100% stacked bar with the two measures and tooltip values. Title it “What-if · Share of baseline processing time” and display “Anchor · Zoey's estimate (~80%)”. Explain “Modelled savings = estimated reduction × selected coverage”.
- Add a compact automation handover panel. The running Python program was written by Codex and lives as a local Codex desktop skill on Zoey’s Mac with SKILL.md, reference data and scripts. Export the full Project folder or clone via GitHub, re-set Python packages, API keys, file paths and permissions, then rerun the same PO test data and verify identical results. Conversation history and memory are excluded from the transfer. The skill can be adapted to Claude’s SKILL.md format. Zoey pays for her Codex membership personally, without company reimbursement.
- Footer addition: “What-if outputs are scenario shares of baseline processing time. Anchor · Zoey's estimate (~80%). The order values are isolated examples.”

## Verify and save

Confirm the unfiltered values against the CSVs. Select Costco portal and confirm the PO and cancellation stay visible while the correction, return and monetary examples return blank. Select Unspecified and check the reverse. Check each coverage slicer in isolation. Test the scenario at 0%, 50% and 100% coverage. Modelled savings should be 0%, 40% and 80% respectively, with the exact anchor label **Zoey's estimate (~80%)**, and remaining shares should be 100%, 60% and 20%. Save from Desktop as a .pbix.
