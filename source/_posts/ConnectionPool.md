---
date: '2020/1/20 22:46:25'
tags:
  - database
categories:
  - Database
thumbnail: ''
permalink: ''
title: Connection Pool
---

Connection Pool이란?
  * 동시 접속자가 가질 수 있는 connection을 하나로 모아놓고 관리한다는 개념. 누군가 접속하면 자신이 관리하는 Pool에서 남아있는 Connection을 제공한다. 하지만 남아있는 connection이 없는 경우, 해당 클라이언트는 대기 상태로 전환시킨다. 이후 connection이 다시 pool에 들어오면 대기상태의 클라이언트에게 순서대로 제공한다.
<!-- more -->

  * 즉, 데이터베이스와 연결된 connection을 미리 만들어서 pool 속에 저장해 두었다가 필요할 때 connection을 pool에서 쓰고 다시 pool에 반환하는 기법.



