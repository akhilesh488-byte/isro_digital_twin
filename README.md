# ISRO Digital Twin

A comprehensive digital twin simulation platform for Indian Space Research Organisation (ISRO) satellite systems and space infrastructure.

## 🚀 Overview

This project creates a virtual replica of ISRO's satellite systems and space assets, enabling real-time monitoring, simulation, analysis, and predictive maintenance through advanced digital twin technology.

## 📋 Table of Contents

- [Features](#features)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [Quick Start](#quick-start)
- [Project Structure](#project-structure)
- [Usage](#usage)
- [Configuration](#configuration)
- [API Documentation](#api-documentation)
- [Architecture](#architecture)
- [Contributing](#contributing)
- [License](#license)
- [Support](#support)

## ✨ Features

- **Real-time Monitoring**: Track satellite systems and space infrastructure status in real-time
- **Simulation Engine**: Advanced physics-based simulation for orbital mechanics and system behavior
- **Predictive Analytics**: Machine learning models for anomaly detection and predictive maintenance
- **Data Visualization**: Interactive dashboards for system visualization and analysis
- **Historical Analysis**: Store and analyze historical data for trend identification
- **Multi-Satellite Support**: Monitor and simulate multiple satellites simultaneously
- **Alert System**: Real-time alerts for critical events and anomalies
- **Export Capabilities**: Export simulation results and reports in multiple formats

## 📦 Prerequisites

- Python 3.8+
- Node.js 14+ (if using web interface)
- PostgreSQL 12+ (optional, for data persistence)
- Docker & Docker Compose (optional, for containerized deployment)

## 🔧 Installation

### Local Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/akhilesh488-byte/isro_digital_twin.git
   cd isro_digital_twin
   ```

2. **Create a virtual environment**
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

4. **Install frontend dependencies (if applicable)**
   ```bash
   npm install
   ```

5. **Configure environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your configuration
   ```

### Docker Installation

```bash
docker-compose up -d
```

## 🚀 Quick Start

1. **Start the application**
   ```bash
   python main.py
   ```

2. **Access the web interface**
   ```
   http://localhost:8000
   ```

3. **Create your first satellite simulation**
   ```python
   from isro_digital_twin import SatelliteSimulator
   
   simulator = SatelliteSimulator()
   satellite = simulator.create_satellite(name="ISRO-SAT-001")
   results = simulator.run_simulation(duration=86400)  # 24 hours
   ```

## 📁 Project Structure

```
isro_digital_twin/
├── src/
│   ├── core/              # Core simulation engine
│   ├── models/            # Data models and schemas
│   ├── api/               # REST API endpoints
│   ├── utils/             # Utility functions
│   └── analytics/         # Analytics and ML modules
├── web/                   # Frontend (if applicable)
│   ├── src/
│   └── public/
├── tests/                 # Test suite
├── docs/                  # Documentation
├── config/                # Configuration files
├── requirements.txt       # Python dependencies
├── package.json          # Node.js dependencies (if applicable)
├── docker-compose.yml    # Docker configuration
├── .env.example          # Environment variables template
└── README.md            # This file
```

## 💻 Usage

### Basic Satellite Simulation

```python
from isro_digital_twin import SatelliteSimulator, Satellite

# Initialize simulator
sim = SatelliteSimulator()

# Create satellite with orbital parameters
satellite = Satellite(
    name="ISRO-SAT-001",
    orbital_altitude=800,  # km
    inclination=98.5,       # degrees
    eccentricity=0.001
)

# Add to simulator and run
sim.add_satellite(satellite)
results = sim.run_simulation(duration=86400)

# Access results
print(results.get_position_data())
print(results.get_system_health())
```

### REST API Usage

```bash
# Start simulation
curl -X POST http://localhost:8000/api/simulations \
  -H "Content-Type: application/json" \
  -d '{
    "satellite_id": "ISRO-SAT-001",
    "duration": 86400
  }'

# Get simulation results
curl http://localhost:8000/api/simulations/{simulation_id}/results

# Get real-time satellite status
curl http://localhost:8000/api/satellites/ISRO-SAT-001/status
```

## ⚙️ Configuration

Create a `.env` file in the project root:

```env
# API Configuration
API_HOST=localhost
API_PORT=8000
API_DEBUG=False

# Database Configuration
DB_TYPE=postgresql
DB_HOST=localhost
DB_PORT=5432
DB_NAME=isro_digital_twin
DB_USER=admin
DB_PASSWORD=your_password

# Simulation Settings
SIMULATION_TIMESTEP=10  # seconds
SIMULATION_MAX_DURATION=604800  # seconds (7 days)

# Logging
LOG_LEVEL=INFO
LOG_FILE=logs/isro_digital_twin.log
```

## 📚 API Documentation

For detailed API documentation, visit:
```
http://localhost:8000/docs
```

Key endpoints:
- `POST /api/simulations` - Create new simulation
- `GET /api/simulations/{id}` - Get simulation details
- `GET /api/simulations/{id}/results` - Get simulation results
- `GET /api/satellites` - List all satellites
- `GET /api/satellites/{id}` - Get satellite details
- `POST /api/alerts` - Create alerts
- `GET /api/health` - System health check

## 🏗️ Architecture

The system is built on a modular architecture:

```
┌─────────────────────────────────────┐
│      User Interface / API            │
├─────────────────────────────────────┤
│    Simulation Engine & Analytics    │
├─────────────────────────────────────┤
│      Data Models & Processing       │
├─────────────────────────────────────┤
│  Database / File Storage / Cache    │
└─────────────────────────────────────┘
```

## 🧪 Testing

Run the test suite:

```bash
# Run all tests
pytest

# Run with coverage
pytest --cov=src

# Run specific test file
pytest tests/test_satellite_simulator.py
```

## 🤝 Contributing

Contributions are welcome! Please follow these steps:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

Please ensure:
- Code follows PEP 8 standards
- Tests are included for new features
- Documentation is updated

---

**Last Updated**: June 2026
**Status**: Active Development
