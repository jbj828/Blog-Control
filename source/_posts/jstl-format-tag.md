---
date: '2020/1/10 10:16:25'
tags:
  - jsp
categories:
  - JSP
thumbnail: ''
permalink: ''
title: Build a multi-lingual App
---

{% asset_img "i18nResult.png" 500 300 "i18nResult" %}

### JSTL Format Tag?

* 다국어 처리, 날짜 숫자를 formatting 할 경우 format tag 사용하면 편하다.

<!-- excerpt -->

#### Multi-lingual App

i18n-messages.jsp
{% codeblock lang:java %}
<%@ taglib uri="http://java.sun.com/jsp/jstl/core" prefix="c" %>
<%@ taglib uri="http://java.sun.com/jsp/jstl/fmt" prefix="fmt" %>


<c:set var="theLocale" 
value="${not empty param.theLocale ? param.theLocale : pageContext.request.locale}"
scope="session" />

<fmt:setLocale value="${theLocale}"/>

<fmt:setBundle basename="com.javit.jsp.tagdemo.i18n.resources.mylabels" />


<html>

<body>

<a href="i18n-messages-test.jsp?theLocale=en_US">English (US)</a>

<a href="i18n-messages-test.jsp?theLocale=es_ES">Spanish (ES)</a>

<a href="i18n-messages-test.jsp?theLocale=de_DE">German (DE)</a>


<hr>


<fmt:message key="label.greeting" /> <br/><br/>

<fmt:message key="label.firstname" /> <i>Jay</i>  <br/>

<fmt:message key="label.lastname" /> <i>Chung</i> <br/><br/>

<fmt:message key="label.welcome" /> <br/>

<hr>

Selected locale : ${theLocale}

</body>

</html>
{% endcodeblock %}


##### Resource 파일

com.javit.jsp.tagdemo.i18n.resources

mylabels.properties
{% codeblock lang:java %}
label.greeting=Howdy
label.firstname=First Name
label.lastname=Last Name
label.welcome=Welcome to the App Transer.
{% endcodeblock %}

mylabels_es_ES.properties
{% codeblock lang:java %}
label.greeting=Hola
label.firstname=Nombre de pila
label.lastname=Apellido
label.welcome=Bienvenido a la aplicación Transer.
{% endcodeblock %}

mylabels_de_DE.properties
{% codeblock lang:java %}
label.greeting=Hallo
label.firstname=Vorname
label.lastname=Nachname
label.welcome=Willkommen beim App Transer.
{% endcodeblock %}

<!-- toc -->