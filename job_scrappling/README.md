Job Postings Web Scraper

A Python-based tool I built to help me automate the search for tech jobs across Lever and Greenhouse job boards. The scraper fetches job postings using Google Search, filters them by role and time period, and exports them into a timestamped Excel file for easy tracking.

✨ Features

🔍 Search Lever and Greenhouse job boards via Google queries.

🎯 Filter jobs by role (sde, aiml, cv, nlp, robo, or all) and by recency (hour, day, week, month, year).

📝 Retrieve detailed info: company name, job title, location, and job description.

📊 Export results into Excel with separate sheets:

Relevant jobs

Potentially relevant jobs

Rejected jobs

🗂️ Automatically remove duplicates and sort alphabetically by company.

⏱️ Timestamped Excel filenames for tracking search history.

⚙️ Prerequisites

Python 3.8+

Dependencies listed in requirements.txt

OR Docker (optional)

🚀 How to Run

Clone the repo:

git clone https://github.com/jeaneude/job-scraper.git
cd job-scraper

Approach 1: Run Locally

Install dependencies:

pip install -r requirements.txt


Run the script:

python jobScraper.py

Approach 2: Run with Docker

Make sure Docker is installed.

Build the image:

docker build -t job-scraper-container .


Run the container (mounting a local data folder to save results):

docker run -it -v "C:/Users/jeane/Documents/scrappling/job-scraper/data:/data" job-scraper-container

🖥️ Usage

When running python jobScraper.py, the script will ask you for:

Number of results → max (all results) or an integer.

Time period → h (hour), d (day), w (week), m (month), or y (year).

Roles → sde, aiml, cv, nlp, robo, or all.

The script will then:

Fetch and display the number of results.

Remove duplicates.

Categorize jobs into Relevant, Maybe Relevant, and Rejected.

Save everything to an Excel file in:

data/jobListings-<timePeriod>-<HH-MM, DD-MM-YYYY>.xlsx

📂 Code Overview

keywordsDict → maps role abbreviations to keyword lists.

selectRoles() → picks the right keywords for your chosen roles.

doGoogleSearch() → performs Google queries and returns job links.

cleanURL() → standardizes job URLs.

getJobInfo() → scrapes job details.

inUSA() → filters jobs by U.S. location.

isRelevantRole() → checks job title relevance.

saveToExcel() → writes results into Excel with multiple sheets.

👤 Author

Jean_eude Gbada

📜 License

This project is licensed under the MIT License – see the LICENSE.md
 file for details.

🙌 Acknowledgments

Inspiration from open-source job scrapers.

Thanks to Lever and Greenhouse for consistent job posting structures.
