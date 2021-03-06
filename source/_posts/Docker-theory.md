---
date: '2020/3/3 10:46:25'
tags:
  - Docker
categories:
  - Docker
thumbnail: ''
permalink: ''
title: What is Docker?
---

Primary theory of Docker

<!-- more -->

출처 : 공부목적으로 [Subicura's Blog](https://subicura.com/)를 참조했습니다.

<br>

### Docker
  * 컨테이너를 관리하는 플랫폼
  * 컨테이너 기반의 오픈소스 가상화 플랫폼
      * 다양한 프로그램, 실행환경을 컨테이너로 추상화하고 동일한 인터페이스를 제공하여 프로그램의 배포 및 관리를 단순하게 해줍니다. 백엔드 프로그램, 데이터베이스 서버, 메시지 큐등 어떤 프로그램도 컨테이너로 추상화할 수 있고 조립PC, AWS, Azure, Google cloud등 어디에서든 실행할 수 있습니다.
      * 즉, 컨테이너는 격리된 공간에서 프로세스가 동작하는 기술입니다.

__Difference between VM and Docker__

<br>

{% asset_img "docker1.png" 500 300 "VM and Docker" %}


<br>

#### Image
  
  '컨테이너 실행에 필요한 파일과 설정값등을 포함하고 있는 것'

  * 이미지는 컨테이너 실행에 필요한 파일과 설정값등을 포함하고 있는 것으로 상태값을 가지지 않고 변하지 않습니다(Immutable). 컨테이너는 이미지를 실행한 상태라고 볼 수 있고 추가되거나 변하는 값은 컨테이너에 저장됩니다. 같은 이미지에서 여러개의 컨테이너를 생성할 수 있고 컨테이너의 상태가 바뀌거나 컨테이너가 삭제되더라도 이미지는 변하지 않고 그대로 남아있습니다.
  * 말그대로 이미지는 컨테이너를 실행하기 위한 모든 정보를 가지고 있기 때문에 더 이상 의존성 파일을 컴파일하고 이것저것 설치할 필요가 없습니다. 이제 새로운 서버가 추가되면 미리 만들어 놓은 이미지를 다운받고 컨테이너를 생성만 하면 됩니다. 한 서버에 여러개의 컨테이너를 실행할 수 있고, 수십, 수백, 수천대의 서버도 문제없습니다.
  * 도커 이미지는 Docker hub에 등록하거나 Docker Registry 저장소를 직접 만들어 관리할 수 있습니다. 현재 공개된 도커 이미지는 50만개가 넘고 Docker hub의 이미지 다운로드 수는 80억회에 이릅니다. 누구나 쉽게 이미지를 만들고 배포할 수 있습니다.

<br>

{% asset_img "docker2.png" 500 300 "Docker Image" %}



