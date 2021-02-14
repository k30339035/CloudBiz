## Zabbix 설치 및 관리 

### 공식 Zabbix Docker 
- https://github.com/zabbix/zabbix-docker

### Zabbix Blog 
- https://blog.zabbix.com/zabbix-docker-containers/7150/


##DOCKER##
```
sudo yum install -y yum-utils device-mapper-persistent-data lvm2
sudo yum-config-manager --add-repo https://download.docker.com/linux/centos/docker-ce.repo
sudo yum install −y docker-ce
sudo systemctl start docker
```

##DOCKER COMPOSE##
```
sudo curl -L "https://github.com/docker/compose/releases/download/1.24.1/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose

yum install git

git clone https://github.com/zabbix/zabbix-docker.git
```
##git reset --hard