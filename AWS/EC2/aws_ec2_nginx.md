# CentOS nginx 설치 

```
cd /etc/yum.repos.d/
vi nginx.repo

[nginx]
name=nginx repo
baseurl=http://nginx.org/packages/centos/7/$basearch/
gpgcheck=0
enabled=1

```

```
yum install nginx -y 
```


