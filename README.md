# Hi there, I'm Dzamal Barambajev 👋
### Systems Integration & DevOps Engineer in Training | Based in Germany 🇩🇪

Automating, securing, and orchestrating advanced self-hosted production systems. Focused on secure routing, self-hosted infrastructure, observability and resilient cloud services.
- 🚀 **Current Learning Focus:** Deep diving into **Kubernetes (K8s)** and Cloud-Native architectures to scale containerized environments.


![Kubernetes](https://img.shields.io/badge/Kubernetes-k3s-blue?logo=kubernetes)
![Docker](https://img.shields.io/badge/Docker-Containers-blue?logo=docker)
![Grafana](https://img.shields.io/badge/Grafana-Monitoring-orange?logo=grafana)
![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-orange?logo=prometheus)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-black?logo=linux)
![Nginx](https://img.shields.io/badge/Nginx-Reverse_Proxy-green?logo=nginx)
![Ansible](https://img.shields.io/badge/Ansible-Automation-CC0000?logo=ansible)
---

## 🛠️ My Production Cloud Server Architecture

I design and maintain a resilient cloud ecosystem on an Ubuntu VPS, prioritizing traffic security, fallback routing, automation, and stateful observation.

```text
                                 [ Public Internet ]
                                          │
                                       Port 443
                                          │
                                          ▼
                         [ Xray Core (VLESS + REALITY) ]
                                          │
                  ┌───────────────────────┴───────────────────────┐
                  │ (Valid VPN Auth)                              │ (Non-VPN Web Traffic)
                  ▼                                               ▼
         [ Obfuscated VPN Tunnel ]                   [ Xray Fallback Routing ]
         (Low-Latency Gateway)                                    │
                                                            Internal: 8443
                                                                  │
                                                                  ▼
                                                   [ Internal Nginx Web Server ]
                                                                  │
                                         ┌────────────────────────┴────────────────────────┐
                                         ▼                                                 ▼
                                  [ Production Site ]                               [ Family Web App ]
                                   (HTML Frontend)                                   (PHP Backed Stack)

 ┌─────────────────────────────────────────────────────────────────────────────────────────────────────────┐
 │                                       Containerized Infrastructure                                      │
 ├───────────────────────────────────────┬─────────────────────────────────────────────────────────────────┤
 │          [ Main System Disk ]         │                     [ 100GB Block Storage ]                     │
 │                 (/)                   │                         (/mnt/storage)                          │
 ├───────────────────────────────────────┼─────────────────────────────────────────────────────────────────┤
 │         [ Uptime Kuma Container ]     │           [ Prometheus ]             ──────>      [ Grafana ]   │
 │         (Real-time Status/Alerts)     │         (30-day Retained TSDB)             (Dashboards/Metrics) │
 └───────────────────────────────────────┴─────────────────────────────────────────────────────────────────┘
                                                            │
                                                     (Automated Cron)
                                                            │
                                                            ▼
                                               [ Daily Encrypted TG Backups ]
```

---

## 🚀 Key Infrastructure Achievements

### 🔒 Stealth Networking & Traffic Obfuscation
* **Advanced Xray Ingress Mesh:** Deployed an edge routing core utilizing **Xray (VLESS-Reality)** on port 443. Configured stealth handshakes that mimic legitimate web destinations, providing bulletproof traffic obfuscation.
* **Smart Fallback Routing:** Engineered custom **Fallback pathways** inside the Xray core. Unauthenticated generic web traffic hitting port 443 is seamlessly routed downstream to an internal port (`8443`), concealing the existence of the VPN gateway.
* **Internal Reverse Proxying:** Configured an internal **Nginx isolation layer** on port 8443 to safely multiplex and host multi-tenant platforms (Production landing pages and PHP family applications) behind the Xray perimeter.
* **Automated SSL Management:** Created automated Certbot event lifecycle triggers (`pre_hook` / `post_hook`) to coordinate short-term Nginx releases, preserving a zero-downtime certificate renewal matrix.

### 📊 Observability & Storage Isolation (GitOps Native)
* **High-Capacity Storage Extension:** Partitioned, formatted, and mounted a dedicated **100 GB external Block Storage disk (`/dev/vdb1` -> `/mnt/storage`)** to prevent stateful observability logs from exhausting system storage.
* **Containerized Telemetry Stack:** Automated the deployment of a synchronized monitoring engine using **Docker Compose**, bundling **Prometheus and Grafana** directly onto the isolated Block Storage array.
* **Data Retention Tuning:** Enforced custom retention windows (`--storage.tsdb.retention.time=30d`) within Prometheus TSDB via Docker Bind Mounts to streamline data durability.
* **Real-time Status Alerting:** Running a containerized **Uptime Kuma** monitoring cell on the primary root node to track site health thresholds and handle sub-second downtime telemetry.

### ⚙️ Systems Engineering & IaC Automation
* **Multi-Node GitOps (Ansible):** Authored an environment-aware Infrastructure as Code (IaC) configuration repo. Implemented an adaptive `hosts` matrix to handle independent SSH keys (`id_ed25519_wsl`) and Python compilation routes based on the origin workstation (Debian Laptop vs. Windows/WSL2).
* **Automated Disaster Recovery:** Programmed scheduled root-level Cron routines executing nightly database dumps, system image archiving, and encrypted sync protocols streaming backups directly to private Telegram nodes.

---

## 🧰 Tech Stack & Tools

* **OS:** Linux (Ubuntu Server, Debian GNU/Linux), WSL2 (Windows Subsystem for Linux)
* **Traffic Obfuscation:** Xray Core (VLESS, REALITY, Fallback), X-UI Framework
* **Automation & IaC:** Ansible, Crontab (Bash scripting)
* **Containers:** Docker, Docker Compose
* **Web Services:** Nginx (Internal Reverse Proxy), PHP, Certbot (ACME)
* **Observability:** Prometheus, Grafana, Uptime Kuma
* **Version Control:** Git, GitHub (GitOps token architecture)

### 🖥️ Live Infrastructure Dashboards

<details>
<summary>📊 Click to expand Grafana Monitoring Dashboard</summary>
<p align="center">
  <br>
<img width="1674" height="898" alt="Снимок экрана 2026-05-19 191308" src="https://github.com/user-attachments/assets/4ce4a086-9a14-440a-9772-a7cb8f6b413e" />

  <br><br>
<img width="1850" height="1067" alt="Снимок экрана 2026-05-19 200246" src="https://github.com/user-attachments/assets/247f90dc-869a-458f-bbcc-984d2105cde3" />

</p>
</details>

<details>
<summary>🔮 Click to expand Xray VPN Control Panel</summary>
<p align="center">
  <br>
<img width="2184" height="1237" alt="Снимок экрана 2026-05-19 195038" src="https://github.com/user-attachments/assets/db8186eb-21ee-4f80-aea8-108064059c18" />

  <br><br>
<img width="2190" height="1246" alt="Снимок экрана 2026-05-19 194840" src="https://github.com/user-attachments/assets/86e6e13f-42dd-423a-b766-9095332e4690" />

</p>
</details>
