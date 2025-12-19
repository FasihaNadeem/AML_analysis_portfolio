# Project Overview 

In this project, I performed a complete AML/KYC analysis. This project is different from my previous two projects because here I worked on both datasets together — the Customer Data and the Transaction Data.

The special thing about this project is that I completed the entire analysis in just one hour and successfully identified four high-risk customers. How did I do it so fast? It was only possible because of Quadratic AI (https://www.quadratichq.com/)

I uploaded my datasets into Quadratic AI, and with the help of 2 clear prompts, the tool generated the full AML analysis for me — including cleaning, merging, red-flag detection, and customer risk categorization.
## Prompt 1:

You have two Excel sheets: “CustomerData” with 100 rows and “TransactionData” with 100 rows. Perform full cleaning, standardization, and merge into a final table named “MasterAML”. Follow these steps carefully:

STEP 1 — CLEAN CUSTOMERDATA:

• Remove duplicate CustomerID rows (keep the most complete row).  
• Remove exact duplicate rows completely.  
• Standardize CustomerID format (CUS001, CUS002, … CUS100).  
• Clean and validate CNIC: keep only 12 numeric digits, remove hyphens or letters.  
• Standardize Full Name: capitalize first letter of each word, rest lowercase.  
• Standardize DOB format to YYYY-MM-DD.  
• Add Age column automatically from DOB.  
• Ensure Monthly Income is numeric; remove commas, symbols, or extra spaces.  
• Standardize Occupation and Business Nature text (capitalize first letter, consistent naming).  
• Clean Address: remove extra spaces, capitalize city names, correct inconsistent formatting.  
• Remove any extra blank columns or hidden whitespace.

STEP 2 — CLEAN TRANSACTIONDATA:

• Remove duplicate TransactionID rows (keep first valid entry).  
• Remove exact duplicates completely.  
• Standardize TransactionID format (TID001, TID002, … TID100).  
• Standardize CustomerID format (CUS001 … CUS100).  
• Clean Amount column: numeric only, remove commas or currency symbols.  
• Standardize Transaction Date to YYYY-MM-DD.  
• Standardize Transaction Type categories `(Cash Deposit, Online Transfer, ATM Withdrawal, Pos Payment, Cheque Deposit, etc.).` 
• Standardize Country and Counterparty fields (consistent spelling and capitalization).  
• Standardize Channel names (Bank Branch, Mobile App, ATM, POS Terminal, Online Banking).  
• Remove extra spaces and inconsistent casing.

STEP 3 — MERGE SHEETS INTO MASTERAML:

• Merge CustomerData and TransactionData using CustomerID.  
• Include the following columns in MasterAML:  
  `CustomerID, Full Name, DOB, Age, Address, CNIC, Occupation, Monthly Income, Business Nature, TransactionID, Transaction Date, Transaction Type, Amount, Counterparty, Channel, Country.`  
• Ensure MasterAML contains **all 100 customers and their associated transactions**.  
• Keep the table fully cleaned, standardized, and ready for AML/KYC analysis.  

Return the final MasterAML table with all 100 rows and complete columns.
## Prompt 2:

You now have a fully cleaned and merged dataset called MasterAML.  
Perform a complete AML/KYC analysis on all customers and their transactions.  
Follow these instructions step-by-step:

STEP 1 — CUSTOMER PROFILE RISK ANALYSIS

• Identify high-risk occupations (real estate, cash-intensive businesses, freelancers with irregular income, traders, jewelers, NGOs, foreign remittance receivers).  
• Identify customers whose monthly income appears unrealistic or mismatched with their occupation.  
• Identify customers with missing or abnormal CNIC, DOB, or Age (below 18 or above 90).  
• Identify customers with unusual address formats or signs of incomplete KYC.  
• Create a column “CustomerRiskLevel” with values: Low, Medium, High.

STEP 2 — TRANSACTION BEHAVIOR ANALYSIS
For each customer, detect:

• Large transactions inconsistent with declared income.  
• Sudden spikes in transaction amounts compared to customer’s historical pattern.  
• High frequency of cash deposits or withdrawals (structuring).  
• Multiple small transactions just below a reporting threshold (e.g., 190,000 PKR, 199,000 PKR).  
• Round-figure structured transactions (10000, 20000, 50000 repeatedly).  
• Transactions to high-risk countries, sanctioned regions, offshore locations.
• Incoming transactions from unknown or unrelated counterparties.  
• Rapid movement of funds (in and out on same day).

STEP 3 — RED FLAG DETECTION
Flag any customer with:

• Transactions > 3x their monthly income.  
• More than 5 cash deposits in 10 days.  
• More than 5 high-value incoming transfers from different senders.  
• Frequent online transfers to unrelated individuals.  
• Counterparty names that do not match expected personal or business relations.  
• Transactions conducted during abnormal hours.  
• Multiple accounts sharing the same address or CNIC (identity risk).  
• ATM withdrawals in multiple cities within 24 hours.

Add a column “RedFlagsDetected” summarizing all triggered red flags.

STEP 4 — RISK SCORING MODEL
Create an overall risk score out of 100 using:

• 30% — Customer profile risk  
• 40% — Transaction behavior anomalies  
• 30% — Red flag count  

Then classify risk category:

• 0–30 → Low  
• 31–60 → Medium  
• 61–100 → High  

Add a column “FinalRiskCategory”.

Return: The updated MasterAML table with new columns: `CustomerRiskLevel, RedFlagsDetected, RedFlagDeatils, RiskScore, FinalRiskCategory`

## Create STR Report:

After Quadratic AI identified the four high-risk customers, I prepared Suspicious Transaction Reports (STRs) for each of them. I used the official STR template from the Financial Monitoring Unit (FMU) Pakistan (https://www.fmu.gov.pk/reporting-forms/
) to ensure the reports were accurate and aligned with Pakistan’s regulatory standards.

I reviewed each customer’s red flags, transaction patterns, and risk indicators, and then documented the findings clearly in the STR format. This step helped me understand how suspicious cases are reported in real financial institutions and how compliance teams escalate high-risk profiles to the FMU.

# Key learnings:

This is one of my favorite project. Using Quadratic AI helped me complete the AML/KYC analysis quickly and efficiently. I realized how important emerging AI tools are for improving work accuracy and speed. AI made identifying red flags and high-risk customers much easier while allowing me to focus on analysis and decision-making.
