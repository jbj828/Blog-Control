---
date: '2020/1/9 10:50:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: JSP Cookies
---

Personalize content with Cookie

<!-- more -->
cookies-homepage.jsp
{% codeblock lang:java %}
<%@ page import="java.net.URLDecoder" %>

<html>
<head><title>Homepage</title></head>


<body>

<%
	String favLang = "Java";

	Cookie[] theCookies = request.getCookies();
	
	if(theCookies != null){
		
		for(Cookie tempCookie : theCookies){
			
			if("myApp.favoriteLanguage".equals(tempCookie.getName())){
				favLang = URLDecoder.decode(tempCookie.getValue(), "UTF-8");
				break;
			}
		}
	}
%>

<h2>Training Portal</h2>

<h3>New books for <%= favLang %></h3>
<ul>
	<li>blah blah</li>
</ul>

<h3>Latest New Report <%= favLang %></h3>
<ul>
	<li>blah blah</li>
</ul>

<h3>Hot Jobs for <%= favLang %></h3>
<ul>
	<li>blah blah</li>
</ul>

<a href="cookies-personalize-form2.html">Personalize this page</a>

</body>
</html>
{% endcodeblock %}

cookies-personalize-form.html
{% codeblock lang:java %}
<html>
<head><title>Personalize form</title></head>

<body>
	<form action="cookies-personalize-response2.jsp">
	
		Select your favorite language: 
		<select name="favoriteLanguage">
		
			<option>Java</option>
			<option>PHP</option>
			<option>C#</option>
	
		</select>
		
		<br/><br/>
		<input type="submit" value="Submit"/>
		
	</form>

</body>
</html>
{% endcodeblock %}

cookies-personalize-response.jsp
{% codeblock lang:java %}
<%@ page import="java.net.URLEncoder" %>

<html>
<head><title>Personalize response</title></head>


<body>

<%
	String favLang = request.getParameter("favoriteLanguage");

	favLang = URLEncoder.encode(favLang, "UTF-8");

	Cookie theCookie = new Cookie("myApp.favoriteLanguage", favLang);
	
	theCookie.setMaxAge(60*60*24*365);
	
	response.addCookie(theCookie);
%>
	
	
	Thanks! We set your favorite language ${param.favoriteLanguage}
	
	<br/><br/>
	
	<a href="cookies-homepage2.jsp">Return to the homepage</a>


</body>
</html>
{% endcodeblock %}


<!-- toc -->