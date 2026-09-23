# AI-Powered Student Career & Placement Analytics

A professional, interactive Streamlit dashboard for analysing student placement outcomes, skill gaps, and personalised career guidance — built on a verified 12,000-student dataset.

---

## 📋 Project Overview

This dashboard analyses placement outcomes for Indian engineering students and provides:

- **Headline KPIs** and the core placement story
- **Threshold-based placement analysis** — verified 100% accuracy on 3-factor rule
- **Skill gap profiling** — placed vs not-placed comparison
- **Per-student eligibility assessment** — instant rule-based evaluation
- **AI Career Advisor** — prioritised, data-driven improvement recommendations
- **Interactive data explorer** with CSV export

---

## 🗂️ Project Files

```
dashboard/
├── app.py                          # Main entry point
├── student_placement_clean.csv     # Cleaned dataset (12,000 rows × 14 cols)
├── requirements.txt                # Python dependencies
├── README.md                       # This file
├── .streamlit/
│   └── config.toml                 # Theme and server config
├── pages/
│   ├── 1_📊_Overview.py            # KPI cards + placement story
│   ├── 2_🎯_Placement_Insights.py  # Threshold charts + segment analysis
│   ├── 3_📉_Skill_Gap_Analysis.py  # Feature comparisons + radar + scatter
│   ├── 4_🧑‍🎓_Student_Assessment.py  # Per-student eligibility checker
│   ├── 5_🤖_AI_Career_Advisor.py   # Personalised improvement plan
│   └── 6_🔍_Data_Explorer.py       # Filterable table + histogram + download
└── utils/
    ├── __init__.py
    ├── data_loader.py              # @st.cache_data, computed columns, filters
    ├── charts.py                   # Reusable Plotly chart builders
    └── theme.py                    # Colour palette, CSS, layout constants
```

---

## 🚀 Quick Start

### 1. Install dependencies

```bash
pip install -r requirements.txt
```

### 2. Run the dashboard

```bash
cd dashboard
streamlit run app.py
```

The app opens at `http://localhost:8501` in your browser.

---

## 📊 Dataset

| Property | Value |
|---|---|
| File | `student_placement_clean.csv` |
| Rows | 12,000 students |
| Columns | 14 (identifier + 12 features + target) |
| Target | `placed` (0 = Not Placed, 1 = Placed) |
| Placement rate | 30.4% (3,652 placed) |

### Feature columns used for analysis

| Column | Type | Description |
|---|---|---|
| `cgpa` | Continuous | Grade point average (5.5–9.8) |
| `aptitude_score` | Integer | Aptitude test score (40–99) |
| `coding_skills` | Integer (1–10) | Coding ability rating |
| `communication_skills` | Integer (1–10) | Communication rating |
| `internships` | Integer (0–3) | Number of internships |
| `certifications` | Integer (0–5) | Number of certifications |
| `projects` | Integer (0–5) | Number of projects |
| `backlogs` | Integer (0–3) | Academic backlogs |
| `degree` | Categorical | BE / BTech / BCA / BSc |
| `branch` | Categorical | CS / IT / DS / AI / Electrical / Mechanical |
| `gender` | Categorical | Male / Female |
| `age` | Integer (20–24) | Student age |

> **Note:** `company_type` and `package_lpa` from the original dataset are excluded — they are post-placement outcome fields, not placement predictors.

---

## 🔑 Key Findings

### Placement is governed by a deterministic three-factor rule

> **`coding_skills ≥ 5` AND `aptitude_score ≥ 60` AND `cgpa ≥ 6.5` → placed = 1**

This rule achieves **100% accuracy** on the 12,000-student dataset. No student below any one of these thresholds is placed; all students meeting all three are placed.

### Correlation with placement (point-biserial r)

| Feature | r | p-value |
|---|---|---|
| coding_skills | **+0.463** | < 0.001 |
| aptitude_score | **+0.390** | < 0.001 |
| cgpa | **+0.265** | < 0.001 |
| communication_skills | −0.006 | 0.545 (NS) |
| backlogs | −0.001 | 0.940 (NS) |
| certifications | +0.007 | 0.457 (NS) |

### Why students are not placed (8,348 not-placed)

| Root Cause | Count | Share |
|---|---|---|
| Only coding < 5 | 2,457 | 29.4% |
| Only aptitude < 60 | 1,874 | 22.4% |
| Coding + Aptitude fail | 1,226 | 14.7% |
| Only CGPA < 6.5 | 1,098 | 13.2% |
| Coding + CGPA fail | 755 | 9.0% |
| Aptitude + CGPA fail | 567 | 6.8% |
| All three fail | 371 | 4.4% |

---

## ⚠️ Disclaimer

All findings are descriptive of the training dataset. The placement eligibility rule and recommendations should not be interpreted as guarantees of placement in any real recruitment process. Real-world placement depends on many additional factors including interview performance, available roles, and company-specific criteria.

---

## 🛠️ Tech Stack

| Library | Version | Role |
|---|---|---|
| Streamlit | ≥ 1.35 | Dashboard framework |
| Plotly | ≥ 5.20 | Interactive charts |
| Pandas | ≥ 2.0 | Data wrangling |
| NumPy | ≥ 1.26 | Numeric operations |
| SciPy | ≥ 1.11 | Statistical tests |

---

## 👤 Author

Built as part of the AI-Powered Student Career & Placement Analytics project · 2025
