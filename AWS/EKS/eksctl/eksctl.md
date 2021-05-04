```
apiVersion: eksctl.io/v1alpha5
kind: ClusterConfig

metadata:
  name: cluster-in-existing-vpc
  region: ap-northeast-2

vpc:
  cidr: 10.10.0.0/16
  clusterEndpoints:
    publicAccess: true
    privateAccess: true 
  subnets:
    public: 
      eu-north-1a: { id: subnet-0b88246b38ebada6d }
      eu-north-1b: { id: subnet-040526aafbb673150 }
      eu-north-1c: { id: subnet-030bc9a9e01ec183e }
    private:
      eu-north-1a: { id: subnet-054ac295729f5aa66 }
      eu-north-1b: { id: subnet-0e350968cb6bddfe4 }
      eu-north-1c: { id: subnet-0a5b73d8be57a05c3 }

nodeGroups:
  - name: ng-1-workers
    labels: { role: workers }
    instanceType: m5.large
    desiredCapacity: 2
    volumeSize: 30
    privateNetworking: true
    ssh:
        allow: true
        publicKeyName: corpseoul 
  - name: ng-2-builders
    labels: { role: builders }
    instanceType: m5.large
    desiredCapacity: 2
    privateNetworking: true
    ssh:
        allow: true
        publicKeyName: corpseoul
    iam:
      withAddonPolicies:
        imageBuilder: true
cloudWatch:
    clusterLoggin:
      enableTypes: ["audit", "authenticator", "controllerManager"]

```
```
eksctl create cluster -f cluster.yaml
```

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