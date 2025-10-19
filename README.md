# 🧩 HR Analytics Dashboard (Tableau)

### 📘 Project Overview
An interactive HR analytics dashboard built in **Tableau** to analyze workforce trends, demographics, and salary insights.  
It enables HR managers to track hiring patterns, evaluate workforce composition, and identify salary discrepancies across departments, genders, and education levels.

---

## 🌐 Live Dashboard
🔗 [View on Tableau Public](https://public.tableau.com/app/profile/himangshu.choudhury/viz/Human_Resource_Dashboard_Summary_Details/HRDetails) 

---

## 📖 User Story
**As an HR Manager**, I want a comprehensive dashboard to analyze human resources data, providing both summary views for high-level insights and detailed employee records for in-depth analysis.

---

## 📊 Dashboard Structure

### **1. Summary View**
The **Summary View** is divided into three sections: **Overview**, **Demographics**, and **Income Analysis**.

#### 🟦 Overview
Provides a snapshot of key HR metrics:
- Total **Hired**, **Active**, and **Terminated** employees.  
- Trend of **Hired vs. Terminated** employees over the years.  
- **Department-wise** and **Job Title** breakdown of total employees.  
- Comparison between **Headquarters (New York)** and **Branch Offices**.  
- **Geographical distribution** of employees by **City** and **State**.

#### 🟩 Demographics
Highlights the workforce composition:
- Gender ratio across the organization.  
- Distribution of employees by **Age Group** and **Education Level**.  
- Correlation between **Education Level** and **Performance Ratings**.  

#### 🟧 Income Analysis
Focuses on salary-related metrics:
- Comparison of **Average Salary by Education Level** and **Gender**.  
- Correlation of **Age vs. Salary** across departments.  

---

### **2. Employee Records View**
A detailed table of all employees, displaying:
- **Name**, **Department**, **Position**, **Gender**, **Age**, **Education**, and **Salary**.  
- Interactive filters for easy navigation and record lookup.

---

## 🧮 Key Calculated Fields

| Field | Formula / Logic |
|-------|------------------|
| **Total Hired** | `COUNT([Employee ID])` |
| **Total Terminated** | `COUNT(IF NOT ISNULL([Termdate]) THEN [Employee ID] END)` |
| **Total Active** | `COUNT(IF ISNULL([Termdate]) THEN [Employee ID] END)` |
| **Location** | `IF [State]='New York' THEN 'HQ' ELSE 'Branch' END` |
| **Age** | `DATEDIFF('year',[Birthdate],TODAY())` |
| **Age Group** | `IF [Age]<25 THEN '<25' ELSEIF [Age]>25 AND [Age]<35 THEN '25-34' ELSEIF [Age]>=35 AND [Age]<45 THEN '35-44' ELSEIF [Age]>=45 AND [Age]<54 THEN '45-54' ELSEIF [Age]>=55 THEN '55+' END` |
| **% Total Hired** | `[Total Hired] / TOTAL([Total Hired])` |
| **% Total Terminated** | `[Total Terminated] / TOTAL([Total Terminated])` |
| **Status** | `IF ISNULL([Termdate]) THEN 'Hired' ELSE 'Terminated' END` |
| **Duration (Years)** | `IF ISNULL([Termdate]) THEN DATEDIFF('year',[Hiredate],TODAY()) ELSE DATEDIFF('year',[Hiredate],[Termdate]) END` |
| **Highest Max (Tree Map)** | `WINDOW_MAX([Total Hire])=[Total Hired]` |
| **Top 2 (Total Hired)** | `RANK([% Total Hired])<=2` |

---

## 🧾 Dataset Description

This dataset was **synthetically generated using the Python `faker` library** to simulate realistic HR data for demonstration and visualization purposes.  
It contains detailed employee records representing multiple departments and locations across the U.S.

| Column Name | Description |
|--------------|-------------|
| **Employee_ID** | Unique identifier assigned to each employee |
| **First Name / Last Name** | Employee’s name details |
| **Gender** | Male or Female |
| **State / City** | Geographic location of the employee (New York represents HQ) |
| **Education Level** | Highest educational qualification (High School, Bachelor, Master, etc.) |
| **Birthdate** | Employee’s date of birth |
| **Hiredate** | Date when the employee joined the organization |
| **Termdate** | Date when the employee left the organization (if applicable) |
| **Department** | Department where the employee works (e.g., IT, Operations, Customer Service) |
| **Job Title** | Employee’s role or designation |
| **Salary** | Annual salary in USD |
| **Performance Rating** | Performance evaluation score or category (e.g., Excellent, Good, Needs Improvement) |

> ⚠️ *This dataset does not represent any real individuals or organizations. It is entirely fictitious and created for learning and portfolio purposes.*

---

## 💡 Insights Derived

- Transparent visualization of **hiring and termination trends** over time.  
- Identification of **salary gaps** by **gender** and **education level**.  
- Understanding of **workforce distribution** across **departments**, **locations**, and **age groups**.  
- Informed decision-making through **performance and education correlation analysis**.  
- Simplified tracking of **employee status** (active, hired, terminated).  

---

## ⚙️ Tools & Technologies

- **Tableau Desktop / Tableau Public** – Data visualization and dashboard design  
- **Excel** – Primary data source  
- **Python (Faker library)** – For generating synthetic HR dataset  
- **Calculated Fields & Parameters** – For dynamic analysis and interactivity  

---

## 📌 Project Highlights

- Designed a **comprehensive Tableau dashboard** for HR analytics and workforce insights.  
- Built **interactive summary and detailed employee record views**.  
- Implemented **calculated fields** to automate HR metrics computation.  
- Delivered a **visually consistent and user-friendly layout** optimized for decision-making.  

---

## Files Included
- `images` — All Project Assets
- `dataset.csv` — Synthetic HR dataset
- `dashboard.twbx` — Tableau workbook
- `README.md` — Project documentation

---

### 👤 Author
**Himangshu Choudhury**  
📍 Assam, India  
