# EIA-860 and EIA-923 Power Plant Data Visualizations

This repository contains a collection of Python scripts designed to process and visualize the **US Energy Information Administration (EIA) Forms 860 and 923**. The analysis focuses on the lifecycle of the US power grid: from historical retirements and current performance to future stranded asset risks.

---

## 📂 Script Directory

### 1. Retirement & Historical Analysis
**Files:** `Plot2.py`, `Retired_or_cancelledgenerators.py`, `heatmap.py`
Focuses on how the US fleet is aging out and where capacity is being lost.
* **Retirement Trends:** Total nameplate capacity retired annually by technology.
* **Age Metrics:** Historical average retirement age (capacity-weighted) and actual vs. projected retirement dates.
* **Spatial Data:** Heatmaps showing retired capacity by county and state.
* **Flow Analysis:** Sankey diagrams illustrating the transition of capacity from active to retired status.

### 2. Fleet Vintage & Performance
**Files:** `gencolumn.py`, `generation.py`, `Firstyearoperating`
Analyzes the "Class of" each year to see how technology dominance has shifted over time.
* **Vintage Generation:** Annual electricity generation (MWh) categorized by the plant's first year of operation.
* **Operating Profile:** Total nameplate capacity currently in service, grouped by start year.
* **Dominance Trends:** Visualizes why Solar and Wind dominate the "Newer Vintage" bars while Coal/Nuclear dominate "Older Vintages."

### 3. Lifespan & Fleet Health
**Files:** `7plots.py`
A deep dive into the physical age of the current infrastructure.
* **Lifespan Benchmarking:** Capacity-weighted operating lifespan vs. historical averages.
* **Over-Age Assets:** Identification of plants operating past their expected "retirement age."
* **Net Changes:** Comparison of proposed additions versus historical retirements.

### 4. Policy Risk & Projections
**Files:** `Strandedassets.py`
Quantifies the impact of clean energy transitions.
* **Stranded Assets:** Measures capacity forced into early retirement if a 2035 decarbonization cutoff is enforced.
* **Projected Retirements:** Future-casting based on historical weighted-average lifespans.

---

## 📊 Data Mapping Reference (EIA-860)

To run these scripts, ensure your local Excel document (from the `Generator` zip) contains the following tabs:

| Data Tab | Primary Use Case |
| :--- | :--- |
| **Operating** | Current fleet capacity, location, and operating years. |
| **Proposed** | Planned additions and expected startup dates. |
| **Retired** | Historical retirement ages and fuel types. |

---

## 🛠 Setup & Requirements

### File Path Configuration
If your Python scripts are in a main folder and the Excel files are in a subfolder, use the following logic in your code:
```python
from pathlib import Path
import pandas as pd

# Dynamic pathing for Mac/Windows
data_folder = Path(__file__).parent / "your_subfolder_name"
df = pd.read_excel(data_folder / "EIA860_File.xlsx", sheet_name='Operating')
