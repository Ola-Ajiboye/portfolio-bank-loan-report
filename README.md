# Bank-Loan-Report

## OVERVIEW
The Bank Loan Report provides a comprehensive analysis to monitor and assess our bank's lending activities and performance, we need to create a comprehensive Bank Loan Report. This report aims to provide insights into key loan-related metrics and their changes over time. The report will help us make data-driven decisions, track our loan portfolio's health, and identify trends that can inform our lending strategies.

### DATA SOURCE
The dataset used for this analysis was downloaded from Kaggle 
### TOOLS
Microsoft Excel – Data Cleaning and Creating a report
SQL Server – Data Analysis
DATA CLEARNING 
Data Cleaning: This involved removing duplicated, fixing inconsistencies, handle missing values, standardize formats, and ensure data accuracy.

## EXPOLARATORY DATA ANALYSIS
EDA provide a clear and insightful view of our lending operations, facilitating data-driven decision-making and enabling us to gain valuable insights into various loan parameters. Below are some of the specific requirements.


![cicc](https://github.com/user-attachments/assets/3a6500d7-87c5-43e6-9afc-bfc682b496a3)


•	Monthly Trends by Issue Date
•	Regional Analysis by State
•	Loan Term Analysis 
•	Employee Length Analysis 
•	Loan Purpose Breakdown 
•	Home Ownership Analysis

## DATA ANALYSIS
### Monthly Trends by Issue Date
Track monthly changes in key metrics such as Total Loan Applications, Total Funded Amount, and Total Amount Received
```sql
SELECT 
MONTH(ISSUE_DATE) AS MONTH_Number,
DATENAME (MONTH, ISSUE_DATE) AS MONTH_NAME,
COUNT(ID) AS TOTAL_LOAN_APPLICATION,
SUM(LOAN_AMOUNT) AS TOTAL_AMOUNT_FOUNDED,
SUM(TOTAL_PAYMENT) AS TOTAL_AMOUNT_RECEIVED
FROM financial_loan
GROUP BY MONTH(ISSUE_DATE), DATENAME (MONTH, ISSUE_DATE)
ORDER BY MONTH(ISSUE_DATE), DATENAME (MONTH, ISSUE_DATE)
```

![xx](https://github.com/user-attachments/assets/2b0af339-a2db-48d5-b930-e48265336e1c)


   Insight: A line chart visualizing these metrics over time will uncover monthly trends and seasonal variations. By identifying periods of higher or lower demand, the bank can forecast future lending volumes and adjust resources accordingly.

### Regional Analysis by State
Understand the geographic distribution of lending activity by tracking Total Loan Applications, Total Funded Amount, and Total Amount Received per state.
SELECT 
```sql
ADDRESS_STATE AS STATE,
COUNT(ID) AS TOTAL_LOAN,
SUM(LOAN_AMOUNT) AS TOTAL_AMOUNT,
SUM(TOTAL_PAYMENT) AS TOTAL_AMOUNT_RECEIVED
FROM financial_loan
GROUP BY ADDRESS_STATE
ORDER BY ADDRESS_STATE
```

Insight: A filled map illustrating state-by-state lending metrics reveals regions with high and low lending activity, allowing the bank to identify areas with growth potential or underserved markets.
   
   ### Loan Term Analysis 
   Assess the distribution of loans by term length, such as 36-month or 60-month loans.
```sql
SELECT 
ADDRESS_STATE AS STATE,
COUNT(ID) AS TOTAL_LOAN,
SUM(LOAN_AMOUNT) AS TOTAL_AMOUNT,
SUM(TOTAL_PAYMENT) AS TOTAL_AMOUNT_RECEIVED
FROM financial_loan
GROUP BY ADDRESS_STATE
ORDER BY ADDRESS_STATE
```

   Insight: A donut chart depicting loan term distribution will highlight borrower preferences for short or long-term loans, helping the bank understand which term lengths are most popular and evaluate associated risks.
   
### Employee Length Analysis 
  Analyze loan metrics based on borrower employment length categories (e.g., 1 year, 5 years, 10+ years).
```sql
SELECT
EMP_LENGTH AS EMPLOYMENT_LENGTH,
COUNT(ID) AS TOTAL_LOAN,
SUM(LOAN_AMOUNT) AS TOTAL_AMOUNT,
SUM(TOTAL_PAYMENT) AS TOTAL_AMOUNT_RECEIVED
FROM financial_loan
GROUP BY EMP_LENGTH 
ORDER BY EMP_LENGTH 
```

   Insight: A bar chart showing loan applications and funded amounts by employment length can reveal how employment stability correlates with lending activity and repayment reliability.
   
### Loan Purpose Breakdown 
   Categorize loans by purpose (like small business, debt consolidation, credit card, car, home improvement) to understand borrower needs.
```sql
SELECT 
PURPOSE AS LOAN_PURPOSE
COUNT(ID) AS TOTAL_LOAN_APPLICATION,
SUM(LOAN_AMOUNT)AS TOTAL_FOUNDED_AMOUNT,
SUM(TOTAL_PAYMENT) AS TOTAL_AMOUNT_RECEIVED
FROM financial_loan
GROUP BY PURPOSE
ORDER BY PURPOSE
```

   Insight: A bar chart showing loan purposes highlights primary reasons for borrowing, informing the bank about popular loan uses and emerging customer needs.

### Home Ownership Analysis
  Examine loan distribution based on home ownership status (e.g., own, rent, mortgage).
  
```sql
SELECT
HOME_OWNERSHIP AS HOME_OWNERSHIP,
COUNT(ID) AS TOTAL_LOAN_APPLICATION,
SUM(LOAN_AMOUNT)AS TOTAL_FOUNDED_AMOUNT,
SUM(TOTAL_PAYMENT) AS TOTAL_AMOUNT_RECEIVED
FROM financial_loan
GROUP BY HOME_OWNERSHIP
ORDER BY HOME_OWNERSHIP
```

 Insight: A tree map displaying loan metrics by home ownership status provides a hierarchical view of how property ownership impacts lending demand and risk. Homeowners may demonstrate lower risk profiles, while renters or those with mortgages may have different lending needs.

 ###  Recommendation
If certain months show consistently high loan applications, consider increasing marketing and operational resources during these periods. In contrast, during low-demand months, focus on efficiency and cost-saving measures.
For states with high lending activity, consider investing in targeted customer service support and localized marketing campaigns. For regions with low activity, conduct a deeper analysis to understand potential barriers and explore tailored lending programs to stimulate growth.
If longer-term loans are more popular, ensure the bank’s risk management strategy accommodates the increased credit risk. Alternatively, consider promoting shorter-term loans to balance the portfolio’s risk exposure.
If longer employment correlates with higher loan repayment rates, consider refining eligibility criteria to favor applicants with stable employment histories. Alternatively, introduce flexible terms for applicants with shorter employment durations but high potential creditworthiness.
For popular purposes like debt consolidation, consider offering specialized loan packages with competitive rates. If certain purposes show high repayment reliability, tailor promotional efforts to emphasize these options.
Consider creating targeted loan products for homeowners (e.g., home improvement loans) and developing flexible lending terms for renters. Use ownership status as an additional risk factor when evaluating applications, particularly in high-risk markets.

### Conclusion
The comprehensive analysis of monthly trends, regional activity, loan terms, employment history, loan purpose, and home ownership offers a holistic view of the bank’s lending operations. By identifying trends, segmenting borrowers, and understanding risk factors, the bank can make data-driven adjustments to its lending strategy, focusing on areas of opportunity while managing risk. These insights empower the bank to allocate resources efficiently, enhance customer engagement, and ultimately support sustainable growth in lending operations.

