### paramiko 설치 - Ubuntu 18.04

```
sudo apt-get update -y 
python -V
# 3.6.9 
sudo apt install python3.8 -y
python -V
# 3.6.9
python3.8 -V
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.6 1
sudo update-alternatives --install /usr/bin/python3 python3 /usr/bin/python3.8 2
sudo update-alternatives --config python3
화면 2 선택 
python3 -V
# 3.8.0
sudo apt-get install python3-pip -y
mkdir -p build/python/lib/python3.8/site-packages
pip3 install paramiko -t build/python/lib/python3.8/site-packages/ --system 
### error 아래 명령어 실행 
sudo -H pip install --upgrade --ignore-installed pip setuptools
pip3 install paramiko -t build/python/lib/python3.8/site-packages/
sudo apt install zip -y
cd build
zip -r packageParamiko.zip .
sudo apt install awscli -y 
```
## lambda 메뉴에서 왼쪽 아래 Layers 선택 
```
layer 이름: packageParamiko 
link URL: https://sungsukms.s3.ap-northeast-2.amazonaws.com/packageParamiko.zip
runtimes 선택 

```


### install requests
1. AWS Lambda Config
2. Building the deployment pacakge 
3. Scheduling cron jobs with AWS Cloudwatch 

```python
import requests

def call_site():
    r = requests.get("www.naver.com")
    if r.status_code == 200:
        return "It was connected"
print(call_site())
```

### lambda handler 
test.call_site

pip3 install requests -t . 
pip3 install setuptools_rust -t .
pip3 install cryptography -t .

pip3 install paramiko -t .
zip -r compressed.zip /path/to/dir


- EC2
```
### Shinsegae Cloud Biz Team. All right reserved.
#### All region and Instance information ### 단일 계정 EC2 확인 
import boto3
session = boto3.session.Session(profile_name="default")
ec2_cli = boto3.client('ec2')
for region in ec2_cli.describe_regions()["Regions"]:
    ec2_cli = session.client(service_name="ec2", region_name=region["RegionName"])
    print(region["RegionName"])
    try:
        response = ec2_cli.describe_instances()
        for reservation in response["Reservations"]:
            for instance in reservation["Instances"]:
                if 'terminated' == str(instance.get('State').get('Name')) or 'pending' == str(instance.get('State').get('Name')):
                    print("############" + instance.get('State').get('Name'))
                else:
                    try:
                        for tags in instance['Tags']:
                            if tags["Key"] == 'Name':
                                vTag = tags["Value"]
                                print(vTag)
                                print(instance.get('PrivateIpAddress'))
                                print(instance.get('InstanceId'))
                                print("#####################################")
                            else:
                                print("No Tag!!!")
                                print(instance.get('PrivateIpAddress'))
                                print(instance.get('InstanceId'))
                                print("************************************")
                    except Exception as e:
                        print(e)
     except Exception as e1:
        print(e1)
```
- CloudWatch 
```
```

-CloudTrail 

```

```
