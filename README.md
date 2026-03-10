# 🚬 Vaping & Workplace Productivity
### A Data-Driven Analysis · Survey · n = 146

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat-square&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-2.x-150458?style=flat-square&logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-Interactive-3F4F75?style=flat-square&logo=plotly&logoColor=white)
![SciPy](https://img.shields.io/badge/SciPy-Stats-8CAAE6?style=flat-square&logo=scipy&logoColor=white)
![Colab](https://img.shields.io/badge/Google_Colab-Notebook-F9AB00?style=flat-square&logo=googlecolab&logoColor=white)

---

## 📌 Overview

This project investigates the **measurable impact of vaping on workplace and academic productivity** through survey analysis, statistical testing, and a custom time-loss model.

The data was collected from **146 active vape users** via a structured Google Forms survey. The analysis spans descriptive statistics, inferential testing, user segmentation, and a quantitative model that estimates how many working minutes per day are lost to vaping behavior.

> **Key finding:** On average, users self-reported operating at **~67% of their normal productivity** while vaping — yet the majority were unaware of the root cause.

---

## 🗂️ Project Structure

```
├── Vaping_Workplace_Productivity.ipynb   # Main analysis notebook
├── survey.csv           # Raw survey data (146 responses)
└── README.md
```

---

## 🔍 Methodology

The project follows a structured data analysis pipeline:

**1. Data Cleaning & Normalization**
- Encoded ordinal categorical variables (`duracion_vape`, `hits_por_periodo`, `duracion_periodo`) using pandas `Categorical` with custom orderings
- Stripped encoding artifacts from Google Forms export
- Renamed columns to short, readable aliases for clean code

**2. Exploratory Data Analysis (EDA)**
- Distribution of productivity scores (mean, median, mode)
- Usage patterns: continuous vs periodic vaping
- Primary reported effects: relaxation, dizziness, happiness, sleepiness, energy

**3. Time-Loss Model**
- Built a parametric model to estimate the % of an 8-hour workday lost to vaping
- Inputs: weighted average hits/session, session duration, vape lifespan, refractory time
- Includes a **sensitivity analysis** across all lifespan scenarios (1–3 days → 1+ month)

**4. Statistical Testing**
- **Chi² + Cramér's V** — independence tests between 6 categorical variable pairs
- **Spearman Correlation Matrix** — monotonic relationships without normality assumption
- **Mann-Whitney U Test** — non-parametric comparison of heavy vs light users

**5. User Segmentation**
- Heavy users (≥8 hits/period) vs Light users
- Awareness profiling: Conscious / Partial / Unaware of vaping's impact

---

## 📊 Key Results

| Finding | Result |
|---------|--------|
| Average self-reported productivity | **6.7 / 10** (67%) |
| Users who vape at work or school | **77%** |
| Estimated workday lost (average user) | **~20–35 minutes/day** |
| Heavy vs Light user productivity difference | **Statistically significant** (p < 0.05) |
| Users unaware of vaping's impact | **Majority** |
| Dizziness → lowest productivity group | ✅ Confirmed |

---

## 📉 Time-Loss Model

The model estimates lost labor time using the following logic:

```python
periods_per_day  = (puffs_per_vape / avg_hits) / avg_vape_lifetime_days
periods_in_shift = periods_per_day * (1/3)   # labor = 1/3 of the day
lost_seconds     = (avg_session_duration + refractory_time) * periods_in_shift
pct_lost         = (lost_seconds / 28800) * 100
```

The sensitivity analysis shows that even **casual users** (vape lasts 3+ weeks) lose a non-trivial portion of their productive time.

---

## 🛠️ Tech Stack

| Tool | Purpose |
|------|---------|
| `pandas` | Data loading, cleaning, transformation |
| `numpy` | Numerical computation |
| `plotly` | All interactive visualizations |
| `scipy.stats` | Chi², Spearman correlation, Mann-Whitney U |
| `Google Colab` | Execution environment |

---

## 📈 Visualizations

All charts are built with **Plotly** on a dark theme and include:

- Histogram with mean/median/mode reference lines
- Bar charts with error bars (± std dev)
- Heatmaps (crosstab & Spearman matrix)
- Violin plots with individual data points
- Donut charts for categorical distributions
- 6-panel consolidated dashboard

---

## ⚠️ Limitations

- **Self-report bias** — users may underestimate negative effects
- **Convenience sample** — 146 respondents, not population-representative
- The time-loss model assumes **uniform behavior** during work hours
- No control for confounders (age, job type, workload, nicotine tolerance)

---

## 🔭 Future Work

- [ ] Expand sample with stratification by industry and role
- [ ] Incorporate objective productivity metrics (tasks completed, error rates)
- [ ] Longitudinal follow-up: same users tracked before and after quitting
- [ ] Regression model to isolate vaping's effect from other variables

---

## 👤 Author

Made with curiosity and Python.  
Feel free to reach out or open an issue if you have questions about the methodology.
