# Grafana Mimir
Mimir is an open source, horizontally scalable, highly available, multi-tenant TSDB for long-term storage for Prometheus

Reference Documentation: https://github.com/grafana/mimir

# 1. Download Grafana Mimir  

Please follow the below steps  

    curl -fLo mimir https://github.com/grafana/mimir/releases/latest/download/mimir-linux-amd64
    chmod +x mimir
    sudo vim demo.yaml

Add the demo.yaml in the same folder.

# 2. Run Grafana Mimir:  

    ./mimir --config.file=./demo.yaml

# 3. Configure Prometheus to write to Grafana Mimir  

    sudo vim /etc/prmetheus/prometheus.yml  

Add the remote write
    remote_write:
    - url: http://localhost:9009/api/v1/push

Restart Prometheus  

    sudo systemctl stop prometheus
    sudo systemctl start prometheus
    sudo systemctl status prometheus

# 4. Add Grafana Mimir as a Prometheus data source  

In a browser, go to the Grafana server at http://localhost:3000/datasources.  

Sign in using the default username admin and password ****.

Configure a new Prometheus data source to query the local Grafana Mimir server using the following settings:

Name:	Mimir  
URL: 
http://mimir:9009/prometheus if you used Docker  
http://localhost:9009/prometheus if you used local binary