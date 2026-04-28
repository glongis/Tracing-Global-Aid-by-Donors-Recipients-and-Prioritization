# Tracing-Global-Aid-Donors-Recipients-Prioritization
Analyzes OECD aid data with Python notebooks for cleaning, sector classification, and Tableau preparation, plus an interactive dashboard mapping donor-to-recipient aid flows by year, sector, and funding amount. (Submission for SP-26 Data Case Competition)

## Tools Used

- Python
- pandas
- NumPy
- scikit-learn
- TF-IDF vectorization
- Jupyter Notebook
- Tableau
- OECD DAC sector classification documentation

## Methodology

The dataset was first cleaned in Python using pandas. Sector codes were standardized, missing values were inspected, and rows with multiple sector codes were split so each project-sector relationship could be represented clearly. When a project had multiple sector codes, its disbursement amount was divided across the split rows to avoid overcounting.

After cleaning, detailed OECD sector codes were mapped into broader aid categories such as education, health, energy, environment and agriculture, humanitarian and disaster aid, and economic development. These broader categories made the analysis more readable and useful for dashboard filtering.

For projects that were missing a broad sector, project descriptions were used to infer likely categories. I used TF-IDF with scikit-learn to identify important words and phrases associated with each known category, then used those words in a rule-based classifier to assign categories to unmarked projects when possible. Finally, the cleaned and categorized data was prepared for Tableau by adding donor and recipient geographic information and grouping aid flows by donor country, recipient country, year, and sector.

## Dashboard

The Tableau dashboard visualizes aid flows from donor countries to recipient countries. Each flow line represents money moving between a donor and recipient country, with line thickness based on total disbursement amount. The dashboard includes filters for year, donor country, and broad sector, allowing users to explore how aid priorities differ across time, geography, and type of assistance. Counties receiving funding are labeled. (The initial loading of the dashboard displays aid from the United States and Belgium in the categories of aid / debt and infrastructure over the years of 2020-20230)

## Repository Contents

- `cleaning_and_classifying.ipynb` — Cleans the OECD dataset, standardizes sector codes, groups sectors, and classifies uncategorized projects.
- `tableau_data_preparation.ipynb` — Prepares the final cleaned data for Tableau, including donor-recipient flow fields.
- `oecd_cleaned.csv` — Cleaned project-level aid dataset.
- `tableau_data.csv` — Tableau-ready dataset used to build the flow map.
- `Donor-to-Recipient Aid Flow Map.twb` — Tableau workbook containing the interactive dashboard.
- `README.md` — Project documentation and methodology.
