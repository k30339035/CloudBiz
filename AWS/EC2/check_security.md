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