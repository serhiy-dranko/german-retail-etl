# Exploratory Data Analysis — German Retail Transactions

## Dataset at a Glance

- Total transactions: [999]
- Date range: [06/05/2025] to [06/05/2026]
- Cities covered: Berlin, München, Hamburg, Frankfurt, Köln, Stuttgart, Düsseldorf, Leipzig
- Products covered: 8 (Kopfhörer, Laptop, Maus, Monitor, Smartphone, Tastatur, USB-Hub, Webcam)

---

## Key Findings

### 1. Revenue by City

Hamburg generates the highest total revenue (€ 494,351.48), followed closely by Stuttgart (€ 486,445.92). This is surprise me because larger cities such as Berlin and München might be expected to lead revenue generation due to their larger populations, yet both cities generated lower revenue than Hamburg and Stuttgart. Frankfurt appears to be underperforming relative to its economic importance and population size, generating the lowest revenue among the listed cities despite having one of the highest quantities sold. As a regional manager, the next question I would investigate is whether differences in revenue are driven by pricing, customer behavior or return rates across cities.

### 2. Product Performance

The product generating the highest revenue is Maus, with total revenue of €487,457.88, followed by Smartphone and Monitor in our TOP 3 list of products. Monitor has the highest average customer satisfaction score at 3.25, indicating strong customer approval. 

Tastatur represents a potential churn risk because it has relatively high sales volume (690 units sold) but the lowest satisfaction score (2.75), suggesting customers may be dissatisfied. 

Smartphones (2.88), USB-hubs (2.88) and Webcams (2.86) also show below-average satisfaction scores while generating important part of revenue. I would recommend that the product team should investigate customer feedback to identify quality, usability, or pricing issues and prioritize product improvements in these categories.

### 3. Return Rates

Stuttgart has the highest return rate at 21.64%, closely followed by Düsseldorf (21.43%) and Berlin (21.19%), suggesting returns are relatively consistent across most cities rather than being isolated to a single region.

The product with the highest number of returns is Laptop with 34 returns (4.73%), which also aligns with it being one of the higher-revenue and likely higher-value items in the catalog. 

There is a small pattern suggesting that higher value or more complex products (Laptops, Monitors) tend to have higher return counts, possibly due to higher customer expectations or compatibility issues, delivery issues (fraigle products).

This pattern could justify action such as reviewing product quality or specifications for laptops, improving given information (especially technical clarity) and analyzing whether returns are driven by defects, buyer misunderstanding or expectation mismatch rather than purely dissatisfaction after use.

### 4. Payment Methods

There is no clearly dominant payment method in this dataset. PayPal (26.63%) and Kreditkarte (26.23%) are almost identical in usage. And  Banküberweisung (23.92%) and Barzahlung (23.22%) also sit very close together, reinforcing that payment preferences are fairly evenly distributed across all four options.

The near-equal split between digital (PayPal, Kreditkarte, Banküberweisung) and more traditional or alternative methods suggests that customers have diverse payment preferences rather than a single trusted default.

### 5. Satisfaction Patterns

Across products, the overall average satisfaction score is approximately 3, which indicates a neutral customer experience rather than strong satisfaction.

The lowest-performing products are Tastatur (2.75), Webcam (2.86), and both Smartphone and USB-Hub (2.88), suggesting consistent dissatisfaction in peripherals and certain electronics categories. 

On the positive side, Monitor (3.25) and Kopfhörer (3.13) stand out as the most well received products, showing relatively better customer experience.

From a data reliability perspective, the results should be treated with caution because four satisfaction values were imputed using city level averages, which reduces variance and may artificially smooth differences between cities or products. In short, the dataset is usable for directional insights, but not precise performance benchmarking.

---

## Anomalies & Data Quality Notes

Several patterns in the dataset require caution before presenting results:

1. Added satisfaction scores (based on city averages) introduces artificial smoothing, which may hide true variability in customer experience. 
2. The existence of zero unit prices and previously removed invalid timestamps suggests that the raw data generation process is not fully stable and may require validation rules at the beginning.

Another notable issue is the weak but observable mismatch between high revenue products and their satisfaction and return performance. For example, laptops generate strong revenue but also show the highest return rate, which could signaling for product complexity or data inconsistency in return classification.

---

## Questions This Data Cannot Answer

What is the reason behind returns or low satisfaction scores?
   There is no qualitative feedback (return reason codes, reviews, or support tickets), so we cannot determine whether issues are due to product defects, shipping problems, or expectation mismatch.

How do marketing, pricing, or promotions influence sales?
   The dataset isn't have any information about discounts, campaigns or pricing dynamics over time. So we don't have ability to explain why certain products outperform others.

---

## Recommended Next Steps

[3 concrete, specific actions a German retail business could take based on your findings.
Not "improve satisfaction" — something like "investigate return rates in München for Laptops
before the Q4 campaign, as the 18% return rate is above the 12% city average"]


   1. Compare pricing strategy and customer expectations for Smartphones and Webcams, which generate strong revenue but relatively low satisfaction scores. If pricing is not aligned with perceived quality, consider targeted discounting before the next promo to reduce dissatisfaction and returns.

   2. Check return reasons and, if possible, segment by city to see high-return trend like in Stuttgart, Düsseldorf are driving disproportionate losses before increacing inventory for the quarter.

   3. Prioritize product review for Tastatur,Smartphone and USB-Hub, as these show consistently low satisfaction despite stable sales volume. Run a targeted customer feedback campaign.