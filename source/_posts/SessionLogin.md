---
date: '2020/1/22 13:46:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: Session Login Form
---

세션을 이용한 로그인 폼 작성법

<!-- more -->

SessionLoginForm.jsp
```
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>


<center>
		<h2> Session Login </h2>
		<form action="SessionLoginProc.jsp" method="post">
		<table border="1" width="400">
			<tr height="50">
				<td width="150" align="center"> ID </td>
				<td width="250"> <input type="text" name="id" /> </td>
			</tr>
			<tr height="50">
				<td width="150" align="center"> Password </td>
				<td width="250"> <input type="password" name="pass" /> </td>
			</tr>
			<tr height="50">
				<td colspan="2" align="center"><input type="submit" value="Login"/></td>
			</tr>
		
		</table>
		</form>
	
	</center>


</body>
</html>
```

SessionLoginProc.jsp
```
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>

<center>

<%
	request.setCharacterEncoding("euc-kr");
	
	//사용자로부터 데이터를 읽어드림
	String id = request.getParameter("id");
	String pass = request.getParameter("pass");
	
	//아이디와 패스워드를 저장
	session.setAttribute("id", id);
	session.setAttribute("pass", pass);
	
	//세션의 유지시간 설정
	session.setMaxInactiveInterval(60);

%>

	<h2> Your id is <%= id %></h2>
	
	<a href="SessionLoginProc2.jsp">Next page</a>
	
	
</center>



</body>
</html>
```

SessionLoginProc2.jsp
```
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<head>
<meta charset="EUC-KR">
<title>Insert title here</title>
</head>
<body>



<center>

<%
	//세션을 이용하여 데이터를 불러드림
	String id = (String) session.getAttribute("id");
	String pass = (String) session.getAttribute("pass");


%>

	<h2> Your id is <%= id %></h2>

</center>




</body>
</html>
```

