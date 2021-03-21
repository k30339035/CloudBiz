### postgre sql

https://www.scalingpostgres.com/tutorials/postgresql-streaming-replication/

```linux
yum install postgresql-server postgresql-contrib

su - postgres
psql

cd /usr/bin

./initdb -D /var/lib/pgsql/data 

./postgres -D /var/lib/pgsql/data # not use

./pg_ctl -D /var/lib/pgsql/data -l logfile start # not use

./pg_ctl -D /var/lib/pgsql/data/ start

psql 

\l

```

### postgre streaming replication 
postgresql12
centos8 

```
sudo dnf -qy 
```