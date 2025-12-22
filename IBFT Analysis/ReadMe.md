# Project Overview

This project focuses on the analysis of Inter Bank Funds Transfer (IBFT) transactions from an AML (Anti-Money Laundering) perspective. The primary purpose of this project is to develop a practical understanding of how IBFT transactions are monitored, analyzed, and assessed for potential financial crime risks using rule-based logic and Excel formulas.

Through this project, I aimed to strengthen my understanding of transaction monitoring concepts such as `high-value transactions, transaction frequency, unusual behavioral patterns, and risk-based prioritization.` The project simulates a real-world fintech or digital wallet environment where AML analysts are required to review alerts and identify suspicious activities efficiently.

For this analysis, a 100-row dummy dataset was created to represent a realistic IBFT transaction scenario. The dataset includes a mix of normal and suspicious transactions, allowing meaningful analysis and identification of red flags.

### Key Findings

The IBFT transaction analysis identified that most transactions were low risk and aligned with normal customer behavior. However, a specific sender account exhibited repeated `high-value transactions with a very high frequency, triggering multiple red flags including fraud indicators and unusual patterns.` These transactions were classified as high risk and would require escalation for enhanced due diligence and potential STR/SAR consideration.

## Data Preparation and Analysis Process

This section explains the step-by-step process followed to analyze IBFT transactions and identify potential red flags.

### Existing Dataset Columns
The original dataset already contained the following transaction-related columns:
- Transaction ID  
- Date & Time  
- Amount  
- Transaction Type  
- Sender Account  
- Receiver Account  
- Receiver Bank  

### These columns were Created for AML Analysis
To perform IBFT monitoring and risk assessment, additional columns were created for analysis purposes:

#### 1. Clean Amount
The original Amount column contained commas and text formatting, which prevented Excel formulas from working correctly. Therefore, the amount values were cleaned and converted into numeric format using the following formula:
`=VALUE(SUBSTITUTE(SUBSTITUTE(C2,",",""),"""",""))`

This step ensured accurate calculations for further analysis.

#### 2. High Value Transaction Flag
Transactions were classified as high value if the amount was greater than or equal to 150,000 PKR. The following formula was used:
`=IF(C2>=150000,"Yes","No")`

This helped identify transactions that required closer monitoring due to higher monetary risk.

#### 3. Sender Transaction Count
To identify frequent transaction behavior, the total number of transactions performed by each sender account was calculated using:
`=COUNTIF($E:$E,E2)`

This allowed detection of repeated transaction patterns from the same sender.

#### 4. Fraud Flag (Frequent Transactions)
Transactions where a sender performed more than 5 transactions were marked as potential fraud indicators using:
`=IF(J2>5,"Yes","No")`

Frequent transactions may indicate structuring or suspicious activity.

#### 5. High Value + Same Sender Pattern
Transactions were flagged when both high-value and frequent transaction conditions were met. The following formula was applied:
`=IF(AND(I2="Yes", K2="Yes"), "Yes", "No")`

This combination represents a stronger AML red flag than individual indicators.

#### 6. Late Night Transaction Detection
Since transactions performed during late-night hours are considered higher risk, the transaction hour was extracted from the Date & Time column using:
`=HOUR(B2)`

Late-night transactions (between 10 PM and 6 AM) were then identified using:
`=IF(OR(M2>=22, M2<=6), "Yes", "No")`

#### 7. Risk Scoring Model
Each red flag was assigned weighted points based on its AML risk severity. The risk score was calculated using:
`=IF(I2="Yes",2,0)
+IF(K2="Yes",2,0)
+IF(L2="Yes",3,0)
+IF(N2="Yes",1,0)`

This scoring system allowed prioritization of transactions based on cumulative risk.

#### 8. Final Risk Classification
Based on the total risk score, transactions were classified into risk categories using:
`=IF(O2>=5,"High",IF(O2>=3,"Medium","Low"))`

This final flag helped identify which transactions required escalation and further review.

## High-Risk Customer Case Analysis

### Customer Profile

- **Customer ID:** CUST0047  
- **Customer Name:** Benjamin Morgan  
- **CNIC:** 42603-456789123-1  
- **Account Number:** AC1231006  
- **Account Open Date:** 15 March 2023  
- **Occupation / Source of Income:** Engineer

### Transaction Behavior Overview
During the analysis period, the customer account **AC1231006** conducted a total of **19 IBFT transactions**, which is significantly higher than normal customer behavior within the dataset.

Most of the transactions were **outgoing transfers** to multiple different beneficiary accounts across various banks, including `UBL, HBL, Meezan Bank, MCB, Bank Alfalah, Faysal Bank, and Standard Chartered.` This indicates wide dispersion of funds rather than regular personal or salary-related usage.

### Key Red Flags Identified

#### 1. High Frequency of Transactions
The customer executed **19 transactions**, exceeding the predefined threshold of **more than 5 transactions**, which triggered the **Frequent Transaction (Fraud) flag**.

- **Risk Indicator:** High transaction frequency  
- **Potential Concern:** Structuring or layering behavior

#### 2. Repeated Transactions from the Same Sender Account
All suspicious transactions originated from the **same sender account (AC1231006)**, reinforcing the **High Value + Same Sender** red flag logic used in the analysis.

- **Risk Indicator:** Single sender with repeated transfers  
- **Potential Concern:** Centralized control of funds
  
#### 3. High-Value Transactions
Although most transactions were moderate in amount, the account also recorded **high-value transactions**, including:
- **PKR 165,000 (Incoming)**
- **PKR 225,000 (Outgoing)**

These transactions crossed the **PKR 150,000 high-value threshold**, increasing the overall risk score.

#### 4. Late-Night Transaction Activity
At least one transaction was executed during late-night hours (**22:10**), triggering the **Late Night Transaction** flag.

- **Risk Indicator:** Non-standard transaction timing  
- **Potential Concern:** Attempt to avoid detection or monitoring

### Risk Scoring Outcome
Due to the combination of:

- High transaction frequency  
- Repeated activity from the same sender  
- Presence of high-value transfers  
- Late-night transaction behavior`

multiple risk points were accumulated, resulting in **risk scores between 5 and 7** across transactions.

### Final Risk Classification
Based on the cumulative red flags and risk scoring model, **all transactions associated with account AC1231006 were classified as HIGH RISK**.

### Conclusion and Escalation Recommendation
The transaction pattern of this customer shows **clear indicators of unusual and potentially suspicious behavior**, inconsistent with typical personal account usage for an individual engineer.

This account would require:

- **Enhanced Due Diligence (EDD)**
- **Detailed source of funds verification**
- **Ongoing transaction monitoring**
- **Consideration for STR/SAR filing**, subject to further investigation`

## Conclusion and Key Learnings

This IBFT transaction analysis project was conducted to develop a practical understanding of transaction monitoring and risk identification in a financial crime context. Using a real-scenario dummy dataset of 100 IBFT transactions, rule-based logic was applied to analyze transaction amounts, frequency, sender behavior, and transaction timing.

The analysis showed that the majority of transactions were low risk and consistent with normal customer behavior. However, one sender account exhibited unusually high transaction frequency along with repeated high-value transfers, including transactions during late-night hours. These combined indicators triggered multiple red flags, resulting in a high-risk classification.

This project reflects how initial transaction monitoring is performed in financial institutions, where suspicious patterns are identified for further investigation, enhanced due diligence, and potential STR/SAR escalation.
