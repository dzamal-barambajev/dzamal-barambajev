# Hallo, ich bin Dzamal Barambajev 👋
### Fachinformatiker für Systemintegration & DevOps Engineer in Ausbildung | Wohnhaft in Deutschland 🇩🇪

Automatisierung, Absicherung und Orchestrierung moderner Self-Hosted-Produktionssysteme. Mein Fokus liegt auf sicherem Routing, Self-Hosted-Infrastruktur, Observability (Überwachung) und resilienten Cloud-Diensten.
- 🚀 **Aktueller Lernfokus:** Vertiefung in **Kubernetes (K8s)** und Cloud-Native-Architekturen zur Skalierung containerisierter Umgebungen.
- 🔄 **Infrastruktur-Migration:** Laufender Transfer von eigenständigen Docker-Workloads in das K3s-Cluster (Erfolgreich abgeschlossen: **Uptime Kuma** via NodePort & PVC).

![Kubernetes](https://img.shields.io/badge/Kubernetes-k3s-blue?logo=kubernetes)
![Docker](https://img.shields.io/badge/Docker-Containers-blue?logo=docker)
![Grafana](https://img.shields.io/badge/Grafana-Monitoring-orange?logo=grafana)
![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-orange?logo=prometheus)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-black?logo=linux)
![Nginx](https://img.shields.io/badge/Nginx-Reverse_Proxy-green?logo=nginx)
![Ansible](https://img.shields.io/badge/Ansible-Automation-CC0000?logo=ansible)
---

## 🛠️ Meine Produktions-Cloud-Server-Architektur

Ich entwerfe und betreibe ein resilientes Cloud-Ökosystem auf einem Ubuntu-VPS. Dabei setze ich klare Prioritäten auf Traffic-Sicherheit, Fallback-Routing, Automatisierung und persistente Systemüberwachung.

![VPS Infrastruktur Architektur](vps-infrastruktur-architektur-de.png)


---

## 🚀 Wichtigste Infrastruktur-Erfolge

### 🔒 Stealth Networking & Traffic-Verschleierung
* **Erweitertes Xray Ingress Mesh:** Implementierung eines Edge-Routing-Kerns mit **Xray (VLESS-Reality)** auf Port 443. Konfiguration von Stealth-Handshakes, die legitime Web-Ziele imitieren, um eine lückenlose Traffic-Verschleierung zu gewährleisten.
* **Intelligentes Fallback-Routing:** Entwicklung maßgeschneiderter **Fallback-Pfade** innerhalb des Xray-Kerns. Nicht authentifizierter, allgemeiner Web-Traffic auf Port 443 wird nahtlos an einen internen Port (`8443`) weitergeleitet, wodurch die Existenz des VPN-Gateways vollständig verborgen bleibt.
* **Internes Reverse-Proxying:** Konfiguration einer internen **Nginx-Isolationsschicht** auf Port 8443 zum sicheren Multiplexen und Hosten von Mandantenplattformen (Produktions-Landingpages und PHP-Familienanwendungen) hinter dem Xray-Perimeter.
* **Automatisiertes SSL-Management:** Erstellung automatisierter Certbot-Lifecycle-Trigger (`pre_hook` / `post_hook`) zur Koordinierung kurzzeitiger Nginx-Freigaben, wodurch ein ausfallfreies Erneuerungsfenster für Zertifikate (Zero-Downtime) gewahrt bleibt.

### 📊 Observability & Storage-Isolation (GitOps Native)
* **Hochkapazitive Speichererweiterung:** Partitionierung, Formatierung und Einbindung eines dedizierten **externen 100 GB Block-Storage-Laufwerks (`/dev/vdb1` -> `/mnt/storage`)**, um zu verhindern, dass persistente Observability-Logs den primären System-Speicher überlasten.
* **Containerisierter Telemetrie-Stack:** Automatisierte Bereitstellung einer synchronisierten Monitoring-Engine mittels **Docker Compose**, die **Prometheus und Grafana** direkt auf dem isolierten Block-Storage-Array bündelt.
* **Optimierung der Datenaufbewahrung:** Durchsetzung maßgeschneiderter Aufbewahrungsfenster (`--storage.tsdb.retention.time=30d`) innerhalb der Prometheus-TSDB via Docker Bind Mounts, um die Langlebigkeit und Effizienz der Datenhaltung zu steuern.
* **Echtzeit-Statusüberwachung:** Betrieb einer containerisierten **Uptime Kuma** Monitoring-Zelle auf dem primären Root-Knoten zur Überwachung von Website-Health-Schwellenwerten und zur Verarbeitung von Sub-Sekunden-Ausfalltelemetrie.

### ⚙️ Systems Engineering & IaC-Automatisierung
* **Multi-Node GitOps (Ansible):** Entwicklung eines umgebungsbewussten Infrastructure-as-Code (IaC) Repositories. Implementierung einer adaptiven `hosts`-Matrix zur Handhabung unabhängiger SSH-Schlüssel (`id_ed25519_wsl`) und Python-Kompilierungspfade, basierend auf der jeweiligen Workstation (Debian Laptop vs. Windows/WSL2).
* **Automatisierte Disaster Recovery:** Programmierung geplanter Root-Cronjobs, die nächtliche Datenbank-Dumps, System-Image-Archivierungen und verschlüsselte Synchronisierungsprotokolle ausführen, um Backups direkt in private Telegram-Knoten zu streamen.

---

## 🧰 Tech Stack & Tools

* **Betriebssysteme:** Linux (Ubuntu Server, Debian GNU/Linux), WSL2 (Windows Subsystem for Linux)
* **Traffic-Verschleierung:** Xray Core (VLESS, REALITY, Fallback), X-UI Framework
* **Automatisierung & IaC:** Ansible, Crontab (Bash-Scripting)
* **Containerisierung:** Docker, Docker Compose
* **Web-Dienste:** Nginx (Interner Reverse Proxy), PHP, Certbot (ACME)
* **Observability:** Prometheus, Grafana, Uptime Kuma
* **Versionsverwaltung:** Git, GitHub (GitOps Token-Architektur)

### 🖥️ Live Infrastructure Dashboards

<details>
<summary>📊 Klicken zum Ausklappen: Grafana Monitoring Dashboard</summary>
<p align="center">
  <br>
<img width="1674" height="898" alt="Снимок экрана 2026-05-19 191308" src="https://github.com/user-attachments/assets/4ce4a086-9a14-440a-9772-a7cb8f6b413e" />

  <br><br>
<img width="1850" height="1067" alt="Снимок экрана 2026-05-19 200246" src="https://github.com/user-attachments/assets/247f90dc-869a-458f-bbcc-984d2105cde3" />

</p>
</details>

<details>
<summary>🔮 Klicken zum Ausklappen: Xray VPN Control Panel</summary>
<p align="center">
  <br>
<img width="2184" height="1237" alt="Снимок экрана 2026-05-19 195038" src="https://github.com/user-attachments/assets/db8186eb-21ee-4f80-aea8-108064059c18" />

  <br><br>
<img width="2190" height="1246" alt="Снимок экрана 2026-05-19 194840" src="https://github.com/user-attachments/assets/86e6e13f-42dd-423a-b766-9095332e4690" />

</p>
</details>
