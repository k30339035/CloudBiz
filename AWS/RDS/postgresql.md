### postgre sql

## postgresql13 Timezone 변경
- Cluster parameter group 변경
```
=> 새로 cluster parameter group 추가 후 timezone을 UTC+9으로 변경 

 * 접속 후 쿼리 확인 
postgres=> show timezone;
 TimeZone
----------
 UTC+9
(1 row)
<Asia/Seoul>

```
- KST 변경 
```
=> cluster parameter group 에서 client_encoding 을 EUC_KR
postgres=> show client_encoding;
 client_encoding
-----------------
 LATIN1
(1 row)
```
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

### pgAdmin
```
choco install pgadmin4 -y 
```

### postgresql 기본 쿼리 예제 
```
create table "users"(
	"name" varchar,
	"age" varchar);
	
insert into users values('father', '45');
insert into users values('son', '3');

select * from users;

update users set age=150 where name='father';

delete from users where name='father';

```

