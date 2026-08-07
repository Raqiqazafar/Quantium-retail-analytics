# Quantium Retail Analytics — Data Preparation & Customer Analytics

## 📋 Overview

This project was completed as part of the **Quantium Virtual Internship** (via Forage), simulating a real-world retail analytics engagement. Acting as a member of Quantium's retail analytics team, the goal was to analyse a supermarket's chip category transaction and customer data to understand purchasing behaviour across different customer segments, and to generate data-driven commercial recommendations for the client's Category Manager.

The analysis was completed in **Python** (originally provided as an R template), using `pandas`, `matplotlib`, and `scipy` for data cleaning, feature engineering, exploratory analysis, and statistical testing.

## 🎯 Business Objective

The client — the Category Manager for chips — wanted to better understand:
- Who their chip-buying customers are (by lifestage and spending profile)
- What drives chip category sales
- Which customer segments to prioritise in the upcoming category strategic review

## 📂 Dataset

| File | Description |
|---|---|
| `QVI_transaction_data.xlsx` | ~265K point-of-sale transactions over 1 year (Jul 2018 – Jun 2019) |
| `QVI_purchase_behaviour.csv` | ~72K customers, segmented by `LIFESTAGE` and `PREMIUM_CUSTOMER` |


## 🧹 Data Cleaning & Preparation

- Removed non-chip products (salsa/dip items) using case-insensitive text matching
- Converted Excel serial date integers to proper datetime format
- Removed 1 duplicate transaction row
- Identified and removed an outlier customer (200 units purchased per transaction, twice in a year) — flagged as a likely commercial buyer rather than a retail customer
- Verified data completeness — confirmed a single missing date (25 Dec 2018 — Christmas Day, when stores are closed)
- Engineered new features from `PROD_NAME`:
  - `PACK_SIZE` — extracted numeric pack weight (g)
  - `BRAND` — extracted and standardised brand names (e.g. merged `RED`→`RRD`, `WW`→`WOOLWORTHS`, `SNBTS`→`SUNBITES`)
- Merged transaction and customer datasets on `LYLTY_CARD_NBR` with zero unmatched records

## 📊 Key Analysis & Insights

| Metric | Insight |
|---|---|
| **Total Sales by Segment** | Budget–Older Families, Mainstream–Young Singles/Couples, and Mainstream–Retirees drive the most category sales |
| **Customer Count** | Mainstream–Young Singles/Couples and Mainstream–Retirees have the largest customer bases |
| **Units per Customer** | Older Families and Young Families buy ~9 units/customer on average — the highest of any segment |
| **Price per Unit** | Mainstream Young/Midage Singles/Couples pay the highest price per unit ($4.07 / $3.99); confirmed **statistically significant** via independent t-test (p < 0.05) |
| **Brand Affinity** | Target segment (Mainstream–Young Singles/Couples) over-indexes on Tyrrells, Twisties, Doritos, Kettle, and Tostitos |
| **Pack Size Affinity** | Same segment prefers larger pack sizes (270g, 330g, 380g) over the category-average favourite (150g–175g) |
|**Pack Size Preference by Lifestage** | Analyzed how specific customer lifestages (e.g., Mainstream Young Singles/Couples) prefer particular pack sizes, visualized through a Python-based matplotlib bar chart to drive targeted category management strategies.|

## 💡 Commercial Recommendation

Target the **Mainstream – Young Singles/Couples** segment — the strongest combination of customer volume, price tolerance, and clear brand/pack-size preference — with increased shelf visibility and promotions for **Tyrrells, Doritos, and Kettle** in **larger pack formats (270g+)** ahead of the upcoming category review.

## 🛠️ Tools & Libraries

- `pandas` — data cleaning, transformation, aggregation
- `matplotlib` — visualisations
- `scipy.stats` — hypothesis testing (independent t-test)
- Google Colab — development environment

