---
title: 내용정리-Git편
date: 2019-07-10 10:27:40
tags: ["Git"]
---
# Git 사용법  

### 1. Git 저장소  
#### 디렉토리를 저장소로 만들기 
기존 프로젝트를 Git으로 관리하고 싶을때, 해당 디렉토리로 이동해서 `git init` 명령어로 새로운 Git 저장소를 만든다.
`init`은 .git이라는 하위 디렉토리를 생성한다. 저장소에 필요한 뼈대 파일을 가지고 있다. 

#### 기존 저장소를 받아오기  
```shell
git clone <URL>
```
`clone` 으로 프로젝트의 히스토리를 전부 받아온다. 

#### 저장소에 파일 추가  
```shell
git add <file>
git commit -m "message"
```
Git이 파일을 관리하게 하려면 저장소에 파일을 추가하고 커밋해야 한다. 
`git log`로 커밋 히스토리를 조회할 수 있다. 

### 2. Git status
status|means
--|--
committed<br>(git repository)|데이터가 로컬 데이터 베이스에 안전하게 저장됨
staged<br>(staging area)| 현재 수정한 파일을 곧 commit할 것이라고 표시한 상태 
modified<br>(working directory)| 수정한 파일을 아직 로컬에서 commit 하지 않은 상태 

### 3. Git push
```shell
git push origin master(current branch)
```
commit한 내용은 아직 로컬 저장소 head에 있다. `push`명령어로 원격 저장소에 올린다.  

### 4. branch  
저장소를 새로 만들면 기본적으로 master branch가 만들어진다.  
```shell
git chechout -b featureX
```
`checkout`명령어로 featureX라는 branch를 만들고 featureX로 변경한다. 
```shell
git chechout master
```
master branch로 다시 돌아올 수 있다. 

### 5. Git pull & merge  
```shell
git pull
```
`pull` 명령어로 원격 저장소 변경 내용이 로컬에 fetch,merge가 된다.  
```shell
git merge <other branch>
```
`merge` 명령어로 다른 branch에 있는 변경 내용을 현재 branch에 병합한다.  
```shell
git diff <origin branch> <other branch>
``` 
`diff` 명령어로 변경내용을 병합하기 전에, 어떻게 바꼈는지 비교할 수 있다.  

### 6. Git 되돌리기  
**commit 수정**
```shell
git commit -m "message"
git add <forgottenfile>
git commit --amend
```
`--amend` 옵션으로 커밋을 수정할 수 있다. 
**unstage로 상태 변경**
staging area와 working directory를 넘나드는 방법  
```shell
git add <file>
```
`add` 명령어로 working directory에 있던 파일을 staging area로 옮긴다.  
```shell
git reset HEAD <file>
```
`reset` 명령어로 staged 상태의 파일을 unstaged로 바꿀 수 있다. 

**modified파일 되돌리기**
```shell
git checkout -- <file>
```
`checkout` 명령어 뒤에 파일명이 오면 working directory에서 수정한 파일을 최근 commit한 파일로 되돌릴 수 있다. 수정한 내용은 모두 사라진다. 
