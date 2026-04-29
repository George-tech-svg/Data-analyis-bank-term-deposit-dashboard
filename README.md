# Bank Term Deposit Subscription Intelligence Dashboard

## Live Dashboard Preview

![Executive Dashboard](screenshots/executive_dashboard.png)
![Customer Segmentation](screenshots/customer_segmentation.png)
![Campaign Optimization](screenshots/campaign_optimization.png)

## Business Problem

A Portuguese banking institution wants to optimize its marketing campaign for term deposit subscriptions. The bank runs telemarketing campaigns but needs to identify which customers are most likely to subscribe, when to call them, and how to allocate marketing resources efficiently.

This dashboard answers three critical questions:
1. Which customers should the marketing team call first?
2. What is the expected return on investment for each customer segment?
3. How can the bank reduce call volume while increasing subscription rate?

## Dataset

- **Source:** UCI Machine Learning Repository – Bank Marketing Dataset
- **File:** bank-full.csv
- **Size:** 45,211 rows, 17 columns
- **Time period:** May 2008 to November 2010
- **Target variable:** y (yes/no – did customer subscribe to term deposit?)

## Tools Used

- Power BI Desktop
- Power Query (M language for data cleaning)
- DAX (measures and calculated columns)

## Data Cleaning Steps in Power Query

1. Replaced "unknown" values with null in job, education, contact, and poutcome columns
2. Created AgeGroup column (Young Adult, Early Career, Mid Career, Pre-Retirement, Retirement)
3. Created BalanceTier column (Overdraft, Low, Medium, High, Very High)
4. Created PreviouslyContacted flag (Yes/No based on pdays)
5. Created CallEfficiency column (Highly Efficient, Efficient, Inefficient, Standard)
6. Removed age outliers (filtered to 18-95 years)
7. Removed duration outliers (filtered to less than 5000 seconds)
8. Created MonthNumber column for proper chronological sorting

## Key DAX Measures

### Base Measures

**Total Customers**
Total Customers = COUNTROWS('bank-full')

**Total Subscribed**
Total Subscribed = CALCULATE(COUNTROWS('bank-full'), 'bank-full'[y] = "yes")

**Subscription Rate Percentage**
Subscription Rate % = DIVIDE([Total Subscribed], [Total Customers]) * 100

**Average Balance**
Average Balance = AVERAGE('bank-full'[balance])


**Average Call Duration**
Average Call Duration = AVERAGE('bank-full'[duration])


### Advanced Measures

**Campaign Cost (assuming $0.50 per call)**

Campaign Cost = [Total Customers] * 0.50


**Revenue Per Subscriber**
Revenue Per Subscriber = AVERAGEX(FILTER('bank-full', 'bank-full'[y] = "yes"), 'bank-full'[balance]) * 0.02


**Total Revenue**
Total Revenue = [Total Subscribed] * [Revenue Per Subscriber]


**Campaign ROI Percentage**
Campaign ROI % = DIVIDE([Total Revenue] - [Campaign Cost], [Campaign Cost]) * 100


**Call Efficiency Ratio**
Call Efficiency Ratio =
DIVIDE(
CALCULATE([Total Subscribed], 'bank-full'[duration] <= 200),
CALCULATE([Total Customers], 'bank-full'[duration] <= 200),
0
) * 100


## Calculated Columns Created

| Column Name | Description |
|-------------|-------------|
| AgeGroup | Groups age into 5 brackets (Young Adult to Retirement) |
| BalanceTier | Groups balance into 5 tiers (Overdraft to Very High) |
| PreviouslyContacted | Yes if pdays not -1, No if pdays = -1 |
| CallEfficiency | Highly Efficient (duration<101 & y=yes), Efficient (duration<201 & y=yes), Inefficient (duration>300 & y=no), else Standard |
| SubProbability | Weighted score from job, education, age, balance, and previous outcome (0-100) |
| CLVEstimate | Customer Lifetime Value Estimate based on balance tier |
| PriorityScore | Weighted combination of SubProbability (40%), balance (30%), call efficiency (20%), and previous contact (10%) |

## Dashboard Pages

### Page 1: Executive Dashboard
- Key metrics cards (Success Rate, Campaign Cost, ROI, Average Balance)
- Slicers for job, age group, and month
- Subscription rate by job type
- Monthly subscription trend
- Subscriptions by age group
- Balance distribution by subscription status
- Top 10 performing customer segments

### Page 2: Customer Segmentation
- Average priority score by job
- Average CLV estimate by job
- Average subscription probability by education
- Subscription rate heat map by age group and job

### Page 3: Campaign Optimization
- Call efficiency distribution by job
- Monthly subscription rate vs ROI
- Subscription rate by previous campaign outcome

## Key Insights

| Insight | Business Action |
|---------|-----------------|
| Retired customers have the highest subscription rate (28-32%) | Target retirement communities and pensioners |
| May and June deliver 18% success rate vs 8% in December | Concentrate marketing efforts in late spring |
| Customers with successful previous campaigns are 3x more likely to subscribe | Build loyalty programs for past responders |
| Higher balance customers show higher subscription rates | Offer premium products to high-balance segments |
| Calls between 200-500 seconds have highest conversion rates | Train agents to maintain optimal call length |

## Files in this Repository

| File | Description |
|------|-------------|
| bank_term_deposit_dashboard.pbix | Power BI file (open with Power BI Desktop) |
| bank_term_deposit_dashboard.pdf | PDF export for users without Power BI |
| screenshots/ | PNG screenshots of all dashboard pages |
| power_query/cleaning_steps.txt | M code for data transformation |
| dax_measures/measures.txt | All DAX formulas |
| data/bank-full.csv | Original dataset (first 100 rows sample) |

## How to Use This Dashboard

1. Download the bank_term_deposit_dashboard.pbix file
2. Open with Power BI Desktop (free version works)
3. Use slicers to filter by job, age group, and month
4. Hover over any visual for detailed tooltips
5. Navigate between pages using tabs at the bottom

## What-If Analysis (Optional Feature Not in Final Dashboard)

The dashboard was designed to include a what-if parameter for call duration targets, allowing users to see how changing call length affects subscription counts. This feature can be added by creating a parameter and measure as documented in the measures.txt file.

## License

This project uses the Bank Marketing Dataset from the UCI Machine Learning Repository for portfolio purposes only. The dataset is publicly available for research and educational use.

## Author

George Onyango Ochieng

Data Analytics | Python Programming | Machine Learning | ICT

Specializing in fraud detection, fintech analytics, and interactive dashboard development using Power BI, Python, and machine learning algorithms.

Certifications completed: Data Analytics (3 months), Python Programming (2.5 months), Machine Learning (4 months), Professional Foundation (3 months)

Connect with me for freelance data analytics and Power BI projects.

## Connect with Me
- Email:george babji1220@gmail.com
- Phone:+254115136359
- Whatsapp:+254111866769
- Upwork Profile: https://upwork.com/freelancers/~01ea729f5447c9e73b
- LinkedIn: https://www.linkedin.com/in/george-onyango-5a5906360/
- GitHub: https://github.com/George-tech-svg/Data-analyis-bank-term-deposit-dashboard
