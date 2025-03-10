## MQTT Climate Monitor

This application collects temperature and humidity data from an MQTT broker, saves it in an SQLite database, and visualizes the data with live updates and 5-minute averages.

## Features
- 🌡️ Continuous monitoring of temperature and humidity
- 📊 Interactive charts displaying 5-minute averages
- 💾 Data storage using SQLite for historical records
- 📱 Responsive layout designed for desktop and mobile use

## Setup Instructions

### Requirements
- Node.js (v14 or later)
- npm (v6 or later)

### Installation Steps
1. Clone the repository:
```bash
git clone https://github.com/yourusername/mqtt-weather-app
cd mqtt-weather-app
```
2. Install dependencies:
```bash
npm install
```
3. Create a `public` folder and add the `index.html` file inside:
```bash
mkdir -p public
cp index.html public/
```
4. Start the server:
```bash
npm start
```
5. Open your browser and navigate to `http://localhost:3000`

## Directory Overview
```
mqtt-weather-app/
├── public/
│   └── index.html     # Frontend UI with Chart.js for visualization
├── server.js          # Express backend for API endpoints and SQLite logic
├── package.json       # Node.js dependencies
├── weather_data.db    # SQLite database (auto-generated)
└── README.md          # Setup instructions
```

## How It Functions
1. The frontend connects to the MQTT broker and shows live temperature and humidity data.
2. Each incoming MQTT message is sent to the backend and recorded in the SQLite database.
3. The backend calculates 5-minute averages and stores them in a separate table.
4. The chart visualizes one hour of historical data (12 five-minute segments).

## API Endpoints
- `POST /api/weather/data` - Save temperature and humidity data from MQTT
- `GET /api/weather/history` - Fetch historical data for chart visualization

## Database Schema
### Raw Data Table
This table stores individual readings from the MQTT broker:
```sql
CREATE TABLE raw_data (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    type TEXT NOT NULL,         -- 'temperature' or 'humidity'
    value REAL NOT NULL,        -- The measured value
    timestamp TEXT NOT NULL     -- ISO-formatted timestamp
);
```

### Average Data Table
This table stores 5-minute average calculations:
```sql
CREATE TABLE avg_data (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    avg_temperature REAL,       -- 5-minute average temperature
    avg_humidity REAL,          -- 5-minute average humidity
    timestamp TEXT NOT NULL     -- ISO-formatted timestamp
);
```


4. Start the server:
   ```bash
   npm start
   ```

5. Access the application:
   Open your browser and navigate to `http://localhost:3000`

## Project Structure

```
mqtt-weather-app/
├── public/
│   └── index.html       # Frontend interface with Chart.js visualization
├── server.js            # Express backend with API endpoints and SQLite logic
├── package.json         # Node.js dependencies
├── weather_data.db      # SQLite database (created automatically)
└── README.md            # Setup instructions
```

## How It Works

1. The frontend connects to the MQTT broker and displays real-time temperature and humidity values
2. Each MQTT message is sent to the backend and stored in the SQLite database
3. Every 5 minutes, the backend calculates averages and stores them in a separate table
4. The chart displays up to one hour of historical data (twelve 5-minute intervals)

## API Endpoints

- `POST /api/weather/data` - Store raw temperature and humidity readings
- `GET /api/weather/history` - Retrieve historical data for charting

## Database Schema

### Raw Data Table
Stores every reading received from MQTT:
```sql
CREATE TABLE raw_data (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  type TEXT NOT NULL,        -- 'temperature' or 'humidity'
  value REAL NOT NULL,       -- The actual reading
  timestamp TEXT NOT NULL    -- ISO format timestamp
);
```

### Average Data Table
Stores 5-minute averages:
```sql
CREATE TABLE avg_data (
  id INTEGER PRIMARY KEY AUTOINCREMENT,
  avg_temperature REAL,      -- 5-minute average temperature
  avg_humidity REAL,         -- 5-minute average humidity
  timestamp TEXT NOT NULL    -- ISO format timestamp
);
```#   m q t t - w e a t h e r - a p p 
 
 
