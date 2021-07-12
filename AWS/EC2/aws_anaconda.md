## Python 32bit
- Path 추가 
```
C:\tools\Anaconda3\Scripts
C:\tools\Anaconda3\Library\bin
```

- 설치 후 64bit를 32bit 변경
```
set CONDA_FORCE_32BIT=1
conda create -n py38_32 python=3.8 anaconda # 설치 진행 - 시간이 좀 걸림..
conda env list 
activate py38_32 
```