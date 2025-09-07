# Job Postings Web Scraper

A Python-based tool designed to automate the search for tech jobs across Lever and Greenhouse job boards. This scraper fetches job postings using Google Search, filters them by role and time period, and exports the results into a timestamped Excel file for easy tracking.

## ✨ Features

* 🔍 Search Lever and Greenhouse job boards via Google queries.
* 🎯 Filter jobs by role: `sde`, `aiml`, `cv`, `nlp`, `robo`, or `all` and by recency: `hour`, `day`, `week`, `month`, `year`.
* 📝 Retrieve detailed information: company name, job title, location, and job description.
* 📊 Export results into Excel with separate sheets:

  * Relevant jobs
  * Potentially relevant jobs
  * Rejected jobs
* 🗂️ Automatically remove duplicates and sort alphabetically by company.
* ⏱️ Timestamped Excel filenames for tracking search history.

## ⚙️ Prerequisites

* Python 3.8+
* Dependencies listed in `requirements.txt`
* Docker (optional)

## 🚀 How to Run

### Clone the Repository

```bash
git clone https://github.com/jeaneude/job-scraper.git
cd job-scraper
```

### Approach 1: Run Locally

```bash
pip install -r requirements.txt
python jobScraper.py
```

### Approach 2: Run with Docker

1. Ensure Docker is installed.
2. Build the image:

```bash
docker build -t job-scraper-container .
```

3. Run the container (mount a local data folder to save results):

```bash
docker run -it -v "C:/Users/jeane/Documents/scrappling/job-scraper/data:/data" job-scraper-container
```

## 🖥️ Usage

When running `python jobScraper.py`, the script will prompt for:

* **Number of results** → max (all results) or a specific integer.
* **Time period** → `h` (hour), `d` (day), `w` (week), `m` (month), or `y` (year).
* **Roles** → `sde`, `aiml`, `cv`, `nlp`, `robo`, or `all`.

The script will then:

* Fetch and display the number of results.
* Remove duplicates.
* Categorize jobs into Relevant, Maybe Relevant, and Rejected.
* Save results to an Excel file in `data/jobListings-<timePeriod>-<HH-MM, DD-MM-YYYY>.xlsx`.

## 📂 Code Overview

* `keywordsDict` → maps role abbreviations to keyword lists.
* `selectRoles()` → picks keywords for chosen roles.
* `doGoogleSearch()` → performs Google queries and returns job links.
* `cleanURL()` → standardizes job URLs.
* `getJobInfo()` → scrapes job details.
* `inUSA()` → filters jobs by U.S. location.
* `isRelevantRole()` → checks job title relevance.
* `saveToExcel()` → writes results into Excel with multiple sheets.

## 👤 Author

Jean\_eude Gbada

## 📜 License

This project is licensed under the MIT License – see the `LICENSE.md` file for details.

## 🙌 Acknowledgments

* Inspired by open-source job scrapers.
* Thanks to Lever and Greenhouse for consistent job posting structures.
