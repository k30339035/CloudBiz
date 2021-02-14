## - S3 Bucket 설정


### - 버켓 생성시 Public 접근 체크하지 않음

Pricipal: * 
Actions: GetObject 
** /* 추가 **
Amazon Resource name(ARN): arn:aws:s3:::sungsuglue/* 

```
{
  "Id": "Policy1612322747522",
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "Stmt1612322744271",
      "Action": [
        "s3:GetObject"
      ],
      "Effect": "Allow",
      "Resource": "arn:aws:s3:::sungsuglue/*",
      "Principal": "*"
    }
  ]
}
```

```
웹서비스로 설정할 경우 주소가 변경 됨. 
변경 된 주소로 서비스 필요. 
가속화 서비스 설정할 경우 마찬가지로 주소 변경 됨. 

```

## CloudFront 
```
Behavior => Viewer Protocol Policy: Redirect HTTP to HTTPS 
Object Caching: Customize
    Minimum TTL: 86400

Error Pages :403 Forbidden -> 잘못된 주소를 설정할 경우 
Customize Error Response: yes
Response Page Path: /Error.html 
HTTP Response Code: 404: Not Found 
```






