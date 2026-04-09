## Historical Gold Price Analysis (22k vs 24k) — Python

Analyze and visualize historical gold prices (22k and 24k) using Python, pandas, seaborn, and matplotlib. The notebook focuses on time-series trends, date-range filtering, and yearly/monthly average comparisons.

### What this project does

- **Loads** historical gold-rate data from an Excel file.
- **Cleans** numeric columns (removes commas and converts to `float`).
- **Visualizes** price trends:
  - Full-range trend (22k vs 24k) over the entire dataset
  - Trend for a **specific year** (user input)
  - Trend for a **custom date range** (user input)
- **Aggregates** average prices:
  - **Yearly** average comparison (22k vs 24k)
  - **Monthly** average comparison for an input year

### Dataset requirements

The notebook expects an Excel file named **`Gold rate.xlsx`** in the same folder as the notebook.

- **File**: `Gold rate.xlsx`
- **Required columns**:
  - **`date`**: date/time values parseable by pandas
  - **`22k`**: numeric (or numeric-as-text; commas are handled)
  - **`24k`**: numeric (or numeric-as-text; commas are handled)

If your file name or column names differ, update the corresponding variables in the notebook (`date_column`, `gold_22k_column`, `gold_24k_column`).

### Project structure

- `7_GoldRateAnalysis.ipynb` — main analysis notebook
- `README.md` — project documentation
- `Gold rate.xlsx` — dataset file (place it locally; not included here)

### Requirements

- **Python**: 3.9+ recommended
- **Packages**:
  - `pandas`
  - `numpy`
  - `matplotlib`
  - `seaborn`
  - `openpyxl` (for reading `.xlsx` via `pd.read_excel`)
  - `jupyter` (to run the notebook)

### Setup (Windows / PowerShell)

From this project directory:

```bash
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

### Run

```bash
jupyter notebook
```

Open `7_GoldRateAnalysis.ipynb` and run cells top-to-bottom.

### Interactive inputs in the notebook

Some cells prompt for:

- **Year** to analyze (e.g., `2021`)
- **Start date** and **end date** for a custom range (expects `YYYY-MM-DD`)

### Outputs

The notebook produces plots directly in the notebook:

- Line plots comparing **22k vs 24k** over time (full range / year / date range)
- Bar plots comparing **average** gold costs (yearly and monthly)

### Notes / troubleshooting

- If you see `SettingWithCopyWarning` from pandas, it’s a warning about chained assignment. The notebook will typically still run; you can avoid the warning by using `.copy()` when filtering before adding columns.
- If `pd.read_excel("Gold rate.xlsx")` fails, make sure:
  - the file exists in the same folder as the notebook
  - `openpyxl` is installed
