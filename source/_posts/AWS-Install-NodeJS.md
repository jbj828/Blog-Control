---
date: '2020/3/6 13:46:25'
tags:
  - AWS
categories:
  - AWS
thumbnail: ''
permalink: ''
title: Install NodeJS on Ubuntu Server
---

Ubuntu Server에 NodeJS 실습환경 구축

<!-- more -->


### NodeJS 설치


#### 설치
참고 : [NodeSource](https://github.com/nodesource/distributions/blob/master/README.md)

PPA를 통하여 최신 버전을 가져온다

`curl -sL https://deb.nodesource.com/setup_13.x | sudo -E bash -`


우분투에 NodeJS를 설치
`sudo apt-get install -y nodejs`


NodeJS와 NPM이 잘 깔렸는지 확인
`node -v`
`npm -v`

NPM이 제 기능을 하게 하기 위해 다음 명령어 실행(이거 없으면 npm install 시 에러 날 확률이 높다)
`sudo apt-get install build-essential`

#### NodeJS Application 생성

`cd /{디렉토리 이름a}`
`ls -al`

`sudo mkdir {디렉토리 이름b}`
`cd {디렉토리 이름b}`

`sudo chown ubuntu .` : 오너를 ubuntu로 바꾼다

<br>

__디렉토리에 웹 애플리케이션 생성__

`npm init` 
`ls -al`

__ExpressJS 프레임웍 설치__

`npm install express`
`ls -al`
`ls -al node_modules/`

__웹 애플리케이션 구동__

`vi app.js`

```
var express = requier('express')
var app = express();
app.get('/', function(req, res){
      res.send('Hello World');
});
app.listen(80, function(){
      console.log('Connected 80');
});
```

`sudo node app.js`

`{IP번호}:80` 을 브라우저 주소에 입력