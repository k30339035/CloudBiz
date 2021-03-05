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


### RDS lambda에서 타입 변경하기
### 스케줄은 CloudWatch에서 설정 하면 됩니다. 
```
import json
import boto3
def lambda_handler(event, context):
    # TODO implement
    boto3.client('rds').modify_db_instance(DBInstanceIdentifier='sungsudb-instance-1', DBInstanceClass='db.t2.medium',
                                           ApplyImmediately=True)
    return {
        'statusCode': 200,
        'body': json.dumps('RDS ApplyImmediately !')
    }

```