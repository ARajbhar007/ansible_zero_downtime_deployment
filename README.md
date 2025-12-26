# Zero-Downtime Deployment with Git, Ansible, Nginx, Prometheus & Grafana

## 🚀 Project Overview
This project demonstrates an automated **Git-driven zero-downtime deployment pipeline** for a simple web application using **Ansible**, **Nginx**, and **Linux servers on AWS EC2**.  
The deployment process ensures **continuous availability** while updating application code, following real-world DevOps best practices.

Monitoring and observability are implemented using **Prometheus** and **Grafana** to track server health, application availability, and system metrics in real time.

---

## 🧩 Architecture

- **Control Node**
  - Hosts Ansible
  - Hosts a **bare Git repository**
  - Triggers deployments using Git hooks

- **Application Servers (2)**
  - Ubuntu EC2 instances
  - Serve the web application
  - Updated sequentially to avoid downtime

- **Load Balancer**
  - Nginx reverse proxy
  - Performs health checks
  - Routes traffic only to healthy app servers

- **Monitoring Server**
  - Prometheus for metrics collection
  - Grafana for dashboards and visualization

---

## 🛠️ Tech Stack

- **Cloud**: AWS EC2 (Ubuntu)
- **Configuration Management**: Ansible
- **Web Server / Load Balancer**: Nginx
- **Version Control**: Git (bare repository + hooks)
- **Monitoring**: Prometheus, Grafana
- **OS**: Linux

---

## ⚙️ Key Features

- ✅ Zero-downtime deployments
- ✅ Git-based automated deployments
- ✅ Nginx load balancing with health checks
- ✅ Ansible-driven server configuration
- ✅ Real-time monitoring with Prometheus & Grafana
- ✅ Production-style architecture

---

## 🔄 Deployment Workflow

1. Developer pushes code to the **bare Git repository**
2. A **post-receive Git hook** triggers deployment
3. Ansible deploys the app to **one server at a time**
4. Nginx temporarily removes the updating server from rotation
5. Application is updated and restarted gracefully
6. Server is added back to the load balancer
7. Traffic continues without interruption

---

## 📊 Monitoring & Observability

- **Node Exporter** installed on all servers
- Prometheus scrapes metrics from:
  - App servers
  - Load balancer
- Grafana dashboards display:
  - CPU & memory usage
  - Server availability
  - Request load & uptime

---

## 🧪 Proof of Zero Downtime

- Continuous application availability during deployments
- No failed requests observed during updates
- Verified via:
  - Browser access
  - Nginx access logs
  - Prometheus metrics

---

## 📁 Project Structure

```text
.
├── ansible/
│   ├── inventory
│   ├── playbooks/
│   └── roles/
├── nginx/
│   └── load-balancer.conf
├── monitoring/
│   ├── prometheus.yml
│   └── grafana/
├── app/
│   └── index.html
└── README.md
