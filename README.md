# UPI-Transaction-Analysis-Dashboard

## Project Overview
This repository contains an interactive **Power BI** dashboard that analyzes **20,000 UPI transactions**.  
The dashboard explores transaction volume and value across cities, banks, devices, payment methods, merchants and customer demographics. It was built as a portfolio / learning project to demonstrate dashboard design, data modeling, DAX, and storytelling using **slicers** and **bookmarks**.

---

## Dataset (source)
- File: `UPI_Transactions.xlsx` (included in this repo)
- Records: **20,000 transactions**
- Key fields: `TransactionID`, `TransactionDate`, `Amount`, `BankNameSent`, `BankNameReceived`, `City`, `DeviceType`, `PaymentMethod`, `MerchantName`, `Purpose`, `CustomerAge`, `Status`, `TransactionTime`, etc.

---

## Quick Summary (calculated from the dataset)
- **Total transactions:** 20,000  
- **Total transaction value (sum of Amount):** ₹19,872,274.03  
- **Overall success rate:** **80.00%** (Success vs Failed)  
- **Top sender banks (by count):** SBI Bank, ICICI Bank, Axis Bank, HDFC Bank (evenly distributed in dataset)  
- **Top receiver banks (by count):** HDFC Bank, SBI Bank, Axis Bank, ICICI Bank  
- **Top cities (by count):** Delhi, Bangalore, Hyderabad, Mumbai (dataset shows equal distribution)  
- **Customer age (summary):** mean ≈ 39.5 years (range 20–59)  
- **Monthly activity sample (Jan–Jun 2024):** roughly 1,666–1,667 transactions / month with monthly totals that vary slightly

---

## What the Dashboard Contains (visuals & features)
 
- **Slicers** (interactive filters): Date (Month/Range), Bank (sent/received), City, Device Type, Payment Method, Gender, Transaction Status, Purpose.  
- **Bookmarks**: Pre-built views for storytelling — e.g., *Overview*, *Bank Comparison*, *City Deep-dive*, *Merchant Snapshot*. Bookmarks toggle visuals and selection states for presentation mode.  
- **Matrix**: Detailed tabular breakdown (TransactionID, Date/Time, Amount, Merchant, Status, Bank names). Used for a row-level drill-through and export.  
- **Charts**:
  - Column/Bar charts for bank & merchant comparisons.
  - Line chart for monthly trends (transaction count and value).
  
- **Tooltips & Drillthroughs**: Hover tooltips show contextual metrics; drillthrough is enabled on merchant and city for deeper analysis.
- **Selection Pane**: Bookmarks and visibility toggles used for clean presentation slides.

---

## Key Insights & Business Takeaways


1. **High volume, but moderate success rate**
   - 20k transactions with an **80% success rate** — there is room to investigate causes of failures (network, bank-specific, or payment-method-specific failures).

2. **Banks are evenly represented**
   - Sending and receiving volumes are distributed across SBI, ICICI, Axis and HDFC in this dataset. Bank-level performance & failure analysis should be done at the transaction-status level to detect issues.

3. **City concentration**
   - The dataset shows primary activity in major metro cities (Delhi, Bangalore, Hyderabad, Mumbai). Prioritize performance and promotional activity in these cities.

4. **Device & Payment Method**
   - Device types (e.g., Mobile, Laptop — as shown in the dashboard slicer) and PaymentMethod distributions indicate where UX improvements or targeted messaging would be most beneficial.

5. **Merchants & Purposes**
   - Top merchants/process categories (Shopping, Food, Bill Payment) capture most transaction value — good targets for merchant partnerships or fee negotiations.

6. **Customer age**
   - Average customer age ~39.5 — tailor communications and product features accordingly.

---

## Data Preparation & Modeling (steps taken)
1. **Import**
   - Loaded `UPI_Transactions.xlsx` into Power BI Desktop (single sheet dataset).
2. **Data cleaning**
   - Converted `TransactionDate` and `TransactionTime` to date/time types.
   - Standardized `Status`, `BankNameSent`, `BankNameReceived`, `DeviceType`, `PaymentMethod`.
   - Handled missing values (filtered or replaced depending on column).
3. **Feature engineering**
   - Added columns: `Month` (Period), `Weekday`, `Hour` (from `TransactionTime`), `IsSuccess` boolean.
4. **Relationships**
   - If using lookup/dimension tables (e.g., merchants, banks) — create star schema relationships. In this project a single table approach was used with measures built directly.
5. **DAX measures**
   - Age groups = if('Sheet1'[CustomerAge]<=25,"A1",
     if ('Sheet1'[CustomerAge]<=35,"A2","A3"))

---

## How to use the PBIX & Interact with the Dashboard
1. Open `UPI_Dashboard.pbix` in **Power BI Desktop**.  
2. Use the **slicers** (left or top area) to filter by Date, City, Bank, Device, Payment Method, Gender, and Status.  
3. Click **bookmarks** (presented as buttons) to jump to curated views (Overview, Bank Comparison, Merchant View, City Map).  
4. Use the **matrix visual** to inspect row-level transactions and right-click to export or drillthrough to merchant detail.  
5. Hover over visuals to see tooltips; click a bar/segment to cross-filter the rest of the page.

---


