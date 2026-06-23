# Job Application Tracker

Automatically reads your Gmail, uses AI (Gemini) to extract job application data, and saves everything to a color-coded Excel file.

## Features
- Reads all job-related emails from Gmail
- AI extracts company, role, stage, source, application method, and more
- Color-coded stages (Applied, Interview, Assessment, Offer, Rejected)
- AI-generated remarks + manual notes column
- Incremental runs — only processes new emails each time
- Two sheets: Job Applications + To Apply (recruiter suggestions)

## Setup

### 1. Gmail API
- Go to [console.cloud.google.com](https://console.cloud.google.com)
- Create a project → Enable Gmail API
- Create OAuth 2.0 credentials (Desktop app)
- Download as `credentials.json` and place in project folder

### 2. Gemini API Key
- Go to [aistudio.google.com](https://aistudio.google.com)
- Create a free API key

### 3. Install Dependencies
pip install google-auth google-auth-oauthlib google-api-python-client google-genai openpyxl

### 4. Configure
Open `job_tracker.py` and replace:
GEMINI_API_KEY = "your-gemini-api-key-here"

### 5. Run
python job_tracker.py

First run fetches all emails from the beginning.
Every run after only processes new emails.

## Output
Excel file saved as `job_tracker_STARTDATE_to_ENDDATE.xlsx` with:

| Column | Description |
|---|---|
| Company | Company name |
| Role | Job title |
| Stage | Applied / Phone Screen / Assessment / Interview / Offer / Rejected |
| Date | Email date |
| Found On | LinkedIn / Indeed / Glassdoor etc. |
| Applied Via | LinkedIn Easy Apply / Workday / Greenhouse etc. |
| Email Type | Confirmation / Rejection / Interview Invite etc. |
| Description | One-line summary |
| Next Steps | What to do next |
| AI Remarks | Smart observations from Gemini |
| My Notes | Your own manual notes |

## Note
Never commit `credentials.json`, `token.json`, or `scanned_ids.json` — these are personal and gitignored.
