---
date: '2020/3/4 13:46:25'
tags:
  - Docker
categories:
  - Docker
thumbnail: ''
permalink: ''
title: Connecting MySQL Container and PHP Container
---

PHP 컨테이너와 MySQL 컨테이너 연동해보기

<!-- more -->

* `cd /home/ubuntu/example`
* `ls`
* `sudo vi Dockerfile`
* RUN 밑에
```
# Connect PHP & MYSQL
RUN apt-get install -y php5.6-mysql
```
:wq!
* `docker build -t example .`

<br>

도커 이미지가 만들어졌으니, 이미지를 이용해서 컨테이너로 띄운다
* `docker images`
* `docker run -p 80:80 -v /home/ubuntu/example/html:/var/www/html example`

<br>

터미널을 하나 더 만들어서 php문서 작업
* `cd /home/ubuntu/example/html`
* `ls`
* `cat index.php`
* `sudo vi index.php`

<br>

문서작업이 많으면 Jupyter에서 직접 작업해도 된다.
* php를 mysql에 연결하기 위한 php문법
```
<?php
    $conn = mysqli_connect(
        '[mysql IPAddress]',
        'test',
        'password',
        'TEST',
        '9876'
    );
    if(mysqli_connect_errno()){
        echo "Failed to connect to MySQL: ".mysqli_connect_error();
    }
    $sql = "SELECT VERSION()";
    $result = mysqli_query($conn, $sql);
    $row = mysqli_fetch_array($result);
    print_r($row["VERSION()"]));
?>
```


<br>
출처 : 동빈나 youtube


