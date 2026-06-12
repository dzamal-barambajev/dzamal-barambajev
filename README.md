# Hallo, ich bin Dzamal Barambajev 👋
### Fachinformatiker für Systemintegration (IHK) | DevOps & Cloud Enthusiast | Wohnhaft in Deutschland 🇩🇪
### 🎯 Ziel des Projekts 
➜ Aufbau einer zentral verwalteten Self-Hosted-Cloud-Plattform, auf der Infrastruktur, Monitoring, Sicherheit und Anwendungen durch standardisierte und automatisierte Prozesse bereitgestellt und verwaltet werden können.


### Der Ursprung des Projekts war ein privater VPN-Dienst🌍
Ausgehend von einem privaten Familien-VPN entwickelte sich dieses Projekt zu einer mehrschichtigen Self-Hosted-Cloud-Plattform mit Kubernetes, Monitoring, Reverse-Proxy-Routing und Infrastruktur-Automatisierung.


## ☁️ Dzamal Cloud Platform
![VPS Infrastruktur Architektur](vps-infrastruktur-architektur-de.png)


---

🌐 VPN ➜ 🔒 Security ➜ 🚦 Nginx Reverse Proxy ➜ 📊 Monitoring ➜ ☸️ Kubernetes ➜ ⚙️ Automation


Aktuelle Entwicklungsbereiche:

✅ Security Hardening & Stealth Networking

✅ Kubernetes (K3s)

✅ Grafana, Prometheus & Observability

✅ Infrastructure as Code (Ansible)

✅ Persistent Storage

✅ Reverse Proxy & Service Routing


### 🚀 Aktueller Plattform-Stand (11 Juni 2026)

<p align="center">
<img width="1604" height="1064" alt="2026-06-11-050714" src="https://github.com/user-attachments/assets/45be44c9-b452-49e1-8292-13c448751dc1" />
</p>


- 🚧 **Aktueller Schwerpunkt:** Migration von Docker-Workloads nach Kubernetes (K3s) und Aufbau einer Ansible-basierten Infrastrukturautomatisierung.

- ☸️ **Kubernetes Migration:** Erfolgreiche Migration zentraler Monitoring-Dienste in das K3s-Cluster
  (Grafana, Prometheus und Uptime Kuma)

- 📊 **Observability Stack:** Grafana, Prometheus, Node Exporter, kube-state-metrics, Kubernetes Metrics Server und Alerting

- 🔐 **Security & Routing:** Xray Reality, Nginx Reverse Proxy, Single-Exposed-Port-Architektur und Security Hardening


![Kubernetes](https://img.shields.io/badge/Kubernetes-k3s-blue?logo=kubernetes)
![Docker](https://img.shields.io/badge/Docker-Containers-blue?logo=docker)
![Grafana](https://img.shields.io/badge/Grafana-Monitoring-orange?logo=grafana)
![Prometheus](https://img.shields.io/badge/Prometheus-Metrics-orange?logo=prometheus)
![Linux](https://img.shields.io/badge/Linux-Ubuntu-black?logo=linux)
![Nginx](https://img.shields.io/badge/Nginx-Reverse_Proxy-green?logo=nginx)
![Ansible](https://img.shields.io/badge/Ansible-Automation-CC0000?logo=ansible)
---

---

## 🚀 Wichtigste Infrastruktur-Erfolge

☸️ Kubernetes & Cloud-Native Engineering

    K3s Cluster Plattform:
    Aufbau und Betrieb einer Kubernetes-Infrastruktur auf einem produktiven Ubuntu VPS.

    Service Migration:
    Migration zentraler Monitoring-Dienste (Grafana, Prometheus und Uptime Kuma) von Docker in Kubernetes.

    Ingress Architektur:
    Betrieb eines zentralen Ingress-Nginx Controllers für Routing, TLS-Termination und Service-Publikation.

    Kubernetes Monitoring:
    Integration von Metrics Server und kube-state-metrics für Cluster-, Node- und Pod-Metriken.

    Persistente Datenhaltung:
    Nutzung von Persistent Volumes (PVC) und Local Path Provisioning für zustandsbehaftete Anwendungen.

### 🔒 Stealth Networking & Traffic-Verschleierung
* **Xray Reality Edge Gateway:** Implementierung eines Edge-Routing-Kerns mit **Xray (VLESS-Reality)** auf Port 443. Konfiguration von Stealth-Handshakes, die legitime Web-Ziele imitieren, um eine lückenlose Traffic-Verschleierung zu gewährleisten.
* **Intelligentes Fallback-Routing:** Entwicklung maßgeschneiderter **Fallback-Pfade** innerhalb des Xray-Kerns. Nicht authentifizierter, allgemeiner Web-Traffic auf Port 443 wird nahtlos an einen internen Port (`8443`) weitergeleitet, wodurch die Existenz des VPN-Gateways vollständig verborgen bleibt.
* **Internes Reverse-Proxying:** Konfiguration einer internen **Nginx-Isolationsschicht** auf Port 8443 zum sicheren Multiplexen und Hosten von Websites, Verwaltungsoberflächen und interne Dienste (Produktions-Landingpages und PHP-Familienanwendungen) hinter dem Xray-Perimeter.
* **Automatisiertes SSL-Management:** Erstellung automatisierter Certbot-Lifecycle-Trigger (`pre_hook` / `post_hook`) zur Koordinierung kurzzeitiger Nginx-Freigaben, wodurch ein ausfallfreies Erneuerungsfenster für Zertifikate (Zero-Downtime) gewahrt bleibt.

### 📊 Observability & Storage-Isolation (GitOps Native)
* **Hochkapazitive Speichererweiterung:** Partitionierung, Formatierung und Einbindung eines dedizierten **externen 100 GB Block-Storage-Laufwerks (`/dev/vdb1` -> `/mnt/storage`)**, um zu verhindern, dass persistente Observability-Logs den primären System-Speicher überlasten.
* **Cloud-Native Observability Stack:** Migration zentraler Monitoring-Dienste (Grafana, Prometheus und Uptime Kuma) in ein Kubernetes (K3s) Cluster mit Persistent Volumes und Ingress Routing.
* **📈 Monitoring-Datenmanagement:** Implementierung einer kontrollierten Datenaufbewahrung innerhalb von Prometheus, um langfristige Metriktrends zu erfassen und gleichzeitig den Speicherverbrauch vorhersehbar zu halten.
* **Service Availability Monitoring:** Betrieb von Uptime Kuma innerhalb des Kubernetes Clusters zur kontinuierlichen Überwachung von Infrastruktur-, Web- und Routing-Diensten.

### ⚙️ Systems Engineering & IaC-Automatisierung
* **Infrastructure as Code (Ansible Automation):** Entwicklung eines umgebungsbewussten Infrastructure-as-Code (IaC) Repositories. Implementierung einer adaptiven `hosts`-Matrix zur Handhabung unabhängiger SSH-Schlüssel (`id_ed25519_wsl`) und Python-Kompilierungspfade, basierend auf der jeweiligen Workstation (Debian Laptop vs. Windows/WSL2).
* **Automatisierte Disaster Recovery:** Programmierung geplanter Root-Cronjobs, die nächtliche Datenbank-Dumps, System-Image-Archivierungen und verschlüsselte Synchronisierungsprotokolle ausführen, um Backups direkt in verschlüsselte Externe-Backup-Speicherorte zu streamen.

---

## 🧰 Tech Stack & Tools

* **Betriebssysteme:** Linux (Ubuntu Server, Debian GNU/Linux), WSL2 (Windows Subsystem for Linux)
* **Kubernetes:** K3s, Ingress-Nginx, CoreDNS, Metrics Server, kube-state-metrics
* **Traffic-Verschleierung:** Xray Core (VLESS, REALITY, Fallback), X-UI Framework
* **Automatisierung & IaC:** Ansible, Cronjobs, Bash
* **Containerisierung:** Kubernetes, Docker, Docker Compose, Portainer
* **Web-Dienste:** Nginx (Interner Reverse Proxy), PHP, Certbot (ACME)
* **Observability:** Prometheus, Grafana, Uptime Kuma
* **Versionsverwaltung:** Git, GitHub (GitOps Token-Architektur)
* **Zertifikatsmanagement:** Certbot, Let's Encrypt
* **Storage:** PVC, Local Path Provisioner, Block Storage 

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

## 🏗️ Architektur-Galerie

### 🚀 Neu Lab (12 Juni 2026)

<p align="center">
<img width="1536" height="1024" alt="DevOps_Lab_12_06_2026_13_12_17" src="https://github.com/user-attachments/assets/c1c78e0d-4dcd-4433-9d3a-9e594bf4228d" />
</p>

