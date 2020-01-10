---
date: '2020/1/9 19:10:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title:
---

### JSTL이란?

* JSP에서 자주 사용하는 기능을 구현하는 커스텀 태그와 라이브러리의 모음이다.

<!-- excerpt -->

### JSTL을 사용한 예시

##### Result

{% asset_img "jsp-jspl.png" 500 300 "jsp-jspl" %}

Student.java
{% codeblock lang:java %}
package com.javit.jsp.tagdemo;

public class Student {
	
	private String firstname;
	private String lastname;
	private boolean goldCustomer;
	
	
	public Student(String firstname, String lastname, boolean goldCustomer) {
		super();
		this.firstname = firstname;
		this.lastname = lastname;
		this.goldCustomer = goldCustomer;
	}


	public String getFirstname() {
		return firstname;
	}


	public void setFirstname(String firstname) {
		this.firstname = firstname;
	}


	public String getLastname() {
		return lastname;
	}


	public void setLastname(String lastname) {
		this.lastname = lastname;
	}


	public boolean isGoldCustomer() {
		return goldCustomer;
	}


	public void setGoldCustomer(boolean goldCustomer) {
		this.goldCustomer = goldCustomer;
	}
}

{% endcodeblock %}


student-shopping.jsp
{% codeblock lang:java %}
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>

<%@ page import="java.util.*, com.javit.jsp.tagdemo.Student" %>


<%
	List<Student> data = new ArrayList<>();

	data.add(new Student("Javit", "Chung", true));
	data.add(new Student("Rene", "Aoki", false));
	data.add(new Student("John", "Doe", false));
	
	pageContext.setAttribute("myStudents", data);
%>


<html>

<body>
	<table border="1">

	<tr>
		<th>First Name</th>
		<th>Last Name</th>
		<th>Gold Customer</th>
	</tr>

	<c:forEach var="tempStudent" items="${myStudents}">
	
		<tr>
			<td>${tempStudent.firstname}</td>
			<td>${tempStudent.lastname}</td>
		 	<td>
		 	
		 		<c:choose>
		 		
			 		<c:when test="${tempStudent.goldCustomer}">
			 			Special Discount
			 		</c:when>
			 		
			 		<c:otherwise>
			 			No Discount
			 		</c:otherwise>
			 		
		 		</c:choose>
		 	</td>
		</tr>
		
	</c:forEach>


	</table>
</body>

</html>
{% endcodeblock %}

