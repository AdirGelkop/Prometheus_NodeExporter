# Prometheus Monitoring Setup

A basic monitoring infrastructure using Prometheus and Node Exporter running with Docker Compose.

## Architecture

┌─────────────────┐           ┌─────────────────┐
│                 │  scrapes  │                 │
│   Prometheus    │◄──────────┤  Node Exporter  │
│    Server       │   metrics │    (9100)       │
│    (9090)       │           │                 │
└────────┬────────┘           └────────┬────────┘
         │                             │
         │                             │
         │                             │
         │                             │
         ▼                             ▼
┌─────────────────────────┐    ┌────────────────────┐
│                         │    │                    │
│    Prometheus UI        │    │    Host System     │
│  (Query & Visualize)    │    │   (CPU/Mem/Disk)   │
│                         │    │                    │
└─────────────────────────┘    └────────────────────┘

- **Prometheus Server**: Central database that collects and stores metrics
- **Node Exporter**: Collects system metrics (CPU, memory, disk, network)

The components work together:
- Node Exporter exposes metrics on port 9100
- Prometheus scrapes these metrics every 15s
- Metrics can be queried and visualized in Prometheus UI

## Project Files

- **prometheus.yml**: Configuration defining what metrics to collect
- **docker-compose.yml**: Container setup for both components

## Getting Started

```bash
# Start the services
docker compose up -d

# Access Prometheus UI
# http://localhost:9090

# View Node Exporter metrics
# http://localhost:9100/metrics
```

## Useful Queries

- **up** - Check if targets are working
- **node_cpu_seconds_total** - CPU usage
- **node_memory_MemFree_bytes** - Free memory
- **node_disk_io_time_seconds_total** - Disk I/O
