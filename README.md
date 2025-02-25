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
O Prometheus estará executando em seu localhost:9090


### **Comandos para instalar o Node_Exporter**

```yaml
wget <URL>
tar xvf <node_exporter.tar.gz>
cd <diretorio_extraido>
sudo groupadd --system prometheus
sudo useradd -s /sbin/nologin --system -g prometheus prometheus
sudo mkdir /var/lib/node/
sudo mv node_exporter /var/lib/node/
sudo vim /etc/systemd/system/node.service
sudo chown -R prometheus:prometheus /var/lib/node
sudo chmod -R 775 /var/lib/node
sudo chmod -R 775 /var/lib/node/*
sudo systemctl daemon-reload
sudo systemctl start node
sudo systemctl enable node
sudo systemctl status node
```

O Node_exporter estará executando em seu localhost:9100

### **Comandos para instalar o Grafana**

Click na URL (https://grafana.com/grafana/download) e selecione a versão que deseja instalar, após isso só seguir o passo a passo.

```yaml
sudo apt-get install -y adduser libfontconfig1 musl
wget https://dl.grafana.com/enterprise/release/grafana-enterprise_<versao>
sudo dpkg -i grafana-enterprise_<versao>
sudo systemctl daemon-reload
sudo systemctl enable grafana-server
sudo systemctl start grafana-server
sudo systemctl status grafana-server
```
O Grafana está executando em seu seu localhost:300

### **Comandos para instalar o Loki**

A URL abaixo contem a documentação oficial para instalação onde mostrará difentes forma de fazer a instalação, nessa documentação será explicado como fazer a instalação com download manual da versão desejada do software
```yaml
https://grafana.com/docs/loki/latest/setup/install/local/
```

Click na URL (https://github.com/grafana/loki/releases/) e selecione a versão que deseja instalar em sua instalação manual, após isso só seguir o passo a passo.

```yaml
wget <URL>
unzip <loki-versão.zip>
sudo mv <loki-versão.zip> /usr/local/bin/loki
sudo chmod +x /usr/local/bin/loki
```

Após baixar e instalar o binário deve-se criar o arquivo de configuração e o serviço do Loki.

Para baixar o arquivo de configuração padrão do loki use os seguintes comandos
```yaml
wget https://raw.githubusercontent.com/grafana/loki/main/cmd/loki/loki-local-config.yaml
sudo mkdir /etc/loki
sudo mv loki-local-config.yaml /etc/loki
```

Para criar o serviço do loki use os seguintes comandos
```yaml
sudo vim /etc/systemd/system/loki.service
    popule o arquivo com o conteudo do arquivo loki.service
sudo systemctl daemon-reload
sudo systemctl start loki
sudo systemctl enable loki
sudo systemctl status loki
```

### **Comandos para instalar o Promtail**

O Promtail é um agente de coleta de logs desenvolvido pelo Grafana para enviar logs ao Loki. Para instala-lo podemos acessar o github oficial e selecionar a versão desejada. 
https://github.com/grafana/loki/releases

Após selecionar o versão desejda, baixar e instalar o binário em seu servidor.
```yaml
wget https://github.com/grafana/loki/releases/download/v3.4.1/promtail-<versao-desejada>.zip
unzip promtail-<versao-desejada>.zip
sudo mv promtail-<versao-desejada>.zip /usr/local/bin/promtail
sudo chmod +x /usr/local/bin/promtail
```

Após baixar e instalar o binário deve-se criar o arquivo de configuração e o serviço do Promtail.

Para baixar o arquivo de configuração padrão do loki use os seguintes comandos
```yaml
wget https://github.com/aussiearef/grafana-udemy/blob/main/loki/config.yml
sudo mkdir /etc/promtail
sudo mv config.yml /etc/promtail
```

Para criar o serviço do loki use os seguintes comandos
```yaml
sudo vim /etc/systemd/system/promtail.service
    popule o arquivo com o conteudo do arquivo promtail.service
sudo systemctl daemon-reload
sudo systemctl start loki
sudo systemctl enable loki
sudo systemctl status loki
```
