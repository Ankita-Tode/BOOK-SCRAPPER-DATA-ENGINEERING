# **B2B Book Data Pipeline**
Deployment link:https://book-scrapper-data-engineering.onrender.com/
# **🌟 Problem Statement**
Many businesses need up-to-date product data for analysis, pricing comparisons, or inventory tracking.  
This project demonstrates a **B2B-style data pipeline** that:

- Scrapes product data from an online bookstore  
- Cleans and standardizes the data  
- Stores it in a database  
- Exposes the data via an API for easy consumption  

**Source:** Books to Scrape (demo scraping site)

🏗️ Project Architecture
The system is designed as a modular ETL (Extract, Transform, Load) pipeline, serving data through a modern API.

🕵️ Scraper (scraper.py)

Responsible for navigating target websites and extracting raw book data.

Outputs: raw_books.csv.

🧹 Data Cleaning (clean_data.py)

Handles data validation, removing duplicates, and formatting prices/ratings.

Outputs: cleaned_books.csv.

🗄️ Database (database.py)

Manages the SQLite connection and schema.

Handles the "Load" phase, persisting cleaned data into books.db.

🚀 API (fastapi.py)

A RESTful interface built with FastAPI to serve the stored book data to external users or front-end applications.


## Project Structure

```text
bookscrapper/
├── book_pipeline/
│   ├── venv/                   # Virtual environment
│   ├── books.db                # SQLite database
│   ├── check_db.py             # Script to verify database entries
│   ├── clean_data.py           # Data cleaning logic
│   ├── cleaned_books.csv       # Processed data output
│   ├── database.py             # Database connection/schema setup
│   ├── main.py                 # Main entry point
│   ├── pipeline.py             # Orchestrates the ETL process
│   ├── raw_books.csv           # Raw scraped data
│   ├── requirements.txt        # Project dependencies
│   ├── runtime.txt             # Python runtime specification
│   └── scraper.py              # Web scraping logic
└── External Libraries/         # Python 3.12 interpreter files
```

# **🛠 Tech Stack**

- **Scraping:** Python, Requests, BeautifulSoup  
- **Data Cleaning:** Pandas, NumPy  
- **Database:** Sqlite 
- **API:** FastAPI
- **Automation:** Cron Jobs  
- **Deployment:** Local machine,  Replit  

# **⚡ Setup Instructions**

1. **Clone the repository**
```bash
git clone <your-repo-url>
cd project

2. Create a virtual environment

python3 -m venv venv
source venv/bin/activate  # Linux / Mac
venv\Scripts\activate     # Windows

3.Install dependencies

pip install -r requirements.txt


4.Environment Variables (optional but recommended)
Create a .env file in the root:

DB_HOST=localhost
DB_USER=root
DB_PASSWORD=
DB_NAME=clean_book
 
6 Run the pipeline manually
python pipeline/pipeline.py

🚀 API Usage

Start the FastAPI server:
uvicorn api.fastapi:app --reload

Access the data:
GET http://127.0.0.1:8000/



✅ Notes / Best Practices
Handle missing or inconsistent data carefully

Wrap API responses in JSON with column names for clarity
Keep credentials in .env rather than hardcoding
