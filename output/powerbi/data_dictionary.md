# Data dictionary

Business observations come from the supplied summary of Zoey Chao’s ChatGPT/Codex chats, read 24 Nov 2026, and her work favorites export (Nov 2026), as noted below. Blank CSV cells mean unspecified. Dollar amounts retain the stated $ notation. The brief does not identify currency codes or transaction dates.

## channels

| Column | Power BI type | Definition and source |
|---|---|---|
| Channel | Text | Costco portal is the only identified channel in the example orders. Unspecified marks examples without a verified channel. Shopify and Amazon come from Zoey’s work favorites export (Nov 2026) and have no example order rows linked in this dataset. |

## orders

| Column | Power BI type | Definition and source |
|---|---|---|
| ExampleID | Text | Local key assigned to each separate chat example. |
| Channel | Text | Costco portal for the Costco PO; channel unspecified for the monetary examples. |
| Example | Text | Display label derived from the supplied examples. |
| PO | Text | Explicit Costco PO identifier. |
| OrderValue | Fixed decimal | Stated order value in dollars as provided. |
| ComponentA | Fixed decimal | First stated component of the split order value. |
| ComponentB | Fixed decimal | Second stated component of the split order value. |
| Source | Text | Required November chat provenance label. |

## order_lines

| Column | Power BI type | Definition and source |
|---|---|---|
| LineID | Text | Local example line key. |
| ExampleID | Text | Verified parent association via the local orders key. |
| SKU | Text | SKU stated for the Costco PO. |
| Quantity | Whole number | Units stated on the Costco PO. |
| Source | Text | Required November chat provenance label. |

## exceptions

| Column | Power BI type | Definition and source |
|---|---|---|
| ExceptionID | Text | Local exception example key. |
| Channel | Text | Costco portal for the Costco cancellation; unspecified otherwise. |
| Example | Text | Exception label derived from the supplied examples. |
| OriginalQty | Whole number | Quantity before the documented correction. |
| CorrectedQty | Whole number | Quantity after the documented correction. |
| ReturnedCartons | Whole number | Carton count for the damaged-goods return. |
| ReturnCost | Fixed decimal | Stated total return cost in dollars as provided. |
| Detail | Text | Verified exception context from the supplied brief. |
| Source | Text | Required November chat provenance label. |

## carton_examples

| Column | Power BI type | Definition and source |
|---|---|---|
| CartonID | Text | Local carton example key. |
| Dimensions | Text | Carton dimensions as stated; unit and order association unspecified. |
| Source | Text | Required November chat provenance label. |

## freight_modes

| Column | Power BI type | Definition and source |
|---|---|---|
| Mode | Text | Mode mentioned or named in the supplied freight scope. |
| Coverage | Text | Qualitative freight or route evidence. Air and Sea reference the Google Sheet named Air Sea Freight Tracking in Zoey’s work favorites export (Nov 2026). Road coverage comes from the supplied brief. |

## systems

| Column | Power BI type | Definition and source |
|---|---|---|
| System | Text | System or tool named in the supplied brief or Zoey’s work favorites export (Nov 2026). The export supplies the new Allied Express, MyTeamGE (Team Global Express), SharePoint / OneDrive (360), Google Sheets and Technocity SharePoint (Roborock RA) rows. Zoey confirmed the Costco portal uses Colladium. |
| Stage | Text | Workflow grouping based on the stated function or tool type. |
| StageSort | Whole number | Display order assigned for this report. |
| Coverage | Text | Stated function or scope from the supplied brief or Zoey’s work favorites export (Nov 2026), including the updated Costco and AusPost portal coverage. |

## automation_parameters

| Column | Power BI type | Definition and source |
|---|---|---|
| EstimateFraction | Decimal number | Zoey’s stated estimate, encoded as a fraction. |
| EstimateLabel | Text | Required wording for Zoey’s stated estimate. |
| CoverageMinPct | Whole number | What-if assumption: minimum slider percentage. |
| CoverageMaxPct | Whole number | What-if assumption: maximum slider percentage. |
| CoverageStepPct | Whole number | What-if assumption: slider increment in percentage points. |
| CoverageDefaultPct | Whole number | What-if assumption: full coverage shown by default. |
| Source | Text | Provenance for the estimate and model configuration. |

## Calculated table

`Coverage[Coverage]` is a Whole number from 0 through 100 generated in Power BI. Its inputs come from `automation_parameters`. Each row represents one hypothetical coverage percentage.
