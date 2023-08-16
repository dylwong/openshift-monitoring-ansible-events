# Prometheus Monitoring with Podman Compose
This repository contains a Podman Compose configuration file that sets up a Prometheus monitoring stack along with Filebeat for log collection. The stack consists of Prometheus, Alertmanager, Grafana, and Filebeat.

# Filebeat is configured to collect and forward logs from Podman containers to Prometheus.

A custom Ansible rulebook is also included in this stack. It's configured to pull a rulebook and custom source plugin from the Ansible Galaxy. The source plugin can handle Prometheus queries and run them at an interval to fetch metric data. In the default setup, this rulebook monitors specific metrics and triggers events accordingly. The focus of this setup is to demonstrate the power of Ansible automation for event-driven monitoring.

Please note that this configuration is intended for demonstration and testing purposes. It is not suitable for production environments.

# Prerequisites
Before you begin, make sure you have the following installed:

- Podman
- Podman Compose
- Ansible
# Getting Started
Clone this repository to your local machine.

Navigate to the repository directory:

```cd prometheus-podman-compose```
Start the Prometheus stack and Filebeat using Podman Compose:

```podman-compose up -d```
Access Prometheus UI by opening your web browser and visiting http://localhost:9090.

Access Grafana UI by opening your web browser and visiting http://localhost:3000. The default credentials are admin/admin.

Explore the dashboards in Grafana to visualize and monitor your Prometheus metrics.

<!> Monitor the Ansible rulebook's activity and events by running: <!>

```ansible-playbook ansible-rulebook/main.yml```
This will execute the Ansible playbook, triggering monitoring events and responses.

# Customization
You can modify the Prometheus configuration in prometheus/config/prometheus.yml to add or change monitoring targets and scraping intervals.

Adjust the Filebeat configuration in filebeat/config/filebeat.yml to collect and forward logs from specific Podman containers.

Customize the Ansible rulebook in the ansible-rulebook directory to define different monitoring and alerting scenarios using Ansible automation.

# Cleanup
When you're done experimenting, you can stop and remove the containers:

```podman-compose down```
[!] Disclaimer [!]
This setup is intended for testing and learning purposes. It is not recommended for production usage without appropriate modifications and security considerations.

``Feel free to replace prometheus-podman-compose with the appropriate directory name if you're using a different directory structure. Additionally, adapt any URLs or paths as needed based on your setup. The emphasized focus in this version is on Ansible events and their role in the monitoring process.``
