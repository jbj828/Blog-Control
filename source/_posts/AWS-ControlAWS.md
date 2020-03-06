---
date: '2020/3/6 11:46:25'
tags:
  - AWS
categories:
  - AWS
thumbnail: ''
permalink: ''
title: The method of Controlling AWS
---

AWS를 제어하는 방법들

<!-- more -->


### Management Console

  * EC2를 생성하고 삭제하고 목록을 열람하는 기능을 제공
  * 이러한 방식을 GUI(Graphical User Interface)라고 한다.
  
### CLI(Command Line Interface)

  * 명령어를 입력하여 컴퓨터를 제어하는 방식
  * `aws ec2 describe-instances`  : Management Console에 나온 내용과 동일한 내용이 텍스트 형식으로 콘솔에 나타난다.
  * 익숙해지면 GUI 방식보다 편리하다.
  * 일련의 연속적인 작업을 한꺼번에 실행가능
    * `aws ec2 describe-instances | grep PublicIp`  : aws의 목록을 알아낸 후 PublicIp만의 텍스트를 추출한 것

### SDK(Software Development Kit)

  * 프로그래밍을 통해 좀 더 섬세한 제어가 가능하도록 하기 위해 AWS에서 제공하는 도구
  * 각각의 언어별로 다른 버전
  * 언어별로 AWS 인프라를 제어할 수 있게 하는 개발 도구
  * 자신이 사용할 수 있는 언어를 통해 AWS 인프라를 편리하게 제어 가능

### API(Application Programming Interface)

  * Restful API : Web을 통해 AWS의 인프라를 제어하거나 인프라의 상태를 알아낼 수 있는 상태
  * 어떤 언어를 사용하건 상관없이 AWS의 인프라 사용 가능
  * 직접 이용하는 건 복잡, 불편
  * 그래서 SDK를 제공하는 것
  * 직접 사용할 일은 없다.
