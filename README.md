# Financial_Risk_Analysis_For-_Improved_Loans-
# Financial Risk Analysis for Improved Loan Approvals

### **Financial Risk Analysis for Improved Loan Approvals**

---

### **Table of Contents**
1. **Introduction**
2. **Problem Statement**
3. **Stakeholders**
4. **Data Preparation**
5. **Data Modeling (DAX Formulas)**
6. **Dashboard**
7. **Insights**
8. **Conclusion**

---

### **1. Introduction**
In the modern banking sector, data-driven decision-making plays a crucial role in optimizing loan approval processes and managing financial risks. This project focuses on analyzing bank loan data to identify key trends, assess risk factors, and provide actionable insights for improving lending strategies. By leveraging data analytics, we aim to enhance loan performance and minimize defaults.

---
### **2. Problem Statement**
Banks and financial institutions face significant challenges in assessing credit risk and predicting loan defaults. An ineffective loan evaluation process can lead to high default rates, impacting financial stability. This project aims to analyze loan data to identify risk factors, improve loan approval criteria, and enhance overall decision-making in the lending process.

---

### **3. Stakeholders**
* Banking Institutions – To refine loan approval criteria and mitigate risks.
* Loan Officers – To enhance decision-making based on data-driven insights.
* Risk Management Teams – To identify key risk factors and minimize default rates.
* Business Executives – To improve financial planning and profitability.

---

### **4. Data Modeling (DAX Formulas)**
* Collected loan dataset containing customer details, loan amounts, repayment history, credit scores, and income levels.
* Cleaned and preprocessed the data by handling missing values and removing inconsistencies.
* Standardized key metrics to ensure accurate analysis and modeling.

## Bad Loan Application 
```DAX
CALCULATE(
 COUNT(financial_loan[id]),
 FILTER(
  financial_loan,
  financial_loan[loan_status] IN {"Charged Off"}
  )
)
```

## Bad Loan Funded Amount  
```DAX
CALCULATE(
SUM(financial_loan[loan_amount]),
FILTER(
financial_loan,
financial_loan[loan_status] IN {"Charged Off"}
)
)
```

## Bad Loan Percentage 
```DAX
DIVIDE(
  CALCULATE(
    COUNT(financial_loan[id]),
    financial_loan[loan_status] IN {"Charged Off"}
    ),
 COUNT(financial_loan[id]),
   0
 ) * 100
```

## Bad Loan Total Received 
```DAX
CALCULATE(
 SUM(financial_loan[total_payment]),
 FILTER(
 financial_loan,
 financial_loan[loan_status] IN {"Charged Off"}
 )
)
```

## Good Loan Application 
```DAX
CALCULATE(
 COUNT([id]),
 FILTER(
 'financial_loan',
 'financial_loan'[loan_status] IN {"Fully Paid", "Current"}
 )
)
```

## Good Loan Funded Amount  
```DAX
CALCULATE(
 SUM(financial_loan[loan_amount]),
 FILTER(
 financial_loan,
 financial_loan[loan_status] IN {"Fully Paid", "Current"}
 )
)
```

## Good Loan Percentage 
```DAX
DIVIDE(
 CALCULATE(
 COUNT(financial_loan[id]),
 financial_loan[loan_status] IN {"Fully Paid", "Current"}
 ),
 COUNT(financial_loan[id]),
 0
 ) * 100
```

## Good  Loan Total Received 
```DAX
CALCULATE(
 SUM(financial_loan[total_payment]),
 FILTER(
 financial_loan,
 financial_loan[loan_status] IN {"Fully Paid", "Current"}
 )
)
```

## MTD Amount Received 
```DAX
CALCULATE(
 SUM(financial_loan[total_payment]),
 DATESMTD(financial_loan[last_payment_date])
)
```

## MTD Funded Amount 
```DAX
CALCULATE(
 SUM(financial_loan[loan_amount]),
 DATESMTD(financial_loan[issue_date])
)
```

---

### **5. Dashboard**
* Designed an interactive Power BI dashboard to visualize key metrics.
* Included loan approval trends, default rates, credit score distribution, and repayment success analysis.
* Enabled filtering by loan type, customer demographics, and time period for deeper insights.

# DashBoard GIF 1
![Image](https://github.com/user-attachments/assets/8e5181a5-4f98-4161-a8e4-d299f52e8882)

# DashBoard GIF 2
![Image](https://github.com/user-attachments/assets/bdd0f1aa-d2ee-4b86-9cd4-22b3fcb7d66b)

# DashBoard Page 1
![Image](https://github.com/user-attachments/assets/668ea6bf-f2ed-4979-a00f-f15fc9e32b79)

## Key Insights:

### Overall Loan Performance:
* Total Loan Applications: 38.6K  
* Total Funded Amount: $435.76M  
* Total Amount Received: $473.1M  
* Average Interest Rate: 12.05%  
* Average Debt-to-Income (DTI) Ratio: 13.33%  

### Good vs. Bad Loans:
* Good Loan Issued: 86.18% of total loans, with 33.2K applications and $370.2M funded.  
* Bad Loan Issued: 13.82% of total loans, with 5.33K applications and $65.5M funded.  
* Total Received from Bad Loans: $37.3M, which is significantly lower than the funded amount.  

### Loan Status Breakdown:
* Fully Paid Loans: 32,145  
* Charged-Off Loans (Defaults): 5,333  
* Current Loans: 1,098  

# DashBoard Page 2
![Image](https://github.com/user-attachments/assets/1a2f57ee-d2cd-4b21-b7ed-57e6ab2c66e4)

### Loan Distribution Insights:
* Top 10 States Funding Loans: California (CA) leads, followed by TX, NY, and FL.  
* Purpose of Loans: Debt consolidation > credit cards > home improvement.  
* Home Ownership Trends: Mortgages > Renters > Owners.  
* Loan Term Preference: 60-month > 36-month loans.  

### Trends Over Time:
* Funded Amount increases monthly.
* Employees with 10+ years of experience receive most funding.

# DashBoard Page 3
![Image](https://github.com/user-attachments/assets/0a27257f-8460-4fe4-ac06-f01477e405d4)

---

### **6. Insights**
* Higher defaults in customers with low credit scores and irregular income.
* Short-term loans perform better than long-term.
* Auto-debit customers default less.
* Self-employed applicants are riskier.

---

### **7. Conclusion**
The analysis highlights key factors influencing loan repayment and default rates. By incorporating data-driven decision-making, banks can optimize loan approval processes and reduce financial risks. Implementing stricter credit score thresholds, offering flexible repayment plans, and promoting auto-debit payments can significantly improve loan performance.
