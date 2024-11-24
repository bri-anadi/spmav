# Server Performance Monitoring and Visualization
Server performance monitoring system for CPU, memory, disk usage, and statistics for web servers (Nginx) and databases (MySQL). Using Prometheus for metrics collection, Grafana for visualization, and Netdata for real-time monitoring.


---
## Usage
| # | Services | Links |
|---|---|--- |
| Host | VMWare Workstation 17 Pro | <https://vmware.com/> |
| Distro | Ubuntu 22.04 LTS | <https://ubuntu.com> |
| Services | Nginx | <https://nginx.org> |
|| Secure Shell / SSH | <https://ssh.com> |
|| Prometheus | <https://prometheus.io> |
|| Grafana | <https://grafana.com> |
|| Netdata | <https://netdata.cloud> |


---
## Getting Started

1. Cek IP Address
   ![00-ip-address.png](images/00-ip-address.png)
   
3. Update Packages
   ![01-update-repo](images/01-update-repo.png)
   
4. Install Packages()
   ![02-install-package](images/02-install-package.png)


---
### Initialization
#### Nginx as Web Service

> Apa itu Nginx? Sebuah service web server yang dapat digunakan sebagai port forwarding, load balancer, sekaligus mail proxy.

1. Install Nginx
   ![03-install-nginx](images/03-install-nginx.png)
   
2. Start & Enable Nginx
   ![04-running-nginx](images/04-running-nginx.png)


#### MySQL as Database

> Apa itu MySQL? Merupakan database yang sangat populer yang berfungsi untuk menyimpan data dan memanage data berbasiskan relational database management system.

3. Install MySQL
   ![05-install-mysql](images/05-install-mysql.png)
  
4. Start & Enable MySQL
   ![06-running-mysql](images/06-running-mysql.png)

   
---
### Prometheus

> Apa itu Prometheus? Sistem monitoring infrastruktur server ataupun aplikasi, tools yang populer karena fleksibilitas dan integrasi dengan banyak platform.

1. Buat pengguna prometheus
![07-create-user](images/07-create-user.png)

2. Buat direktori
![08-create-directory](images/08-create-directory.png)

3. Download Prometheus
![09-install-prometheus](images/09-install-prometheus.png)

4. Extract file prometheus
![10-extract-prometheus](images/10-extract-prometheus.png)

5. Salin file prometheus ke folder bin
![11-copy-prometheus](images/11-copy-prometheus.png)

6. Salin konfigurasi consoles ke direktori prometheus
![12-copy-console-prometheus](images/12-copy-console-prometheus.png)

7. Buat file konfigurasi prometheus
![13-conf-prometheus](images/13-conf-prometheus.png)

8. Buat file service prometheus
![14-conf-prometheus-service](images/14-conf-prometheus-service.png)


> Apa itu Node Exporter?

9. Install node exporter
![15-install-node-exporter](images/15-install-node-exporter.png)

11. Extract file node exporter
![16-extract-node-exporter](images/16-extract-node-exporter.png)

12. Salin file node expoerter ke folder bin
![17-copy-node-exporter](images/17-copy-node-exporter.png)

13. Buat file service node exporter
![18-conf-node-exporter](images/18-conf-node-exporter.png)


> Apa itu MySQL Exporter?

13. Download mysql exporter
![19-install-mysqld-exporter](images/19-install-mysqld-exporter.png)

15. Extract file mysql exporter
![20-extract-mysqld-exporter](images/20-extract-mysqld-exporter.png)

16. Salin file mysql exporter ke direktori bin
![21-copy-mysqld-exporter](images/21-copy-mysqld-exporter.png)

17. Buat akses ke user exporter
![22-running-mysql](images/22-running-mysql.png)

18. Buat file konfigurasi mysql exporter
![23-conf-mysqld-exporter](images/23-conf-mysqld-exporter.png)

19. Buat file service mysql exporter
![24-conf-mysqld-exporter-service](images/24-conf-mysqld-exporter-services.png)

---
### Grafana
> Apa itu Grafana? Adalah tools untuk memvisualisasikan data bahkan alerting ditambah dengan keunggulan open source dan customable.

1. Tambahkan Grafana gpg
![25-add-grafana-gpg](images/25-add-grafana-gpg.png)

2. Tambahkan repository Grafana
![26-add-grafana-repo](images/26-add-grafana-repo.png)

3. Update repository
![27-update-grafana-repo](images/27-update-grafana-repo.png)

4. Install Grafana
![28-install-grafana](images/28-install-grafana.png)

5. Running Grafana
![29-running-grafana](images/29-running-grafana.png)


---
### Netdata
> Apa itu Netdata? Netdata merupakan tools monitoring real-time untuk melihat resources pada server.

1. Install Netdata
![30-install-netdata](images/30-install-netdata.png)
  
2. Proses install Netdata
![31-process-running-grafana](images/31-process-running-grafana.png)

3. Berhasil install Netdata
![32-success-running-grafana](images/32-success-running-grafana.png)

---
## Flow
```mermaid
graph
A[Server/Aplikasi]  --> B[Node Exporter/MySQL Exporter/dll] --> C[Prometheus] --> D[Alertmanager] --> F[Notifications]
C --> E[Grafana] --> G[Dashboard/Alerts]
```


## Running Public

1. Menjalankan Grafana
```ssh -R 80:localhost:3000 serveo.net```

2. Menjalankan Prometheus
```ssh -R 80:localhost:9090 serveo.net```

3. Menjalankan Netdata
```ssh -R 80:localhost:19999 serveo.net```


> Coming Soon!
