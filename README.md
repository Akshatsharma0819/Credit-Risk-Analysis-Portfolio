# 🏦 Credit Risk Analysis Dashboard (End-to-End Project)

![Dashboard Preview](assets/dashboard_final.png)
*(Note: View the interactive dashboard layout in the `assets` folder or download the .pbix file)*

---

### 📊 Project Overview
This project analyzes financial lending data to identify the key drivers of loan default. By processing over **100k+ loan records**, I built an interactive "Fintech-Style" Power BI dashboard that helps risk managers identify toxic borrower segments and optimize lending strategies.

**Tools Used:** Power BI, Python (Pandas), DAX, Power Query.

---

### ❓ The Business Problem
Minimizing default rates is the key to profitability in peer-to-peer lending. I set out to answer three critical questions:
1.  **Capacity:** At what Debt-to-Income (DTI) ratio does risk become unmanageable?
2.  **Time:** Are long-term loans (60 months) significantly riskier than short-term ones?
3.  **Intent:** Which loan purposes (e.g., Small Business vs. Wedding) drive the most defaults?

---

### 💡 Key Strategic Insights
By engineering a dynamic **"Default Rate %"** metric (`AVERAGE(Target)`), the analysis revealed:

* **⚠️ The "30% DTI" Cliff:** Borrower risk remains stable (~12%) until DTI hits **30**, after which default probability spikes aggressively.
    * *Recommendation:* Cap DTI approval strictly at 30 for high-risk grades.
* **📅 The Term Trap:** **60-Month loans** carry a **~16.5% default rate** compared to just **~10.5%** for 36-month loans.
    * *Recommendation:* Increase interest rate premiums on 60-month terms to offset the +50% higher risk.
* **🎯 The "Education" Surprise:** Contrary to intuition, **Educational Loans** are the most toxic segment (**36% Default Rate**), while **Wedding Loans** are relatively safe.

---

### 📂 Repository Structure

| Folder | Description |
| :--- | :--- |
| **`assets/`** | Contains dashboard screenshots and demo recordings. |
| **`data/`** | Contains the **sample dataset** (`loan_data_sample.csv`). *Note: The full raw file is >1GB and is not uploaded.* |
| **`notebooks/`** | Python Jupyter Notebooks used for initial Data Cleaning and EDA. |
| **`Root`** | Contains the main **Power BI file (`.pbix`)**. |

---

### 🛠️ Technical Workflow

#### 1. Data Engineering (Python & Power Query)
Before visualization, I used Python for initial data quality checks.
* **Missing Values:** Handled nulls in `emp_length` and `revol_util`.
* **Outlier Detection:** Identified and filtered DTI > 100 artifacts.
* **[📄 View the Python Notebook](notebooks/Data_Cleaning_and_EDA.ipynb)**

#### 2. Risk Modeling (DAX)
* Created a binary `Target` variable to classify "Charged Off" vs. "Fully Paid" loans.
    ```dax
    Target = IF(CONTAINSSTRING('Table'[loan_status], "Charged Off"), 1, 0)
    ```
* Calculated dynamic risk probability:
    ```dax
    Default Rate % = AVERAGE('Table'[Target])
    ```

#### 3. Dashboard Design (UI/UX)
* Implemented a **"Midnight Fintech"** dark theme for high-contrast executive reporting.
* Designed custom JSON themes to standardize colors across visual cards.

---

### 🚀 How to Use
1.  Clone the repository.
2.  Open `Credit_Risk_Dashboard.pbix` in Power BI Desktop.
3.  The data source is embedded, but you can reconnect it to `data/loan_data_sample.csv` to refresh.

---

### 📬 Contact
**Akshat Sharma** 
www.linkedin.com/in/akshat-sharma-b81739314
