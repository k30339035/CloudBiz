###  변경에 대한 책임은 본인 소유하에 진행하셔야 합니다. 정보전달에 목적이 있습니다. 
### 해당 내용 변경으로 인한 책임은 스크립트 수행자에게 있습니다. 
### 해당 내용은 샘플 정책입니다. 각 회사 환경에 맞게 수정하셔서 사용하시기를 권해 드립니다. 
###
```sh
#/bin/sh
echo "START"
vhost=$1
vcpu=$2

# Security List - 01
function list01()
{
        echo "[01] List"
}

function list02()
{
        echo "[02] List"
}
add(){
        result=$(($1+$2))
        echo $result
}
change_sshd_root(){
        sed -i 's/PermitRootLoging yes/PermitRootLogin no/g' /etc/ssh/sshd_config
}
recover_sshd_root(){
        sed -i 's/PermitRootLoging no/PermitRootLogin yes/g' /etc/ssh/sshd_config
}
change_max_days(){
        sed -i 's/PASS_MAX_DAYS\t99999/PASS_MAX_DAYS\t60/g' /etc/login.defs
}
change_min_days(){
        sed -i 's/PASS_MIN_DAYS\t0/PASS_MIN_DAYS\t-1/g' /etc/login.defs
}
change_min_len(){
        sed -i 's/PASS_MIN_LEN\t5/PASS_MIN_LEN\t-1/g' /etc/login.defs
}
list01
list02
change_sshd_root
#recover_sshd_root
#
change_max_days
change_min_days
change_min_len

add 2 3

if [ -f /etc/passwd ]; then
        ls -laF /etc/passwd
        echo "[Confirm]: Permission 444 Confirm."
fi
echo;

service sshd restart 
echo "END"

```