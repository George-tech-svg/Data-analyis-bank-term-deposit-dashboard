
# Bank Term Deposit Dashboard (Power BI Project)

## Dashboard Preview

![Executive Dashboard](bank-term-deposit-dashboard (1)\bank-term-deposit-dashboard\screenshots\executive_dashboard)
![Customer Segmentation](bank-term-deposit-dashboard (1)\bank-term-deposit-dashboard\screenshots\<img width="779" height="486" alt="customer_segmentation" src="https://github.com/user-attachments/assets/e3d29d87-44c8-4b4a-886e-525e369f9f30" />
)
![Campaign Optimization](bank-term-deposit-dashboard (1)\bank-term-deposit-dashboard\screenshots\campaign_optimization.png)

## Overview
This project is a Power BI dashboard designed to help a bank improve its telemarketing campaigns for term deposit subscriptions.

The dashboard helps answer:
- Who should be contacted first
- Which customers are most valuable
- How to increase success rate while reducing costs

---

## Business Problem
The bank runs marketing campaigns through phone calls but faces challenges:
- Low subscription success rate
- High calling costs
- Poor targeting of customers

This dashboard provides data-driven insights to improve decision-making and campaign performance.

---

## Dataset
- Source: UCI Machine Learning Repository – Bank Marketing Dataset  
- File: `bank-full.csv`  
- Records: 45,211  
- Features: 17 columns  
- Target Variable: `y` (Yes/No – subscription)

---

## Tools Used
- Power BI Desktop  
- Power Query (Data Cleaning)  
- DAX (Data Analysis Expressions)  

---

## Data Preparation
The dataset was cleaned and transformed using Power Query:

- Replaced "unknown" values with null  
- Created Age Groups (Young, Mid, Retired, etc.)  
- Created Balance Tiers (Low, Medium, High)  
- Identified previously contacted customers  
- Removed outliers (age and call duration)  
- Sorted months correctly for time analysis  

---

## Key Metrics
- **Total Customers** – Number of people contacted  
- **Total Subscribed** – Customers who subscribed  
- **Subscription Rate (%)** – Campaign success rate  
- **Average Balance** – Customer financial strength  
- **Campaign Cost** – Total cost of calls  
- **Revenue** – Estimated income from subscriptions  
- **ROI (%)** – Profitability of campaign  

---

## Advanced Features
- **Priority Score** – Ranks customers based on likelihood to subscribe  
- **Subscription Probability** – Predicts customer behavior  
- **Customer Lifetime Value (CLV)** – Estimates long-term value  
- **Call Efficiency Analysis** – Measures effectiveness of calls  

---

## Dashboard Pages

### 1. Executive Dashboard
- Key KPIs (Success Rate, ROI, Cost)
- Monthly trends
- Top-performing customer segments

### 2. Customer Segmentation
- Performance by job and education
- Age group analysis
- Customer value insights

### 3. Campaign Optimization
- Best call duration
- Best months for campaigns
- Impact of previous campaigns

---

## Key Insights
- Retired customers have the highest subscription rate (~30%)  
- May and June have the highest campaign success  
- Previously contacted customers are 3x more likely to subscribe  
- High-balance customers show better conversion  
- Optimal call duration is between 200–500 seconds  

---

## Project Files
- `bank_term_deposit_dashboard.pbix` – Main Power BI dashboard  
- `dashboard.pdf` – Exported report  
- `screenshots/` – Dashboard previews  
- `cleaning_steps.txt` – Power Query transformations  
- `measures.txt` – DAX calculations  
- `bank-full.csv` – Dataset sample  

---

## How to Use
1. Download the `.pbix` file  
2. Open using Power BI Desktop  
3. Use filters (job, age, month)  
4. Interact with visuals to explore insights  

---

## Author
**George Onyango Ochieng**  

Data Analytics | Python Programming | Machine Learning | ICT  

Focused on building data-driven solutions for business insights, fintech, and decision-making.

---

## Contact
- Email: georgebabji1220@gmail.com  
- Phone: +254115136359  
- WhatsApp: +254111866769  

- Upwork: https://upwork.com/freelancers/~01ea729f5447c9e73b  
- LinkedIn: https://www.linkedin.com/in/george-onyango-5a5906360/  
- GitHub: https://github.com/George-tech-svg/Data-analyis-bank-term-deposit-dashboard  

---

## License
This project uses the UCI Bank Marketing Dataset for educational and portfolio purposes only.

---

## Final Note
This project demonstrates how data analytics can be used to improve marketing efficiency, reduce costs, and increase revenue through better decision-making.
