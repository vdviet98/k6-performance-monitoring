# K6 Performance Monitoring Server

Performance testing monitoring stack using K6, InfluxDB, Grafana, and Loki.

## Tech Stack

- **InfluxDB 1.8**: Time-series database for metrics storage
- **Grafana**: Visualization dashboard
- **Loki**: Log aggregation system
- **Docker Compose**: Container orchestration

## Prerequisites

- Docker Desktop
- Git

## Setup

### 1. Clone repository
```bash
git clone <repo-url>
cd k6-performance-monitoring
```

### 2. Create `.env` file

Copy from template:
```bash
copy .env.example .env
```

Update passwords in `.env` file

### 3. Start services
```bash
docker compose up -d
```

### 4. Verify services
```bash
docker compose ps
```

### 5. Access Grafana

- URL: http://localhost:3000
- Username: `admin`
- Password: (check your `.env` file)

## Services

| Service   | Port | Purpose                    |
|-----------|------|----------------------------|
| InfluxDB  | 8086 | Metrics storage            |
| Grafana   | 3000 | Visualization dashboard    |
| Loki      | 3100 | Log aggregation            |

## Datasources

Datasources are automatically provisioned on Grafana startup:

- **InfluxDB**: Default datasource for K6 metrics
- **Loki**: Log storage for K6 console logs

## Folder Structure
```
k6-performance-monitoring/
├── docker-compose.yml           # Services definition
├── .env                         # Environment variables (not committed)
├── .env.example                 # Template
├── grafana/
│   ├── datasources/            # Auto-provision datasources
│   └── dashboards/             # Dashboard configs (coming soon)
└── influxdb/                   # InfluxDB data (auto-generated)
```

## Commands

### Start services
```bash
docker compose up -d
```

### Stop services
```bash
docker compose down
```

### View logs
```bash
docker compose logs -f
docker compose logs grafana
```

### Restart specific service
```bash
docker compose restart grafana
```

## Troubleshooting

### Check container status
```bash
docker compose ps
docker ps
```

### View container logs
```bash
docker compose logs <service-name>
```

### Remove all data and restart fresh
```bash
docker compose down -v
docker compose up -d
```