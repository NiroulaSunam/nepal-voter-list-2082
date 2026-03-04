# 🗳️ Nepal Voter List Scraper — Changunarayan Ward 2, Dubakot, Bhaktapur

A simple Python script that scrapes the official Nepal Election Commission voter list for a particular center and saves it as both CSV and Excel files.

---

## 📍 Target Location

| Field | Value |
|---|---|
| Pradesh | Bagmati (बागमती) |
| Jilla | Bhaktapur (भक्तपुर) |
| Na. Pa. | Changunarayan Municipality (चाँगुनारायण नगरपालिका) |
| Ward No. | 2 |
| Polling Center | २ नं. नयाँ वडा कार्यालय भवन, दुवाकोट |
| Total Voters | ~3,889 entries | 

---

## ✨ What It Does

- Sends a direct HTTP POST request to the Election Commission website
- Parses the full voter list table (no browser needed)
- Saves output as:
  - `voter_list.csv` - CSV File
  - `voter_list.xlsx` - Excel File

### Columns scraped:
1. सि.नं. (Serial No.)
2. मतदाता नं (Voter ID)
3. मतदाताको नाम (Voter Name)
4. उमेर (Age)
5. लिङ्ग (Gender)
6. पति/पत्नीको नाम (Spouse Name)
7. पिता/माताको नाम (Father/Mother Name)

---

## Setup

**Requirements:** Python 3.9+

```bash
# Clone or download the project
cd nepal-voter-list-2082

# Create a virtual environment
python3 -m venv .venv
source .venv/bin/activate

# Install dependencies
pip install requests beautifulsoup4 openpyxl urllib3
```

---

## Run

```bash
python3 voter_scraper.py
```

Output files `voter_list.csv` and `voter_list.xlsx` will be saved in the same folder.

---

## How It Works

The Nepal Election Commission website at [voterlist.election.gov.np](https://voterlist.election.gov.np/view_ward.php) uses a standard HTML form. Instead of opening a browser and clicking through dropdowns, this script:

1. Sends the form values directly via HTTP POST
2. Parses the returned HTML table using BeautifulSoup
3. Extracts all voter records in one request (the server returns all rows at once)
4. Saves to CSV and formatted Excel

---

## Notes

- This script uses `verify=False` to bypass SSL issues with LibreSSL on macOS. This is safe for this use case as the data is publicly available.
- The voter data is publicly available on the official Election Commission of Nepal website.
- This is intended for personal/research use only.

---

## Dependencies

| Package | Purpose |
|---|---|
| `requests` | HTTP requests to the election website |
| `beautifulsoup4` | Parse HTML and extract table data |
| `openpyxl` | Generate formatted Excel output |
| `urllib3` | SSL warning suppression |

---

## Built With

Built as a side quest with the help of AI (Claude by Anthropic). The goal was simple — find names on the voter list for my own area without clicking through hundreds of pages manually.

---

*Data source: [Election Commission of Nepal](https://voterlist.election.gov.np)*