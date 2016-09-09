Project Name : Facebook_Login 
prerequisites:
1. IDE: Eclipse IDE
2. Server : apache-tomcat-8.0.32
3. JAVA : 1.8

Steps:
1- put the war file in the webapps folder "Facebook_Login.war"
2- start the tomcat server
3- hit the url : http://localhost:8080/Facebook_Login

About Application:
we have created the application in which we login via facebook oauth.
for this we have created 3 java file and their functionalities are below:-
1. FBConnection.java : the java file is used to make the connection form facebook (by using FB_APP_ID ,FB_APP_SECRET and REDIRECT_URI) and provide successfully authentication.
2. FBGraph.java : this java file is used to get JSON data by their accessToken and parse the json and put in the map.
3. FabHotelHomePage.java : this java file is used (mainly this is servlet) to render successfully logined page to the user.

Othe Details :
Facebook account Details:-
name : Harikesh Kumar
App ID : 1098214170268176
Api version : v2.7
App Secret : a011f4e9574401a860560a52534a2ec5
REDIRECT_URI = "http://localhost:8080/Facebook_Login/fbhome";

Index.jsp
------------------------------------------------------------------------------------------------------------------------------------------------
<%@page import="com.fabHotel.login.facebook.FBConnection"%>
<%@ page language="java" contentType="text/html; charset=ISO-8859-1"
	pageEncoding="ISO-8859-1"%>
<%
	FBConnection fbConnection = new FBConnection();
%>
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=ISO-8859-1">
<title>Java Facebook Login</title>
</head>
<body style="text-align: center; margin: 0 auto;">
	<div
		style="margin: 0 auto; background-image: url(./img/fbloginbckgrnd.jpg); height: 360px; width: 610px;">
		<a href="<%=fbConnection.getFBAuthUrl()%>"> <img
			style="margin-top: 138px;" src="./img/facebookloginbutton.png" />
		</a>
	</div>
</body>
</html>

web.xml
----------------------------------------------------------------------------------------------------------------------------------------------------
<web-app xmlns="http://java.sun.com/xml/ns/j2ee"
    xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
    xsi:schemaLocation="http://java.sun.com/xml/ns/j2ee http://java.sun.com/xml/ns/j2ee/web-app_2_4.xsd"
    version="2.4">

    <servlet>
        <servlet-name>FabHotelHomePage</servlet-name>
        <servlet-class>com.fabHotel.login.facebook.FabHotelHomePage</servlet-class>
    </servlet>

    <servlet-mapping>
        <servlet-name>FabHotelHomePage</servlet-name>
        <url-pattern>/fbhome</url-pattern>
    </servlet-mapping>

</web-app>   