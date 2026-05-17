# Hi there, I'm Dzamal Barambajev 👋
### Systems Integration & DevOps Engineer in Training | Based in Germany 🇩🇪

Automating, securing, and orchestrating advanced self-hosted production systems. Expert in traffic obfuscation, secure routing topologies, and scalable monitoring infrastructure.

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
* **Advanced Xray Ingress Mesh:** Deployed an edge routing core utilizing **Xray (VLESS-Reality)** on port 443 [      ]. Configured stealth handshakes that mimic legitimate web destinations, providing bulletproof traffic obfuscation.
* **Smart Fallback Routing:** Engineered custom **Fallback pathways** inside the Xray core. Unauthenticated generic web traffic hitting port 443 is seamlessly routed downstream to an internal port (`8443`), concealing the existence of the VPN gateway [      ].
* **Internal Reverse Proxying:** Configured an internal **Nginx isolation layer** on port 8443 to safely multiplex and host multi-tenant platforms (Production landing pages and PHP family applications) behind the Xray perimeter [      ].
* **Automated SSL Management:** Created automated Certbot event lifecycle triggers (`pre_hook` / `post_hook`) to coordinate short-term Nginx releases, preserving a zero-downtime certificate renewal matrix [      ].

### 📊 Observability & Storage Isolation (GitOps Native)
* **High-Capacity Storage Extension:** Partitioned, formatted, and mounted a dedicated **100 GB external Block Storage disk (`/dev/vdb1` -> `/mnt/storage`)** to prevent stateful observability logs from exhausting system storage [      ].
* **Containerized Telemetry Stack:** Automated the deployment of a synchronized monitoring engine using **Docker Compose**, bundling **Prometheus and Grafana** directly onto the isolated Block Storage array [      ].
* **Data Retention Tuning:** Enforced custom retention windows (`--storage.tsdb.retention.time=30d`) within Prometheus TSDB via Docker Bind Mounts to streamline data durability [      ].
* **Real-time Status Alerting:** Running a containerized **Uptime Kuma** monitoring cell on the primary root node to track site health thresholds and handle sub-second downtime telemetry.

### ⚙️ Systems Engineering & IaC Automation
* **Multi-Node GitOps (Ansible):** Authored an environment-aware Infrastructure as Code (IaC) configuration repo [      ]. Implemented an adaptive `hosts` matrix to handle independent SSH keys (`id_ed25519_wsl`) and Python compilation routes based on the origin workstation (Debian Laptop vs. Windows/WSL2).
* **Automated Disaster Recovery:** Programmed scheduled root-level Cron routines executing nightly database dumps, system image archiving, and encrypted sync protocols streaming backups directly to private Telegram nodes [      ].

---

## 🧰 Tech Stack & Tools

* **OS:** Linux (Ubuntu Server, Debian GNU/Linux), WSL2 (Windows Subsystem for Linux)
* **Traffic Obfuscation:** Xray Core (VLESS, REALITY, Fallback), X-UI Framework [      ]
* **Automation & IaC:** Ansible, Crontab (Bash scripting) [      ]
* **Containers:** Docker, Docker Compose
* **Web Services:** Nginx (Internal Reverse Proxy), PHP, Certbot (ACME) [      ]
* **Observability:** Prometheus, Grafana, Uptime Kuma [      ]
* **Version Control:** Git, GitHub (GitOps token architecture) [      ]
