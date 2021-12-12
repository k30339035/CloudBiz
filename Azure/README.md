## Azure cli 
- Azure cli 설치
- https://docs.microsoft.com/ko-kr/cli/azure/install-azure-cli
```
choco install azure-cli -y
```
- Azure cli 확인
```
az version
az --version # 
```
- Azure upgrade 
```
az upgrade
```
- Azure login
```
az login
az login -u sungsu.kim@shinsegae.com
Password: 
```

## azure 전체 위치 
```
az account list-locations
```
## azure 리소스 
```
az resource list
```

```
az group create -l koreacentral -n shinsegaegroup # -l location -n name
az group list 
az storage account create -g shinsegaegroup -n shinsegaegroup
```
## Compute
```
az vm create -n ubuntuVM -g acgRG --image UbuntuLTS --subscription []
```
## Storage Gateway
```
```
##