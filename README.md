# 📊 Home-Property-Real-Estate-: AI-Driven Real Estate Intelligence
portfolio-Project

## 📌 Project Overview
This enterprise-grade Power BI repository evaluates **100,000 property transaction records** across regions, capturing a cumulative market volume of **$193bn**. Moving beyond flat, static reporting, this architecture utilizes native machine learning diagnostics—specifically **Key Influencers** and **Top Segments**—to extract multi-variable lifecycle drivers dictating property purchase prices.

---

## 🛠️ Data Infrastructure & Advanced DAX Engineering
To guarantee analytical accuracy and bypass data conflation during statistical distribution, the model implements a granular, row-level grain expanded via `house_id`. 

The data transformation layer relies on custom **Data Analysis Expressions (DAX)** to isolate transaction behaviors:

### 1. Built Category (Calculated Column)
Maps property lifecycles dynamically and flags non-linear variations, cleanly segregating unique off-plan market profiles:
```dax
Built Category = 
VAR TimelineDifference = YEAR('housing_data'[date]) - 'housing_data'[year_build]
RETURN
    SWITCH(
        TRUE(),
        ISBLANK('housing_data'[year_build]), "Unknown",
        TimelineDifference < 0, "Pre-built / ကြိုပွိင့်",
        TimelineDifference <= 5, "Brand New (0-5 Years)",
        TimelineDifference <= 15, "Recent (6-15 Years)",
        "Established (16+ Years)"
    )
```

### 2. Year Over Year Growth % (Time-Intelligence Measure)
Monitors macro-level capital performance trends across shifting market timelines:
```dax
Year Over Year Growth % = 
VAR CurrentYearSales = SUM('housing_data'[purchase_price])
VAR PreviousYearSales = CALCULATE(SUM('housing_data'[purchase_price]), SAMEPERIODLASTYEAR('Date_Table'[Date]))
RETURN
    DIVIDE(CurrentYearSales - PreviousYearSales, PreviousYearSales, 0)
```

---

## 🔎 Key Influencers & Segment Breakdown

### 📉 Page 1: Drivers for Price Decrease (The Stagnation Window)
- **Primary Influencer:** Property age acts as the single highest indicator for market devaluation when entering its mid-life lifecycle.
- **AI Segment 1 Condition:** `House Age` is **greater than 16 and less than or equal to 45 years**.
- **Statistical Output:** Encompassing **27,461 data points** (27.5% of the model), the segment drops to an average of **$1.54M**, making it a massive **$385.8K lower** than the overall baseline average of $1.93M.

### 📈 Page 2: Drivers for Price Increase (The Premium Curves)
The ML engine isolated a definitive U-Curve pricing structure, identifying two separate high-value sectors:
- **Segment 1 (The Youth Premium):** Properties aged **16 years or newer** experience a steep value surge. It clocks an average of **$2.50M**, driving prices a staggering **$573.9K higher** than the baseline market rate.
- **Segment 2 (The Vintage Resurgence):** Structural assets exceeding **75 years old** gain historical landmark premiums. This sector contains **28,375 data points** and boosts average pricing to **$2.23M** (a **$303K increase** over baseline).

---

## 🖼️ Dashboard Previews & Visualizations
<img width="575" height="325" alt="image" src="https://github.com/user-attachments/assets/ea029eeb-70c5-48b8-88e0-4bb58ce6d8a8" />


### 📊 Model Core Architecture & Slicer Controls
![Main Dashboard View](<img width="576" height="325" alt="image" src="https://github.com/user-attachments/assets/3f0329c2-3033-4f8e-a36e-698425795d7d" />
)


### 🤖 Machine Learning Diagnostic Layouts
![Key Influencers Analysis](<img width="604" height="334" alt="image" src="https://github.com/user-attachments/assets/55306898-d00e-431b-ba30-e44c452d64f6" />
)(<img width="604" height="304" alt="image" src="https://github.com/user-attachments/assets/e1ab6f2b-ded6-4177-9a05-92e85cc2dee1" />)


---

## 💡 Business Takeaways
1. **The Stagnation Valley:** Property investors can deliberately target properties in the 16–45 year valley for aggressive value-buys, using the $385.8K discount margin as negotiating leverage.
2. **Premium Allocations:** Capital allocations should favor high-velocity turnarounds in brand-new builds (≤16 years) or historical vintage investments (>75 years) to optimize premium yield performance.

---

## 🧑‍💻 Technical Competencies Demonstrated
- **Advanced Data Modeling:** One-to-Many star schema connectivity across independent dimension calendars and fact tables.
- **AI Visual Customization:** Implementing continuous-to-categorical bin transitions alongside contextualized Smart Narrative tokens.
- **Granularity Optimization:** Row-level parent-table indexing to guarantee exact mathematical outputs across visual dependencies.

---
*Maintained by **Paing Soe Tun** | Microsoft Certified: Power Bi Data Analyst Associate*
