# ⚽ Premier League ETL Pipeline

<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/en/f/f2/Premier_League_Logo.svg" alt="Premier League Logo" width="200">
</p>

<p align="center">
  <img src="./docs/etl_schema.svg" alt="ETL Pipeline" width="700">
</p>

<p align="center">
  <strong>Automated ETL pipeline extracting Premier League data from RapidAPI, transforming with Python, and loading to PostgreSQL for dashboard analytics</strong>
</p>

---

## 📊 Pipeline Architecture

```
RapidAPI (Football API) → Python/Jupyter (Transform) → PostgreSQL → Dashboard
```

**Extract**: Fetches Premier League data from RapidAPI Football API  
**Transform**: Cleans and processes data using Python in Jupyter Notebook  
**Load**: Stores structured data in PostgreSQL for visualization

---

## 🚀 Quick Start

### Prerequisites
- Python 3.8+
- PostgreSQL database
- RapidAPI account with Football API subscription

### Installation

```bash
# Clone repository
git clone https://github.com/idabella/python_sql_football_data_pipeline.git
cd python_sql_football_data_pipeline

# Create virtual environment
python -m venv venv
source venv/bin/activate  # Windows: venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Configuration

Create `.env` file with your credentials:

```env
# RapidAPI Configuration
RAPIDAPI_KEY=your_rapidapi_key
RAPIDAPI_HOST=api-football-v1.p.rapidapi.com

# PostgreSQL Configuration
DB_HOST=localhost
DB_PORT=5432
DB_NAME=premier_league
DB_USER=your_username
DB_PASSWORD=your_password
```

### Run Pipeline

```bash
jupyter notebook Premier_league_etl.ipynb
```

Execute cells sequentially to run the complete ETL process.

---

## 📁 Project Structure

```
├── Premier_league_etl.ipynb    # Main ETL notebook
├── requirements.txt             # Python dependencies
├── .env                         # Configuration (not tracked)
├── README.md
└── docs/
    └── etl_schema.svg          # Pipeline diagram
```

---

## 🔧 Technologies

- **RapidAPI Football API** - Data source
- **Python/Pandas** - Data transformation
- **Jupyter Notebook** - Development environment
- **PostgreSQL** - Data warehouse
- **SQLAlchemy** - Database connector

---

## 📊 Data Pipeline

### 1. Extract
Connects to RapidAPI Football API to fetch:
- Match results
- Player statistics
- Team standings
- Season data

### 2. Transform
Python transformations include:
- Data cleaning and validation
- Type conversions
- Null handling
- Data normalization
- Feature engineering

### 3. Load
Loads processed data to PostgreSQL tables:
- `matches` - Match results and details
- `players` - Player statistics
- `teams` - Team information
- `standings` - League standings

---

## 💡 Usage Example

```python
# Sample code from notebook
import pandas as pd
from sqlalchemy import create_engine
import requests

# Extract from RapidAPI
headers = {
    'x-rapidapi-key': os.getenv('RAPIDAPI_KEY'),
    'x-rapidapi-host': os.getenv('RAPIDAPI_HOST')
}
response = requests.get(api_url, headers=headers)
data = response.json()

# Transform
df = pd.DataFrame(data)
df_cleaned = transform_data(df)

# Load to PostgreSQL
engine = create_engine(f'postgresql://{user}:{password}@{host}:{port}/{db}')
df_cleaned.to_sql('matches', engine, if_exists='replace')
```

---

## 🤝 Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/Enhancement`)
3. Commit changes (`git commit -m 'Add Enhancement'`)
4. Push to branch (`git push origin feature/Enhancement`)
5. Open Pull Request

---

## 📄 License

This project is currently unlicensed.

---

## 🙏 Acknowledgments

- [RapidAPI Football API](https://rapidapi.com/api-sports/api/api-football) for comprehensive data
- Open-source Python community

---

<p align="center">Made with ⚽ and Python</p>
