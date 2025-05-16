# Prometheus Monitoring Setup

A basic monitoring infrastructure using Prometheus and Node Exporter running with Docker Compose.

## Architecture
```mermaid
graph TD
    A[Host System] --> B[Node Exporter\n:9100]
    B -- exposes metrics --> C[Prometheus Server\n:9090]
    C --> D[Prometheus UI\nQuery & Visualize]
    
    style A fill:#f9f9f9,stroke:#333,stroke-width:2px
    style B fill:#dff0d8,stroke:#4cae4c,stroke-width:2px
    style C fill:#d9edf7,stroke:#31708f,stroke-width:2px
    style D fill:#fcf8e3,stroke:#8a6d3b,stroke-width:2px
```

- **Host System** : The underlying system being monitored
- **Node Exporter** : Collects system metrics (CPU, memory, disk, network)
- **Prometheus Server** : Scrapes and stores metrics from Node Exporter
- **Prometheus UI** : Web interface for querying and visualizing the collected metrics


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
