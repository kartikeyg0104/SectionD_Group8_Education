# Job Market Analytics – LinkedIn Hiring Trends in India

A data analytics capstone project on **LinkedIn job postings in India**, focused on understanding where jobs are, which sectors and work models dominate, and how competitive different roles are across locations, company sizes, and experience levels.

---

## 📌 Project Overview

This project uses a **7‑day snapshot (168 hours)** of LinkedIn India job postings and converts it into:

- A **cleaned, structured dataset** in Google Sheets  
- Pivot‑based analysis and charts  
- A final **interactive dashboard** titled “Job Market Trends & Hiring Insights”

The dashboard answers:

- Which **sectors** (IT Engineering, Data Analytics, Management, Sales & Mktg, HR, Other) are hiring the most?  
- How are jobs split across **On‑Site, Remote, and Hybrid** work types?  
- Which **states** and **company categories** are driving hiring?  
- How many **applications** do different sectors and levels attract?

---

## 📂 Repository Structure

```text
.
├─ raw_dataset/
│  ├─ linkdin_Job_data.csv
│  └─ SecD_Team08_JobMarketAnalytics-Raw_Data_(Frozen).csv
├─ cleaned_dataset/
│  ├─ SecD_Team08_JobMarketAnalytics-Final-Cleaned-Dataset.csv
│  └─ SecD_Team08_JobMarketAnalytics-Data-Dictionary.csv
├─ calculations_and_pivots/
│  └─ SecD_Team08_JobMarketAnalytics-Pivot-Tables-and-Calculations.csv
├─ dashboards/
│  ├─ dashboard-link.md
│  └─dashboard_image.png
├─ presentation/
│  └─ JobMarket_Analytics_Presentation.pptx 
├─ documentation/
│  └─ JobMarket_Analytics_Report.pdf
└─ README.md
```
---

## 🧠 Data Description

**Source:** LinkedIn Job Postings (public pages, India; original file hosted on Kaggle).
**Time window:** last **168 hours (7 days)** at the time of extraction.

- Raw data: 7,927 rows × 16 columns 
- Cleaned data: 5,074 unique job postings × 16 columns 

Main columns (see data dictionary for full list):

- `Job_ID`, `Job_Title`, `Job_Sector`
- `Job_Type`, `Job_Level`
- `Work_Type` (On‑Site, Remote, Hybrid)
- `Company_Size`, `company category` (Small, Medium, Big, Unknown)
- `City`, `State`, `Industry`
- `no_of_application`, `Posted_Hours_Ago`, `linkedin_followers`

Limitations: no salary data, skills are unstructured, and some values for `Job_Level` / `Industry` are `Unknown`. 

---

## 🧹 Data Cleaning Notes

All primary work was done in **Google Sheets**.

- Removed duplicate `Job_ID` records → 5,074 unique jobs.
- Dropped non‑informative columns (e.g., `company_id`).
- Cleaned numeric fields (`no_of_application`, `linkedin_followers`) by stripping text and commas.
- Split combined fields (`Full-time · Associate`) into `Job_Type` and `Job_Level`.
- Parsed location into `City` and `State`, and normalised posting age into `Posted_Hours_Ago` (hours).
- Engineered:
    - `Job_Sector` from `Job_Title` + `Industry`
    - `company category` from `Company_Size` (Small / Medium / Big / Unknown)
- Used `"Unknown"` instead of dropping rows with missing level/industry. 

---

## 📊 KPI Tiles (Dashboard)

The final dashboard uses **four** KPIs, calculated on the “Final Cleaned Dataset” sheet:

- **Total Jobs**
`=COUNTA('Final Cleaned Dataset'!A:A)` → **5,075**
- **Total Applications**
`=SUM('Final Cleaned Dataset'!M:M)` → **90,845**
- **Avg Applications per Job (Avg Apps)**
`=AVERAGE('Final Cleaned Dataset'!M:M)` → **18**
- **Remote Work_Type % (Remote %)**
`=ROUND(100 * (COUNTIF('Final Cleaned Dataset'!G:G,"Remote") / COUNTA('Final Cleaned Dataset'!A:A)))` → **35%**

These summarise overall **volume, interest, and flexibility** in the job market.

---

## 🖼 Dashboard Screenshots

<img src="dashboards/dashboard_image.png" width="100%" />


The dashboard views show:

- % of total jobs by **work type** (On‑Site, Remote, Hybrid).
- Work type split within each **Job_Sector**.
- An **opportunity map** by sector and job level.
- Job counts by **company category** (Small, Medium, Big).
- A **competition matrix** (applications vs followers).
- % of total jobs by **state**.

---

## 📜 Data Dictionary (Quick View)

Full dictionary:
`cleaned_dataset/Copy-of-SecD_Team08_JobMarketAnalytics-Data-Dictionary.csv`.

Key fields:


| Column | Description |
| :-- | :-- |
| `Job_ID` | Unique LinkedIn job identifier |
| `Job_Title` | Cleaned job title |
| `Job_Sector` | Sector bucket (IT Eng, Data, Mgmt, Sales \& Mktg, HR, Other) |
| `Job_Type` | Full‑time / Part‑time / Contract / Internship |
| `Job_Level` | Entry / Associate / Mid‑Senior / Director / Executive / Internship / Unknown |
| `Work_Type` | On‑Site / Remote / Hybrid |
| `company category` | Small / Medium / Big / Unknown |
| `State` | Indian state of the job |
| `no_of_application` | Number of LinkedIn applications |
| `linkedin_followers` | Company follower count |
| `Posted_Hours_Ago` | Time since posting (hours) |


---

## 💡 Key Insights

From the cleaned dataset and final analysis:

- IT Engineering and Data Analytics together contribute **≈55%** of all jobs, showing a **tech‑heavy market**.
- On‑Site roles are about **46%**, while **Remote (~35%) + Hybrid (~19%)** together slightly exceed On‑Site, so **flexible work is mainstream**.
- Mid‑Senior roles dominate (≈54%), and **Entry‑level roles are only ≈2%**, indicating a fresher gap.
- Jobs are concentrated in a few states such as **Karnataka, Maharashtra, Uttar Pradesh, Delhi, and Telangana**.
- **Small and Medium companies** post most jobs; however, the competition matrix shows **large brands** attract far more applications per posting.

---

## 🔍 Suggested Exploration

If you use this repo as a starting point, you can:

- Filter the dashboard by **Work_Type / Job_Sector / State** to explore specific segments.
- Analyse **applications per job** for different sectors and company categories.
- Extend the analysis in Python/R using the cleaned CSV (time‑series, modelling, etc.).

---

## 🚀 Getting Started

1. Clone the repository:
```bash
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

2. Open `cleaned_dataset/Copy-of-SecD_Team08_JobMarketAnalytics-Final-Cleaned-Dataset.csv` in **Google Sheets** or your preferred tool.
3. Explore `calculations_and_pivots/` to inspect pivot tables and formulas.
4. View the dashboard screenshots in `dashboards/` or open the live Google Sheets dashboard link if you add it.
5. For full narrative and methodology, read `documentation/JobMarket_Analytics_Report.pdf`.

---

## 🙌 Acknowledgements

- LinkedIn, for providing the underlying job postings.
- Faculty mentors **Archit Raj** and **Satyaki Das** for guidance on the DVA capstone.
- Teammates of **SecD_Group08** – Shreyash Golhani, Nishant Ranjan Singh, Aditya Bhardwaj, Krishna Gehlot, Kartikey Gupta, and Shivam Mishra – for sourcing, cleaning, analysis, dashboarding, and documentation.
