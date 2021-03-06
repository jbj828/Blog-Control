---
date: '2020/3/3 14:46:25'
tags:
  - Docker
  - AWS
categories:
  - Docker
  - AWS
thumbnail: ''
permalink: ''
title: Install AWS EC2 Instance and Jupyter Notebook(환경설정) 
---

Docker Tutorial 1

<!-- more -->

### AWS EC2 인스턴스 생성 및 접속

<Br>

  1. AWS에서 ubuntu 18버전으로 먼저 인스턴스 생성
  2. key pair는 관리자만 실행가능하도록 환경설정
      * 오른쪽마우스 -> 속성 -> 보안 -> 고급 -> 상속사용
      * key pair는 무조건 C드라이브 안에 넣기
  3. 명령프롬프트 관리자 권한으로 실행
      * cd 키페어 위치
      * aws 홈페이지 가서 연결버튼 누름
      * ssh 링크 복사해서 cmd에 복사
      * 연결완료 되면 pwd 입력 -> `현재 서버위치`

<br>

### Jupyter Notebook 설치, HTTPS 적용, 시스템 서비스 설정하기

<br>

  * __Jypyter Notebook__ : 콘솔창이 아닌 웹브라우저 환경에서 해당 서버에 바로 접근해서 해당 서버를 관리할 수 있도록 해주는 유틸
      1. sudo apt-get update  :  apt-get명령의 업데이트
      2. sudo apt-get install python3-pip
            * ubuntu 18.04버전엔 pyhton3가 디폴트로 깔려있다. 그래서 python3는 깔 필요없고 파이썬 관련 패키지를 설치할 수 있도록 도와주는 python3-pip를 설치
      3. sudo pip3 install notebook  : jupyter notebook 설치
   
   <br>

   만들어진 주피터를 통해서 서버의 외부에서 해당 서버에 웹브라우저를 이용해서 접속할 수 있도록 된 것. 이제 주피터 접속을 위한 비밀번호 설정을 해줘야 함.
      <br>

      1. python3
      2. from notebook.auth import passwd
      3. passwd()   :  패스워드 함수 호출(비밀번호를 설정하겠다는 의미)
      4. 나온 hash값 복사해서 메모장 붙여넣기
      5. exit()

    <br>

    서버에서 주피터 노트북을 실행해서 외부에서 접속 했을 때 비밀번호를 입력해야 서버에 접속할 수 있도록 하기 위해 주피터 환경설정 진행

  <br>

      1. jupyter notebook --generate-config    : 환경설정 파일 만듦
      2. sudo vi 바로 윗줄 환경설정 위치값 붙여넣기
            * ex)  sudo vi /home/ubuntu/.jupyter/jupyter_notebook_config.py         
      3. 제일 밑으로 내려가서 'a'눌러서 수정모드로 변환
      4. c = get_config()
      5. c.NotebookApp.password = u'sha1 : 복사해둔 해시값'
      6. c.NotebookApp.ip = '172.31.14.123'    이거는 화면 제목 창에 나온 주소 그대로 적으면 됨
      7. c.NotebookApp.notebook_dir = '/'
      8. esc버튼 누르고
      9. :wq!

    <br>

      1. sudo jupyter-notebook --allow-root   : 주피터 노트북을 루트권한을 가진 상태로 실행
         * 8888포트로 주피터 노트북이 열린 것 확인가능

    <br>

      1. AWS 웹사이트 다시 돌아가서 
      2. '설명'란 안에 있는
      3. '보안그룹' 의 'launch-wizard-1' 클릭
      4. '인바운드'
      5. '편집'
      6. '규칙추가'
      7. 포트범위 : 8888
      8. 소스 : 0.0.0.0/0  (두 개 다)

    <br>

       1. 인스턴스 화면으로 돌아옴
       2. '설명'란에 'IPv4 퍼블릭 IP'에 있는 주소 복사
       3. 주소창에 붙이고 ':8888' 붙여서 엔터
   
    <br>

    * 더 이상 ssh가 필요하지 않고 바로 웹 브라우저에서 해당 서버에 접속할 수 있어서 매우 편리해졌다. 하지만 우린 주피터를 항상 실행할 수 있는 상태로 만들고 싶다

<br>

  1. 다시 cmd로 돌아와서 'ctrl+z'로 해당 서버 종료 
  2. bg   : background상태에서 돌아가게 함
  3. disown -h   : 소유권 포기
        * 이제 주피터 노트북이 항상 실행 중인 상태가 됨
<br>

언제 어디서나 웹브라우저로 서버를 관리할 수 있게 됨
하지만 지금의 주피터 노트북은 ssl인증서가 적용되지 않은 상태라서 통신과정에서 상당히 위험.
<br>

그러므로 https를 적용해야됨

<br>

  1. sudo netstat -nap | grep 8888  : 현재 8888포트가 실행 중인 피아이디를 알 수 있다
  2. sudo kill -9 '파이썬 옆 숫자'
      * 해당 주피터 노트북을 종료시킬 수 있음
      * 웹브라우저에서 새로고침하면 적용 안 됨

<br>

### HTTPS 적용

<br>

*환경설정에 개인키와 공개키를 넣는 작업*

<br>

  1. cd /home/ubuntu
  2. pwd
  3. mkdir ssl
  4. cd ssl
  5. sudo openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout "cert.key" -out "cert.pem" -batch     *개인키 공개키 생성*
  6. ls
  7. sudo vi 바로 윗줄 환경설정 다시 열기
  ex)  sudo vi /home/ubuntu/.jupyter/jupyter_notebook_config.py 
    *방향키 위쪽 버튼 눌러서 찾기*
  8. 'a'눌러서 시작
  9. c.NotebookApp.certfile = u'/home/ubuntu/ssl/cert.pem'
  10. c.Notebop.keyfile = u'/home/ubuntu/ssl/cert.key'
  11. esc버튼
  12. :wq!

<Br>

  1. sudo jupyter-notebook --allow-root   *주피터 노트북 실행*
  
      * https://주소:8888 넣으면 ssl이 적용이 된 상태로 서버에 접속가능
      * 여기까지가 우리 주피터 노트북에 ssl(인증서)까지 적용한 것

<br>

### 시스템 서비스 설정하기

  * 서버가 재부팅되면 자동으로 주피터 노트북이 실행이 안됨. 그래서 주피터 노트북을 시스템 서비스로서 등록시켜서 재부팅해도 자동실행 가능하도록 함.

<br>

  1. 먼저 ctrl+c 눌러서 서버 구동 종료
  2. which jupyter-notebook    *주피터 노트북 실행파일의 경로를 찾기 위한 명령*
  3. sudo vi /etc/systemd/system/jupyter.service    *시스템 서비스로 등록하기 위해 서비스 파일 작성*
  4. *서비스 파일 작성*
  ```
  [Unit]
  Description=Jupyter Notebook Server

  [Service]
  Type=simple
  User=ubuntu  //기본적으로 AWS ec2에 ssh명령을 이용해서 접속할 땐 ubuntu계정으로 접속하기 때문
  ExecStart=/usr/bin/sudo /usr/local/bin/jupyter-notebook --allow-root --config=/home/ubuntu/.jupyter/jupyter_notebook_config.py

  [Install]
  WantedBy=multi-user.target
  ```
  :wq!입력

  <br>

  *주피터 노트북을 구동시키도록 함*
  1. sudo systemctl daemon-reload *데몬을 다시 로드할수 있도록*
  2. sudo systemctl enable jupyter *주피터서비스를 사용가능하도록 만듦* 
  3. sudo systemctl start jupyter  *항상 실행상태가 되도록 만듦*

<br>

  * 실행 중인 주피터 서비스를 확인
      1. sudo systemctl status jupyter
      2. 확인 후 'q'눌러서 상태확인 마침
   
   <br>

  * 주피터 서비스를 다시 시작하고자 할 때
      1. sudo systemctl restart jupyter

<br>

이제 aws ec2를 재부팅하더라도 주피터 노트북 서비스가 자동으로 실행되어서 구동중인 상태가 될 수 있도록 처리한 것. 항상 주피터를 이용해서 해당 서버에 접속해 관리할 수 있도록 된 것.



