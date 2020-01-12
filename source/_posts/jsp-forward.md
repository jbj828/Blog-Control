---
date: '2020/1/12 00:10:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: JSP forward action tag
---


다른 페이지로 프로그램의 제어를 이동할 때 사용되는 대표적 두 가지 기술

* respones.sendRedirect() 내장객체
* <jsp:forward> 액션태그

<!-- more -->
  
forward 액션 태그는 다른 페이지로 프로그램의 제어를 이동할 때 사용되는 액션 태그
JSP 페이지 내에 forward 액션 태그를 만나게 되면, 그전까지 출력 버퍼에 저장되어 있던 내용을 제거하고 forward 액션 태그가 지정하는 페이지로 이동한다.

하지만 sendRedirect는 단순히 페이지만 이동 가능하며 정보는 다음 페이지로 전달되지 않는다.


{% codeblock lang:java %}
<jsp:forward page="nextPage.jsp" />

<jsp:forward page="nextPage.jsp"></jsp:forward>

<jsp:forward page='<%=expression + ".jsp"%>' />
{% endcodeblock %}


* forward 액션 태그의 page 속성은 이동할 페이지명을 기술하고 상대경로, 절대경로로 지정할 수 있다.

* forward 액션 태그에서 포워딩되는 페이지에 파라미터 값을 전달할 수 있다.


{% codeblock lang:java %}
<jsp:forward page="abc.jsp">

<jsp:param name="paramName1" value="var1" />

<jsp:param name="paramName2" value="var2" />

</jsp:forward>
{% endcodeblock %}

- 넘어온 파라미터는 다음과 같이 받을 수 있다.

{% codeblock lang:java %}
<%

String name = request.getParameter("paramName1");

%>
{% endcodeblock %}

