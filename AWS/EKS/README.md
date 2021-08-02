# - EKS
## EKS Anywhere 
```

```

## Kubectl 설치 
kubectl cluster-info

```
curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl
chmod +x ./kubectl
mv ./kubectl /usr/local/bin/kubectl
```

## kubectl version 

```
kubectl version --short
```

```
aws eks update-cluster-version \
 --region <region-code> \
 --name <my-cluster> \
 --kubernetes-version <1.18>


aws eks update-cluster-version \
 --region ap-northeast-2 \
 --name demo-windows-cluster \
 --kubernetes-version 1.16

aws eks update-cluster-version \
 --region ap-northeast-2 \
 --name demo-windows-cluster \
 --kubernetes-version 1.17


aws eks update-cluster-version \
 --region ap-northeast-2 \
 --name demo-windows-cluster \
 --kubernetes-version 1.18

aws eks update-cluster-version \
 --region ap-northeast-2 \
 --name demo-windows-cluster \
 --kubernetes-version 1.19



# Kubeproxy 이미지 확인 
kubectl get daemonset kube-proxy --namespace kube-system -o=jsonpath='{$.spec.template.spec.containers[:1].image}'

 kubectl set image daemonset.apps/kube-proxy \
  -n kube-system \
  kube-proxy=<602401143452.dkr.ecr.us-west-2.amazonaws.com>/eks/kube-proxy:v<1.18.9>-eksbuild.1

  kubectl set image daemonset.apps/kube-proxy \
  -n kube-system \
  kube-proxy=602401143452.dkr.ecr.ap-northeast-2.amazonaws.com/eks/kube-proxy:v1.16.15-eksbuild.1


  602401143452.dkr.ecr.ap-northeast-2.amazonaws.com/eks/kube-proxy:v1.15.11-eksbuild.1
602401143452.dkr.ecr.ap-northeast-2.amazonaws.com/eks/kube-proxy:v1.16.15-eksbuild.1
1.16.15

```




### EKS Windows

### https://aws.amazon.com/ko/blogs/korea/amazon-eks-windows-container-support-now-generally-available/


```
ap-northeast-2b ap-northeast-2a ap-northeast-2c

# Create Cluster
eksctl create cluster --name=sungsumart2 \
                      --region=ap-northeast-2 \
                      --version 1.15 \ 
                      --without-nodegroup
                      --node-type t3.medium \
                      --zones=ap-northeast-2a,ap-northeast-2c \


eksctl create nodegroup --cluster=sungsumart2 \
                       --region=ap-northeast-2 \
                       --name=sungsumart2-ng-public1 \
                       --node-type=t3.medium \
                       --nodes=2 \
                       --nodes-min=2 \
                       --nodes-max=4 \
                       --node-volume-size=20 \
                       --ssh-access \
                       --ssh-public-key=corpseoul \
                       --managed \
                       --asg-access \
                       --external-dns-access \
                       --full-ecr-access \
                       --appmesh-access \
                       --alb-ingress-access 



```


```
eksctl create cluster \
--name demo-windows-cluster \
--version 1.15 \
--nodegroup-name standard-workers \
--node-type t3.medium \
--nodes 2 \
--nodes-min 1 \
--nodes-max 3 \
--node-ami auto

eksctl create cluster \
--name demo-windows-cluster \
--region=ap-northeast-2
--version 1.15 \
--nodegroup-name standard-workers \
--node-type t3.medium \
--nodes 1 \
--nodes-min 1 \
--nodes-max 3 \
--node-ami auto



eksctl utils install-vpc-controllers --name demo-windows-cluster --approve
```

```
eksctl create nodegroup \
--region ap-northeast-2 \
--cluster demo-windows-cluster \
--version 1.15 \
--name windows-ng \
--node-type t3.medium \
--nodes 3 \
--nodes-min 1 \
--nodes-max 5 \
--node-ami-family WindowsServer2019FullContainer \
--node-ami ami-0f85de0441a8dcf46
```
### 아래 명령어 수행 
```
eksctl create nodegroup \
--region ap-northeast-2 \
--cluster demo-windows-cluster \
--version 1.15 \
--name windows-ng \
--node-type t3.medium \
--nodes 3 \
--nodes-min 1 \
--nodes-max 4 \
--node-ami-family WindowsServer2019FullContainer \


echo date && 
eksctl create nodegroup \
--region ap-northeast-2 \
--cluster demo-windows-cluster \
--version 1.16 \
--name windows-ng4 \
--node-type t2.micro \
--nodes 1 \
--nodes-min 1 \
--nodes-max 4 \
--node-ami-family WindowsServer2019FullContainer \
echo date \


eksctl create nodegroup \
--region ap-northeast-2 \
--cluster demo-windows-cluster \
--version 1.17 \
--name windows-ng5 \
--node-type t2.micro \
--nodes 1 \
--nodes-min 1 \
--nodes-max 4 \
--node-ami-family WindowsServer2019FullContainer \
--ssh-access \
--ssh-public-key corpseoul 


date && 
eksctl delete nodegroup \
--cluster demo-windows-cluster \
--name windows-ng5
date 

date && 
eksctl delete nodegroup \
--cluster demo-windows-cluster \
--name windows-ng2
date \

date && 
eksctl delete nodegroup \
--cluster demo-windows-cluster \
--name windows-ng
date \

date && 
eksctl delete cluster --name demo-windows-cluster
date

```yaml
date && 
eksctl delete cluster --name sungsumart2
date


eksctl delete nodegroup \
--cluster sungsumart2 \
--name sungsumart2-ng-public1
```
kubectl run sungsu-pod1 --image stacksimplify/kubenginex:1.0.0 --generator=run-pod/v1




## not work 
kubectl apply -f https://raw.githubusercontent.com/aws/containers-roadmap/master/preview-programs/eks-windows-preview/windows-server-IIS.yaml
kubectl apply -f https://github.com/aws/containers-roadmap/blob/master/preview-programs/zz_archive/eks-windows-preview/windows-server-IIS.yaml

## work well 
kubectl apply -f https://raw.githubusercontent.com/aws/containers-roadmap/master/preview-programs/zz_archive/eks-windows-preview/windows-server-IIS.yaml

kubectl exec -it windows-server-iis-66bf9745b-xsbsx powershell

kubectl exec -it windows-server-iis-6c68545d57-7t62w powershell


Invoke-WebRequest -Uri https://aws.amazon.com/blogs/aws/ -UseBasicParsing

exit

kubectl get svc windows-server-iis-service


http://ae585f56ccf404913a40aec4a2868226-1688949653.ap-northeast-2.elb.amazonaws.com/default.html

```

### HPA

1. Metric Server 설치 

https://github.com/kubernetes-sigs/metrics-server/releases


```
# not work
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.4.2/components.yaml
kubectl delete -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.4.2/components.yaml

```

```
# work well
kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.3.7/components.yaml
kubectl get pods -n kube-system

kubectl apply -f https://github.com/kubernetes-sigs/metrics-server/releases/download/v0.3.6/components.yaml
kubectl get pods -n kube-system

```

```
kubectl apply -f kube-manifests/
kubectl get pods 
kubectl get svc
```
### 외부 IP 확인 명령어 
```
kubectl get nodes -o wide
```
15.165.161.144:31231


브라우저 확인 
15.165.161.144:31231

2. 
```
kubectl get deploy
kubectl autoscale deployment demo-deployment --cpu-percent=30 --min=1 --max=15
kubectl autoscale deployment hpa-demo-deployment --cpu-percent=30 --min=1 --max=15
kubectl get deploy

kubectl describe hpa/hpa-demo-deployment 

```
### Autoscale 조건 확인 
```
kubectl get horizontalpodautoscaler.autoscaling/hpa-demo-deployment




```
