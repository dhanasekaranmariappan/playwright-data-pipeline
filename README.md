# 🤖 Playwright Data Pipeline — Automated Web Data Collection & Processing

> End-to-end automated data collection system: scrape → validate → clean → store → report.

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=flat&logo=python&logoColor=white)
![Playwright](https://img.shields.io/badge/Playwright-2EAD33?style=flat&logo=playwright&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=flat&logo=javascript&logoColor=black)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=flat&logo=pandas)
![MySQL](https://img.shields.io/badge/MySQL-00000F?style=flat&logo=mysql&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-green?style=flat)

---

## 🧠 What This Project Does

This pipeline automates the full lifecycle of web-sourced data: from browser-based collection to structured, analytics-ready output. It replaces manual copy-paste workflows with a reliable, scheduled, error-handled automation system.

**Pipeline stages:**
1. **Collect** — Playwright browser automation extracts structured data from target web sources
2. **Validate** — Schema checks, type enforcement, and completeness validation on raw data
3. **Clean** — Pandas-based deduplication, normalisation, and null handling
4. **Store** — Structured output to MySQL database or CSV
5. **Report** — Auto-generated summary report with Plotly visualisations

---

## 🗂 Project Structure

```
playwright-data-pipeline/
├── collector/
│   ├── scraper.py          # Playwright page interaction logic
│   ├── scheduler.py        # Cron-style job scheduling
│   └── config.py           # Target URLs and selectors (configurable)
├── processor/
│   ├── validator.py        # Schema and completeness checks
│   ├── cleaner.py          # Pandas cleaning pipeline
│   └── transformer.py      # Type casting, normalisation, enrichment
├── storage/
│   ├── db.py               # MySQL connection and insert logic
│   └── exporter.py         # CSV / JSON export utilities
├── reporter/
│   └── report.py           # Plotly summary visualisations
├── tests/
│   └── test_pipeline.py    # Unit tests for each stage
├── main.py                 # Run the full pipeline
├── requirements.txt
└── README.md
```

---

## ⚡ Quick Start

```bash
git clone https://github.com/dhanasekaranmariappan/playwright-data-pipeline.git
cd playwright-data-pipeline
pip install -r requirements.txt
playwright install chromium
```

```python
# Run the full pipeline
python main.py

# Or run individual stages
from collector.scraper import collect
from processor.cleaner import clean
from storage.db import save

raw = collect(url="https://example.com/data-table")
clean_df = clean(raw)
save(clean_df, table="collected_data")
```

---

## 🔁 Pipeline Flow

```
[Target Website]
      │
      ▼
[Playwright Scraper] ──► Raw Data (JSON/Dict)
      │
      ▼
[Validator] ──► Flag missing/malformed records
      │
      ▼
[Pandas Cleaner] ──► Deduplicated, typed, normalised DataFrame
      │
      ├──► [MySQL Storage] ──► Queryable database table
      │
      └──► [Plotly Reporter] ──► HTML summary dashboard
```

---

## ✅ Features

- **Headless browser automation** — handles JavaScript-rendered pages
- **Retry logic** — automatically retries failed page loads with exponential backoff
- **Scheduling** — configurable run intervals (hourly, daily, custom cron)
- **Validation layer** — catches bad data before it enters your database
- **Modular stages** — run any stage independently or chain them all
- **Configurable selectors** — swap target sites without rewriting core logic

---

## 🛠 Tech Stack

| Tool | Purpose |
|------|---------|
| Playwright (Python) | Browser automation & data extraction |
| JavaScript | Page interaction scripts where needed |
| Pandas | Data cleaning and transformation |
| MySQL | Structured data storage |
| Plotly | Output visualisation and reporting |
| Schedule | Lightweight job scheduling |

---

## 🔗 Related Projects

- [eda-toolkit](../eda-toolkit) — EDA library used to analyse datasets collected by this pipeline
- [ml-learning-lab](../ml-learning-lab) — ML experiments using this pipeline's outputs as training data

---

## 👤 Author

**Dhanasekaran Mariappan** — Python Data Engineer | Learning ML Engineering  
📧 dhanasekaranmariappan2202@gmail.com | [LinkedIn](https://www.linkedin.com/in/dhanasekaran-mariappan-22feb2000/) | Open to EU relocation
