

```
sudo yum install golang fuse git


export GOROOT=/usr/lib/golang
export GOBIN=$GOROOT/bin
export GOPATH=/usr/local/golang
export PATH=$PATH:$GOROOT/bin

go get github.com/kahing/goofys

aws configure

$GOPATH/bin/goofys <bucket> <mountpoint>

$GOPATH/bin/goofys sungsukms /data

goofys sungsukim /data

# fstab 
goofys#sungsukms	/data	fuse	_netdev,allow_other,--file-mode=0666,--dir-mode=0777,--uid=1001,--gid=1001,--profile=default	0 0

touch 1
touch 2

```
