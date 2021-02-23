# RDS

## 1. RDS 연결

```
mysql -h sungsudb.cluster-cpjqp9c0hcm6.ap-northeast-2.rds.amazonaws.com -u admin -p
```

### database 생성 
```
create database datacenter;
```

### database 확인
```
show databases;
```

```
create table server(cpu varchar(30), 
    memory number(40),
    disk varchar(30)
)

INSERT INTO server VALUES ( '1.44Mhz', CEIL( RAND() * 3333), '30GiB');

select * from server;
```
https://aws.amazon.com/rds/features/multi-az/