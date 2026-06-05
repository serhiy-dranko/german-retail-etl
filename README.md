# German Retail ETL Pipeline

A complete end-to-end data project simulating a retail analytics pipeline for
8 German cities — built as part of a structured data learning curriculum.

---

## Project Summary

This project builds a simple end-to-end ETL pipeline that processes synthetic retail transaction data generated from Mockaroo. 
It extracts raw CSV sales records, cleans and standardizes the data in Google Sheets, improve it with calculated metrics such as total revenue and data quality flags, and loads the processed results into a dashboard-ready format for analysis. 
The final output enables analysis of product performance, regional sales differences, customer satisfaction, return behavior, and payment preferences. 
From this project, a user can learn how raw, inconsistent transactional data is transformed into structured business insights and how data quality issues directly impact reporting accuracy and decision making.

---

## The Data Value Chain in This Project

| Stage | What Happens in This Project |
|---|---|
| 1. Collection | Mockaroo generates synthetic retail transactions for 8 German cities |
| 2. Storage | Raw CSV saved to data/raw/ — unmodified, never edited |
| 3. Processing | Google Sheets: nulls handled, formats standardised, invalid rows removed |
| 4. Analysis | SUMIF/AVERAGEIF aggregations by city, product, payment method |
| 5. Visualization | Dashboard tab with KPI cards and 3 charts, labelled in German |
| 6. Insight | EDA findings — top city, return patterns, product satisfaction gaps |
| 7. Decision | Specific recommendations for store managers based on findings |

---

## Repository Structure


```
german-retail-etl/
│
├── README.md                  ← Main project documentation (biggest file today)
├── data/
│   ├── raw/
│   │   └── mockaroo_export.csv        ← Your original Mockaroo file, unmodified
│   └── cleaned/
│       └── german_retail_cleaned.csv  ← Exported cleaned_data tab from Day 2
├── analysis/
│   └── ANALYSIS.md            ← Your EDA findings written up
├── docs/
│   ├── pipeline.md            ← ETL pipeline documentation
│   ├── data_dictionary.md     ← What every column means
│   └── decisions.md           ← Why you made the choices you made
├── REFLECTIONS.md             ← Personal reflection connecting to career goals
├── LICENSE
└── README.md

```

---

## Pipeline at a Glance

[Extract] → [Raw Storage] → [Transform] → [Clean Storage] → [Load] → [Dashboard]
Mockaroo      data/raw/       Sheets        data/cleaned/    Sheets    Dashboard tab


---

## Key Findings

1. Hamburg is the highest revenue city with € 494,351.48, outperforming larger cities like Berlin (€420,601.00) and München (€384,555.27), suggesting that revenue is not strictly correlated with population size in this dataset.

2. Laptop shows the highest return rate at 4.73% (34 returns out of 719 orders), which is significantly higher than other products such as Kopfhörer (2.63%), indicating a potential quality or expectation mismatch for higher-value items.

3. Maus is the top revenue-generating product at €487,457.88, driven by the highest unit sales (783 units), making it the strongest overall contributor to product-level revenue performance

---

## Tools Used

| Tool | Purpose | Stage |
|---|---|---|
| Mockaroo | Synthetic data generation | Extract |
| Google Sheets | Cleaning, transformation, aggregation, dashboarding | Transform + Load |
| GitHub | Version control and documentation | Throughout |

---

## Google Sheets Workbook

[[ETL_Pipeline_German_Retail]](https://docs.google.com/spreadsheets/d/1pWYyMCEyost35KsXeJIOLMIdUPGNk8Q_bWxhlbyaF1Q/edit?usp=sharing)

---

## What I Learned

1. Spreadsheet-based ETL is transparent and easy to audit, but it becomes fragile quickly because a single formula or manual edit can silently change downstream results.
2. Return rates and satisfaction scores do not always move together, which means operational issues (returns) and perception issues (satisfaction) need to be analyzed separately rather than treated as the same signal.
3. Aggregated city-level insights can hide important product-level problems, so slicing data only by geography or only by product is not enough for decision making.

---

## About This Project

Built during Week 1 of a self-directed data learning curriculum.
Topics covered: data roles, ETL pipelines, data cleaning, EDA, and decision-making with data.

Serhiy Dranko · 05.05.2026