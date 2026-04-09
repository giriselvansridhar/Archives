## Historical Gold Price Analysis (22k vs 24k) — Python



Python, Data Analysis, Data Analytics, Exploratory Data Analysis (EDA), Time Series Analysis, Data Cleaning, Data Wrangling, pandas, NumPy, Matplotlib, Seaborn, Jupyter Notebook, Excel Analytics, Data Visualization, Trend Analysis, GroupBy Aggregation, Feature Engineering (Year/Month), Business Insights, Reporting

### Tech stack

- **Language**: Python
- **Tools**: Jupyter Notebook
- **Libraries**: pandas, numpy, matplotlib, seaborn, openpyxl
- **Data source**: Microsoft Excel (`.xlsx`)

### Project

This project is a simple, beginner-friendly analysis of gold prices over time.

- **Goal**: compare how **22k** and **24k** gold prices change across days, months, and years.
- **Where the work happens**: `7_GoldRateAnalysis.ipynb` (a Jupyter Notebook).
- **Dataset needed**: an Excel file named **`Gold rate.xlsx`** in the same folder.

**`Gold rate.xlsx` must have these columns:**

- **`date`**: the date for each record
- **`22k`**: 22k gold price
- **`24k`**: 24k gold price

The notebook also cleans the price columns (it removes commas and converts them into numbers).

### Innovative angle (what makes it stand out)

- **Interactive analysis**: you can enter a **year** or a **date range** to instantly generate focused trend charts.
- **Side-by-side comparison**: 22k vs 24k is always shown together, making it easy to compare premium/price gap.
- **Multi-level insights**: daily trend (line charts) + summarized insights (yearly/monthly averages).
- **Reusable structure**: you can swap in a different dataset by keeping the same column names.

### Output

When you run the notebook, you will see charts (plots) inside Jupyter:

- **Line chart (full timeline)**: 22k vs 24k trend across all dates in the file
- **Line chart (one year)**: 22k vs 24k trend for the year you enter
- **Line chart (custom date range)**: 22k vs 24k trend between the start and end date you enter
- **Bar chart (yearly averages)**: average 22k vs 24k price for each year
- **Bar chart (monthly averages)**: average 22k vs 24k price for each month in the year you enter

### Output understanding (very simple)

- **Line chart**:
  - X-axis = time (dates)
  - Y-axis = gold price
  - Two lines = two types of gold (**22k** and **24k**)
  - If the line goes up, price increased; if it goes down, price decreased

- **Bar chart**:
  - Each bar shows an **average** price (a “typical” value)
  - Yearly bars help you compare year-to-year
  - Monthly bars help you compare months within a year

### Output interpretation (what you can conclude)

From the charts you can quickly answer questions like:

- **Is gold getting more expensive over the years?**
- **How much higher is 24k compared to 22k (most of the time)?**
- **In a specific year, were there big jumps or drops?**
- **In a specific year, which months were cheaper or more expensive on average?**

Important note: these charts show **patterns in your dataset**. They do not predict future prices.



- Performed **time-series EDA** on historical gold prices (22k vs 24k) using **Python (pandas, NumPy)** and **Excel** inputs.
- Built **data cleaning** steps to standardize numeric columns (removed thousand separators and converted to `float`) for reliable analytics.
- Created **interactive visualizations** (Matplotlib/Seaborn) for full timeline, **year-based**, and **custom date-range** trend analysis.
- Generated **yearly and monthly aggregations** using `groupby` to compare average prices and highlight long-term patterns.
- Communicated insights through clear plots and layman-friendly interpretation to support quick decision-making.

### Learning (layman terms)

By doing this project, you learn:

- **How to open an Excel file in Python** (`pandas`)
- **How to clean data** (turn “text numbers” into real numbers)
- **How to look at trends over time** using charts
- **How to compute simple averages** by year and month
- **How to compare two categories** (22k vs 24k) in a clear visual way

### How to run (Windows / PowerShell)

From this project directory:

```bash
python -m venv .venv
.\.venv\Scripts\Activate.ps1
python -m pip install --upgrade pip
pip install pandas numpy matplotlib seaborn openpyxl jupyter
```

Start Jupyter:

```bash
jupyter notebook
```

Open `7_GoldRateAnalysis.ipynb` and run the cells from top to bottom.

### Inputs you will type in the notebook

Some cells ask for:

- **Year** (example: `2021`)
- **Start date** and **end date** (format: `YYYY-MM-DD`)

### Troubleshooting

- If the notebook cannot find the file, make sure **`Gold rate.xlsx`** is in the same folder as the notebook.
- If Excel reading fails, install `openpyxl` (it is included in the install command above).
- If you see a pandas `SettingWithCopyWarning`, it’s just a warning; the notebook usually still runs.

### Next improvements (optional, for innovation)

- Add an **export step** to save charts as PNG and save summary tables to CSV for reporting.
- Add a small **data validation** step (check missing dates, duplicates, negative prices).
- Add a **price gap analysis** column: \( \text{24k} - \text{22k} \) and visualize how the gap changes over time.
- Add a simple **inflation-adjusted view** if CPI data is available (real price vs nominal price).
