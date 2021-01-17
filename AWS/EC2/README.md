## 추가 sudo user
### central 사용자 추가 
```
adduser central
passwd central

usermod -aG wheel central 

su - central 
```

### root권한 얻기 위한 파일 편집 
```
vi /etc/passwd
central:x:1002:1002::/home/central:/bin/bash
```
### root 그룹으로 변경 
```
central:x:0:0::/home/central:/bin/bash
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
