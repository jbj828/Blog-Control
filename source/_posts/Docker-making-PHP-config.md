---
date: '2020/3/4 10:46:25'
tags:
  - Docker
categories:
  - Docker
thumbnail: ''
permalink: ''
title: Making Apache and PHP configuration with Docker Image
---

Docker 이미지로 Apache 및 PHP 개발환경 구축하기

<!-- more -->

아파치 웹서버만 포함되어있는 도커이미지를 더 수정해서 PHP까지 추가해본다. 볼륨을 공유할 수 있도록 해서 PHP 소스코드가 동작할 수 있도록 개발한다.

<br>

__컨테이너 제거__

* `docker ps -a`  : 80번 포트의 컨테이너가 구동 중
* ```docker rm -f `docker ps -a -q` ```  : -f옵션은 컨테이너를 강제 삭제 시킴. docker ps에 -a -q를 붙여서 현재 존재하는 모든 컨테이너 명단을 가져온다.
* `docker ps -a`  : 컨테이너 확인해 본다

<br>

__도커파일 수정__

* `cd /home/ubuntu/example` : 저번에 만든 도커 파일 위치
* `ls` 
* `sudo vi Dockerfile`

* 도커파일에 php 설치 
```
//MAINTAINER 밑에
# Avoiding user interaction with tzdata
ENV DEBIAN_FRONTEND=noninteractive

// 기존 RUN 밑에
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:ondrej/php # For Installing PHP 5.6
RUN apt-get update
RUN apt-get install -y php5.6
```

* `docker build -t example .`
* `docker images`

빌드가 완료되면 기존에 존재하던 이미지는 `none`으로 바뀜. 사용되지 않는 이미지는 삭제한다. 하지만 삭제하고자 할 때 특정한 컨테이너에서 구동 중인 것은 삭제가 진행 안됨. 먼저 컨테이너부터 삭제 진행
* `docker rm -f 컨테이너아이디` : docker ps -a에서 확인가능
* `docker rmi -f d 이미지아이디`  

__Example 레포지터리를 컨테이너에 띄우기__

* `docker run -p 80:80 -v /home/ubuntu/example/html:/var/www/html example`  : 80번 포트를 열고, volume옵션을 열어주어서 마운팅을 진행한다. /home/ubuntu/example/html 과 /var/www/html을 서로 연결해준다. 후자는 php의 소스코드가 놓이는 기본 경로. 
이렇게 마운팅 된 경로는 호스트에다 파일을 넣어주면 자동으로 컨테이너의 해당 경로에 실제로 파일이 놓인 것과 같은 효과를 낸다.
* /html/ubuntu/example/html 의 경로를 복사해 주피터에서 새로운 터미널을 열어 복사한다
* `cd /html/ubuntu/example/html`
* `ls`
  : 이제 이 새로운 터미널에서 html문서나 php문서를 작성하면 이 컨테이너 내부에 있는 php소스코드 경로와 연결이 되기 때문에 실제 웹 서버에 php코드가 놓이는 것과 동일한 효과를 낸다
* 80번 포트에서 새로고침하면 php가 적용 된 문서가 나타난다

__PHP 소스코드 작성__

새로운 터미널에서.
* `sudo vi index.php`
```
<?php phpinfo(); ?>
```
:wq!

* 다시 새로고침하면 컨테이너 안에 설치되어 있는 php환경설정 내용이 등장.


<br>

* php와 apache가 설치된 하나의 image를 직접 만들었기 때문에 이제 docker run 을 통해 이 컨테이너를 띄울 수 있다
* `docker run -p 81:80 -v /home/ubuntu/example/html:/var/www/html example`
* AWS가서 81번도 방화벽을 열어준다


출처 : 동빈나 youtube

