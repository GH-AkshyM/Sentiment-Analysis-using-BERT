# Sentiment-Analysis-using-BERT

## ↪️Overview:
IronPlay is an online retail business that experienced a decline in customer engagement and conversion rates despite increased spending on digital marketing. The purpose of this project is to analyze customer behavior, marketing performance, and customer feedback to understand what is going wrong and where improvements are needed.

The focus of this analysis is on:
- Conversion funnel performance
- Customer engagement across marketing content
- Customer feedback and sentiment

*I hope you will enjoy this read. Thank you for stopping by!!*

## Business Context:
Over recent months, IronPlay observed a steady decline in user interaction across both its website and marketing campaigns. Fewer visitors were progressing through the purchase journey and completing transactions, leading to a noticeable drop in conversion rates.

At the same time, marketing spend continued to increase, but this additional investment did not translate into corresponding revenue growth, raising concerns about traffic quality and campaign effectiveness.

In parallel, IronPlay accumulated a large volume of customer reviews and social media comments. While this feedback contained valuable signals about customer experience, it was not being analyzed in a structured or consistent way, making it difficult to identify recurring issues or priorities.

## 🎯Objectives:

### Improve Conversion Rates
- Identify where users drop off during the purchase journey
- Understand which channels and devices underperform
- Highlight friction points affecting checkout completion

### Improve Customer Engagement
- Compare engagement levels across different types of marketing content
- Identify channels that attract high-quality traffic
- Understand behavior differences between new and returning users

### Understand Customer Feedback
- Analyze customer reviews and social media comments
- Identify recurring positive and negative themes
- Link feedback patterns to engagement and conversion issues


## 🗂Data Overview
The analysis is based on:
- Website interaction and session data
- Conversion funnel data (visit → cart → purchase)
- Marketing campaign performance data
- Customer reviews and social media comments

The dataset is anonymized and structured to reflect a realistic e-commerce setup.

## 📊Approach


Data preparation and ETL were handled upstream in SQL to keep the model lean and consistent. Core business metrics were implemented in DAX to support interactive analysis across filters, slicers, and dimensions within the report.

Customer feedback required separate processing. Reviews and social media comments were analyzed using Python to derive sentiment labels and key themes and the results were saved and joined back with behavioral and conversion data for analysis.

You can find the SQL queries I used here:

### Sentiment analysis using Python

For sentiment analysis, I used Python since this wasn’t something that could be handled cleanly in SQL or DAX. I’m still a beginner with Python, so this part of the project involved a lot of trial and error. My basic programming background from college helped me follow the logic and debug issues, even when I didn’t fully understand everything at first.

I started with VADER(a pre-trained model) because it’s commonly used for reviews and social media text and was easy to get running. While it worked technically, the results didn’t feel right. Many reviews were labeled positive or neutral even when the wording clearly suggested dissatisfaction. After manually checking a sample of outputs, it was clear the model was missing context and nuance.

Since I wasn’t confident using those results, I went back and explored other options. I eventually switched to a RoBERTa-based sentiment model(another pre-trained model from 'Hugging Face'), which produced outputs that aligned much better with what the reviews were actually saying. The difference was noticeable, especially for longer comments and feedback that wasn’t explicitly positive or negative.

This part of the project took time, but it was a useful learning experience. More importantly, it reinforced the need to sanity-check model outputs instead of assuming they are correct just because they run without errors. The final sentiment results were saved and used in the analysis alongside conversion and engagement data.

You can find the python scripts here:

## 🖥Dashboard Highlights:
The IronPlay Analytics Dashboard is structured around three questions:

1. Are visitors converting? (Journey)

2. Are they still engaging with content? (Engagement)

3. What are customers actually saying? (Review)

Each page answers one question clearly, without mixing signals.



## 💡Key Findings
### test
## Year-over-Year Performance Overview

### 2023: Strong Baseline
2023 represents IronPlay’s healthiest year across all major dimensions. Conversion rates were high, revenue was at its peak, and engagement metrics showed consistent interaction across products and months. The funnel behaved as expected, with reasonable drop-offs and strong checkout completion.

This year serves as the benchmark for evaluating subsequent performance.

### 2024: Structural Decline
In 2024, performance declined sharply across multiple areas:
- Conversion rate dropped significantly compared to 2023
- Revenue fell by ~10%
- Engagement metrics (likes, clicks) declined faster than traffic volume

The most notable change was increased drop-off at the checkout stage, indicating friction after purchase intent was already established. At the same time, engagement quality deteriorated, suggesting that marketing campaigns were driving weaker or less relevant traffic.

This was not a seasonal dip. The decline was consistent across months and products, pointing to a structural issue rather than short-term volatility.

### 2025: Stabilization, Not Recovery
In 2025, metrics stopped deteriorating, but they did not return to 2023 levels:
- Conversion rate improved slightly versus 2024
- Revenue remained essentially flat
- Engagement collapsed further, especially likes and clicks

Purchases in 2025 appear to be driven by high-intent users and a small set of strong products, rather than by broad marketing effectiveness. While the funnel became more stable, the absence of engagement limits growth potential.
<details>
<summary>Journey – Yearly Views</summary>

**2023**
![Journey 2023](https://github.com/GH-AkshyM/Sentiment-Analysis-using-BERT/blob/main/Schreenshots/2023%20conversion.png)

**2024**
![Journey 2024](https://github.com/GH-AkshyM/Sentiment-Analysis-using-BERT/blob/main/Schreenshots/2024%20conversion.png)

**2025**
![Journey 2025](https://github.com/GH-AkshyM/Sentiment-Analysis-using-BERT/blob/main/Schreenshots/2025%20conversion.png)

</details>

## Conversion & Funnel Insights

Across all three years, the early funnel (homepage to product page) remains relatively healthy. Users show interest and browse products consistently.

The main breakdown occurs at checkout:
- Checkout retention dropped sharply in 2024
- Partial recovery in 2025, but still below 2023 levels

This suggests that pricing, checkout UX, shipping clarity, or trust signals are likely contributors. Importantly, this confirms the issue is **funnel efficiency**, not traffic volume.

## Product-Level Behavior

Product conversion analysis shows a clear shift over time:
- 2023 had a balanced mix of converting products
- 2024 leaned toward seasonal and outdoor products
- 2025 became highly concentrated around a few high-performing SKUs

In 2025, products like Hockey Stick, Climbing Rope, and Surfboard carry a disproportionate share of conversions. While these products perform well, this concentration increases business risk and limits scalability.

Mid-priced products consistently show stronger conversion than both low and high price extremes, indicating a clear pricing sweet spot.

## Engagement Trends (Root Cause)

Engagement metrics explain much of the conversion story:
- 2023 showed healthy interaction across views, likes, and clicks
- 2024 saw a steep drop, especially in likes and clicks
- 2025 engagement nearly flatlined

The decline in engagement happened faster than the decline in revenue. This indicates that marketing relevance and audience attention weakened before conversion stabilized. By 2025, engagement was no longer a reliable leading indicator.

In practical terms, IronPlay is currently selling **despite** marketing engagement, not because of it.

## Key Takeaways

- 2023 was the strongest operational baseline
- 2024 introduced structural issues, especially at checkout and in engagement quality
- 2025 shows stabilization, but not recovery
- The core problem is funnel efficiency and experience, not traffic volume
- Conversion is increasingly dependent on a small set of products
- Engagement decay limits future growth even if conversion stabilizes
- Customer sentiment supports product quality but highlights experience gaps


### test 
## 🛠Recommendations

## Recommendations

### 1. Fix Checkout Before Spending Another Dollar on Traffic
The data consistently shows that intent is not the problem — users reach product pages and enter checkout, but a large share fail to complete purchases. This issue emerged in 2024 and remains unresolved in 2025.

Before scaling marketing efforts, IronPlay should audit the checkout experience end-to-end, focusing on pricing transparency, shipping clarity, payment options, and friction points across devices. Improving checkout completion will deliver immediate gains because it acts on users who have already demonstrated purchase intent.

---

### 2. Treat Engagement as a Leading Indicator, Not a Vanity Metric
Engagement collapsed faster than revenue between 2023 and 2025, signaling declining relevance well before conversion stabilized. Likes and clicks are no longer predictive of sales, which means current campaigns are not building demand.

IronPlay should reset its engagement strategy by prioritizing fewer, higher-quality campaigns tied to specific products and use cases. Engagement metrics should be monitored as early warning signals, not success metrics, and poor-performing content should be retired quickly instead of optimized incrementally.

---

### 3. Double Down on Proven Products — but Reduce Concentration Risk
By 2025, conversion performance became heavily concentrated in a small set of products. While this keeps revenue stable in the short term, it increases dependency risk and limits scalability.

High-performing products should be used as anchors for growth through bundling, cross-selling, and focused campaigns. At the same time, underperforming but high-interest products should be selectively tested with improved product pages, pricing experiments, or social proof rather than being treated as lost causes.

---

### 4. Align Pricing Strategy to the Mid-Range Sweet Spot
Across all years, mid-priced products consistently outperform low and high price extremes in conversion. This pattern holds even as overall performance declines.

Instead of aggressive discounting or premium expansion, IronPlay should optimize around its strongest price band. Pricing tests, bundles, and promotions should be designed to pull users toward this range, where confidence and perceived value are highest.

---

### 5. Shift from Global Campaigns to Geo-Specific Execution
Conversion performance varies significantly by country, and leadership changes year over year. This indicates that a single global strategy is inefficient.

IronPlay should focus marketing and merchandising efforts on consistently high-converting regions and adapt messaging, pricing, or fulfillment strategies locally. Geo-specific execution offers higher ROI than increasing overall reach.

---

### 6. Use Customer Feedback as a Diagnostic Layer, Not Just Social Proof
Sentiment analysis and ratings show that customers generally like the products, which rules out product quality as the primary issue. This makes customer feedback more valuable as a diagnostic tool than as a promotional asset.

Recurring themes in feedback should be reviewed alongside funnel drop-offs to identify experience-related friction. Closing this loop will help prioritize fixes that actually improve conversion rather than surface-level optimizations.

---

### 7. Measure Recovery Against 2023, Not Year-over-Year Noise
Small improvements in 2025 may appear positive in isolation, but they remain well below the 2023 baseline. Treating stabilization as recovery risks masking unresolved issues.

All future performance should be benchmarked against 2023 funnel health, engagement quality, and product mix. Growth should only be declared once those benchmarks are meaningfully exceeded.


### Customer Experience
- Address delivery-related complaints
- Improve clarity around pricing and shipping timelines
- Monitor customer feedback regularly instead of ad-hoc reviews
