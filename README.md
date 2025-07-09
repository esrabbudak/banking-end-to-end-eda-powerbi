# Banking EDA Case Study - End-to-End Project
![Dashboard Preview](./Banking%20Domain/dashboard/Dashboard-image.png)


This project presents an **end-to-end data analysis** of a fictional banking dataset. The goal is to explore, clean, and analyze customer financial behavior using Python (EDA), and visualize insights through a well-designed **Power BI dashboard**.

---

## Problem Statement

Banks need a deeper understanding of customer financial behavior to:
- Improve customer segmentation
- Assess risk and product engagement
- Optimize credit and deposit strategies

**Our goal:** Use the available customer dataset to uncover insights on deposits, loans, savings, and risk metrics — and present them interactively.

---

## 📁 Dataset

The dataset contains information about **3000 banking customers**, including:

- Demographics (age, gender, nationality, etc.)
- Financial data (income, deposits, loans, credit card balance)
- Account types (checking, savings, foreign currency)
- Behavioral classifications (loyalty, risk, occupation, etc.)


---
## ⚙️ Tools & Technologies

- Python (Pandas, Seaborn, Matplotlib)
- Jupyter Notebook
- Power BI (Dashboard design)
- Git & GitHub
	
---
## 📊 Power BI Dashboard

The dashboard was built in Power BI using cleaned data and calculated fields with DAX. It contains three main sections:

- Loan Analysis
- Deposit Analysis
- Summary


### Key KPIs (DAX Calculations)

- **Total Clients**  
  `Total Clients = DISTINCTCOUNT('Clients - Banking'[Client ID])`

- **Total Loan**  
  `Total Loan = SUM('Clients - Banking'[Bank Loans]) + SUM('Clients - Banking'[Business Lending]) + SUM('Clients - Banking'[Credit Card Balance])`

- **Total Deposit**  
  `Total Deposit = SUM('Clients - Banking'[Bank Deposits]) + SUM('Clients - Banking'[Saving Accounts]) + SUM('Clients - Banking'[Checking Accounts]) + SUM('Clients - Banking'[Foreign Currency Account])`

- **Engagement Timeframe**  
  ```DAX
  Engagement Days = DATEDIFF('Clients - Banking'[Joined Bank], TODAY(), DAY)

  Engagement Timeframe = 
  SWITCH(TRUE(),
    'Clients - Banking'[Engagement Days] < 365, "1 Year",
    'Clients - Banking'[Engagement Days] < 1825, "5 Years",
    'Clients - Banking'[Engagement Days] < 3650, "10 Years",
    'Clients - Banking'[Engagement Days] < 7300, "20 Years",
    "> 20 Years")

Each KPI is dynamically filtered based on slicers.

---

## 📌 Key Findings

- Customers in the **high-income band** hold significantly higher bank deposits compared to medium and low-income customers.  
- As the **Risk Weighting** increases, the average loan amount taken by customers also rises — indicating a correlation between perceived risk and borrowing behavior.  
- Customers can be effectively segmented based on **Occupation**, **Loyalty Classification**, and **Income Band**, allowing for better-targeted financial strategies.  
- The **Engagement Timeframe** was calculated using the `"Joined Bank"` field through a custom DAX formula. This value was then used as a dashboard filter to analyze how customer tenure relates to savings and loan behavior.  
- **Processing Fees** were also derived using DAX based on each customer's `"Fee Structure"` (High, Mid, Low). This allowed estimation of revenue generated from different customer segments.

---

## 🎯 Project Purpose

This project was created to develop basic skills in:

- 🔍 **Data Cleaning and Exploratory Data Analysis** using Python (Pandas, Seaborn, Matplotlib)  
- 📊 **Building interactive dashboards** and defining meaningful measures in Power BI  
- 🧠 **Creating DAX Calculated Columns** for advanced segmentation and business logic  
- 💼 **Delivering real-world financial insights** in the banking domain using structured customer data
