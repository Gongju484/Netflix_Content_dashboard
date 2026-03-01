# Netflix_Content_dashboard

# 🎬 Netflix Content Dashboard — Power BI Mini Project 3

> A one-page interactive Netflix content dashboard built using Power BI as part of my Data Analytics training at Global Quest Technologies.


## 📁 Dataset Overview

| Column | Description |
|---|---|
| show_id | Unique ID for each title |
| type | Movie or TV Show |
| title | Name of the content |
| director | Director name |
| cast | Main cast |
| country | Country of production |
| date_added | Date added to Netflix |
| release_year | Year of original release |
| rating | Content rating (PG, R, TV-MA etc.) |
| duration | Duration in minutes or seasons |
| listed_in | Genre/Category |
| description | Short description |

**Key Facts:**
- 🎬 8,809 total titles
- 🎥 Movies + TV Shows
- 🗓️ Release years: 1925 – 2024
- 🌍 Top countries: USA, India, UK, Japan, South Korea

---

## 🛠️ Tools & Technologies

- **Power BI Desktop** — Dashboard creation and visualization
- **Power Query** — Data cleaning and transformation
- **DAX** — Custom measures and calculations
- **CSV** — Source data format

---

## 🔧 Power Query Steps Applied

- Removed 14 unnecessary unnamed columns (Unnamed: 12 to Unnamed: 25)
- Changed date_added column to Date data type
- Changed release_year to Whole Number data type
- Replaced null values in director column with "Unknown"
- Replaced null values in country column with "Unknown"
- Added custom column: Year_Added = Date.Year([date_added])
- Added custom column: Month_Added = Date.MonthName([date_added])
- Added custom column: Duration_Number (extracted numeric value from duration)
- Added custom column: Is_Movie (1 for Movie, 0 for TV Show)

---

## 📐 DAX Measures Created

Total Titles = COUNTROWS(netflix_titles)

Total Movies = CALCULATE([Total Titles], netflix_titles[type] = "Movie")

Total TV Shows = CALCULATE([Total Titles], netflix_titles[type] = "TV Show")

Movie % = DIVIDE([Total Movies], [Total Titles])

TV Show % = DIVIDE([Total TV Shows], [Total Titles])

Avg Release Year = AVERAGE(netflix_titles[release_year])

Titles Added This Year =
CALCULATE([Total Titles], netflix_titles[Year_Added] = YEAR(TODAY()))

Most Common Rating =
CALCULATE(
    FIRSTNONBLANK(netflix_titles[rating], 1),
    TOPN(1, VALUES(netflix_titles[rating]), [Total Titles])
)

---

## 📈 Dashboard Visuals

| Visual | Type | Fields Used |
|---|---|---|
| Total Titles | KPI Card | Total Titles |
| Total Movies | KPI Card | Total Movies |
| Total TV Shows | KPI Card | Total TV Shows |
| Movie % | KPI Card | Movie % |
| TV Show % | KPI Card | TV Show % |
| Content Added by Year | Area Chart | Year_Added × Total Titles (by type) |
| Movies vs TV Shows | Donut Chart | type × Total Titles |
| Top 10 Countries | Bar Chart | country × Total Titles + Top N Filter |
| Top 10 Genres | Bar Chart | listed_in × Total Titles + Top N Filter |
| Type Slicer | Slicer | type |
| Rating Slicer | Slicer | rating |

---

## 🔍 Key Findings

- 📌 8,809 total titles across Movies and TV Shows
- 📌 Movies dominate the platform at ~69% of all content
- 📌 United States leads with 2,819 titles, followed by India (972)
- 📌 Dramas and Documentaries are the most common genres
- 📌 Content additions peaked between 2018–2020
- 📌 TV-MA is the most common content rating

---

## 🎨 Dashboard Theme

Netflix-inspired dark theme:
- Background: #141414 (Netflix Black)
- Card background: #1F1F1F (Dark Grey)
- Accent color: #E50914 (Netflix Red)
- Text: #FFFFFF (White)

---


This is Mini Project 3 of my Data Analytics training.
Mini Project 1 — Amazon Best Sellers Dataset (2009–2019)
Mini Project 2 — Baskin Robbins Sales Dataset (50,000 transactions)
Mini Project 3 — Netflix Content Dataset (8,809 titles)
