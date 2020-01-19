---
date: '2020/1/19 15:46:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: Cookie Login Form
---

쿠키를 이용해 로그인 폼 작성하는 방법
<!-- more -->

CookieLoginForm.jsp
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

	<%
		//사용자 컴퓨터의 쿠키 저장소로부터 쿠키값을 읽어드림 - 몇 개인지 모르기에 배열을 이용하여 쿠키값을 저장
		Cookie[] cookies = request.getCookies();
		String id ="";
		
		//쿠키값이 없을 수도 있기에 null처리 해줌
		if(cookies != null){
			for(int i=0; i< cookies.length; i++){
				if(cookies[i].getName().equals("id")){
					id = cookies[i].getValue();
					break; // 우리가 원하는 데이터를 찾았기에 반복문을 빠져나옴
				}
			}
		}
		
	
	%>

	<center>
		<h2> Cookie Login </h2>
		<form action="CookieLoginProc.jsp" method="post">
		<table border="1" width="400">
			<tr height="50">
				<td width="150" align="center"> ID </td>
				<td width="250"> <input type="text" name="id" value=<%= id %> /> </td>
			</tr>
			<tr height="50">
				<td width="150" align="center"> Password </td>
				<td width="250"> <input type="password" name="password" /> </td>
			</tr>
			<tr height="50">
				<td colspan="2" align="center"><input type="checkbox" name="save"> Save ID </td>
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

CookieLoginProc.jsp
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

<%
	request.setCharacterEncoding("euc-kr");

	//아이디 저장 체크박스가 체크되었는 판단 여부
	String save = request.getParameter("save");
	//아이디 값을 저장
	String id = request.getParameter("id");
	
	//체크 되었는지 비교 판단
	if(save != null){ //아이디 저장이 눌렸다면
	
	//쿠키를 사용하려면 쿠키클래스를 생성해주어야 함
	Cookie cookie = new Cookie("id", id); // 첫번째 String 키 값을 적어줌, 두번째 String엔 해당하는 value 값을 넣어줌
	
	//쿠키 유효시간 설정
	cookie.setMaxAge(60*10); //10분간 유효
	
	//사용자에게 쿠키값을 넘겨준다
	response.addCookie(cookie);
	
	out.write("Cookie is generated.");
	
	}
%>

</body>
</html>
```



