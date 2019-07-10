---
title: 내용정리-Gitflow
date: 2019-07-10 10:47:33
tags: ["Gitflow"]
categories:
- 내용정리
---
# Gitflow

### 1. Gitflow 설치  
```shell
apt-get install git-flow
```

### 2. Gitflow 초기화  
```shell
git flow init
```

### 3. feature branch
master branch에서 develop branch를 만든다.   
기능 개발은 develop branch에서 한다.  
```shell
git flow feature start feature/name
```
develop branch에서 feature/name branch를 생성하고 feature branch로 전환한다.  

**_flow feature finish_**
```shell
git flow feature finish feature/name
```
feature/name branch를 develop branch로 merge후 해당 feature branch가 삭제되며 develop branch로 전환된다.   

**_merge&delete_**
finish를 하면 깔끔하게 merge와 delete가 같이 되지만 실수로 merge를 했을 경우, branch를 따로 삭제해야 한다. 삭제가 필수는 아니지만 보통 기능구현이 끝난 branch는 삭제하는 걸로 알고 있다.  
```shell
git checkout develop
git merge origin develop
git branch -d feature/name
git remote prune origin
git push origin :feature/name
```