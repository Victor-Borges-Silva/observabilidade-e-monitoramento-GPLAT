# observabilidade-e-monitoramento-GPLAT
Repositório destinado ao estudo de Observabilidade e Monitoramento usando Grafana, Prometheus,Loki, Alloy e Tempo

### **Comandos para instalar o Prometheus**

```yaml
wget <URL>
tar xvf <prometheus.tar.gz>
cd <diretorio_extraido>
sudo mv prometheus promtool /usr/local/bin/
sudo mv prometheus.yml /etc/prometheus/
vim /etc/systemd/system/prometheus.service
    Adicionar o conteudo do arquivo prometheus.serice
sudo groupadd --system prometheus
sudo useradd -s /sbin/nologin --system -g prometheus prometheus
sudo mkdir /var/lib/prometheus
sudo mkdir -p /etc/prometheus/rules
sudo mkdir -p /etc/prometheus/files_sd
sudo chown -R prometheus:prometheus /etc/prometheus
sudo chown -R prometheus:prometheus /etc/prometheus/*
sudo chmod -R 775 /etc/prometheus
sudo chmod -R 775 /etc/prometheus/*
sudo chown -R prometheus:prometheus /var/lib/prometheus
sudo chown -R prometheus:prometheus /var/lib/prometheus/*
sudo systemctl daemon-reload
sudo systemctl enable prometheus
sudo systemctl start prometheus
sudo systemctl status prometheus
```

