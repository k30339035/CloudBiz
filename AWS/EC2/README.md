# CentOS 기본 작업
yum update -y
yum install unzip -y 

curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64-2.0.30.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install



## 추가 sudo user
### sample 사용자 추가 
```
adduser sample
passwd sample

usermod -aG wheel sample 

su - sample 
```

### root권한 얻기 위한 파일 편집 
```
vi /etc/passwd
sample:x:1002:1002::/home/sample:/bin/bash
```
### root 그룹으로 변경 
```
sample:x:0:0::/home/sample:/bin/bash
```

### No supported authentication methods available(server sent: publickey,gssapi-keyex,gssapi-with-mic)
```
vi /etc/ssh/sshd_config

# To disable tunneled clear text passwords, change to no here!
# PasswordAuthentication yes
```
### PasswordAuthentication 변경 
```
# To disable tunneled clear text passwords, change to no here!
PasswordAuthentication yes
```
sshd 재시작 
```
service sshd restart 
```
AMI 복사 후 로그인 할 경우 PasswordAuthentication no 로 된 경우가 있으며 yes로 변경해야 설정 적용 됨
```
PasswordAuthentication no
service sshd restart 
```
