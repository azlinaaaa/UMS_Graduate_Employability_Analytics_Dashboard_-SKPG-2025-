# 🎓 UMS Graduate Employability Analytics Dashboard (SKPG 2025)

## 📌 Project Overview
This project presents an interactive **Graduate Tracer Dashboard (Pengesanan Graduan 2025 - SKPG)** developed using **Power BI** to analyze graduate outcomes from University Malaysia Sabah (UMS).

The dashboard is designed to support **data-driven decision making** for:
- Deans of each faculty
- Vice Chancellor (VC)
- Deputy Vice Chancellor (DVC)
- University top management  

👉 It is used during **faculty-level and executive meetings** to monitor graduate employability performance and support strategic planning.

---

## 📂 Dataset
- **Source**: Raw dataset from University Malaysia Sabah (UMS)  
- Covers **18 faculties** and multiple academic programs  

---

## 🧹 Data Preparation
The dataset was processed through:

- Handling missing (blank) values  
- Cleaning and standardizing employment categories  
- Ensuring data consistency  
- Validating totals for accurate reporting  

---

## 📊 Dashboard Design

[![OVERALL Dashboard](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/c73f83990b0b3523d2137b0addc2c3424ddc96ce/Dashboard/Overall_Dashboard.png)

### 📊 Bar Chart (Graduate Status Distribution)
- 157 Employed  
- 50 Further Studies  
- 33 Unemployed  
- 6 Skill Enhancement  
- 1 Awaiting Placement  

👉 Bar Cahrt can highlights the highest and lowest categories clearly.

---

### 📈 KPI Cards
- Total Graduates: 247  
- Employed: 157  
- Unemployed: 33  
- Further Studies: 50  
- Skill Enhancement: 6  
- Awaiting Placement: 1  

👉 Provides a quick executive summary.

---

### 🎛️ Slicers
- Faculty (18 faculties)  
- Program (dynamic based on selected faculty)  

✔ Allows users to focus on specific faculty and program  
✔ Improves usability and analysis efficiency  

---

## 📐 DAX Measures (Core Calculations)

### 📉 Graduate Employment (GE) – Optimized

```DAX
% GE KESELURUHAN =
DIVIDE(
    CALCULATE(
        SUM('ANALISIS FAKULTI'[Bekerja]),
        ALLEXCEPT('ANALISIS FAKULTI', 'ANALISIS FAKULTI'[FPIA])
    ),
    CALCULATE(
        SUM('ANALISIS FAKULTI'[Jumlah Graduan]),
        ALLEXCEPT('ANALISIS FAKULTI', 'ANALISIS FAKULTI'[FPIA])
    ),
    0
)
```

👉 Measures proportion of employed graduates at faculty level.

---

### 📈 Graduate Marketability (GM)

```DAX
% GM KESELURUHAN = 
DIVIDE(
    CALCULATE(
        SUM('ANALISIS FAKULTI'[Jumlah Graduan]) 
        - SUM('ANALISIS FAKULTI'[Belum bekerja]),
        ALLEXCEPT('ANALISIS FAKULTI', 'ANALISIS FAKULTI'[FPIA])
    ),
    CALCULATE(
        SUM('ANALISIS FAKULTI'[Jumlah Graduan]),
        ALLEXCEPT('ANALISIS FAKULTI', 'ANALISIS FAKULTI'[FPIA])
    ),
    0
)
```

👉 Includes employed, further studies, skill enhancement, and awaiting placement.

---

## 📊 Key Metrics

### 📉 Graduate Employment (GE)
- Measures employment rate only  
- Example: 63.56% (ASTIF)  

---

### 📈 Graduate Marketability (GM)
- Broader indicator of graduate success  
- Example: 86.64% (ASTIF)  

---

## 🔍 Analytical Capabilities
- Compare across 18 faculties  
- Drill down into specific programs  
- Identify unemployed graduates  
- Support intervention planning  

---

## 🎓 Program-Level Dashboard
Example: PhD in Computer Science  

### 📌 Program-Level Dashboard
![Program Dashboard](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/c73f83990b0b3523d2137b0addc2c3424ddc96ce/Dashboard/FKI_ProgramPengajian_Dashboard.png)

⚠️ Note:
- GE and GM remain constant  
- Calculated at faculty level, not per program  

---

## 🛠️ Tools & Technologies
- Power BI  
- DAX (Data Analysis Expressions)  
- Data Cleaning & Transformation  

---

## 💡 Key Insights
- 50 graduates pursue further studies  
- 33 graduates are unemployed and can be tracked  
- GM provides a more holistic view than GE  

---

## 🎯 Business Impact

This dashboard supports:

### 👨‍🏫 Deans
- Monitor faculty-level graduate performance  

### 🏫 University Management
- Track employability trends  

### 👔 Executive Meetings
Used in discussions with:
- Vice Chancellor (VC)  
- Deputy Vice Chancellor (DVC)  

👉 Enables data-driven decision making and strategic planning  
