## Exploratory Data Analysis (EDA) Automation Tool (Django + Pandas)

**EDA Automation Tool** is a web-based GUI that automates common Exploratory Data Analysis (EDA) steps for tabular datasets. The app lets a user upload a dataset and interactively run EDA operations (shape, schema, head/tail, value counts, datatype conversion) inside a Django web interface.

This project is designed to demonstrate end-to-end skills across **Python**, **Django**, and **data analysis with Pandas/NumPy**—including UI integration, file handling, and presenting analysis output to end users.

---

## Project (What it does)

- **Upload dataset**: Upload a file from the homepage.
- **Run EDA via GUI**: Execute common EDA operations using dropdown tools and forms.
- **Session-based “observations”**: Save results per observation tab (useful for documenting analysis steps).
- **Present results**: Outputs are rendered back to the browser (tables/text) so a user can review insights quickly.

---

## Output (What you get)

From the operations page, the tool produces:

- **Dataset preview**: `Head(n)` and `Tail(n)` tables.
- **Dataset size**: `Shape` as (rows, columns).
- **Schema / column metadata**:
  - `Info` returns a table with **column name**, **non-null count**, and **dtype**.
  - `Datatypes` returns a table of **column → dtype**.
- **Categorical / discrete distribution**:
  - `Value Counts` for a selected column as a table of **value → count**.
- **Datatype conversion feedback**:
  - Converts a column dtype and returns a success/error message.

**UI output format**:
- Tables are rendered as HTML tables (Bootstrap-styled).
- Scalar outputs (e.g., shape) are shown as plain text.

---

## Output Interpretation (How to read the results)

- **Head / Tail**: Quickly validate whether the upload is correct, confirm column meanings, detect unexpected values (e.g., “NA”, “?”, 0, negative values).
- **Shape**: Helps scope the dataset and feasibility of downstream steps (e.g., large row counts, wide feature sets).
- **Info (non-null + dtype)**:
  - Non-null counts highlight missingness and potential data quality issues.
  - Dtypes highlight columns that may need conversion (e.g., numeric stored as strings).
- **Datatypes**: Helps identify categorical vs numeric columns and plan preprocessing steps.
- **Value counts**:
  - Shows class imbalance, outliers in categorical fields, or unexpected cardinality.
  - Useful for deciding encoding strategies, grouping rare categories, or cleaning.
- **Datatype conversion message**:
  - Confirms successful conversion or alerts that conversion introduced missing values (data quality risk).

---

## Learning Outcomes (What this project demonstrates)

- **Backend engineering**: Django project structure, routing, views, templates, sessions.
- **File handling**: Accepting user uploads, storing files on disk, basic metadata persistence.
- **Data analysis**: Pandas-based inspection utilities (info, dtypes, head/tail, value counts).
- **Data quality thinking**: Missingness detection, datatype correctness, validation via UI feedback.
- **UI integration**: Turning analysis outputs into readable HTML tables for non-technical users.

---

## Tech Stack (ATS keywords)

- **Language**: Python
- **Web framework**: Django
- **Data / EDA**: Pandas, NumPy
- **Visualization (planned/partial)**: Matplotlib, Seaborn
- **Frontend**: HTML, Bootstrap
- **Storage**: Local file storage, SQLite (default Django database)

---

## Application Routes (Current)

- **Homepage (upload)**: `/`
- **Operations page**: `/operations/`

---

## How to Run Locally (Windows / PowerShell)

From the Django project directory:

```bash
cd "D:\01_Projects\Archives\Exploratory Data Analysis Automation Tool\main\edatoll"
python -m pip install django numpy pandas matplotlib seaborn scikit-learn
python manage.py migrate
python manage.py runserver 8000
```

Then open:
- `http://127.0.0.1:8000/`

---

## Typical Workflow (Recruiter-friendly demo flow)

1. Start the server and open the homepage.
2. Upload a small CSV dataset (e.g., car prices, sales, HR, etc.).
3. Go to `/operations/` and run:
   - `Shape` to understand dataset size
   - `Info` and `Datatypes` to validate schema
   - `Value Counts` on a categorical column to inspect distribution
   - `Head` / `Tail` to validate raw records
4. Add an **Observation** name to document what you learned (session-based tabs).

---

## Notes / Known Gaps (Transparent engineering)

- Some UI menu items (replace values, encoding, heatmap, drop column, export) are present in the template but may not be fully wired in the backend yet.
- Upload/metadata paths are evolving (file is stored under an uploads folder and metadata is written to `main.json`).

---

## Next Improvements (If continuing development)

- Wire remaining operations (replace, one-hot encoding, null heatmap, drop column).
- Add support for XLSX/XLS (currently CSV read logic is used).
- Add export for a reproducible EDA notebook/report (HTML/PDF/Notebook).
- Add basic validations (file type checks, size limits) and production-ready settings.
