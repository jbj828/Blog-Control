---
date: '2020/1/12 10:14:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: Java Bean and useBean
---

Java Bean?

자바 빈(Bean)이란?

- 웹 페이지를 구축하다보면 같은 기능을 갖지만 페이지 구성이 달라질 경우 같은 수고를 반복할 경우가 있다.
<!-- more -->
- 웹 페이지를 보다 효율적이고 생산적으로 작성하려면 코드를 재활용 할 수 있어야 한다.


- 웹 사이트를 개발할 때, JSP로 웹 페이지를 디자인 하고 내부적인 데이터 처리는 자바 빈으로 구현한다.

- 빈(Bean)은 재활용이 가능한 컴포넌트(Component)와 마찬가지로 소프트웨어를 부품화 한것이다.

- 소프트웨어도 부품화하여 개발하는데 이를 자바에서 빈(Bean)이라고 하고 일반적으로 컴포넌트라고 한다.

- 빈(Bean)은 한번 개발하고 나면 여러가지 페이지에서 동시에 가져다 사용할 수 있다.

- 빈(Bean)은 재사용 가능한 객체로서 대부분 데이터를 저장하는 역할을 한다.

<!-- more -->


다음은  java bean 과 useBean을 활용한 예시이다.

MemberJoin.jsp
{% codeblock lang:java %}
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<body>


	<center>
	<h2>Join</h2>
		<form action="MemberJoinProc.jsp" method="post">
		
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
					<td width="150" align="center">Address</td>
					<td width="350" align="center"> 
					<input type="text" name="address" size="40" />
					</td>
				</tr>
				
				<tr height="50">
					<td align="center" colspan="2">
					<input type="submit" value="Join Now">
					<input type="reset" value="Cancel">
					</td>
				</tr>
			</table>
		</form>
	</center>

</body>
</html>
{% endcodeblock %}


Java Resources 파일
bean.MemberBean.java
{% codeblock lang:java %}
package bean;

public class MemberBean {
	
	private String id;
	private String pass1;
	private String email;
	private String tel;
	private String address;
	
	
	public String getId() {
		return id;
	}
	public void setId(String id) {
		this.id = id;
	}
	public String getPass1() {
		return pass1;
	}
	public void setPass1(String pass1) {
		this.pass1 = pass1;
	}
	public String getEmail() {
		return email;
	}
	public void setEmail(String email) {
		this.email = email;
	}
	public String getTel() {
		return tel;
	}
	public void setTel(String tel) {
		this.tel = tel;
	}
	public String getAddress() {
		return address;
	}
	public void setAddress(String address) {
		this.address = address;
	}

}

{% endcodeblock %}


MemberJoinProc.jsp
{% codeblock lang:java %}
<%@ page language="java" contentType="text/html; charset=EUC-KR"
    pageEncoding="EUC-KR"%>
<!DOCTYPE html>
<html>
<body>

	<center>
		<h2>User's Information</h2>
		
		<%
			request.setCharacterEncoding("euc-kr");		
		%>
		
		<!-- request로 넘어온 데이터를 자바 빈즈랑 맵핑 시켜주는 useBean  -->
		<jsp:useBean id="mbean" class="bean.MemberBean"><!-- 객체생성 MemberBean mbean = new MemberBean()  -->
		<!-- jsp 내용을 자바빈 클래스(MemberBean을 의미)에 데이터를 맵핑(넣어줌) -->
			<jsp:setProperty name="mbean" property="*"/><!-- 자동으로 모두 맵핑 시켜주세요  -->
		</jsp:useBean>
		
		<h2>Your id is <jsp:getProperty property="id" name="mbean"/></h2>
		<h2>Your password is <jsp:getProperty property="pass1" name="mbean"/></h2>
		<h2>Your email is <jsp:getProperty property="email" name="mbean"/></h2>
		
		<h2>Your phone number is <%= mbean.getTel() %></h2>
		
	</center>

</body>
</html>
{% endcodeblock %}

