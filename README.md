# Sentiment-Analysis-using-BERT

## ↪️Overview:
IronPlay is an online retail business that experienced a decline in customer engagement and conversion rates despite increased spending on digital marketing. The purpose of this project is to analyze customer behavior, marketing performance, and customer feedback to understand what is going wrong and where improvements are needed.

The focus of this analysis is on:
- Conversion funnel performance
- Customer engagement across marketing content
- Customer feedback and sentiment



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

---

## Approach

Data preparation and ETL were handled upstream in SQL to keep the model lean and consistent. Core business metrics were implemented in DAX to support interactive analysis across filters, slicers, and dimensions within the report.

Customer feedback required separate processing. Reviews and social media comments were analyzed using Python to derive sentiment labels and key themes and the results were saved and joined back with behavioral and conversion data for analysis.

You can find the SQL queries I used here:

### Sentiment analysis using Python

For sentiment analysis, I used Python since this wasn’t something that could be handled cleanly in SQL or DAX. I’m still a beginner with Python, so this part of the project involved a lot of trial and error. My basic programming background from college helped me follow the logic and debug issues, even when I didn’t fully understand everything at first.

I started with VADER because it’s commonly used for reviews and social media text and was easy to get running. While it worked technically, the results didn’t feel right. Many reviews were labeled positive or neutral even when the wording clearly suggested dissatisfaction. After manually checking a sample of outputs, it was clear the model was missing context and nuance.

Since I wasn’t confident using those results, I went back and explored other options. I eventually switched to a RoBERTa-based sentiment model, which produced outputs that aligned much better with what the reviews were actually saying. The difference was noticeable, especially for longer comments and feedback that wasn’t explicitly positive or negative.

This part of the project took time, but it was a useful learning experience. More importantly, it reinforced the need to sanity-check model outputs instead of assuming they are correct just because they run without errors. The final sentiment results were saved and used in the analysis alongside conversion and engagement data.

You can find the python scripts here:

## Key Findings

### Conversion
- Significant drop-off at the cart and checkout stages
- Mobile users convert at a lower rate than desktop users
- Some paid campaigns generate traffic but poor conversion

### Engagement
- Product-focused and informational content performs better than purely promotional content
- Returning users show higher engagement than first-time visitors
- Engagement varies significantly by marketing channel

### Customer Feedback
**Frequent negative themes:**
- Delivery delays
- Pricing concerns
- Checkout experience issues

**Frequent positive themes:**
- Product quality
- Customer support

---

## Recommendations

### Conversion
- Simplify checkout and reduce unnecessary steps
- Improve mobile checkout experience
- Introduce cart abandonment follow-ups

### Engagement
- Shift focus toward high-performing content types
- Reduce spend on low-quality traffic sources
- Personalize campaigns based on user behavior

### Customer Experience
- Address delivery-related complaints
- Improve clarity around pricing and shipping timelines
- Monitor customer feedback regularly instead of ad-hoc reviews

---

## Tools Used
- Power BI
- SQL
- Excel

---

## Notes
This project is designed to reflect how a data analyst would approach a real e-commerce performance problem: starting with business questions, validating them with data, and ending with practical recommendations.

---

Author: *Your Name*  
Role: Data Analyst
