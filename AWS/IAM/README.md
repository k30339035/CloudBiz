## IAM
### 사용자 IP 제한 정책 
- 1. ip_limit 인라인 정책 생성 후에 IAM 사용자에게 정책 부여 

```
{
    "Version": "2012-10-17",
    "Statement": {
        "Effect": "Deny",
        "Action": "*",
        "Resource": "*",
        "Condition": {
            "NotIpAddress": {
                "aws:SourceIp": [
                    "112.158.14.35/32",
                    "203.0.113.0/24"
                ]
            },
            "Bool": {
                "aws:ViaAWSService": "false"
            }
        }
    }
}
```