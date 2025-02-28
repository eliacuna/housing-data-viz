# Housing & Homelessness Data Visualization Platform

A comprehensive data visualization platform that explores the relationship between housing availability, affordability, luxury housing inventory, and homelessness across the United States.

## Project Overview

This application visualizes the complex relationships between housing market factors and homelessness rates across US counties and states. It uses data from multiple federal sources including HUD, BLS, and private sources like Zillow to analyze trends and correlations.

Key features:
- Interactive US map visualization with state and county-level data
- Correlation analysis between luxury housing, affordable housing, and homelessness
- 5-year trend analysis (2020-2025)
- Live data updates via scheduled API calls

## Architecture

![Architecture Diagram](./images/architecture-diagram.png)

The application consists of three main components:
1. **React Frontend**: Interactive data visualization interface
2. **Python Flask Backend**: API endpoints and data processing
3. **PostgreSQL Database**: Structured data storage and analytics

## Data Sources

- **Housing and Urban Development (HUD)**: Affordable housing inventory, homelessness counts, and shelter capacity
- **Zillow Research Data**: Housing prices, rental costs, housing inventory, and luxury market metrics
- **Bureau of Labor Statistics (BLS)**: Income data, unemployment rates, labor force participation

## Technologies Used

### Frontend
- React (with hooks, context)
- react-simple-maps for geographic visualizations
- recharts for data charting
- shadcn/ui components for UI elements
- Tailwind CSS for styling

### Backend
- Python 3.9+
- Flask for API endpoints
- Pandas for data processing and analysis
- psycopg2 for PostgreSQL connectivity
- APScheduler for automated data updates

### Database
- PostgreSQL 13+
- PostGIS extension for geographic data

## Getting Started

### Prerequisites
- Node.js 16+
- Python 3.9+
- PostgreSQL 13+
- Docker and Docker Compose (optional)

### Installation

#### Using Docker (recommended)
```bash
# Clone the repository
git clone https://github.com/yourusername/housing-viz-platform.git
cd housing-viz-platform

# Build and start the containers
docker-compose up -d
```

#### Manual Installation

1. Set up the database:
```bash
psql -U postgres -f database/setup.sql
```

2. Install backend dependencies:
```bash
cd backend
python -m venv venv
source venv/bin/activate  # On Windows: venv\Scripts\activate
pip install -r requirements.txt
```

3. Install frontend dependencies:
```bash
cd frontend
npm install
```

4. Start the backend server:
```bash
cd backend
python app.py
```

5. Start the frontend development server:
```bash
cd frontend
npm start
```

### Environment Variables

Create a `.env` file with the following variables:

```
# Database
DB_HOST=localhost
DB_NAME=housing_data
DB_USER=postgres
DB_PASSWORD=your_password
DB_PORT=5432

# APIs
HUD_API_KEY=your_hud_api_key
ZILLOW_API_KEY=your_zillow_api_key
BLS_API_KEY=your_bls_api_key

# Flask
FLASK_APP=app.py
FLASK_ENV=development
```

## Project Structure

```
housing-viz-platform/
├── frontend/             # React application
│   ├── public/           # Static files
│   └── src/              # React source code
│       ├── components/   # UI components
│       ├── hooks/        # Custom React hooks
│       ├── pages/        # Page components
│       └── api/          # API client
├── backend/              # Python Flask API
│   ├── app.py            # Main application
│   └── data_processing.py  # Data processing scripts
├── database/             # Database setup
│   └── setup.sql         # Schema creation script
└── docs/                 # Documentation
    └── images/           # Diagrams and screenshots
```

## Data Flow

1. **Data Collection**: Scheduled jobs fetch data from HUD, Zillow, and BLS APIs
2. **Data Processing**: Python scripts process, normalize, and calculate derived metrics
3. **Storage**: Processed data is stored in PostgreSQL with appropriate indexing
4. **API**: Flask endpoints provide data to the frontend
5. **Visualization**: React components visualize the data with interactive maps and charts

## Research Focus

This visualization aims to explore:
- The correlation between luxury housing development and homelessness rates
- The impact of affordable housing availability on homelessness
- Regional variations in housing affordability
- The relationship between shelter capacity and homelessness management
- Trends in housing affordability over time (2020-2025)

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- HUD for providing open data on housing and homelessness
- Zillow Research for housing market data
- Bureau of Labor Statistics for income and employment data
