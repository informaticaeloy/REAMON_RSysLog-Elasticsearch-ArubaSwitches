# REAMON_RSysLog-Elasticsearch-ArubaSwitches
Sistema de monitorización de LOGs de una red con Switches Aruba de HP, que envían sus logs al syslog server, montado en un Ubuntu 20.04.2 LTS Desktop con Elasticsearch (si quiere)

### 0. Prerrequisitos

Partimos de un entorno virtualizado:

* Ubuntu 20.04.2 LTS Desktop

* 2 cores

* 8 GB de RAM

* 30 GB de disco duro

* Net bridge

### 1. Instalación de Elasticsearch

> Importamos la key PGP de elasticsearch

```shell
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
```

sudo apt-get install apt-transport-https

echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list

sudo apt-get update && sudo apt-get install elasticsearch

![image](https://user-images.githubusercontent.com/20743678/186390930-fa46b614-b183-4b65-811b-dfc9abcb3d87.png)

sudo systemctl daemon-reload

sudo systemctl status elasticsearch.service 

![image](https://user-images.githubusercontent.com/20743678/186391580-abae086a-2058-4230-b577-4dff35542be1.png)

sudo systemctl enable elasticsearch.service 

sudo systemctl start elasticsearch.service 

sudo systemctl status elasticsearch.service 

![image](https://user-images.githubusercontent.com/20743678/186391844-1069fe7f-a50b-49c9-8d94-5392ed240610.png)

sudo su

cd /etc/elasticsearch

nano elasticsearch.yml

línea 61

![image](https://user-images.githubusercontent.com/20743678/186392598-88ec6d03-b14f-4313-9faa-5feac5e7964b.png)

línea 100

![image](https://user-images.githubusercontent.com/20743678/186392175-9d81762e-aa7a-409c-a324-8301667435f5.png)

systemctl restart elasticsearch.service

http://<ip_de_nuestro_ubuntu>:9200

![image](https://user-images.githubusercontent.com/20743678/186393243-308efc2e-fa1f-47ff-ae7c-2487999c0531.png)

### 2. Instalación de Grafana



