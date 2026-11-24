# Real Data — Data Dictionary

Source files: Zoey's working Google Sheets, read read-only on 24 Nov 2026.
All figures are aggregated counts only. No customer names, addresses, phone
numbers, emails, individual order IDs, tracking numbers, or any row-level
personal data are included in this file, the dashboard, or the repo.

## real_data_aggregates.csv

One row per metric. Columns: `metric`, `value`, `source_sheet`, `source_tab`,
`as_of`.

### Online Order Inquiries (sheet: Online Order Inquiries)
- `inquiries_total_nov2026` = 254 — items on the consolidated tracking tab
  ("total sheet"), Nov 2026. Statuses: Completed 153 (60%), In Progress 70
  (28%), Pending 31 (12%).
- `inquiries_topic_*` — keyword counts on the same 254 items; an item can
  mention more than one topic, so topic counts sum to more than 254:
  address change 84, cancellation 37, tracking 15, return 8, refund 3,
  stock 2, other 112.
- `inquiries_open_total` = 53 — items on the live Open tab. Statuses: On Hold
  16, Wait for response 14, Urgent 13, Pending 4, Kitty to follow 3, Closed 2,
  1 unlabelled.
- `inquiries_closed_total` = 103 — items on the Closed tab, all Closed.
- WATCH LIST (570 rows, Nov 2025–Mar 2026, mostly no status) is historical
  only and was NOT used for any dashboard figure.

### Costco Amazon x 360 delivery 2026
- `delivery_delivering_orders` = 135, `delivery_delivering_units` = 23,461 —
  Delivering tab. Company split: Amazon 69, Costco AU 44, Costco NZ 5,
  ALDI 2, 15 unlabelled. Top products by orders: Qrevo L Pro 25, Qrevo L 18,
  Qrevo Curv 2 Flow 13, E2 PRO 11, Potensic Atom 2 Drone 11.
- `delivery_delivered_listed` = 246 — orders listed on the Delivered tab;
  `delivery_delivered_marked_y` = 194 (79%) marked Delivered=Y. Company split
  of the listed rows: Costco AU 153, Costco 43, Amazon 24, Costco NZ 24.
  Product split and unit total for the Delivered tab are NOT usable — columns
  shift between rows — and are not shown.
- `delivery_cancelled` = 9 — Cancelled tab (Costco AU 6, NZ 3).
- `ra_collections` = 8, `ra_approved_units` = 122, `ra_stores` = 7 — RA
  Collecting tab. Bookings: Confirmed 6, Pending 2; collected 5.
- RA Collection Time is a reference timetable (17 store entries), not order
  data, and was not used.

### 360 ILS RETURN LIST
- `returns_records` = 681, `returns_units` = 1,284 — Return List MEL + SYD +
  WA, Dec 2025–Nov 2026. MEL 501 records / 874 units; SYD 177 / 399;
  WA 3 / 11.
- Outcomes: back into stock 186, received in CartonCloud 277 (MEL), sent to
  Technocity 31, resend to customer 13, dispose 9, other/blank 165.
- Product family: Roborock 442, Segway 73, other/accessory 166.
- MEL monthly peak: Jan 2026 (105). SYD Nov 2026: 53; Oct 2026: 44.
- `lit_short_supply_records` = 13, `lit_short_supply_units` = 14 — LIT tab
  (short-supply / credit claims), all TollIPEC, Dec 2025–Feb 2026.

### Hohem Amazon Order
- `hohem_orders` = 34, `hohem_completed` = 32 (94%), `hohem_cancelled` = 2,
  `hohem_units` = 34 — Nov 2025–Jun 2026 (peak Dec 2025: 16).
- Carriers: Australia Post 23, StarTrack 5, Allied Express 3.
- Top products: iSteady M7 Black 13, iSteady V3 White 10.
- This sheet contains buyer names, phone numbers and home addresses — none
  of that was copied anywhere; aggregates only.

## Not included (and why)
- Air Sea Freight Tracking.xlsx — an Office (.xlsx) file; the Sheets API
  rejects it, and Google Drive is not connected, so it could not be opened
  at all. No freight numbers from it. The dashboard states this honestly
  instead of showing freight figures.
- Cin7, Shopify, CartonCloud, Colladium, EWE, Costco Traffic, AusPost
  portals, MyTeamGE, Technocity SharePoint, 360 SharePoint/OneDrive —
  login-gated; no logins were attempted, nothing was changed. Allied Express
  Track & Trace is public but is a single-parcel lookup with no aggregate
  data. SOH / incoming-stock figures are therefore not in the dashboard.
- Returns are analysis only. The automation is order-pushing (推單); it does
  not automate returns.

## Labelling
- Figures on the dashboard's Real Data page are labelled REAL with the source
  sheet name and as-of date (24 Nov 2026).
- The Power BI portfolio project's V1 figures remain labelled SIMULATED and
  are never mixed with real data without a clear label.
- The What-if 65% modelled time saving is a modelled figure (midpoint of
  Zoey's revised 60–70% estimate), not measured. It is unchanged by this
  update.
