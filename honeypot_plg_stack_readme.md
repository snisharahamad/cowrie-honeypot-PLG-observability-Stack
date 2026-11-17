# Cowrie Honeypot & PLG Observability Stack

A production-ready SSH/Telnet honeypot architecture designed to capture automated attacks, collect telemetry, and visualize network activity.

This project integrates a decoupled observability stack (PLG) to parse, aggregate, and display authentication attempts and executed payloads without manual log inspection.

## 🏗️ Architecture & Stack

The environment is containerized using Docker Compose and segmented into four core services:

* **Cowrie:** A medium-to-high interaction SSH and Telnet honeypot designed to log authentication attempts and shell interactions.
* **Promtail:** A log collector configured to tail Cowrie's JSON logs, extract relevant labels, and forward them.
* **Loki:** A horizontally scalable log aggregation system that indexes the data streams sent by Promtail.
* **Grafana:** The visualization layer, connected to Loki, displaying metrics such as top attacker IPs and most used credentials.

## 🚀 Key Features

* **Real-time Threat Monitoring:** Logs are instantly processed and visualized.
* **Decoupled Architecture:** The logging layer (Loki/Promtail) is separated from the application layer (Cowrie).
* **Infrastructure as Code (IaC):** The Grafana dashboard is exported as a `dashboard.json` file, allowing redeployment without migrating local databases.

## 🛠️ Deployment

*Requirement: Docker and Docker Compose installed. Port 22 must be free on the host machine.*

**1. Clone the repository**
```bash
git clone https://github.com/snisharahamad/sentinel-honeypot.git
cd sentinel-honeypot
```

**2. Launch the Stack**
```bash
docker compose up -d
```

**3. Access the Dashboards**
Navigate to `http://<YOUR_SERVER_IP>:3000` to access Grafana and import the provided `dashboard.json` file.