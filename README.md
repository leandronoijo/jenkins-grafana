# Jenkins Monitoring Stack

## Overview
This project sets up a monitoring stack using Grafana, Jenkins, and InfluxDB within Docker containers. It is designed for development and testing purposes, providing an environment to monitor Jenkins for scheduled tasks and cron jobs, with Grafana for log visualization and InfluxDB as the backend database. It is essential to customize and secure this stack further before deploying it in a production environment.

## Features
- **Jenkins:** Automates tasks and cron jobs, with a user-friendly dashboard for log management.
- **Grafana:** Visualizes logs and metrics in a powerful, elegant interface.
- **InfluxDB:** A time-series database for efficient logging data storage.

## Prerequisites
- Docker and Docker Compose installed on your system.
- Basic understanding of Docker, Jenkins, Grafana, and InfluxDB.

## Installation & Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/leandronoijo/jenkins-grafana.git
   cd jenkins-grafana
   ```

2. **Environment Variables:**
   Create a `.env` file in the project root with `INFLUXDB_PASS` and `INFLUXDB_USER`.

3. **Docker Compose:**
   ```bash
   docker-compose up -d
   ```

4. **Accessing Services:**
   - **Jenkins:** `http://localhost:8080`
   - **Grafana:** `http://localhost:3000`
   - **InfluxDB:** Backend service with no direct UI.

## Configuration
- **Jenkins:** Managed via `jenkins.yaml` in the `jenkins` directory. [Documentation](https://plugins.jenkins.io/configuration-as-code/)
- **Grafana:** Configured in `./grafana/provisioning`. [Documentation](https://grafana.com/docs/grafana/latest/administration/provisioning/)

## Usage
Create and monitor Jenkins jobs, visualized through the Grafana dashboard.
The Connections between Jenkins -> InfluxDB -> Grafana Source is already made.
You can find in Grafana a Dashboard under General -> Jobs Status to get started.

## Contributing
Contributions are welcome. Please adhere to standard open-source guidelines.

## License  
This project is open source under the [MIT License](https://opensource.org/licenses/MIT).