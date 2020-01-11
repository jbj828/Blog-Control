---
date: '2020/1/11 14:01:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: JSP include action tag
---


Include action tag?

include 액션 태그는 include 디렉티브(<%@include>) 와 같이 다른 페이지를 현재 페이지에 포함시킬 수 있다. include 디렉티브는 단순하게 소스의 내용이 텍스트로 포함 되지만 include 액션 태그는 포함시킬 페이지의 처리 결과를 포함시킬 수 있다.

<br/>

<!-- more -->


* include 액션태그를 이용한 홈페이지 작성
{% asset_img "jsp-include.png" 100 500 "jsp-include" %}

* Main.jsp
{% codeblock lang:java %}
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<body>

<center>
	<table width="800" border="1">
	<!-- Top -->
		<tr height="150">
			<td align="center" colspan="2"> 
				<jsp:include page="Top.jsp">
					<jsp:param value="jbj828" name="id"/>
				</jsp:include>
			</td>
		</tr>
	<!-- Left  Center-->
		<tr height="400">
			<td align="center" width="200">
				<jsp:include page="Left.jsp"/>
			</td>
			<td align="center" width="600">
				<jsp:include page="Center.jsp"/>
			</td>
		</tr>
	<!-- Bottom  -->
		<tr height="100">
			<td align="center" colspan="2">
				<jsp:include page="Bottom.jsp"/>
			</td>
		</tr>	
	</table>

</center>

</body>
</html>
{% endcodeblock %}

* Top.jsp
{% codeblock lang:java %}
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<body>
	<!-- Top  -->
	<table width="800">
		<tr height="100">
		<!-- logo image -->
			<td colspan="2" align="center" width="260">
				<img src="img/campingLogo.png" width="200" height="60">
			</td>
			<td colspan="4" align="center">
			<font size="13">Camping Site</font>
			</td>
		</tr>
		<tr height="50">
			<td width="110" align="center">Tent</td>
			<td width="110" align="center">Hat</td>
			<td width="110" align="center">Food</td>
			<td width="110" align="center">Knife</td>
			<td width="110" align="center">Chair</td>
			<td width="110" align="center">Table</td>
			<td width="140" align="center"><%= request.getParameter("id")%></td>
		
		</tr>
	</table>

</body>
</html>
{% endcodeblock %}

* Left.jsp
{% codeblock lang:java %}
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<body>

	<table width="200" >
		<tr height="40">
			<td width="200" align="center"> <a href="#">SnowPeak</a></td>
		</tr>
		<tr height="40">
			<td width="200" align="center"> <a href="#">Coleman</a></td>
		</tr>
		<tr height="40">
			<td width="200" align="center"> <a href="#">Zip</a></td>
		</tr>
		<tr height="40">
			<td width="200" align="center"> <a href="#">Cobea</a></td>
		</tr>
	
	</table>

</body>
</html>
{% endcodeblock %}

* Center.jsp
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

	<table width="600">
		<tr height="400">
			<td align="center">
				<img src="img/campingSite.png" width="400" height="300"/>
			</td>
		</tr>	 
	</table>

</body>
</html>
{% endcodeblock %}

* Bottom.jsp
{% codeblock lang:java %}
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<body>

	<table width="800">
		<tr height="100">
			<td align="center">
				Blog
				About
				Shop
				Contact
				Pricing
				API
				Training
				Status <br>
				Security
				Terms
				Privacy
				Help
			</td>
		</tr>
	</table>

</body>
</html>
{% endcodeblock %}

<!-- toc -->