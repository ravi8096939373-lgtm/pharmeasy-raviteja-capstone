# PharmEasy Regional Pulse — Analytics & AI Capstone

## What this project implements
A reproducible regional-sales data-quality pipeline based on the capstone instructions captured in the session. It covers data generation, cleaning, SQL validation, MoM flagging, CII narrative reporting, review-gate/audit logging, and a Streamlit + Plotly dashboard.

## Acceptance criteria
- **2,159 raw rows**
- **59 exact duplicate rows**
- **2,100 clean unique orders**
- **16 raw region variants**
- **10 master regions**
- **9 active regions**
- **Kurnool = 0 orders**
- **48 missing categories filled**
- **94 missing profits filled**
- **Guntur April sales = ₹100,000**
- **Guntur May sales = ₹222,190**
- **Guntur Apr→May = +122.19%**
- **8% absolute MoM monitoring threshold**
- LEFT JOIN / INNER JOIN / COUNT(order_id) / duplicate-key checks
- Overview + Category + Detail dashboard with Region filter

## Repository structure
```text
data/        raw export + master region file
scripts/     dataset generator, cleaning, pipeline
outputs/     clean data, SQLite DB, metrics, memo, audit and review files
sql/         verification queries
app/         Streamlit dashboard
README.md
requirements.txt
```

## Exactly three run commands
```bash
python scripts/generate_dataset.py
python scripts/run_pipeline.py
streamlit run app/app.py
```

## Cleaning methodology
1. Remove exact duplicates.
2. Standardize region values against the master list, including known aliases.
3. Fill missing category from product-to-category mapping.
4. Fill missing profit using observed mean profit margin by category.
5. Validate schema, master-region membership and unique order IDs.

## Important interpretation
The 8% threshold is an **alert/monitoring rule**, not a statistical significance test. A flagged region should be investigated rather than automatically assigned a cause.

## Submission checklist
- Make the GitHub repository **Public**.
- Commit all files and confirm they are visible without login.
- Run all three commands successfully.
- Open the Streamlit dashboard.
- Verify the SQL checks and Guntur +122.19% result.
- Review the memo/dashboard personally before submitting.
- Do not include API keys, paid services or signup-gated dependencies.
- Do not submit another student's repository or copy work you cannot explain.




Raw Dataset
     ↓
Schema Validation
     ↓
Duplicate Detection
     ↓
Region Normalization
     ↓
Missing Value Handling
     ↓
Data Quality Validation
     ↓
SQL Validation
     ↓
Regional Analysis
     ↓
Significance Flagging
     ↓
Dashboard
     ↓
Stakeholder Insights


PIPELINE


Raw rows: 2,159
Duplicate rows: 59
Clean rows: 2,100
Master regions: 10
Active regions: 9
Kurnool orders: 0





scripts/generate_dataset.py
scripts/run_pipeline.py
app/app.py









pandas
numpy
matplotlib
plotly
streamlit
openpyxl
