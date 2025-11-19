# AML_analysis_portfolio
## 📌 Project Overview
In this project, I started with a dataset of 100 Pakistan-based transactions. After analyzing the data, I identified 21 high-risk customers. Out of these, I further investigated and restricted 20 customers based on suspicious activity.

Finally, I focused on 8 high-risk customers, whose transactions were highlighted in the Suspicious Transaction Report (STR) for compliance purposes.
## Step 1: Data Import & Cleaning

First, I imported the dataset into Excel for analysis. The original dataset contained the following columns:
`transaction_id, customer_id, customer_name, age, gender, city, account_type, account_open_date,
transaction_date, transaction_type, amount_PKR, currency, channel, counterparty_country, is_cash` 
For analysis purposes, I created additional helper columns:
`risk_score, auto_flag, T_type_point, Amount_points, Country_points, is_cash`
These helper columns were used to calculate risk levels and highlight suspicious activity.
## Step 2: Applying Rules to Identify Suspicious Transactions

Next, I applied additional rules to detect suspicious transactions. For this, I created the following helper columns:
`Country_count, is_cash_points, txn_count, num_high_risk_countries, cash_txn_count,
high_val_trans, round_amount_flag, per_day_cos_deposit_withdrawl, newacc_high_trans`
Finally, I consolidated the results into a Suspicious_Customer column.
Customers who met 2 or more risk criteria were considered high-risk.
This resulted in 20 high-risk customers.
## Step 3: Focusing on High-Risk Customers

From the suspicious transactions dataset, I separately added the 21 customers identified as risky.
After the further analysis, I found 6 high-risk customers who required immediate action. These analysis include:
Reviewing transaction patterns for unusual frequency or amounts

Checking cash transactions vs non-cash transactions
Looking for transactions with high-risk countries
Identifying round amounts or high-value transactions
Evaluating new accounts with unusually high activity

These customers are: 
`Usman Javed, Ahmed Javed, Sara Saeed, Huma Butt, Ayesha Qureshi and Usman Qureshi`
## Step 4: Creating the Suspicious Transaction Report (STR)

After identifying the high-risk customers, I created a Suspicious Transaction Report (STR) using the template from FMU Pakistan.
I entered all the relevant details from the dataset into the STR template.
Some information, such as customer background details, was not included because it was not part of the dataset.
The STR was written for practice purposes only to simulate real reporting procedures.
## Conclusion:
Through this project, I learned about the rules and strategies used to identify suspicious transactions. It helped me understand how certain transaction patterns trigger risk alerts and gave me practical exposure to AML analysis.

This project also improved my analytical thinking, as I had to carefully evaluate multiple criteria to determine high-risk customers.

However, despite gaining this knowledge, I realized that some aspects could not be fully applied due to limitations in the dataset, such as missing customer background details and other information required for a complete STR.

Overall, this project was a valuable learning experience in transaction monitoring and AML reporting.
