# 🏦 Indian Banking Transactions Analysis Using Excel

> End-to-end Excel project: raw banking transaction data → data audit and cleaning in **Power Query** → **Pivot Tables** → interactive **dashboard** → business insights and recommendations.

![Dashboard](https://github.com/user-attachments/assets/41d3aa92-08b1-4ed1-b988-72adf38acfa2)

---

## 📌 1. Business Context

India's banking industry processes billions of digital transactions every month. Banks need analytics to monitor KPIs, detect fraud and improve service delivery. This project turns a raw transaction dataset into insights that leadership teams can act on.

## 🎯 2. Business Objectives

- Analyse transaction trends across branches and regions
- Identify fraud-prone accounts and patterns
- Compare the performance of payment channels (UPI, Cash, Cards, Net Banking)
- Track the status of transactions (Completed, Failed, Reversed, Pending)
- Build an Excel dashboard of key banking KPIs for leadership

## ❓ 3. Problem Statement

Convert raw banking transaction data into business insights and answer:

1. What are the regional and monthly transaction trends?
2. Which branches handle the highest and lowest transaction volumes?
3. What is the breakdown of deposits, withdrawals, cheques and transfers?
4. Are there signs of fraudulent transactions?
5. How does each payment channel perform?
6. What proportion of transactions fail or reverse?

---

## 📂 4. Dataset

| Item | Detail |
|---|---|
| Source file | `Indian_Banking_data.xlsx` (sheet `Sheet1`) |
| Records | **500 transactions** |
| Columns (raw) | 16 |
| Columns (cleaned) | 18 |
| Period | 11 Jul 2023 to 6 Jul 2025 |
| Coverage | 5 regions, 25 cities / branches, 4 account types, 4 transaction types, 5 payment modes |

**Fields**

| Group | Fields |
|---|---|
| Transaction | Transaction ID, Transaction Date, Transaction Type, Transaction Amount, Payment Mode, Transaction Status, Balance After Txn, Is Fraud |
| Customer | Customer ID, Customer Name, Account Number, Account Type |
| Location | Region, City, Branch Name |
| Derived (added by me) | Month Name, Year, Day Name |

> **Note on the case study brief:** the brief lists a *Channel* field (UPI, ATM, Online, Branch, Mobile App) and a *North-East* region. This dataset uses **Payment Mode** (Cash, Credit Card, Debit Card, Net Banking, UPI) and has 5 regions (Central, East, North, South, West), so the channel analysis uses Payment Mode.

---

## 🔄 5. Workflow

```
Raw data (Indian_Banking_data.xlsx)
        │
        ▼
Step 1  Data understanding
        ▼
Step 2  Data audit and cleaning (Power Query Editor)
        ▼
Step 3  Create derived columns (Month Name, Year, Day Name)
        ▼
Step 4  Load clean table to Excel ("Transaction" sheet, 500 rows × 18 columns)
        ▼
Step 5  Build Pivot Tables
        ▼
Step 6  Build Pivot Charts and KPI cards
        ▼
Step 7  Assemble the dashboard and add slicers
        ▼
Step 8  Insights and recommendations
```

### Step 1: Data Understanding
- Reviewed all 16 columns and their business meaning.
- Classified fields as **transactional** (ID, date, type, amount, mode, status, balance, fraud flag), **customer-level** (customer ID and name, account number and type) and **location** (region, city, branch).
- Identified data types: numeric (amount, balance, customer ID, account number), date (transaction date) and categorical (region, city, branch, account type, transaction type, payment mode, status, fraud flag).

### Step 2: Data Cleaning in Power Query Editor
Loaded the data with **Data → From Table/Range** and checked each item below.

| Check | Result | Action |
|---|---|---|
| Duplicate Transaction IDs | **0** found | None needed |
| Duplicate rows | **0** found | None needed |
| Missing values | None in the 15 data columns | None needed |
| Empty column `year_month` | **100% empty** (500 of 500 blank) | **Removed** |
| Extra spaces in text columns | None | None needed |
| Inconsistent naming or letter case (e.g. "Delhi" vs "DELHI") | None; every category had one consistent spelling | None needed |
| Negative or zero amounts | None (range ₹1,553 to ₹5.96 lakh) | None needed |
| Data types | Dates stored as Date, amounts as Decimal, IDs as numbers, others as Text | Confirmed |
| Row count | 500 before and 500 after | No rows lost |

### Step 3: Derived Columns
Added three columns from **Transaction Date** to enable time-based analysis:

| New column | Used for |
|---|---|
| **Month Name** | Monthly trend and seasonality |
| **Year** | Year-wise comparison |
| **Day Name** | Weekday patterns |

### Step 4: Load to Excel
Closed and loaded the query as a table on the **Transaction** sheet: **500 rows × 18 columns**, ready for pivoting and refreshable through **Data → Refresh All**.

**Before vs after**

| | Raw file | Cleaned file |
|---|---|---|
| Rows | 500 | 500 |
| Columns | 16 | 18 |
| Removed | | `year_month` (empty) |
| Added | | Month Name, Year, Day Name |

### Step 5: Pivot Tables
Built pivot tables on one sheet, each answering a business question:

| # | Pivot | Question answered |
|---|---|---|
| 1 | Transaction count by Transaction Type | Breakdown of deposits, withdrawals, cheques and transfers |
| 2 | Transaction count and value by Region | Regional performance |
| 3 | Transaction value by City | Top and bottom cities |
| 4 | Transaction count by Branch | Highest and lowest volume branches |
| 5 | Transaction value by Month | Monthly trend and seasonality |
| 6 | Transaction count by Year | Year-wise growth |
| 7 | Transaction value by Payment Mode | Channel performance |
| 8 | Payment Mode × Transaction Status | Failed, reversed and pending share per channel |
| 9 | Account Type × Payment Mode | How each account type pays |
| 10 | Region × Transaction Type | Regional product mix |
| 11 | Fraud count by Month | Fraud seasonality |
| 12 | Fraud count by Payment Mode | Fraud-prone channels |

### Step 6: Charts and KPI Cards
Converted the pivots into 8 pivot charts and 5 KPI cards.

**KPI cards:** Total Transactions · Total Amount · Average Amount · Fraud Transactions · Top Payment Mode

**Charts**

| Chart | Type | Insight shown |
|---|---|---|
| Transactions by type | Bar | Deposit / withdrawal / cheque / transfer mix |
| Transaction value by city | Bar | Top and bottom cities |
| Monthly trend | Line | Peaks and dips through the year |
| Account type by payment mode | Clustered bar | Payment habits per account type |
| Status split by payment mode | 100% stacked bar | Failure and reversal rates per channel |
| Region by transaction type | Line | Regional product mix |
| Transactions by branch | Line | Branch volume ranking |
| Payment mode share | Pie | Channel usage |

### Step 7: Dashboard and Slicers
- Placed KPI cards on top and charts in a grid below on a single **Dashboard** sheet.
- Added **slicers** (Year, Region, Payment Mode and others) connected to all pivot tables so one click filters everything.

---

## 📊 6. Key Findings

### Headline numbers

| KPI | Value |
|---|---|
| Total transactions | **500** |
| Total transaction value | **₹9.39 crore** |
| Average transaction | **₹1.88 lakh** |
| Fraud transactions | **13 (2.6%)** worth ≈ ₹23.4 lakh |
| Completed transactions | **434 (86.8%)** |
| Failed / Reversed / Pending | **26 (5.2%) / 21 (4.2%) / 19 (3.8%)** |

### Regional and branch performance
- **North** leads by value (₹2.05 crore, 110 transactions); **South** is lowest (₹1.73 crore).
- **Highest-volume branches:** Chennai and Indore (28 transactions each), then Ahmedabad (26).
- **Lowest-volume branch:** Mumbai (12 transactions), followed by Ranchi (14) and Raipur (15).
- **Highest value:** Chennai (₹63.7 lakh), Indore (₹52.9 lakh), Ahmedabad (₹47.1 lakh). **Lowest value:** Kochi (₹13.2 lakh).

### Transaction mix
- **Cheque** carries the most value (₹3.28 crore) with the highest average ticket (about ₹3.04 lakh).
- **Online Transfer** follows (₹3.09 crore); **Deposit** has the most transactions (140).
- **Withdrawal** has the lowest value (₹87 lakh) and smallest average ticket.

### Channel (payment mode) performance
- **Debit Card** leads on both count (128) and value (₹2.39 crore); **UPI** is second by value (₹1.86 crore).
- **Net Banking** has the lowest volume (80) and value (₹1.62 crore).
- **Cash** has the weakest completion rate (**83.7%**): 6.1% failed and **8.2% reversed**.
- **Credit Card** has the highest completion (89.0%) but the highest failure rate (7.0%).
- **UPI** has the lowest failure rate (2.1%) but the highest pending share (**8.5%**).

### Trends
- **November and January** are peak months (≈ ₹1.01 crore each); **September** is lowest (₹56 lakh).
- **Friday** is the busiest weekday (93 transactions); **Thursday** the quietest (52).
- **2024** is the busiest year (257 transactions). Data runs July 2023 to July 2025, so 2023 and 2025 are partial years and are not directly comparable.

### Fraud patterns
- **13 fraud cases** (2.6% of transactions).
- **Cash** has the highest fraud rate (**5.1%**), roughly double most other modes (1.6% to 2.5%).
- **Central (4.1%)** and **West (4.0%)** regions have the highest fraud rates; **South (1.0%)** and **East (1.1%)** the lowest.
- **Savings accounts** account for 7 of the 13 fraud cases.
- **Online Transfers and Withdrawals** make up 10 of the 13 fraud cases (5 each).
- **March and May** have 4 cases each (8 of 13); **Wednesday** has the most (5).
- **Bhopal** has the most fraud cases of any city (3).
- **11 of the 13 fraud cases were marked "Completed"**, meaning most suspected fraud was not stopped before completion.
- Fraud fell from 3.9% of transactions in 2024 to 2.4% in 2025.

> ⚠️ With only 13 fraud cases, these patterns are indicative and should be validated on a larger dataset.

---

## 💡 7. Recommendations

1. **Strengthen cash controls:** add verification and limits, since cash has the highest fraud rate and the weakest completion rate.
2. **Stop fraud before completion:** introduce real-time checks for Online Transfers and Withdrawals, because most fraud currently completes.
3. **Targeted monitoring:** prioritise Central and West regions and Savings accounts.
4. **Plan for March and May:** increase fraud monitoring in those months.
5. **Fix failures:** investigate Credit Card failures and Cash reversals; clear UPI pending items faster.
6. **Support low-volume branches:** Mumbai, Ranchi, Raipur and Kochi need a growth or review plan.
7. **Replicate what works:** study Chennai and Indore branch practices and the North region's performance.
8. **Promote Debit Card and UPI** with offers while keeping fraud rules in place.

---

## 📁 8. Repository Structure

```
Indian-Banking-Transactions-Dashboard/
│   ├── Indian_Banking_data.xlsx            # original raw dataset
│   └── Banking_Transactions_Cleaned.xlsx   # cleaned data, pivot tables, dashboard
│   ├── dashboard.png
|   └── README.md
```

## ▶️ 9. How to Use

1. Download the repository and open the cleaned workbook in Excel (2016 or later).
2. Open the **Dashboard** sheet and click the slicers to filter every chart.
3. After changing the data, use **Data → Refresh All**.

## 🧠 10. Skills Demonstrated

Data cleaning · Power Query · Pivot Tables · Pivot Charts · Dashboard design · Slicers · Business insights

## 👤 11. Author

**Yashwanth Chalamalla**

- LinkedIn: `https://www.linkedin.com/in/yashwanth-chalamalla/`
- Email: `chalamallan11@gmail.com`

⭐ If you like this project, please star the repository.
