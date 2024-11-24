# Server Performance Monitoring and Visualization
Server performance monitoring system for CPU, memory, disk usage, and statistics for web servers (Nginx) and databases (MySQL). Using Prometheus for metrics collection, Grafana for visualization, and Netdata for real-time monitoring.


---
## Usage
| # | Services | Purpose | Links |
|---|---|---|---|
| Host | VMWare Workstation 17 Pro | Virtualization | <https://vmware.com/> |
| Distro | Ubuntu 22.04 LTS | Operating System | <https://ubuntu.com> |
| Services | Nginx | WebServer | <https://nginx.org> |
|| MySQL | Database | <https://mysql.com> |
|| Secure Shell / SSH | Secure Access | <https://ssh.com> |
|| Prometheus | Metrics Collection | <https://prometheus.io> |
|| Grafana | Data Visualization | <https://grafana.com> |
|| Netdata | Real-time Monitoring | <https://netdata.cloud> |


---
## Getting Started

1. Cek IP Address
![00-ip-address.png](images/00-ip-address.png)

2. Update Packages
![01-update-repo](images/01-update-repo.png)
   
3. Install Packages
![02-install-package](images/02-install-package.png)


---
### Initialization
#### Nginx as Web Service

> _Apa itu Nginx? Sebuah service web server yang dapat digunakan sebagai port forwarding, load balancer, sekaligus mail proxy._

1. Install Nginx
![03-install-nginx](images/03-install-nginx.png)
   
2. Start & Enable Nginx
![04-running-nginx](images/04-running-nginx.png)


#### MySQL as Database

> _Apa itu MySQL? Merupakan database yang sangat populer yang berfungsi untuk menyimpan data dan memanage data berbasiskan relational database management system._

3. Install MySQL
![05-install-mysql](images/05-install-mysql.png)
  
4. Start & Enable MySQL
![06-running-mysql](images/06-running-mysql.png)

   
---
### Prometheus

> _Apa itu Prometheus? Sistem monitoring infrastruktur server ataupun aplikasi, tools yang populer karena fleksibilitas dan integrasi dengan banyak platform._

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


> _Apa itu Node Exporter? Merupakan service yang berfungsi untuk mengumpulkan resources pada node yang sedang running._

9. Install node exporter
![15-install-node-exporter](images/15-install-node-exporter.png)

11. Extract file node exporter
![16-extract-node-exporter](images/16-extract-node-exporter.png)

12. Salin file node expoerter ke folder bin
![17-copy-node-exporter](images/17-copy-node-exporter.png)

13. Buat file service node exporter
![18-conf-node-exporter](images/18-conf-node-exporter.png)


> _Apa itu MySQL Exporter? Secara sederhana adalah merupakan service yang digunakan untuk menampilkan resources dari mysql agar dapat divisualisasikan menjadi grafik._

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
![24-conf-mysqld-exporter-service](images/24-conf-mysqld-exporter-service.png)

---
### Grafana
> _Apa itu Grafana? Adalah tools untuk memvisualisasikan data bahkan alerting ditambah dengan keunggulan open source dan customable._

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
> _Apa itu Netdata? Netdata merupakan tools monitoring real-time untuk melihat resources pada server._

1. Install Netdata
![30-install-netdata](images/30-install-netdata.png)
  
2. Proses install Netdata
![31-process-install-netdata](images/31-process-install-netdata.png)

3. Berhasil install Netdata
![32-success-install-netdata](images/32-success-install-netdata.png)

---
### More Configuration

> _Set permission? penggunaan chown bertujuan untuk memberikan hak kepemilikan folder atau file kepada user._

1. Buat akses untuk user prometheus
![33-ownable-user](images/33-ownable-user.png)

2. Reload systemd
![34-reload-services](images/34-reload-services.png)

3. Jalankan services prometheus, node_exporter, mysql_exporter
![35-start-services](images/35-start-services.png)

---
## Flow
```mermaid
graph
A[Server/Aplikasi]  --> B[Node Exporter/MySQL Exporter/dll] --> C[Prometheus] --> D[Alertmanager] --> F[Notifications]
C --> E[Grafana] --> G[Dashboard/Alerts]
```

---
## Running Public

1. Menjalankan Grafana
   ```
   ssh -R 80:localhost:3000 serveo.net
   ```

2. Menjalankan Prometheus
   ```
   ssh -R 80:localhost:9090 serveo.net
   ```

3. Menjalankan Netdata
   ```
   ssh -R 80:localhost:19999 serveo.net
   ```

---
## Testing
1. Login Grafana dengan default credential `admin:admin`
![36-test-login-grafana](images/36-test-login-grafana.png)

2. Cek Node yang terkoneksi berupa server `ubuntuserver2204`
![37-test-grafana-node](images/37-test-grafana-node.png)

3. Tampilan dashboard dari Grafana
![38-test-grafana-dashboard](images/38-test-grafana-dashboard.png)

4. Menambahkan Prometheus pada Grafana
![39-test-grafana-source-prometheus](images/39-test-grafana-source-prometheus.png)

5. Prometheus berhasil ditambahkan pada Grafana
![40-test-grafana-source-prometheus-chart](images/40-test-grafana-source-prometheus-chart.png)

6. Menambahkan Node Exporter ke Grafana
![41-test-grafana-source-node-exporter](images/41-test-grafana-source-node-exporter.png)

7. Node Exporter selesai ditambahkan ke Grafana
![42-test-grafana-source-node-exporter-chart](images/42-test-grafana-source-node-exporter-chart.png)

8. Tambah MySQL pada Source Data Grafana
![43-test-grafana-source-mysql](images/43-test-grafana-source-mysql.png)

9. MySQL berhasil ditambahkan
![44-test-grafana-source-mysql-chart](images/44-test-grafana-source-mysql-chart.png)

10. Menambahkan Nginx Web Server ke Grafana
![45-test-grafana-source-nginx](images/45-test-grafana-source-nginx.png)

11. Semua Services yang telah ditambahkan ke Grafana
![46-test-grafana-sources](images/46-test-grafana-sources.png)

12. Melakukan Login ke Prometheus
![47-test-prometheus](images/47-test-prometheus.png)

13. Login ke Netdata menggunakan guest
![48-test-netdata](images/48-test-netdata.png)

14. Realtime Resources pada Node Server
![49-test-netdata-chart](images/49-test-netdata-chart.png)

---
## Conclusion

Pembahasan services monitoring dengan mengimplementasikan Prometheus, Grafana, Netdata dengan beberapa services sebagai sample yang dimonitoring seperti MySQL dan Nginx. Hasil yang didapat bertujuan untuk memantau proses yang terjadi pada server, berguna untuk mendeteksi serangan ke server sehingga dapat membuat alerting untuk memberitahu bahwa ada attack ke server.
