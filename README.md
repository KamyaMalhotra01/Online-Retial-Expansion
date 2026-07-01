# Online Retail Expansion Insights 📊

Power BI + Excel analysis of a UK-based online retailer's 2010–2011 transaction data, built to answer four strategic questions for a global expansion decision: revenue seasonality, top-performing markets, highest-value customers, and global product demand. Delivered as an executive-ready Power BI report and a stakeholder presentation deck.

---

## Business Problem

Leadership needed data-backed answers to four questions before committing budget to international expansion:

1. **Revenue Seasonality** – When do sales peak and dip across 2011, and what does that mean for inventory/staffing planning?
2. **Country Performance** – Which non-UK markets generate the most revenue and volume?
3. **Customer Value** – Who are the highest-value customers, and how concentrated is revenue among them?
4. **Demand Mapping** – What does product demand look like across all 36 non-UK markets, to identify the next wave of expansion targets?

---

## Findings

### 1 · Monthly Revenue Trend (2011)
- Revenue surges **Sep–Nov**, peaking at **£1.49M in November** driven by pre-holiday B2B and gift-season restocking.
- Lowest point is **£521K in February** — consistent with post-holiday cool-down patterns.
- The December dip (£635K) reflects a **partial month of data**, not a true demand loss — an important nuance for forecasting.
---

### 2 · Top 10 International Markets by Revenue
- **Netherlands (£280K) and EIRE (£270K)** lead all non-UK markets in both revenue and quantity sold.
- **Germany and France** form a strong second tier at ~£220K each.
- Revenue and quantity curves diverge at Spain — markets below this point are high-volume but low-revenue, suggesting lower unit price products or smaller basket sizes.

---

### 3 · Top 10 Highest Revenue-Generating Customers
- Customer **14646 (£280.2K)** and **18102 (£259.7K)** are in a tier of their own — both sit well above the group average of £154K.
- The top 2 customers together contribute **~£540K**, while customers ranked 7–10 combined contribute only **~£349K** — a stark concentration of revenue risk.
- Retention strategy should start at the top and work down.

---

### 4 · Global Product Demand Treemap (Excl. UK)
- **Netherlands (201K units)** is the dominant non-UK demand market, followed by **EIRE (147K)** and **Germany (119K)**.
- The treemap reveals the next expansion wave — **Norway (19K), Portugal (16K), Finland** — markets with meaningful demand but under-resourced commercial coverage.
- Visual encoding by area makes it instantly clear where to prioritise versus where to monitor.

---

## Recommendations Delivered

| # | Recommendation | Insight it came from |
|---|---------------|----------------------|
| 1 | Plan inventory & staffing around the Sep–Nov Q4 surge | November £1.49M peak, February £521K trough |
| 2 | Lead expansion with Netherlands, EIRE, Germany, France | Consistent top 4 across revenue and volume |
| 3 | Launch retention coverage for top 10 customers | Top 2 customers = £540K; 7–10 combined = £349K |
| 4 | Greenlight Norway, Portugal, Finland as next wave | Mid-tier demand visible in treemap |

---

## Methodology

### 1. Data Profiling
Before any cleaning, each column was profiled to understand data types, value distributions, and anomalies: invoice numbers (numeric vs. cancellation-prefixed), stock codes, text descriptions, quantities (including negatives), unit prices, customer IDs (with significant nulls), and country. This step informed every downstream decision.

### 2. Data Cleaning (Excel)

**Handling missing Customer IDs** — A meaningful portion of transactions had no CustomerID. Rather than dropping these rows and losing valid sales volume, nulls were replaced with `0` to preserve the transaction record while flagging it as unidentified. Values were propagated consistently across the dataset using Excel's fill-down technique after sorting.

**Isolating cancellations** — Cancelled transactions were identifiable by a `C` prefix on the InvoiceNo (e.g. `C536379`). These were filtered using a text filter and removed from the main sales table, as including reversals would inflate gross revenue figures and distort customer-level and country-level analysis.

**Separating returns** — Transactions with negative quantities represent returned or reversed line items. Rather than deleting this data, it was extracted into a dedicated `Returns` sheet (`online_retail_returns.xlsx`, ~10K rows). This keeps the main analysis clean while preserving the returns data for future analysis — such as return rate by country, product, or customer segment.

### 3. Data Modeling & Analysis (Power BI)
The cleaned dataset was loaded into Power BI and structured into a semantic model. DAX measures were written to compute monthly revenue, cumulative sales, country-level aggregations, and customer revenue rankings. Visuals were built to directly answer each of the four business questions posed by leadership — no exploratory charts, only decision-relevant outputs.

### 4. Insight Communication (PowerPoint)
Findings were translated into a stakeholder deck structured around the four leadership questions. Each slide maps one question to one answer to one recommended action — designed for an executive audience that needs decisions, not data.

---

## Tools & Skills Used

| Tool | Purpose |
|------|---------|
| **Power BI** | Data modeling, DAX measures, interactive report design (PBIP format for Git version control) |
| **Microsoft Excel** | Data profiling, cleaning, column engineering (Month/Year extraction, return isolation) |
| **PowerPoint** | Translating findings into a four-question executive narrative |
| **Data Storytelling** | Structuring output around decisions leadership needed to make, not raw charts |

---

## Dataset
Based on the public **[UCI Online Retail dataset](https://archive.ics.uci.edu/dataset/352/online+retail)**: transactional records for a UK-based online gift retailer, Dec 2010 – Dec 2011, covering invoices, products, quantities, unit prices, customers, and 38 countries.

---

