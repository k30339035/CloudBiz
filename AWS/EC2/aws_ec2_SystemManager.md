# AWS System Manager 

### Private Subnet EC2 접속 
### AmazonSSMManagedInstanceCore IAM 권한 추가
### Endpoint EC2 추가 
### Endpoint EC2.messages 추가
### Endpoint ssm.messages 추가 

### Managed Instance 추가 

```
sudo status amazon-ssm-agent

sudo systemctl status amazon-ssm-agent 

Get-Service AmazonSSMAgent 
```

### SSM 포트 포워딩
- https://docs.aws.amazon.com/ko_kr/systems-manager/latest/userguide/session-manager-working-with-install-plugin.html#install-plugin-windows
```
- 직접 인터넷 연결 필요 없음
- SG 사용하지 않음 
- 
```
### 권한
```
AmazonSSMManagedInstanceCore 
# 설치 확인
aws --version
# 세션 매니저 플러그인 확인 
session-manager-plugin 
The Session Manager plugin was installed successfully. Use the AWS CLI to start a session.
```