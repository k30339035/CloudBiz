## S3 Bucket 설정


# 버켓 생성시 Public 접근 체크하지 않음

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


CloudFront 
