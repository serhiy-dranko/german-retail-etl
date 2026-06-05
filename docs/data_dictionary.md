## Data Dictionary — German Retail Transactions

### raw dataset (`mockaroo_export.csv`)


| Column | Data Type | Description | Example Value | Notes |
|---|---|---|---|---|
| transaction_id | Integer | Unique identifier for each transaction | 1, 2, 3 | Auto-incremented by Mockaroo |
| timestamp | Datetime | Date and time of transaction | 2024-03-15 14:22:00 | Format: YYYY-MM-DD HH:MM:SS |
| customer_name | String | Full name of the customer | Anna Müller | Synthetic — not real |
| city | String | German city where sale occurred | Berlin | One of 8 cities |
| product | String | Product purchased | Laptop | One of 8 products |
| category | String | Product category | Electronics | Electronics or Zubehör |
| quantity | Integer | Number of units purchased | 3 | Should be ≥ 1 |
| unit_price_eur | Float | Price per unit in euros | 849.99 | 2 decimal places |
| payment_method | String | How the customer paid | Kreditkarte | One of 4 methods |
| satisfaction_score | Integer | Customer satisfaction rating | 4 | Scale 1–5 |
| returned | String | Whether item was returned | Nein | Ja or Nein |

### cleaned dataset (`german_retail_cleaned.csv`)

All columns from raw_data, plus:

| Column | Data Type | Description | Example Value | Notes |
|---|---|---|---|---|
| total_revenue_eur | Float | quantity × unit_price_eur | 2549.97 | Derived field added during Transform |
| data_quality_flag | String | Row-level quality marker | OK | OK or REVIEW — see pipeline.md |
