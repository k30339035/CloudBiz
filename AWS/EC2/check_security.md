###  변경에 대한 책임은 본인 소유하에 진행하셔야 합니다. 정보전달에 목적이 있습니다. 
### 해당 내용 변경으로 인한 책임은 스크립트 수행자에게 있습니다. 
### 해당 내용은 샘플 정책입니다. 각 회사 환경에 맞게 수정하셔서 사용하시기를 권해 드립니다. 
### vi execute_script.sh
### chmod +x execute_script.sh
### ./execute_script.sh
###
```sh
#/bin/sh
echo "START"
vhost=$1
vcpu=$2

find_string(){
    if grep -q sungsu /etc/login.defs; then echo "result"; fi
}

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

delete_group(){
    delete_user="lp rpcuser systemd-network ec2-instance-connect nfsnobody rngd"
    for u in $delete_user:
    do
        echo $u
        userdel $u
    done
    
    delete_group="tty disk mem kmem cdrom man dialout floppy games tape video lock audio utmp utempter input slocate  stapusr stapsys stapdev"
    for i in $delete_group:
    do 
        echo $i 
        groupdel $i
    done
}

## 1.03 게정 잠금 임계값 설정
change_sshd_root(){
        sed -i 's/PermitRootLogin yes/PermitRootLogin no/g' /etc/ssh/sshd_config
}
##
recover_sshd_root(){
        sed -i 's/PermitRootLogin no/PermitRootLogin yes/g' /etc/ssh/sshd_config
}

## 1.06 root 계정 su 제한

sed -i '6a\auth        required      pam_tally2.so deny=5 unlock_time=120 no_magic_root'   /etc/pam.d/system-auth
sed -i '9a\account     required      pam_tally2.so no_magic_root'   /etc/pam.d/system-auth
sed -i '14a\password    requisite     pam_cracklib.so try_first_pass retry=3 type= minlen=8 lcredit=-1 ucredit=-1 dcredit=-1 ocredit=-1' /etc/pam.d/system-auth
## 
change_max_days(){
    if [ "`sed -n '/^PASS_MAX_DAYS/p' /etc/login.defs`" != "" ]; 
    then
        sed -i 's/^PASS_MAX_DAYS/#PASS_MAX_DAYS/' /etc/login.defs
        sed -i '25a\PASS_MAX_DAYS   90' /etc/login.defs
    fi
      #  sed -i 's/PASS_MAX_DAYS\t99999/PASS_MAX_DAYS\t60/g' /etc/login.defs
}
##
change_min_days(){
    if [ "`sed -n '/^PASS_MIN_DAYS/p' /etc/login.defs`" != "" ]; 
    then
        sed -i 's/^PASS_MIN_DAYS/#PASS_MIN_DAYS/' /etc/login.defs
        sed -i '26a\PASS_MIN_DAYS   1' /etc/login.defs
    fi
#        sed -i 's/PASS_MIN_DAYS\t0/PASS_MIN_DAYS\t-1/g' /etc/login.defs
}
## 
change_min_len(){
    if [ "`sed -n '/^PASS_MIN_LEN/p' /etc/login.defs`" != "" ]; 
    then
        sed -i 's/^PASS_MIN_LEN/#PASS_MIN_LEN/' /etc/login.defs
        sed -i '29a\PASS_MIN_LEN    8' /etc/login.defs
    fi
#        sed -i 's/PASS_MIN_LEN\t5/PASS_MIN_LEN\t-1/g' /etc/login.defs
}



## 1.15 Session Timeout

echo "export TMOUT=300" >> /etc/profile
cat /etc/profile | grep TMOUT


if [ -f /etc/passwd ]; then
        ls -laF /etc/passwd
        echo "[Confirm]: Permission 444 Confirm."
fi
echo;


change_unix_chkpwd(){
    if [ "`ls -alL /sbin/unix_chkpwd | awk '{ print $1 }'`" == "-rwsr-xr-x" ];
    then
        chmod +s /sbin/unix_chkpwd
        echo "/sbin/unix_chkpwd"
        ls -alL /sbin/unix_chkpwd
    fi 
}

change_usrbinat(){
    if [ "`ls -alL /usr/bin/at | awk '{ print $1 }'`" == "-rwsr-xr-x" ];
    then
        chmod +s /usr/bin/at
        echo "/usr/bin/at"
        ls -alL /usr/bin/at
    fi 
}

change_usrbinnewgrp(){
    if [ "`ls -alL /usr/bin/newgrp | awk '{ print $1 }'`" == "-rwsr-xr-x" ];
    then
        chmod +s /usr/bin/newgrp
        echo "/usr/bin/newgrp"
        ls -alL /usr/bin/newgrp
    fi 
}

# UL-64
# 문서에서 누락됨.
chmod 4700 /bin/at
chmod 640 /etc/at.deny

# UL-67
cat <<EOL > /etc/issue.net
####################################################################
####################################################################
#####                This Shinsegae I&C assets                 #####
#####    WARINNG!!   Authorized Users outside Restraining      #####
#####              /illegal legal action when approaching      #####
####################################################################
####################################################################
EOL

cat /etc/issue.net

sed -i 's/^#Banner none/Banner \/etc\/issue.net/g' /etc/ssh/sshd_config

delete_group

list01
list02
change_sshd_root
#recover_sshd_root
#
change_max_days
change_min_days
change_min_len

change_unix_chkpwd
change_usrbinat
change_usrbinnewgrp

add 2 3


service sshd restart 
echo "END"

```