---
date: '2020/1/11 00:16:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: JSP 내장객체 
---
### JSP 내장객체란?
* 자주 사용되는 객체(클래스 9개)로 별도의 선언 없이 사용 가능하다

대표적으로 request, response, session 등이 있다.

이번 예는 request 를 중심으로 만든 회원가입 페이지이다.

<!-- more -->

Result

{% asset_img "request2.png" 500 300 "request2" %}


RequestJoin.jsp
{% codeblock lang:java %}
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
	<h2>Join</h2>
		<form action="RequestJoinProc.jsp" method="post">
		
			<table width="500" border="1">
			
				<tr height="50">
					<td width="150" align="center">ID</td>
					<td width="350" align="center"> 
					<input type="text" name="id" size="40" placeholder="Write the ID" />
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">Password</td>
					<td width="350" align="center"> 
					<input type="password" name="pass1" size="40" />
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">Password check</td>
					<td width="350" align="center"> 
					<input type="password" name="pass2" size="40" />
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">E-mail</td>
					<td width="350" align="center"> 
					<input type="email" name="email" size="40" />
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">Phone Number</td>
					<td width="350" align="center"> 
					<input type="tel" name="tel" size="40" />
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">Hobby</td>
					<td width="350" align="center">
						<input type="checkbox" name="hobby" value="exercise">Exercise &nbsp;&nbsp;
						<input type="checkbox" name="hobby" value="programming">Programming &nbsp;&nbsp;
						<input type="checkbox" name="hobby" value="reading">Reading &nbsp;&nbsp;
					</td>
				</tr>
				
				<tr height="50">
					<td width="150" align="center">Job</td>
					<td width="350" align="center">
						<select name="job">
						<option>Teacher</option>
						<option>Programmer</option>
						<option>Doctor</option>
						<option>Student</option>
						<option>Unemployed</option>
						</select>
					</td>
					</tr>
					
				<tr height="50">
					<td width="150" align="center">Age</td>
					<td width="350" align="center">
						<input type="radio" name="age" value="20">20s &nbsp;&nbsp;
						<input type="radio" name="age" value="30">30s &nbsp;&nbsp;
						<input type="radio" name="age" value="40">40s &nbsp;&nbsp;
						<input type="radio" name="age" value="50">50s &nbsp;&nbsp;
					</td>
				</tr>
					
				<tr height="50">
					<td width="150" align="center">Your Story</td>
					<td width="350" align="center">
					<textarea rows="5" cols="40" name="info"></textarea>
					</td>
					</tr>
					
				<tr height="50">
					<td align="center" colspan="2">
					<input type="submit" value="Join Now">
					<input type="reset" value="Cancel">
					</td>
			</table>
		</form>
	</center>
</body>
</html>
{% endcodeblock %}

RequestJoinProc.jsp
{% codeblock lang:java %}
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>

<body>
	<center>
		<h2>Member information</h2>
		
<%
	request.setCharacterEncoding("EUC-KR"); 
	// if method is post, the hanguel would be not printed. This will prevent that situation.
	
	String id = request.getParameter("id");
	String pass1 = request.getParameter("pass1");
	String pass2 = request.getParameter("pass2");
	String email = request.getParameter("email");
	String tel = request.getParameter("tel");
	
	String[] hobbies = request.getParameterValues("hobby");
	
	String job = request.getParameter("job");
	String age = request.getParameter("age");
	String info = request.getParameter("info");
	
	//checking password is the same with password2
	if(!pass1.equals(pass2)){
%>	
	<script type="text/javascript">
		alert("The password is not corret.");
		history.go(-1);
	</script>	
<% 	
	}

%>
	
<center>
	<table width="500" border="1">
		<tr height="50">
			<td width="150" align="center">ID</td>
			<td width="350" align="center"> <%= id %>
		</tr>
		<tr height="50">
			<td width="150" align="center">Password</td>
			<td width="350" align="center"> <%= pass1 %>
		</tr>
		<tr height="50">
			<td width="150" align="center">E-mail</td>
			<td width="350" align="center"> <%= email %>
		</tr>
		<tr height="50">
			<td width="150" align="center">Phone Number</td>
			<td width="350" align="center"> <%= tel %>
		</tr>
		<tr height="50">
			<td width="150" align="center">Hobby</td>
			<td width="350" align="center"> 
			<%
				for(int i=0; i < hobbies.length; i++){
					out.write(hobbies[i]+ " ");
				}
			%>		
		
			</td>
		</tr>
		<tr height="50">
			<td width="150" align="center">Job</td>
			<td width="350" align="center"> <%= job %>
		</tr>
		<tr height="50">
			<td width="150" align="center">Age</td>
			<td width="350" align="center"> <%= age %>
		</tr>
		<tr height="50">
			<td width="150" align="center">Your Story</td>
			<td width="350" align="center"> <%= info %>
		</tr>
	
	
	</table>
</center>
	</center>
</body>
</html>
{% endcodeblock %}




<!-- toc -->