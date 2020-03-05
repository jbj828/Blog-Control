---
date: '2020/3/5 10:46:25'
tags:
  - Docker
categories:
  - Docker
thumbnail: ''
permalink: ''
title: Connecting Dockerhub and Github
---

Dockerhub와 Github 연동하기

<!-- more -->

### Dockerhub?
  * 도커의 이미지 용량은 메가에서 기가단위까지 거대하다. 이러한 큰 용량의 이미지를 Dockerhub를 통해 공개이미지로서 무료로 관리할 수 있게 만든 것.

### Dockerhub와 Github 연동 이유?
  * 깃허브의 특정한 프로젝트에 있는 도커파일을 도커허브 측에서 자동으로 빌드를 수행해준다. 소스코드를 수정해서 깃허브에 업로드만 하면 자동으로 도커허브에서 그것을 감지해서 도커파일을 이용해 다시 빌드를 수행해주기 때문에 매우 쉽게 도커이미지를 컨테이너로 띄울 수 있게 된다.

### 과정

* Dockerhub에서 Create a Repository
* Github과 연동하여 해당 github repository와 연동
* dockerhub에서 build 진행

<br>

* 빌드가 완료되면 우리의 서버에서 현재 구동 중인 모든 도커이미지를 제거해도 됨.
* ```docker rm -f `docker ps -a -q` ``` : 컨테이너 삭제
* ```docker rmi -f `docker images` ```  : 이미지 삭제
* `docker ps -a` : 모든 이미지와 컨테이너 제거 확인


<br>

__ReadMe 파일 만들기__

* Github에서 readme 파일 만들기
```
# Docker 실전 연습 예제입니다.
### Installation
<pre>
cd /home
git clone https://github.com/jbj828/Docker-Practice
cd Docker-Practice
</pre>
### Run
<pre>
# Login For Private Docker Repository
docker login
docker pull jbj828/docker-practice
docker run -p 80:80 -v /home/Docker-Practice/Project:/var/www/html jbj828/docker-practice
</pre>
```

<br>

__Readme파일에서 프로젝트 경로안에 index.html 파일이 존재하도록 설정했기 때문에, 깃 프로젝트의 구성을 바꿔준다__

* `ls`
* `cd /home/ubuntu`
* `ls`
* `cd Docker-Practice/`
* `mkdir Project`
* `mv index.php ./Project/index.php`
* `cd Project`
* `ls`  : 이제 Project 폴더안에 index.php가 존재

<br>

* `cd ..`
* `git add .`
* `git commit -m "Change index.php path"`
* `git push`
* Readme.md파일을 수정했기 때문에 소스코드 충돌 메세지가 뜬다. 이럴 때는 pull 먼저 진행하면 된다
* `git pull`
* Merge관련 메세지 나오면 그냥 밖으로 나옴
* `git push`
  




<br>
출처 : 동빈나 youtube
