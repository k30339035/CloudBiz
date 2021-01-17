# Git 

## git 명령어 요약
```
git init
git add <file>
git status
git commit
git push
git pull
git clone
```

### git 버전
```
git --version
```
### 로컬 저장소 초기화 
```
git init
```

### 인덱스에 파일 추가
```
git add <file>
git add *.html

```
### 전체 파일 추가 - .
```
git add .
```

#### untrack 파일 - (인덱스에서 제외)
```
git remove --cached index.html app.js 
```
### git 파일 상태 
```
git status 
```
### git 인덱스에 커밋
```
git commit 
```

파일 내용 수정
```
# Initial commit => Initial commit 
```

### 추가 파일 확인 
```
git commit -am "web"
```
### 파일변경 
```
git commit -m "app.js"
```
### 파일 무시
```
touch .gitignore 
```
#### .gitignore 파일내에 파일명을 기술 

```
log.txt
/images
/external
*.txt
```

### 사용자 
```
git config --global user.name koreasungsu
```
### E-mail 추가 
```
git config --global user.email sungsu.kim@shinsegae.com 
```
### 적용 확인 
```
git config --global -e 
```
아래 정보 생성합니다. 
<p align="center">
<a url="https://www.github.com/">  <img src="https://github.com/k30339035/CloudBiz/blob/main/git/gitconfig.JPG"> </a>
</p>


### 커밋
```
 git commit -am "web"
```
### 원격 저장소 보내기 
```
git push 
```
<p align="center">
<a url="https://www.github.com/">  <img src="https://github.com/k30339035/CloudBiz/blob/main/git/githublogin.JPG"> </a>
</p>

<p align="center">
<a url="https://www.github.com/">  <img src="https://github.com/k30339035/CloudBiz/blob/main/git/github_auth.JPG"> </a>
</p>


<p align="center">
<a url="https://www.github.com/">  <img src="https://github.com/k30339035/CloudBiz/blob/main/git/authsuccess.JPG"> </a>
</p>


```
git config --global credential.useHttpPath true 
git config --global -e 
```
### 원격 저장소에서 다운
```
git pull
```

### 원격 저장소 복사
```
git clone 
```

## git branch 
```
git branch login 
git status
git commit -m 'another branch'
```
### git branch 변경
```
git checkout login 
Switched to branch 'login'
M       app.js
M       index.html
```
###
```
git add .
git commit -m 'login form'
```
### git master 변경
```
git checkout master 

```
### git merge
```
git merge
```
###  "Added login" 파일 추가   
```
Added login 
```
