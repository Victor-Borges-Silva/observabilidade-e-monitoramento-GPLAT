## **Configurando ShoeHub**

No arquivo prometheus.yaml configura o novo trabalho

```yaml
scrape_configs:
  - job_name: "shoehub"
    static_configs:
      - targets: ["localhost:8030"]
        labels:
          instance: "ShoeHub"
```
# **Baixando imagem docker**

Para executar a aplicação é necessário baixar o imagem docker que contem o serviço 

```yaml
  docker pull aussiearef/shoehub
```


Para **testar** o funcionado é possível executar a imagem 

```yaml
  docker run -p 8030:8080 -i aussiearef/shoehub
```

# **Criando serviço**

A criação do serviço é importante para que o docker seja executado em segundo plano e caso o serviço venha a cair ele será reiniciado automaticamente

```yaml
[Unit]
Description=Run ShoeHub Docker Container
After=docker.service
Requires=docker.service

[Service]
Restart=always
ExecStart=/usr/bin/docker run -p 8030:8080 -i aussiearef/shoehub
ExecStop=/usr/bin/docker stop shoehub
ExecStopPost=/usr/bin/docker rm shoehub

[Install]
WantedBy=multi-user.target
```

Para finalizar a criação do serviço é necessário habilita-lo e inicia-lo

```yaml
sudo systemctl daemon-reload
sudo systemctl enable shoehub.service
sudo systemctl start shoehub.service
sudo systemctl status shoehub.service
```