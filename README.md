# 🎓 UMS Graduate Employability Analytics Dashboard (SKPG 2025)

## 📌 Project Overview

This repository hosts the **UMS Graduate Tracer Dashboard** – an enterprise-grade Power BI analytics solution developed for **Universiti Malaysia Sabah (UMS)**. The dashboard transforms raw graduate tracer data into actionable intelligence for university leadership.

### 🎯 Primary Stakeholders & Use Cases

| Stakeholder | Purpose |
|-------------|---------|
| **Vice Chancellor (VC)** | University-wide employability performance review |
| **Deputy Vice Chancellor (DVC)** | Strategic KPI tracking & resource allocation |
| **Faculty Deans** | Faculty-level performance monitoring & program improvement |
| **Executive Management** | Data-driven decision making for academic planning |

### 💼 Business Impact

> **Enables faculty-level and executive meetings** with real-time graduate outcome insights, supporting strategic planning and enhancing UMS’s institutional reputation for graduate employability.

This dashboard bridges the gap between raw graduate tracer data and executive decision-making. By consolidating employability metrics across faculties, it allows leadership to quickly identify underperforming areas, allocate resources effectively, and design targeted interventions to improve graduate outcomes.

At the executive level, it reduces reliance on manual reporting and enables data-driven discussions during strategic meetings, particularly for tracking institutional KPIs such as Graduate Employability (GE) and Graduate Marketability (GM).

---

## 📂 Dataset Overview

| Attribute | Details |
|-----------|---------|
| **Source** | Raw graduate tracer data – University Malaysia Sabah (UMS) |
| **Coverage** | 18 faculties + multiple academic programs |
| **Data Year** | SKPG 2025 |
| **Data Format** | Structured dataset (CSV/Excel) |

---

## 🧹 Data Preparation & ETL

The raw dataset underwent a rigorous cleaning and transformation process:

- ✅ Handling missing (null/blank) values
- ✅ Standardizing employment category labels
- ✅ Ensuring data consistency across 18 faculties
- ✅ Validating graduate totals for accurate reporting
- ✅ Structuring data for DAX calculations

This step was critical to ensure data reliability and consistency across faculties. Given that the dataset originated from multiple sources and formats, inconsistencies in labeling and missing values could significantly impact KPI accuracy.

By standardizing categories and validating totals, the dataset was transformed into a clean analytical layer, ensuring that all downstream visualizations and calculations reflect accurate institutional performance.

---

## 🖥️ Dashboard Features

![Overall Dashboard](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/625ad5403ced7ccb8a24c573210e61a9d735ffa9/Dashboard/Overall_Dashboard.png)

#### Key Components:

| Feature | Description |
|---------|-------------|
| **📊 Bar Chart** | Sorted highest to lowest – enables rapid analysis of graduate outcomes |
| **📇 KPI Cards** | Exact numerical values for each outcome category |
| **🎛️ Slicers** | Dynamic filtering by **Faculty** & **Program of Study** |
| **📐 GE & GM Metrics** | Faculty-level calculations (not program-specific) |
| **🏛️ Faculty Filter** | View data for any of 18 faculties |

The dashboard is designed with an executive-first approach, prioritizing clarity and speed of interpretation.

- The sorted bar chart allows stakeholders to immediately identify top and bottom performing categories without manual comparison.
- KPI cards provide quick numerical summaries for high-level reporting.
- Interactive slicers enable drill-down analysis, allowing users to transition from university-wide insights to specific faculties or programs.

This design ensures that both strategic (VC/DVC) and operational (Deans) users can extract value from the same dashboard.

## 📐 Core DAX Formulas

**% Graduate Employability (GE) – Overall**
```dax
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

**% Graduate Marketability (GM) – Overall**
```dax
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

> **⚠️ Important:** GE & GM are calculated **at faculty level only**, not per program. This ensures consistency in executive reporting.

Graduate Employability (GE) and Graduate Marketability (GM) are standardized KPIs used in higher education performance tracking.

GE measures the proportion of graduates who are employed, reflecting immediate job placement success.
GM expands this definition by including graduates who are pursuing further studies, undergoing upskilling, or awaiting placement.

By calculating these metrics at the faculty level, the dashboard avoids distortion caused by small program sample sizes and ensures fair comparison across faculties.

---

## 🏛️ Faculty Performance Dashboards

### 1. Faculty of Computer & Informatics (FKI)

![FKI Faculty Dashboard](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/625ad5403ced7ccb8a24c573210e61a9d735ffa9/Dashboard/FKI_Faculty.png)

| Metric | Value |
|--------|-------|
| Total Graduates | 376 |
| Employed | 289 |
| Unemployed | 36 |
| Further Study | 18 |
| Upskilling | 25 |
| Waiting Placement | 8 |
| **GE** | **76.86%** |
| **GM** | **90.43%** |

The Faculty of Computer & Informatics demonstrates strong employability performance with a GE of 76.86% and GM of 90.43%.

However, the presence of unemployed graduates (36) suggests potential gaps in job alignment or market demand, indicating opportunities for curriculum enhancement or stronger industry collaboration.

---

### 📘 FKI – Data Science Program

![FKI Data Science Program](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/625ad5403ced7ccb8a24c573210e61a9d735ffa9/Dashboard/FKI_Faculty_Program_Data_Science.png)

| Metric | Value |
|--------|-------|
| Total Graduates | 73 |
| Employed | 53 |
| Unemployed | 12 |
| Further Study | 3 |
| Upskilling | 4 |
| Waiting Placement | 1 |
| Faculty | Computer & Informatics |
| Program | Data Science |

---

### 2. Faculty of Engineering (FKJ)

![FKJ Faculty Dashboard](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/625ad5403ced7ccb8a24c573210e61a9d735ffa9/Dashboard/FKJ_Faculty.png)

| Metric | Value |
|--------|-------|
| Total Graduates | 312 |
| Employed | 254 |
| Unemployed | 28 |
| Further Study | 20 |
| Upskilling | 7 |
| Waiting Placement | 3 |
| **GE** | **81.41%** |
| **GM** | **91.03%** |

Engineering shows the highest employability among the three faculties (GE: 81.41%), indicating strong industry demand.

The Oil & Gas program, however, reveals a unique pattern where a large proportion of graduates pursue further studies (14 out of 21), suggesting either specialization requirements or limited immediate job opportunities in the sector.

---

### ⛽ FKJ – Oil & Gas Program

![FKJ Oil & Gas Program](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/625ad5403ced7ccb8a24c573210e61a9d735ffa9/Dashboard/FKJ_Faculty_Program_Oil_and_Gas.png)

| Metric | Value |
|--------|-------|
| Total Graduates | 21 |
| Employed | 2 |
| Unemployed | 3 |
| Further Study | 14 |
| Upskilling | 1 |
| Waiting Placement | 1 |
| Faculty | Engineering |
| Program | Oil & Gas |

---

### 3. Faculty of Medicine & Health Sciences

![FMHS Faculty Dashboard](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/625ad5403ced7ccb8a24c573210e61a9d735ffa9/Dashboard/FSSK_Faculty.png)

| Metric | Value |
|--------|-------|
| Total Graduates | 247 |
| Employed | 157 |
| Unemployed | 33 |
| Further Study | 50 |
| Upskilling | 6 |
| Waiting Placement | 1 |
| **GE** | **63.56%** |
| **GM** | **86.64%** |

The Faculty of Medicine & Health Sciences has a relatively lower GE (63.56%) but maintains a high GM (86.64%).

This is largely influenced by the Medical Doctor program, where a significant number of graduates are in waiting placement (31) — a structural characteristic of the medical profession rather than a performance issue.

---

### 🩺 FMHS – Medical Doctor Program

![FMHS Medical Doctor Program](https://github.com/azlinaaaa/UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/blob/625ad5403ced7ccb8a24c573210e61a9d735ffa9/Dashboard/FSSK_Faculty_Program_Medical_Doctor.png)

| Metric | Value |
|--------|-------|
| Total Graduates | 91 |
| Employed | 58 |
| Unemployed | 0 |
| Further Study | 2 |
| Upskilling | 0 |
| Waiting Placement | 31 |
| Faculty | Medicine & Health Sciences |
| Program | Medical Doctor |

---

## 📊 Executive Summary Dashboard

| Faculty | Graduates | Employed | GE (%) | GM (%) |
|---------|-----------|----------|--------|--------|
| Computer & Informatics (FKI) | 376 | 289 | 76.86% | 90.43% |
| Engineering (FKJ) | 312 | 254 | 81.41% | 91.03% |
| Medicine & Health Sciences | 247 | 157 | 63.56% | 86.64% |

The executive summary provides a consolidated view of faculty performance, enabling quick benchmarking across faculties.

From this view:

- Engineering leads in employability (GE)
- Computer & Informatics shows balanced performance
- Medicine reflects structural employment pathways rather than traditional job placement

This allows leadership to differentiate between performance issues vs systemic factors.

---

## 👔 Executive Meeting Use Cases

| Meeting Type | Dashboard Application |
|--------------|----------------------|
| **VC Monthly Review** | University-wide GE/GM trends, faculty ranking |
| **DVC Strategic Planning** | Resource allocation to low-GE faculties |
| **Faculty Dean Meetings** | Program-level drill-down for underperforming courses |
| **Board of Directors** | Institutional employability KPIs |

The dashboard is specifically designed to support multiple levels of decision-making:

- At the VC level, it provides a high-level overview of institutional performance.
- At the DVC level, it supports strategic interventions and policy decisions.
- At the faculty level, it enables targeted program improvements.

This multi-layer usability makes the dashboard a central decision-support system within the university.

---

## 🛠️ Technical Stack

| Component | Technology |
|-----------|------------|
| Dashboard | Power BI Desktop |
| Data Processing | Power Query (ETL) |
| Calculations | DAX (Data Analysis Expressions) |
| Data Source | UMS Graduate Tracer Dataset (SKPG 2025) |
| Version Control | GitHub |

---

## 📁 Repository Structure

```
UMS_Graduate_Employability_Analytics_Dashboard_-SKPG-2025-/
│
├── Dashboard/
│   ├── Overall_Dashboard.png
│   ├── FKI_Faculty.png
│   ├── FKI_Faculty_Program_Data_Science.png
│   ├── FKJ_Faculty.png
│   ├── FKJ_Faculty_Program_Oil_and_Gas.png
│   ├── FSSK_Faculty.png
│   └── FSSK_Faculty_Program_Medical_Doctor.png
│
├── Data/
│   └── ANALISIS_FAKULTI.csv
│
├── UMS_Graduate_Dashboard.pbix
└── README.md
```


---

## 📄 License

© 2025 Universiti Malaysia Sabah (UMS) – All Rights Reserved  
This dashboard is for **internal university governance and executive decision-making only**. Not for external redistribution without written permission.

---
