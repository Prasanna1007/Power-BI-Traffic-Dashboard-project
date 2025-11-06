# Power-BI-Traffic-Dashboard-project
“Power BI dashboard analyzing AdWords keyword performance and position trends.”

# 📊 Internship Traffic Data Dashboard (Power BI)

An interactive Power BI dashboard that analyzes Google AdWords keyword, CPC, and position data to uncover traffic trends and performance insights.

---

## 🧩 Project Overview

This project connects multiple AdWords-related tables (`adword_maintable`, `cpc_dimtable`, `traffic_dimtable`, `keyword_dimtable`, and `position_dimtable`) from MySQL to Power BI.  
It visualizes **search performance, cost efficiency, and ranking improvements** across keywords and campaigns.

---

## 🧠 Key Features

✅ **KPI Cards**
- **Total Traffic** — overall visits or impressions  
- **Total Cost** — total ad spend  
- **Avg CPC (Weighted)** — cost-per-click average  
- **Avg Position** — search position performance  
- **Position Δ (Change)** — ranking improvement indicator  

✅ **Interactive Visuals**
- **Total Traffic by Month**
- **Top 10 Keywords by Traffic**
- **Top 10 Titles by Traffic**
- **Position Δ by Keyword** *(green = improved, red = declined)*
- **Keyword & Month slicers** for filtering  

✅ **Custom Theme**
- Clean blue-white palette  
- Minimal card shadows  
- Consistent typography  

---

## 🧮 DAX Measures

```DAX
Total Traffic = SUM('internshipproject_trafficdata traffic_dimtable'[Traffic])

Total Cost = SUM('internshipproject_trafficdata traffic_dimtable'[Traffic_Cost])

Avg CPC (Weighted) =
DIVIDE(
    [Total Cost],
    [Total Traffic],
    BLANK()
)

Avg Position =
AVERAGE('internshipproject_trafficdata position_dimtable'[Position])

Position Δ =
AVERAGE('internshipproject_trafficdata position_dimtable'[Prev_Position]) -
AVERAGE('internshipproject_trafficdata position_dimtable'[Position])
