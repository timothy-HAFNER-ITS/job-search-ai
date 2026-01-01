# 🚀 Universal Job Scraper v2.1 - Quick Start Guide
## ⚡ 30-Second Start (NEW - Fully Automated!)
```bash# 1. Extract the zipunzip universal_job_scraper_v2.zip
# 2. Install dependencies (if not already installed)pip3 install -r requirements.txt
# 3. Run EVERYTHING with ONE command! ⭐ NEWpython3 run_job_scraper.py```
**What happens automatically:**1. ✅ You enter job URLs when prompted2. ✅ Scraper extracts all job data 3. ✅ **API server starts AUTOMATICALLY** 🎉4. ✅ Jobs immediately available at localhost:5000/json
**That's it!** One command does everything!
---




## 📋 Prerequisites
Before running the scraper, make sure you have:
### ✅ Python 3.7 or Higher```bashpython3 --version# Should show: Python 3.7 or higher```
### ✅ Required Packages (Install Once)
The `requirements.txt` file includes all dependencies:
```requests>=2.31.0 # HTTP client for web scrapingbeautifulsoup4>=4.12.0 # HTML parsing librarylxml>=4.9.0 # Fast XML/HTML parserselenium>=4.15.0 # Optional - for JavaScript-heavy sitesflask>=3.0.0 # API server frameworkflask-cors>=4.0.0 # CORS support for n8n integration```
**Install all at once:**```bashpip3 install -r requirements.txt```
**Or install individually:**```bashpip3 install requests beautifulsoup4 lxml selenium flask flask-cors```
### 🔧 Optional: Selenium WebDriver
**Only needed if scraping JavaScript-heavy sites** (Randstad, Indeed, StepStone work without it!)
**macOS:**```bashbrew install geckodriver # For Firefoxbrew install chromedriver # For Chrome```
**Linux:**```bashsudo apt install firefox-geckodriver```
**Windows:**Download from https://github.com/mozilla/geckodriver/releases
---


## ✅ Verify Installation
Test that everything is ready:
```bashpython3 -c "import requestsfrom bs4 import BeautifulSoupimport lxmlfrom flask import Flaskfrom flask_cors import CORSprint('✅ All packages installed correctly!')print('✅ Ready to scrape jobs!')"```
---

## 🌐 Start API Server
```bashpython3 universal_api_server.py```
**Access your data:**- 📊 JSON: localhost:5000/json- 📡 RSS: localhost:5000/rss.xml- 📈 Status: localhost:5000/status
---

## 🎯 What Makes This Universal?
### ✅ Works with Multiple Sites
**Supported (Tested):**- Randstad.de- Indeed.de / Indeed.com- StepStone.de
**Should Work (Generic Adapter):**- LinkedIn Jobs- Monster.de- Xing Jobs- Most job boards
### 🧠 Intelligent Extraction
The scraper **automatically adapts** to different website layouts:
```python# Extracts salary from ANY of these formats:€50,000 - €60,00050.000 - 60.000 €€50k per annum$50,000 - $60,000£50,000 - £60,000```
No code changes needed!
### 🏢 Hiring Company Information ⭐ NEW
Now extracts the **actual hiring company** (not the job board):
```json{ "company": "Tech Solutions GmbH", // ← Actual employer "company_address": "Hauptstraße 123", "company_city": "Munich", "company_postal_code": "80331"}```
### 📍 Advanced Filtering
```bash# Berlin jobs onlycurl "localhost:5000/json?location=Berlin"
# High-salary jobs (€60k+)curl "localhost:5000/json?min_salary=60000"
# Full-time onlycurl "localhost:5000/json?type=full-time"
# Randstad jobs onlycurl "localhost:5000/jobs/randstad.de"
# Combine filterscurl "localhost:5000/json?location=Munich&min_salary=70000&type=full-time"```
---

## 💡 Example Workflows
### 1️⃣ Daily Job Alerts (n8n)
```javascript// n8n HTTP Request NodeGET localhost:5000/json?min_salary=60000
// Filter new jobs→ Compare with database→ Send email for new matches→ Save to database```
### 2️⃣ Multi-Site Comparison
```bash# Scrape 3 sites with one commandpython3 run_job_scraper.py# Enter: Randstad, Indeed, StepStone URLs
# Compare resultscurl localhost:5000/sources
# Output:{ "sources": [ {"name": "randstad.de", "count": 9}, {"name": "indeed.de", "count": 15}, {"name": "stepstone.de", "count": 25} ]}```
### 3️⃣ Salary Analysis
```bash# Get all jobscurl localhost:5000/json > jobs.json
# Analyze with jqcat jobs.json | jq '.jobs[] | select(.salary) | {title, company, salary, source}'```
---

## 🔄 Manual Process (If Preferred)
### Step 1: Scrape Jobs
```bashpython3 universal_job_scraper.py```
Enter your URLs when prompted.
### Step 2: Start API Server
```bashpython3 universal_api_server.py```
---

## 🎉 You're Ready!
The **Universal Job Scraper v2.1** now features:- ✅ **One-command workflow** (automated)- ✅ **Multi-site support** (Randstad, Indeed, StepStone, +more)- ✅ **Intelligent extraction** (adapts to different layouts)- ✅ **Hiring company info** (actual employer, not job board)- ✅ **Company address** (street, city, postal code)- ✅ **Advanced filtering** (location, salary, type, source)- ✅ **16 fields per job** (comprehensive data)
**Happy multi-site job hunting!** 🚀
---
**Version**: 2.1.0 **Last Updated**: November 24, 2025 **Package Size**: 41KB **New Feature**: Automated workflow with `run_job_scraper.py`
