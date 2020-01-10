---
date: '2020/1/8 22:46:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: Session example
---

Tracking user actions with session


<!-- excerpt -->

#### Result
{% asset_img "jsp-session-study.png" 500 300 "title" %}




{% codeblock lang:java %}
<%@ page import="java.util.*" %>


<html>
<body>

<!-- Step 1: Create HTML form -->
<form action="todo-demo.jsp">
	Add new item: <input type="text" name="theItem"/>
	
	<input type="submit" value="Submit"/>
</form>


<!-- Step 2: Add new item to "To Do" list -->

<%
	List<String> items = (List<String>) session.getAttribute("myToDoList");
	
	if(items == null){
		items = new ArrayList<String>();
		session.setAttribute("myToDoList", items);
	}
	
	String theItem = request.getParameter("theItem");
	if(theItem != null){
		items.add(theItem);
	}
%>

<!-- Step 3: Display all "To Do" item from the session -->

<hr>
<b>To list items:</b> <br/>

<ol>
<%
	for(String temp: items){
		out.println("<li>" + temp + "</li>");
	}
%>
</ol>

</body>

</html>
{% endcodeblock %}
