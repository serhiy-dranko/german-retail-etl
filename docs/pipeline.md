# ETL Pipeline Documentation

## Overview

This ETL pipeline processes transactional sales data generated from Mockaroo and prepares it for business reporting and analysis. The pipeline extracts raw CSV data, applies data quality corrections and enrichment rules in Google Sheets, and loads the cleaned dataset into reporting dashboards for business users.

---

## Pipeline Diagram

[Extract] → [Raw Storage] → [Transform] → [Clean Storage] → [Load] → [Dashboard]
Mockaroo      data/raw/       Sheets        data/cleaned/    Sheets    Dashboard tab

---

## Stage 1 — Extract

**Source:** Mockaroo (mockaroo.com)
**Format:** CSV
**Row count:** 1000 rows
**Fields:** transaction_id, timestamp, customer_name, city, product, category, quantity, unit_price_eur, payment_method, satisfaction_score, returned
**Known issues at extraction:** 

    - City values contained inconsistent capitalization and formatting (berlin, MÜNCHEN).
    - Quantity contained invalid values (0 and negative quantities).
    - Unit price contained zero values that were treated as missing data.
    - Satisfaction score had missing values that were imputed using the average score by city.
    - One record contained an invalid timestamp (1899-01-01 01:01:01) and was removed.
    - total_revenue_eur was not present in the source data and was derived as quantity * unit_price_eur.
    - data_quality_flag was not present in the source data and was created using validation rules to identify records requiring review.

---

## Stage 2 — Transform

### 2a — Cleaning

| Issue | Rows Affected | Rule Applied | Outcome |
|---|---|---|---|
| Lowercase city names | 3 | Standardised to title case | Fixed |
| Invalid quantity (≤ 0) | 3 | Set to 1 | Fixed |
| Missing satisfaction score | 4 | Imputed with city average | Estimated — flagged |
| Zero unit price | 2 | Set to NULL | Flagged for review |
| Invalid timestamp (1899) | 1 | Row deleted | Removed |

### 2b — Enrichment

| New Column | Formula Logic | Reason Added |
|---|---|---|
| total_revenue_eur | quantity * unit_price_eur | Required for revenue analysis |
| data_quality_flag | OR check on quality fields | Transparency for downstream users |

### 2c — Aggregation (Google Sheets formulas used)

| Summary Table | Formula Used | Sheet Tab |
|---|---|---|
| Revenue by City | SUMIF, COUNTIF, AVERAGEIF | transformed_data |
| Returns Analysis by City | COUNTIFS | transformed_data |
| Product Performance | SUMIF, AVERAGEIF | transformed_data |
| Payment Method Breakdown | COUNTIF | transformed_data |

---

## Stage 3 — Load

**Destination:** Google Sheets `dashboard` tab + CSV exports in `data/cleaned/`
**Consumers:** Store manager / business analyst
**Refresh cadence:** Manual — data must be re-exported when source updates

---

## Tool Used at Each Stage

| Stage | Tool | Why |
|---|---|---|
| Extract | Mockaroo | Free, realistic synthetic data with custom fields |
| Store raw | Google Sheets (`raw_data` tab) | Accessible, no setup required |
| Transform | Google Sheets formulas + manual fixes | Visible, auditable, beginner-friendly |
| Store clean | Google Sheets (`cleaned_data` tab) + CSV export | Portable and shareable |
| Load | Google Sheets (`dashboard` tab) | Charts and KPI cells without extra tools |

---

## Limitations of This Pipeline

1. Limited scalability
Google Sheets performs well for small datasets but may become slow or unreliable with significantly larger volumes of data.

2. Manual refresh process
The pipeline is not automated. New source data must be manually exported, uploaded, transformed, and loaded into the dashboard.

3. No automated data validation before loading
Data quality checks rely on formulas and manual review rather than a dedicated validation framework.

4. Single-user maintenance process
Data cleaning and transformation steps are performed manually, making the process dependent on the knowledge and availability of the individual maintaining the spreadsheet.