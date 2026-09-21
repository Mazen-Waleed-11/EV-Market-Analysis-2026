
# 🚗⚡ EV Global Market 2026 — Power BI Dashboard

A professional, multi-page Power BI report built on a 2,000-record EV market dataset spanning **20 brands** across **6 countries**. The report follows a **Hierarchical Hub-and-Spoke** structure — moving the viewer from the global big picture down to individual brand and model performance.

---

## 📊 Dashboard Structure

| Page | Name | Focus |
|------|------|-------|
| 1 | **Global Executive Summary** | Geopolitical blocs, global KPIs, tech benchmarking |
| 2 | **Regional & Country Deep-Dive** | Per-country toggle, value maps, segment mix |
| 3 | **Competitive Landscape** | Brand leaderboard, scatter plots, efficiency rankings |
| 4 | **Brand / Model Drill-Through** | Model-level detail, safety, variant performance |

---

## 📁 Dataset Overview

**File:** `ev_market_2026_modified.csv`
**Records:** 2,000 rows × 25 columns

### Columns

| Column | Type | Description |
|--------|------|-------------|
| `ev_id` | Integer | Unique record identifier |
| `brand` | Text | EV manufacturer name |
| `model` | Text | Vehicle model name |
| `year` | Integer | Model year |
| `variant` | Text | Trim level (Standard / Long Range / Performance / Premium) |
| `price_usd` | Decimal | Retail price in USD |
| `battery_capacity_kwh` | Decimal | Battery size in kilowatt-hours |
| `range_miles` | Decimal | EPA-estimated range in miles |
| `charging_speed_kw` | Decimal | Max DC fast-charging speed in kW |
| `acceleration_0_60_mph` | Decimal | 0–60 mph time in seconds |
| `top_speed_mph` | Decimal | Top speed in mph |
| `horsepower` | Integer | Motor output in hp |
| `torque_nm` | Integer | Torque in Newton-metres |
| `drive_type` | Text | AWD / FWD / RWD |
| `seating_capacity` | Integer | Number of seats |
| `body_type` | Text | Coupe / Hatchback / Sedan / SUV / Truck / Van |
| `cargo_volume_cubic_ft` | Decimal | Cargo space in cubic feet |
| `weight_kg` | Decimal | Curb weight in kg |
| `safety_rating` | Integer | Safety score (1–5) |
| `autopilot_level` | Integer | SAE autonomy level (0–3) |
| `country_of_origin` | Text | Manufacturing country |
| `market_segment` | Text | Budget / Mid-Range / Premium / Luxury |
| `annual_sales_units` | Integer | Yearly units sold |
| `customer_rating` | Decimal | Customer satisfaction score |
| `warranty_years` | Integer | Warranty duration in years |

### Coverage

- **20 Brands:** Audi, BMW, BYD, Fisker, Ford, GM/Chevrolet, Honda, Hyundai, Kia, Lucid, Mercedes, NIO, Polestar, Porsche, Rivian, Tesla, Toyota, Volkswagen, Volvo, Xiaomi
- **6 Countries:** China, Germany, Japan, South Korea, Sweden, USA
- **4 Market Segments:** Budget, Mid-Range, Premium, Luxury
- **3 Geopolitical Blocs:** Asia · Europe · North America

---

## 🛠️ Tools & Techniques

| Tool | Usage |
|------|-------|
| **Power BI Desktop** | Report building, visuals, publishing |
| **Power Query (M Language)** | Data cleaning, type casting, custom column creation |
| **DAX** | KPI measures, variance calculations, % share metrics |
| **Custom JSON Theme** | Consistent "Deep Ocean Tech" dark color palette |

---

## 🔧 Key Power Query Transformations

- Fixed inconsistent country casing (`Us` → `USA`)
- Added **`Bloc`** column: Asia / Europe / North America
- Added **`Price_Tier`** column: Under \$40K / \$40K–\$70K / \$70K–\$100K / Over \$100K
- Standardized `body_type` to Proper Case
- Enforced correct data types across all 25 columns

---

## 📐 Key DAX Measures

```dax
-- Core KPIs
Total Sales Units = SUM(EV_Data[annual_sales_units])
Avg Price USD     = AVERAGE(EV_Data[price_usd])
Avg Range Miles   = AVERAGE(EV_Data[range_miles])
Efficiency Score  = DIVIDE(AVERAGE(EV_Data[range_miles]), AVERAGE(EV_Data[battery_capacity_kwh]), 0)

-- Country vs Global Variance
Price vs Global Avg    = [Avg Price USD] - CALCULATE(AVERAGE(EV_Data[price_usd]), ALL(EV_Data))
Range vs Global Avg    = [Avg Range Miles] - CALCULATE(AVERAGE(EV_Data[range_miles]), ALL(EV_Data))
Charging vs Global Avg = [Avg Charging Speed kW] - CALCULATE(AVERAGE(EV_Data[charging_speed_kw]), ALL(EV_Data))

-- Share
% of Global Sales = DIVIDE([Total Sales Units], CALCULATE([Total Sales Units], ALL(EV_Data)), 0)
```

---

## 🎨 Color Theme — "Deep Ocean Tech"

| Role | Color |
|------|-------|
| Page Background | `#0D1B2A` |
| Visual Background | `#132F4C` |
| Header / Title Bar | `#0A2540` |
| Primary Blue | `#42A5F5` |
| Asia Bloc | `#EF5350` |
| Europe Bloc | `#26C6DA` |
| North America Bloc | `#42A5F5` |
| Positive / Good | `#66BB6A` |
| Negative / Bad | `#EF5350` |
| Accent Teal | `#00B4D8` |

Theme applied via a custom **`EV_Theme_v2.json`** file (included in this repository).

---

## 📂 Repository Structure

```
📦 ev-market-2026-powerbi
 ┣ 📄 ev_market_2026_modified.csv   ← Source dataset
 ┣ 📄 EV_Theme_v2.json              ← Custom Power BI color theme
 ┣ 📄 EV_Market_2026.pbix           ← Power BI report file
 ┗ 📄 README.md                     ← This file
```

---

## 🚀 How to Use

1. Clone or download this repository
2. Open **`EV_Market_2026.pbix`** in Power BI Desktop
3. If prompted, update the CSV file path in **Transform Data → Advanced Editor** to match your local path
4. The theme applies automatically — if not, go to **View → Themes → Browse** and load `EV_Theme_v2.json`
5. Use the **Country Slicer** on Page 2 to toggle between the 6 countries
6. Click any brand on Page 3 to drill through to Page 4 for model-level detail

---

## 💡 Key Insights the Report Surfaces

- Which **geopolitical bloc** leads in sales volume, battery tech, and charging speed
- Which **countries** produce the most expensive vs most efficient EVs
- Which **brands** are "Value Leaders" vs "Overpriced" on a Price × Range scatter plot
- Which **market segments** dominate each country
- How each country benchmarks against the **global average** across 3 key metrics

---

## 👤 Author

**Mazen Waleed Aboelmagd**
Computer Science Student — MSA University
Data Analytics & Business Intelligence

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/mazen-waleed-cs)

---

> *Dataset used for academic and portfolio purposes.*
