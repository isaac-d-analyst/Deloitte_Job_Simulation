# Daikibo Industrials — Manufacturing Downtime Analysis
### Deloitte Australia Job Simulation | Isaac Okolie | Tableau

---

## 📌 What This Project Is About

This project is a **data analysis job simulation** completed as part of the
**Deloitte Australia Data Analytics Job Simulation (Forage)**.

Daikibo Industrials is a global manufacturing company with factories across Japan,
Germany, and China. The task was to analyze machine telemetry data to identify
which factories and machines experienced the most downtime — and build an
interactive Tableau dashboard to communicate the findings to leadership.

---

## 🎯 Project Objectives

- Import and structure JSON telemetry data into Tableau
- Create a calculated field to quantify machine downtime in minutes
- Build a **Downtime Per Factory** chart to identify the highest-risk locations
- Build a **Downtime Per Machine** chart to identify the most failure-prone device types
- Combine both charts into a single interactive dashboard with filter synchronization

---

## 📊 Dataset Overview

| Property | Detail |
|----------|--------|
| Dataset | Daikibo Telemetry Data (JSON) |
| Total Records | 160,704 Events |
| File Format | JSON |
| Analysis Tool | Tableau |

### Key Fields:
- **deviceID** — Unique machine identifier
- **deviceType** — Type of manufacturing machine
- **timestamp** — Event timestamp
- **location.country** — Country of the factory
- **location.city** — City of the factory
- **location.area** — Industrial area
- **location.factory** — Factory name
- **location.section** — Section within the factory
- **data.status** — Machine status: `healthy` or `unhealthy`
- **data.temperature** — Machine temperature reading

---

## 🏭 Factories in Scope

| Factory | Country | City | Records |
|---------|---------|------|---------|
| daikibo-factory-meiyo | Japan | Tokyo | 40,176 |
| daikibo-factory-seiko | Japan | Tokyo | 40,176 |
| daikibo-berlin | Germany | Berlin | 40,176 |
| daikibo-shenzhen | China | Shenzhen | 40,176 |

---

## 🔧 Machine Types Monitored

AirWrench, CNC, ConveyorBelt, Furnace, HeavyDutyDrill,
LaserCutter, LaserWelder, MetalPress, SpotWelder

---

## 🛠️ Tools Used

| Tool | Purpose |
|------|---------|
| **Tableau** | Data visualization and dashboard design |
| **JSON** | Raw telemetry data format |

---

## ⚙️ Calculated Field

To quantify machine downtime, a calculated field named **Unhealthy** was created in Tableau:

```
IF [Status] = "unhealthy" THEN 10 ELSE 0 END
```

**Logic:** Each telemetry reading is sent every 10 minutes. If a machine reports
`unhealthy` status, it is counted as 10 minutes of downtime. If `healthy`, it
contributes 0 minutes. Summing this field per factory or device gives total
downtime in minutes.

---

## 📋 Status Distribution

| Status | Count | % of Total |
|--------|-------|-----------|
| Healthy | 160,601 | 99.94% |
| Unhealthy | 103 | 0.06% |

---

## 📈 Key Findings

### Downtime Per Factory (Minutes)

| Factory | Downtime (Mins) | Rank |
|---------|----------------|------|
| daikibo-factory-seiko | **480 mins** | #1 — Most Downtime |
| daikibo-shenzhen | **420 mins** | #2 |
| daikibo-factory-meiyo | **110 mins** | #3 |
| daikibo-berlin | **20 mins** | #4 — Least Downtime |

### Downtime Per Machine Type (Minutes)

| Device Type | Downtime (Mins) | Rank |
|-------------|----------------|------|
| LaserWelder | **480 mins** | #1 — Most Downtime |
| LaserCutter | **430 mins** | #2 |
| HeavyDutyDrill | **70 mins** | #3 |
| Furnace | **20 mins** | #4 |
| CNC | **10 mins** | #5 |
| SpotWelder | **10 mins** | #5 |
| ConveyorBelt | **10 mins** | #5 |
| MetalPress | **0 mins** | — No Downtime |
| AirWrench | **0 mins** | — No Downtime |

---

## 💡 Key Insights

1. **daikibo-factory-seiko** had the highest factory downtime at 480 minutes — a critical maintenance priority
2. **daikibo-shenzhen** follows closely at 420 minutes — also requires urgent operational review
3. **daikibo-berlin** is the best-performing factory with only 20 minutes of downtime
4. **LaserWelder** is the most failure-prone machine type across all factories
5. **LaserCutter** also shows significant downtime — both laser-based machines are high-risk
6. **MetalPress** and **AirWrench** recorded zero downtime — reliable and well-maintained

---

## ✅ Recommendations

1. Prioritize maintenance and inspection schedules for **daikibo-factory-seiko** and **daikibo-shenzhen**
2. Investigate root causes of repeated failures in **LaserWelder** and **LaserCutter** machines
3. Review operational practices at **daikibo-berlin** and apply learnings to higher-downtime factories
4. Implement predictive maintenance protocols for laser-based equipment across all factories

---

## 🖥️ Dashboard Design

The Tableau dashboard combines two interactive charts:

| Sheet | Chart Type | Visual |
|-------|-----------|--------|
| Sheet 1 | Bar Chart | Downtime Per Factory |
| Sheet 2 | Bar Chart | Downtime Per Machine Type |

**Interactive Feature:** Selecting a factory bar in Sheet 1 automatically filters
Sheet 2 to show only the machine downtime for that specific factory — enabling
drill-down analysis from location to machine level.

---

## 📁 Files in This Repository

| File | Description |
|------|-------------|
| `daikibo-telemetry-data.json` | Raw telemetry dataset — 160,704 records |
| `daikibo-dashboard.twbx` | Tableau packaged workbook |
| `screenshots/dashboard.png` | Dashboard screenshot |
| `README.md` | This documentation file |

---

## 🏢 About the Simulation

This project was completed as part of the **Deloitte Australia Technology
Virtual Experience Program** — a job simulation designed to replicate real
client engagements handled by Deloitte's technology consulting teams.

---

## 👤 Author

**Isaac Okolie**
Data Analyst & Data Analytics Tutor | Nigeria

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?logo=linkedin)](https://linkedin.com/in/isaac-okolie)

---

*Deloitte Australia Data Analytics Job Simulation | Manufacturing Analytics | Tableau*
