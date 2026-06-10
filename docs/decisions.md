# Decision Log

## Decision 1 — Imputing missing satisfaction scores with city average

**Date:** 05.06.2026
**Context:** 4 rows had blank satisfaction_score values after extraction

**Options considered:**
- Delete the rows entirely
- Impute with the overall dataset average
- Impute with the city-level average
- Leave as NULL

**Decision:** Imputed with city-level average
**Reason:** City-level average is more contextually accurate than the overall average.
Deleting rows would unnecessarily reduce dataset size.
**Risk:** Imputed values reduce variance in satisfaction data. Any analysis of
satisfaction score distributions should note that 4 values are estimated, not real.

---

## Decision 2 — Deleting the 1899 timestamp row rather than correcting it

**Context:** One row had a timestamp year of 1899 (row 666) — clearly a data entry error

**Options considered:**
- Attempt to guess the correct date
- Replace with today's date
- Delete the row
- Keep and flag it

**Decision:** Delete the row
**Reason:** It's better not to guess the date and exclude the data before we find the cause of this error
**Risk:** The total summary does not include items sold in this order.

---

## Decision 3 — Setting zero-price rows to NULL rather than estimating a price

**Context:** Three rows had a quantity =< 0  — clearly a data entry error

**Options considered:**
- Attempt to guess the correct quantity
- Replace with 0
- Delete the row
- Keep and flag it


**Decision:** Replace with 0
**Reason:** It's better not to guess a quantity and replace by 0 before we find the cause of this error
**Risk:** The total summary does not include items quantity in this orders.

---

## Decision 4 — Using SUMIF/AVERAGEIF formulas rather than pivot tables

**Context:** Need to aggregate data by city, product, and payment method for reporting.

**Options considered:**
 - Pivot tables
 - Fill in tables manually using a calculator
 - SUMIF / AVERAGEIF formulas

 **Decision:** Use SUMIF / AVERAGEIF formulas
 **Reason:** To understand how aggregations work under the hood and build transferable SQL thinking instead of relying on automated pivot logic.
 **Risk:** More manual work and higher chance of formula errors compared to pivot tables.

---

## Decision 5 — Keeping the raw_data tab unedited and copying to cleaned_data

[Why is this separation important? What would break if you edited raw_data directly?]

**Context:** The dataset needed cleaning and transformation before analysis, but also required a reliable source of truth for debugging and auditability.

**Options considered:**
 - Clean everything in the same sheet
 - Edit raw_data directly
 - Copy raw_data into a separate cleaned_data tab

 **Decision:** Copy raw_data into a separate cleaned_data tab
 **Reason:** This preserves the original dataset as an immutable source of truth while allowing transformations, corrections, and feature creation without risking data loss or overwriting mistakes.
 **Risk:** Everything is still manual, so if the file is lost or broken, the whole ETL pipeline is gone.
