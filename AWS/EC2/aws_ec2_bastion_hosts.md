### bastion host 
```
ssh-agent bash
ls # 키 확인 
ssh-add sungsukeypair.pem
ssh-add -l

# ssh -A ec2-user@public_ip
ssh -A ec2-user@3.36.118.3
# private 노드 연결 
ssh ec2-user@10.1.45.10
```


