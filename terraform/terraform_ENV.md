## 

## terraform for AWS
```
terraform init 

$ export AWS_ACCESS_KEY_ID="myaccesskey"
$ export AWS_SECRET_ACCESS_KEY="mysecretkey"
terraform plan

terraform plan -destroy 
terraform destroy 


cd modules/networking
touch variables.tf
1. variables 
touch main.tf
2. main.tf 

3. touch output.tf

cd ~/terraform/staging
touch _main.tf
touch variables.tf
cd ~/terraform/staging
terraform get
terraform plan


touch terraform.tfvars

terraform apply

########### Web 
cd ~/terrform/modules/web

touch main.tf

mkdir files
touch files/user_data.sh
```

## resources
```
resource "<provider> <resource_type>" "name" {
    config options...
    key="value"
    key2 = "another value" 
}
```

## terraform 명령어
```
terraform state list
terraform state show aws_

```

## terraform 결과 출력 
```
terraform output 
```

## terraform server 삭제
```
terraform destroy -target aws_instance.web-server-instance 
terraform apply -target aws_instance.web-server-instance 
````


## terraform variable
```
terraform apply -var "subnet_prefix=10.100.100.0/24" 

terrform apply -var-file example.tfvars 
```


## Terraform Troubleshooting
1. Spot Instance 사용 후 Spot 이 먼저 종료될 경우 네트워크 리소스 삭제 되지 않는 현상
```
aws_subnet.subnet-uno: Still destroying... [id=subnet-0f43ac090d6ba9360, 19m10s elapsed]
aws_subnet.subnet-uno: Still destroying... [id=subnet-0f43ac090d6ba9360, 19m20s elapsed]
aws_subnet.subnet-uno: Still destroying... [id=subnet-0f43ac090d6ba9360, 19m30s elapsed]
aws_subnet.subnet-uno: Still destroying... [id=subnet-0f43ac090d6ba9360, 19m40s elapsed]
aws_subnet.subnet-uno: Still destroying... [id=subnet-0f43ac090d6ba9360, 19m50s elapsed]
aws_subnet.subnet-uno: Still destroying... [id=subnet-0f43ac090d6ba9360, 20m0s elapsed]
╷
│ Error: Error waiting for internet gateway (igw-0690192e95f6b417a) to detach: timeout while waiting for state to become 'detached' (last state: 'detaching', timeout: 15m0s)     
│
│
╵
╷
│ Error: error deleting subnet (subnet-0f43ac090d6ba9360): timeout while waiting for state to become 'destroyed' (last state: 'pending', timeout: 20m0s)

```


## Ubuntu 설치 
```
#sudo wget https://releases.hashicorp.com/terraform/0.12.18/terraform_0.12.18_linux_amd64.zip
#sudo unzip terraform_0.12.18_linux_amd64.zip

sudo wget https://releases.hashicorp.com/terraform/1.0.3/terraform_1.0.3_linux_amd64.zip
sudo unzip terraform_1.0.3_linux_amd64.zip
sudo mv terraform /usr/local/bin/
terraform -v
```
