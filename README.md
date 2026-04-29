# Bank Term Deposit Subscription Dashboard

## Live Dashboard Preview

![Executive Dashboard](screenshots/executive_dashboard.png)
![Customer Segmentation](screenshots/customer_segmentation.png)
![Campaign Optimization](screenshots/campaign_optimization.png)

---

## What Problem Does This Dashboard Solve?

A bank in Portugal runs telemarketing campaigns to sell term deposits. But they have a problem. They do not know which customers to call first. They do not know when to call. They waste money calling the wrong people.

This dashboard answers three simple questions:

1. Which customers should the marketing team call first?
2. How much money will the bank make from each customer segment?
3. How can the bank call fewer people but get more subscriptions?

---

## About the Data

| Item | Details |
|------|---------|
| Source | UCI Machine Learning Repository |
| File name | bank-full.csv |
| Number of rows | 45,211 customers |
| Number of columns | 17 |
| Time period | May 2008 to November 2010 |
| What we are predicting | Whether a customer will subscribe (yes or no) |

---

## Tools I Used

- Power BI Desktop – to build the dashboard
- Power Query – to clean the data
- DAX – to create calculations and measures

---

## The Original Columns (Before Cleaning)

These are the columns that came with the dataset:

| Column Name | What It Means |
|-------------|---------------|
| age | Customer's age in years |
| job | Type of job (admin, blue-collar, retired, student, etc.) |
| marital | Married, single, or divorced |
| education | Primary, secondary, or tertiary |
| default | Does the customer have credit default? (yes or no) |
| balance | Average yearly account balance |
| housing | Does the customer have a housing loan? (yes or no) |
| loan | Does the customer have a personal loan? (yes or no) |
| contact | How the customer was contacted (cellular or telephone) |
| day | Day of the month when last contacted |
| month | Month of the year when last contacted |
| duration | Length of the last call in seconds |
| campaign | Number of calls made during this campaign |
| pdays | Days since previous campaign contact (-1 means never contacted) |
| previous | Number of contacts before this campaign |
| poutcome | Outcome of the previous campaign (success or failure) |
| y | Did the customer subscribe? (yes or no) – this is our target |

---

## New Columns I Created (After Cleaning)

I created these columns to get better insights:

| Column Name | What It Means |
|-------------|---------------|
| AgeGroup | Young Adult, Early Career, Mid Career, Pre-Retirement, Retirement |
| BalanceTier | Overdraft, Low, Medium, High, Very High |
| PreviouslyContacted | Yes if contacted before, No if never contacted |
| CallEfficiency | Highly Efficient, Efficient, Inefficient, or Standard |
| SubProbability | Score from 0 to 100 showing how likely a customer is to subscribe |
| CLVEstimate | Customer Lifetime Value estimate in dollars |
| PriorityScore | Combined score from 0 to 100 telling who to call first |
| MonthNumber | Number from 1 to 12 to sort months correctly (Jan=1, Dec=12) |

---

## How I Cleaned the Data in Power Query

1. Changed "unknown" values to empty (null) so they do not affect calculations
2. Created AgeGroup column to group customers by age brackets
3. Created BalanceTier column to group customers by how much money they have
4. Created PreviouslyContacted column to know if a customer was contacted before
5. Created CallEfficiency column to measure how effective each call was
6. Removed customers younger than 18 and older than 95 (outliers)
7. Removed calls longer than 5000 seconds (too long to be realistic)
8. Created MonthNumber column to sort months from January to December

---

## Key Calculations (DAX Measures)

**Total Customers**
Total Customers = COUNTROWS('bank-full')

text

**Total Subscribed**
Total Subscribed = CALCULATE(COUNTROWS('bank-full'), 'bank-full'[y] = "yes")

text

**Subscription Rate Percentage**
Subscription Rate % = DIVIDE([Total Subscribed], [Total Customers]) * 100

text

**Average Balance**
Average Balance = AVERAGE('bank-full'[balance])

text

**Average Call Duration**
Average Call Duration = AVERAGE('bank-full'[duration])

text

**Campaign Cost (assuming $0.50 per call)**
Campaign Cost = [Total Customers] * 0.50

text

**Revenue Per Subscriber**
Revenue Per Subscriber = AVERAGEX(FILTER('bank-full', 'bank-full'[y] = "yes"), 'bank-full'[balance]) * 0.02

text

**Total Revenue**
Total Revenue = [Total Subscribed] * [Revenue Per Subscriber]

text

**Campaign ROI Percentage**
Campaign ROI % = DIVIDE([Total Revenue] - [Campaign Cost], [Campaign Cost]) * 100

text

**Call Efficiency Ratio**
Call Efficiency Ratio =
DIVIDE(
CALCULATE([Total Subscribed], 'bank-full'[duration] <= 200),
CALCULATE([Total Customers], 'bank-full'[duration] <= 200),
0
) * 100

text

---

## What You Will Find on Each Dashboard Page

### Page 1: Executive Dashboard
- Key numbers: Success Rate, Campaign Cost, ROI, Average Balance
- Filters to slice by job, age group, and month
- Chart showing subscription rate by job type
- Chart showing monthly subscription trends
- Chart showing subscriptions by age group
- Chart showing balance distribution for subscribers vs non-subscribers
- Table showing top 10 customer segments

### Page 2: Customer Segmentation
- Average priority score by job
- Average customer lifetime value by job
- Average subscription probability by education level
- Heat map showing subscription rates by age group and job

### Page 3: Campaign Optimization
- Call efficiency distribution by job
- Monthly subscription rate compared to monthly ROI
- Subscription rate by previous campaign outcome

---

## What I Learned From This Data

| Finding | What The Bank Should Do |
|---------|------------------------|
| Retired customers have the highest subscription rate (28-32%) | Call retired customers first |
| May and June have 18% success rate, December only 8% | Run more campaigns in late spring |
| Customers with successful past campaigns are 3x more likely to subscribe again | Focus on past successful customers |
| Customers with higher balances subscribe more | Offer premium products to rich customers |
| Calls between 200 and 500 seconds work best | Train callers to keep conversations in this range |

---

## Files in This Repository

| File | What It Is |
|------|-------------|
| bank_term_deposit_dashboard.pbix | The Power BI file (open with Power BI Desktop) |
| bank_term_deposit_dashboard.pdf | PDF version for people without Power BI |
| screenshots/ | Pictures of all three dashboard pages |
| power_query/cleaning_steps.txt | All the Power Query M code I wrote |
| dax_measures/measures.txt | All the DAX formulas I created |
| data/bank-full.csv | The original dataset (first 100 rows only) |

---

## How to Use This Dashboard

1. Download the file called `bank_term_deposit_dashboard.pbix`
2. Open it with Power BI Desktop (it is free)
3. Use the buttons on the left to filter by job, age group, or month
4. Hover your mouse over any chart to see more details
5. Click the tabs at the bottom to switch between the three pages

---

## My Certificates

| Certificate | Link |
|-------------|------|
| Data Analytics | [View Certificate](https://savanna.alxafrica.com/certificates/T95s3SPMxZ) |
| Data Science | [View Certificate](https://savanna.alxafrica.com/certificates/flJS2ZXs6r) |
| Professional Foundations | [View Certificate](https://savanna.alxafrica.com/certificates/RYz9rB28SJ) |
| Python Programming | [View Certificate](https://savanna.alxafrica.com/certificates/Ee8x6JfGCh) |
| Machine Learning | [View Certificate](https://savanna.alxafrica.com/certificates/7zsMrEN5m2) |

---

## About Me

**George Onyango Ochieng**

I work with data. I clean it, analyze it, and turn it into dashboards that help businesses make better decisions.

I have completed certificates in:
- Data Analytics (3 months)
- Python Programming (2.5 months)
- Machine Learning (4 months)
- Professional Foundation (3 months)

I build dashboards using Power BI, Python, and machine learning. I focus on fintech, fraud detection, and customer analytics.

I am looking for freelance data analytics and Power BI work.

---

## Contact Me

- **Call or Text:** +254115136359
- **WhatsApp:** +254111866769
- **Email:** georgebabji1220@gmail.com
- **Upwork:** https://upwork.com/freelancers/~01ea729f5447c9e73b
- **LinkedIn:** https://www.linkedin.com/in/george-onyango-5a5906360/
- **GitHub:** https://github.com/George-tech-svg/Data-analyis-bank-term-deposit-dashboard
