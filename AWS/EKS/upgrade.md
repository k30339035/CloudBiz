- https://docs.aws.amazon.com/ko_kr/eks/latest/userguide/update-cluster.html
```
kubectl cluster-info

kubectl version 

kubectl get pods -o wide 

compute -> Node group update 

kubectl get pods -o wide 
## node 변경 됨 

kubectl get nodes 
## 노드 교체 

kubectl get ing 

kubectl set image daemonset.apps/kube-proxy -n kube-system kube-proxy=602401143452.dkr.ecr.ap-northeast-2.amazonaws.com/eks/kube-proxy:v1.16.8

kubectl get pod -n kube-system -l k8s-app=kube-dns

kubectl describe deployment coredns --namespace kube-system | grep Image | cur -d "/" -f 3 

kubectl describe deployment coredns --namespace kube-system | grep Image | cur -d "/" -f 2



```