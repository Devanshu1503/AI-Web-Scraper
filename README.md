# 🕊️ AI Web Scraper for Parish Data

A multi-stage pipeline built to support the Catholic Leadership Institute (CLI) in extracting and analyzing parish-related data from diocesan and parish websites across the United States. The project enables data-driven insights into parish operations, sacramental schedules, and engagement activity.

---

## 📌 Project Overview

This project automates the scraping of parish names, website URLs, sacramental schedules, and contact information using web scraping and AI tools. Cleaned and structured outputs are integrated into a Power BI dashboard for further analysis. The workflow consists of three core stages:

1. **Web scraping diocesan directories and parish websites**
2. **AI-based structured data extraction and cleaning**
3. **Visualization in a Power BI dashboard**

---

## 🧩 Project Components

### 🏛️ Diocesan and Parish Web Scraper

This scraper collects parish names and website URLs from diocesan directories using Playwright and BeautifulSoup. It supports multiple dioceses and handles dynamic content and pagination.

**Key Features:**
- Scrapes multiple diocesan directories
- Handles JavaScript-heavy pages
- Outputs: `parish_results.csv`

**Setup:**
```bash
pip install playwright beautifulsoup4
playwright install
```

**Usage:**
```bash
python parish_scraper.py
```

**Output:**
- `parish_results.csv` with columns: Parish Name, Website URL

---

### 🧠 AI-Based Scraping & Data Cleaning

The AI-enhanced pipeline processes scraped parish websites using ScrapeGraphAI and multiple scripts to produce structured data tables used for Power BI visualization.

**Steps:**

1. `parish_results.csv` → `parish_results_cleaner.py` → `cleaned_urls.csv`
2. `cleaned_urls.csv` → `ParishScraperGivenCSV.py` → `RawScrapedParishData.csv`
3. `RawScrapedParishData.csv` → `Combined_Cleaner.py` → `JSON-like_Final_File.csv` and `CouldNotScrape.csv`
4. `JSON-like_Final_File.csv` → `ConvertCsvTo6CsvTables.py` → Final structured tables

---

## 📊 Power BI Dashboard

The dashboard visualizes activity from the final cleaned tables, combining both VT-scraped data and CLI-provided scores.

**Input Tables:**
- ParishTable
- MassTimesTable
- ConfessionTable
- AdorationTable
- DaysAdoration, DaysConfession, DaysMass
- SacramentsByDay
- ActivityRankings
- CLI_Data
- Diocese Locations
- OverlappedParishes

**Dashboard Pages:**
1. VT Overview
2. VT Sacrament
3. VT Face Cards
4. CLI Overview
5. CLI/VT Scoring State
6. CLI/VT Face Cards
7. CLI/VT Scoring Comparison

**Notable Metrics:**
- Sacramental Importance (e.g. Mass: 3, Confession: 2, Adoration: 1)
- Combined and Normalized Activity Scores
- ParishUnique field to differentiate similarly named parishes

---

## ⚠️ Limitations and Considerations

- Sacramental weights may need refinement to reduce clustering in dashboard scores.
- Duplicate parishes may exist due to shared names and ZIP assumptions.
- Python scripts run within Power BI require enabling Python scripting and specific libraries (`pyzipcode`, `ZipCodeDatabase`).
- Power BI privacy settings may restrict sharing; consider using a dedicated workspace or publish-to-web option.

---

## 📫 Contact

**Devanshu Khadka**  
- [LinkedIn](https://linkedin.com/in/devanshukhadka)  
- 📧 khadkadevanshu@gmail.com

---

## 🔒 License

Internal use only. Please contact before reuse or distribution.

