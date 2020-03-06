---
date: '2020/3/3 22:46:25'
tags:
  - Docker
  - AWS
categories:
  - Docker
  - AWS
thumbnail: ''
permalink: ''
title: Install Docker on AWS EC2 and run the web server through Dockerfile
---

Docker Tutorial 2

<!-- more -->

__주피터에 도커 설치하기__

<br>

* `df -h`  : 메모리가 어느정도 남았는지 체크
* `sudo apt update` : 설치는 apt를 이용해서 하기 때문에 먼저 apt 업데이트 명령 수행
* `sudo apt install apt-transport-https`  : 유틸 설치
* `sudo apt install ca-certificates`  : 유틸 설치
* `sudo apt install curl` : 유틸설치, 특정한 웹사이트에서 어떠한 데이터를 다운로드 받을 때 쓰는 것
* `sudo apt install software-properties-common`

<br>

* `curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -`  : curl을 이용해서 실제로 도커를 설치하기 위해 gpg내용을 다운로드 받고 그 내용을 apt기능을 위한 리스트에 추가할 수 있도록 함.

<br>
  
* `sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu bionic stable"`  : 도커는 레포지터리에서 다운로드 가능, 우분투 18.04버전에 맞는 도커를 다운로드 해야함.
* `sudo apt update`

__이것으로 apt-list에 docker를 다운로드 받기 위한 경로가 추가되었다__

<br>

__이제 실제로 도커를 다운로드 받는다__

* `apt-cache policy docker-ce`
* `sudo apt install docker-ce`  : 도커는 설치하게 되면 시스템 서비스로 등록되기 때문에 언제 어디서든 이용가능

<br>

* `sudo systemctl status docker`  : 도커 서비스 상태 확인
* `q` : 눌러서 원래로 돌아옴
* `docker pull hello-world`  : docker의 *pull* 명령은 특정한 서버파일 자체를 이미지 형태로 다운로드 받을 수 있게 해줌
* `docker images` : 이미지 확인

<br>

__다운로드 받은 이미지를 실제 컨테이너로 만들기__

* `docker run hello-world`  : hello-world 컨테이너를 띄움. 즉 이 명령을 내리자마자 우리의 서버 위에 하나의 서버가 별도로 더 생성되어 서버가 동작하고 작업이 종료된 것.
* `docker ps -a` : 어떤 컨테이너가 동작했는지 확인가능

<br>

__컨테이너 삭제__

* `docker rm 컨테이너아이디`  : docker ps -a로 아이디 확인 가능
* `docker images` : 삭제를 하더라도 이미지 파일은 남아있음


<br>

### Docker 파일을 직접 작성해서 하나의 서버 이미지를 직접 만들기

* `ls`  : 현재 디렉토리의 파일에 대한 리스트를 보여줌
* `cd /home/ubuntu`
* `ls`
* `mkdir example`
* `cd example`
* `ls`
* `sudo vi Dockerfile`

<br>

__도커파일 작성__
```
FROM ubuntu:18.04
MAINTAINER ByungJae Chung <jbj828@naver.com>

RUN apt-get update //해당 서버가 웹 서버를 구동할 수 있도록 설정
RUN apt-get install -y apache2 # Install Apache web server (Only 'yes') // y옵션 넣는 이유는 설치할 때 용량 크면 설치 할 것인지 물어본다. docker이미지 만들 때는 행동예측이 어렵기에 무조건 설치한다는 뜻

EXPOSE 80 # Open HTTP Port  // 아파치 웹서버의 기본 포트인 80번 포트를 열 수 있도록 만들어준 것

CMD ["apachectl", "-D", "FOREGROUND"] //특정한 컨테이너는 작업 수행하자마자 바로 종료되기 때문에 아파치가 항상 구동중인 상태로 만들기 위해 명시
```
`:wq!`

<br>

__Build Docker File__

도커 이미지를 만드는 것
* `ls`
* `docker build -t example .`
* `docker images` : 확인
    * 만약 error가 났다면 error message 보고 docker file 들어가서 수정하고 다시 build하기

<br>

__만든 이미지를 활용해 실제 웹서버 컨테이너 구동__

* `docker run -p 80:80 example` : 왼쪽은 현재 우리 서버의 포트를 넣고 오른쪽엔 컨테이너의 포트 넣기 - 호스트의 80번 포트와 컨테이너의 80번 포트가 연결됨, 실제로 호스트 서버의 80번 포트에 접속했을 때 사용자는 컨테이너의 80번 포트에 접속할 수 있게 됨

<Br>

* 이후 AWS -> 보안그룹/launch-wizard-1 -> 편집 ->
  규칙추가 -> 유형:HTTP
* 서버의 80번 포트로 검색해봄 (주소창에서 주소명만 복사해서 `:80` 붙임) 