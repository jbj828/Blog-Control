---
date: '2020/3/4 16:46:25'
tags:
  - Docker
categories:
  - Docker
thumbnail: ''
permalink: ''
title: Posting Docker project to Github
---

Github에 Docker 프로젝트 올리기

<!-- more -->

* Github에 새로운 Repository 생성

<br>

*AWS EC2의 ubuntu 18.04버전에는 자동으로 깃 프로그램이 설치되어 있어 바로 사용가능*

#### 만들어진 Repository와 우리의 서버와 연동시키기 위해 클론부터 함

* `cd /home/ubuntu`
* `git clone 깃허브 레포지터리 복사`
* `ls`
* `cd 레포지터리 이름`

<br>

이제 깃프로젝트에 소스코드를 올리면 됨
* `sudo vi 레포지터리이름`
* `:wq!`  : 그냥 파일 저장할 수 있도록 해주고 주피터를 이용해서 소스코드 작성
* 이전에 작성한 example폴더의 Docker 파일 그대로 복사 붙여넣기(이렇게 깃 프로젝트를 만들었다)

* 주피터 홈에서 new -> text file   하나의 php 코드도 만들어줌
* 이름은 index.php
* 내용은 이전에 작성했던 index.php내용 그대로 넣음

<br>

__이제 실제로 깃에 올려보자__

* `ls`
* `cat Dockerfile` : 내용확인
* `cat index.php` : 내용확인
* `git add .`
* `git commit -m "이름"`
* `git push`
 


<br>
출처 : 동빈나 youtube
