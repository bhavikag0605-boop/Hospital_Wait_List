# Hospital_Wait_List

## 📌 Project Overview

An end-to-end interactive Power BI dashboard analyzing hospital patient waitlist trends across specialties, case types, age profiles, and time bands. The dashboard empowers healthcare administrators and analysts to monitor waitlist growth, identify bottlenecks, and make data-driven operational decisions to improve patient throughput and reduce wait times.

## 🎯 Business Problem

Healthcare systems struggle to manage growing patient backlogs, especially post-pandemic. This project addresses the challenge of tracking and comparing waitlist volumes across medical specialties and patient demographics to prioritize resource allocation and reduce patient wait times.

## 📊 Dashboard Pages

| Page | Description |
|------|-------------|
| **Summary** | High-level KPIs, trend lines, donut chart, specialty matrix |
| **Detail** | Granular pivot analysis by specialty, age, and time band |
| **Drill Down** | Specialty group bar chart for deep-dive exploration |

## 🔑 Key Metrics & Features

- **Latest Month Wait List** — real-time KPI card for current backlog volume
- **PY Latest Month Wait List** — prior-year comparison for YoY trend tracking
- **Avg/Med Wait List** — toggle between Average and Median calculation methods
- **Dynamic Title** — context-aware visuals that update with slicer selections
- **Trend Line Charts** — time-series analysis by Case Type (Inpatient / Outpatient / Day Case)
- **Donut Chart** — case type distribution at a glance
- **Column Chart** — waitlist breakdown by Time Bands and Age Profile
- **Specialty Matrix** — pivot table ranking specialties by average waitlist volume

## 🗂️ Data Model

| Table | Role |
|-------|------|
| All_Data | Fact table — waitlist records with dates and totals |
| Calculation Method | Dimension — Avg vs Median toggle |
| Mapping_Specialty1 | Dimension — specialty group mapping |

**Key Columns:** Archive_Date, Case_Type, Specialty_Name, Age_Profile, Time_Bands, Total

## ⚙️ DAX Measures

```dax
Latest Month Wait List =
    CALCULATE(SUM(All_Data[Total]),
        All_Data[Archive_Date] = MAX(All_Data[Archive_Date]))

PY Latest Month Wait List =
    CALCULATE([Latest Month Wait List],
        SAMEPERIODLASTYEAR(All_Data[Archive_Date]))

Avg/Med Wait List =
    SWITCH(SELECTEDVALUE('Calculation Method'[Calc Method]),
        "Average", AVERAGE(All_Data[Total]),
        "Median",  MEDIAN(All_Data[Total]))
```

## 🛠️ Tools & Technologies

- **Microsoft Power BI Desktop** — Report authoring & DAX development
- **Power Query (M Language)** — Data ingestion & transformation
- **DAX** — Custom measures, KPIs, and dynamic calculations
- **Data Modeling** — Star schema with fact & dimension tables

## 📈 Key Insights

- Identified specialties with the highest waitlist growth year-over-year
- Revealed that long-wait time bands (18+ months) concentrate in specific surgical specialties, enabling targeted resource reallocation
- Median-based filtering exposed outlier distortion in average metrics, surfacing more reliable trends for decision-making


## 🚀 Getting Started

1. Download and install [Power BI Desktop](https://powerbi.microsoft.com/desktop/)
2. Clone this repository:
   ```bash
   git clone https://github.com/yourusername/hospital-waitlist-analysis.git
   ```
3. Open `hospital_analysis.pbix` in Power BI Desktop
4. Use the slicers (Date, Case Type, Specialty) to explore the dashboard

## 👤 Author

🔗 [LinkedIn](www.linkedin.com/in/bhavika-gaikwad-282175250)
🐙 [GitHub](https://github.com/bhavikag0605-boop)
