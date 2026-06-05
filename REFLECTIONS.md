# Reflections — Week 1 Data Learning

## What I Built This Week

This week I built a complete small-scale ETL pipeline using Mockaroo generated CSV data and Google Sheets as the main processing environment.

It includes a structured workflow with a raw_data tab for untouched source data, a cleaned_data tab for transformed and enriched records, and a dashboard tab that summarizes key business metrics such as revenue, return rates, product performance, and customer satisfaction. 

I implemented data cleaning rules (fixing city formatting, handling invalid quantities, removing corrupted timestamps), created calculated fields like total_revenue_eur and data_quality_flag, and built aggregated reports using SUMIF and AVERAGEIF formulas. 

The result is a fully working analytics pipeline that turns messy transactional data into structured insights suitable for making a business decision .

---

## Day-by-Day Connections

### Day 1 → Day 5
How did understanding data roles change how I approached this project?

Understanding data roles shifted this project from “just cleaning a dataset” to seeing it as a simplified version of real production workflows

Which role did I feel closest to while working — analyst, engineer, or scientist?

The analyst mindset felt the most natural, especially when building summaries, identifying patterns, and turning numbers into insights
The engineering side (structuring raw vs cleaned data, building repeatable steps) felt more mechanical and less intuitive.
The scientific part was present in the imputation and interpretation steps, but felt less dominant.

Which parts of the pipeline felt natural, and which felt unfamiliar?

Everything was familiar from my previous job, but now it's more organized.

### Day 2 → Day 5
What from the ETL theory on Day 2 did I only truly understand when I built it myself?

ETL theory only became real when I actually had to manually move data between raw, cleaned, and dashboard stages.

What surprised me about the Transform stage?

Google Sheets interface. A bit different logic if we compare with Microsoft products. 

What would I have done differently if I had to build the pipeline again from scratch?

If rebuilding the pipeline, I would define data validation rules earlier and reduce manual edits by structuring transformation logic more systematically from the start.


### Day 3 → Day 5
What was the messiest part of the data?
The messiest part of the data was inconsistent and invalid values (city formatting issues, zero prices, negative quantities, and one corrupted timestamp).

What would I have missed in the analysis if I had skipped cleaning entirely?

If cleaning had been skipped, key insights like product performance and regional return rates would have been misleading or partially incorrect

Did cleaning reveal anything about the data that changed my analysis?

Cleaning also revealed that some “patterns” (like differences in satisfaction) were partly influenced by missing value handling, not just real customer behavior.


### Day 4 → Day 5
Look at your three recommendations in ANALYSIS.md.

Are they genuinely data-driven, or are they assumptions dressed in numbers?

The recommendations are partly data-driven, but still subject to interpretation, especially when linking returns, satisfaction, and revenue to causal explanations.They are strong directional signals, but not proven causal relationships.

How would you measure whether those recommendations actually worked
if the store manager acted on them?

To measure whether they worked, I would track changes over time in returns, satisfaction, and repeat purchase rates for the affected products and cities, ideally comparing before/after periods or as pricing or product adjustments.

---

## What I Would Tell Someone Starting This Tomorrow

1. Don’t trust cleaned data just because it looks clean. Every rule you apply changes the story.
2. Record all changes in change_log 
3. Spend more time defining metrics before building dashboards, otherwise you will rebuild everything twice.

---

## Career Direction

Based on what I enjoyed and struggled with this week:
- The role I find most interesting is: [and why — be specific]

    Data Engineer, because I enjoyed building the ETL structure, separating raw and cleaned data, and thinking about how data flows instead of just analyzing outputs.

- The skill gap I need to close first is:

    Python for data processing, plus understanding how to build more automated and scalable pipelines instead of manual spreadsheet-based workflows.

- The type of data problem I want to work on eventually is:

    Data infrastructure and pipeline problems where messy raw data from different sources is transformed into reliable, analysis-ready datasets for business use.

---

## Open Questions

How can I build visually strong charts in Google Sheets and what actually makes a chart “good” for decision-making?
How can I reduce manual work in Google Sheets without immediately jumping to Python or SQL?

These become the agenda for Week 3.
