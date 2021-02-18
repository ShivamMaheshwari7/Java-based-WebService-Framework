# Java-based-WebService-Framework
Framework makes it easy to create applications and services with absolute minimum fuss. Small over view of the frame work and user can easily use the framework to produce backends of the web applications/projects.

You can use this framework to create backend/serverside services for web requests, Now user not need to know about servlets or edit Web.xml,user can simply use the framework and all its need can be solved.

Benifits of using this FrameWork:-
===========================

1)Absolutely no requirement for XML configuration.

2)No need to write servlets Classes for every new web Request.

3)User dont have to worry about get/post request and how to Handle them.

4)User dont have to worry about how to handle multipart requests and how to parse them and process them.

5)User can use ServicesDoc tool in framework to find list of services inside application.

Getting Started.(steps to use the Framework)
===========================

1)Download this git repository.

2)Extract the zip File.

3)Copy/cut web.xml to tomcat9/Webapps/"Project Name"/WEB-INF/.
User just need to change/write a single word inside web.xml and that was the param-value against param-name 'SERVICE_PACKAGE_PREFIX' i.e. by default there was "bobby", user have to change it.

User have to write the folder-name/folder-name-starts-with there in which services which are using this Framework exists.

Note : the folder-name mention here should exists inside tomcat9/Webapps/"project name"/WEB-INF/classes/.

Now you can forget about web.Xml as you dont have to change or configure it again.

<init-param>
<param-name>SERVICE_PACKAGE_PREFIX</param-name>
<param-value>bobby</param-value>
</init-param>
