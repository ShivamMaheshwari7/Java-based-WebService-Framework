# Java-based-WebService-Framework
Framework makes it easy to create applications and services with absolute minimum fuss. Small over view of the frame work and user can easily use the framework to produce backends of the web applications/projects.

You can use this framework to create backend/serverside services for web requests, Now user not need to know about servlets or edit Web.xml,user can simply use the framework and all its need can be solved.

Benifits of using this FrameWork:-
===========================

1) Absolutely no requirement for XML configuration.

2) No need to write servlets Classes for every new web Request.

3) User dont have to worry about get/post request and how to Handle them.

4) User dont have to worry about how to handle multipart requests and how to parse them and process them.

5) User can use ServicesDoc tool in framework to find list of services inside application.

Getting Started.(steps to use the Framework)
===========================

1) Download this git repository.

2) Extract the zip File.

3) Copy/cut [web.xml](web.xml) to tomcat9/Webapps/"Project Name"/WEB-INF/.

   User just need to change/write a single word inside [web.xml](web.xml) and that was the param-value against param-name 'SERVICE_PACKAGE_PREFIX' i.e. by default there was "bobby", user have to change it.

   User have to write the folder-name/folder-name-starts-with there in which services which are using this Framework exists.

   Note : the folder-name mention here should exists inside tomcat9/Webapps/"project name"/WEB-INF/classes/.

   ```
   <init-param>
   <param-name>SERVICE_PACKAGE_PREFIX</param-name>
   <param-value>bobby</param-value>
   </init-param>
   ```
   the above example show how to write folder-name in which services classes are located (services classes are classes using the framework to create web service for requests).

   User also have to change a single word inside [web.xml](web.xml), instead of 'schoolService' user have to write his/her application entity name there.

   ```
   <servlet>
   <servlet-name>TMWebRock</servlet-name>
   <servlet-class>com.thinking.machines.webrock.TMWebRock</servlet-class>
   </servlet>
   <servlet-mapping>
   <servlet-name>TMWebRock</servlet-name>
   <url-pattern>/schoolService/*</url-pattern>
   </servlet-mapping>
   ```

   In above piece of code user have to make change only in line number 7. i.e. replace 'schoolService' with other word.
   
   Now you can forget about [web.xml](web.xml) as you dont have to change or configure it again.

4) Now copy [webServiceFramework.jar](webServiceFramework.jar) to tomcat9/Webapps/"Project Name"/WEB-INF/lib/.
Tomcat search for servlet classes in classes folder or lib folder.

5) Now copy all files inside [Dependencies](Dependencies) folder and paste them inside tomcat9/lib/.
these are all the files you will ever need to create a web service. Our framework is Dependent on some of the these files. some of the jar file may already be present there you can skip those files.

6) You are done setting up the environment,now you can use the frameWork easily.

Tutorials and reference documentation:-
===========================

user can create Web service by using these annotations on class and Methods. User dont have to worry about how these webservices will run when request arrives. User can request Data, HttpServletRequest and HttpServletResponse from framework.

Annotations User can use are:
---------------------
1) @Path("/employee")

	Path annotation can be applied to class and method.value of path should starts with front Slash followed by path.
	Example:-
	``` markdow
	import com.thinking.machines.webrock.annotations.*;
	@Path("/employee")
	public class Employee
	{
	@Path("/view")
	public void view()
	{
		System.out.println("View Service");
	}}
	```
	user can access this service by sending request to "User's entity name"/employee/view.

2) @RequestParameter("username").

	RequestParameter annotation can only be applied on Parameter. User can use the following annotation to request data from framework which arrives as web request.
framework finds the value of the annotation and search for data with given name in request Bag and if found provide this requested data to user without user having to worry about conversions. 
	Example:-
	```
	import com.thinking.machines.webrock.annotations.*;
	@Path("/employee")
	public class Employee
	{
	@Path("/add")
	public String add(@RequestParameter("username") String name,@RequestParameter("gender") String gender,@RequestParameter("indian") boolean indian)
	{
	System.out.println(name+"----"+gender+"-----"+indian);
	return "Add model service Used";
	}
	}
	```
	Example url to access add service
	http://localhost:8080/"user's-application-context-name"/"user's-entity-name"/employee/add?username=Shivam+Maheshwari&gender=male&indian=true
	To access Boolean data client user must send data as True or TRUE or true and same goes for it counterpart.

3) @SecuredAccess(checkPost="com.thinking.machines.secured.Security",guard="securityGuardOne")
	
	By using this annotation user dont have to write verification code for every service that need to be secured,user can just apply this annotation to all the services that are needed to be secured from unidentified access. SecuredAccess annotation can only be applied on Method.
	=> checkPost = full classname(with package) to your verification class.
	=> guard = method name within user's verification class.
	Example:-
	```
	import com.thinking.machines.webrock.annotations.*;
	@Path("/employee")
	public class Employee
	{
	@Path("/get")
	@SecuredAccess(checkPost="com.thinking.machines.secured.Security",guard="securityGuardOne")
	public String get()
	{
	System.out.println("Get method got invoked and returned a String");
	return "School Getted";
	}
	}
	```
	value of checkPost should be a full name to the actual class that verify user based on the users details and value of guard should be method name inside that verification class.

4) @Forward("/employee/view")

5) @Get

6) @Post

7) @InjectApplicationScope

8) @InjectSessionScope

9) @InjectRequestScope

10) @InjectApplicationDirectory

11) @InjectRequestParameter("username")

12) @OnStartup(priority=1)

13) @AutoWired(name="username")
