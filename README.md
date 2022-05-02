# Servlets & JSP

## Setting Up Development Environment

To build JSP Applications, you need:

1. Java Application Server (like Tomcat)
1. Java Integrated Development Envirnoment (IDE) (like Eclipse)

To Connect Eclipse tp Tomcat, open eclipse, on the botton click on add new server on the servers tab. Select Apache >Tomcat, browse to Tomcat installed location and click on finish.

<br>

## JSP Fundamentals

JSP is an HTML page with java code sprinkled in. JSP is processed on the server. Result of java code will generate HTML and returned back to the browser.<br>
JSP file goes in you webapp folder and have a .jsp extension. You can put java code inside <%= %>

### Hello World Program

File > New > Dynamic Web Project

```html
<html>
  <body>
    <h3>Hello World of Java!</h3>
    The time on the server is <%= new java.util.Date() %>
  </body>
</html>
```

To run right click JSP file > Run As > Run on Server

### JSP Scripting Elements

| Element         | Syntax                                |
| --------------- | ------------------------------------- |
| JSP Expression  | <%= some java expression %>           |
| JSP Scriplets   | <% some java code: 1 or many lines %> |
| JSP Decalration | <%! variable or method declaration %> |

**JSP Expression:** <%= new String("Hello World") %> <br>
**JSP Scriplets:** <% out.println("\<br/> Hello World"); %> <br>
**JSP Decalration:** <%! String hello() { return "Hello"; } %> <%= hello() %>

### JSP Build-In Objects

| Objects     | Description                                         |
| ----------- | --------------------------------------------------- |
| request     | Contains HTTP request headers and form data         |
| response    | Provides HTTP support for sending response          |
| out         | JspWriter for including content in HTML page        |
| session     | Unique session for each user of the web application |
| application | Shared data for all users of the web application    |

### Including Files in JSP

```html
<jsp:include page="my-header.html" /> <jsp:include page="my-footer.jsp" />
```

<br>

## Servlet Fundamentals

Java class processed on the server.<br>
To create a servlet right click > New > Servlet

```java
@WebServlet("/helloWorld") // this is the endpoint
public class HelloWorldServlet extends HttpServlet {
    public HelloWorldServlet() {
        super();
    }

	protected void doGet(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {

		// Step 1: set the content type
		response.setContentType("text/html");

		// Step 2: get the printwriter
		PrintWriter out = response.getWriter();

		// Step 3: generate HTML content
		out.println("<html><body>");
		out.println("<h2>Hello World</h2>");
		out.println("</body></html>");
	}

	protected void doPost(HttpServletRequest request, HttpServletResponse response) throws ServletException, IOException {
		// TODO Auto-generated method stub
		doGet(request, response);
	}
}
```

### Servlets vs JSP

Servlets for business logic and JSP for presentation view<br>
Model-View-Controller (MVC) design pattern

### Form Data

Create HTML Form in form tag action="servletName" method="GET"<br>
Create servlet and getparameters by request.getParameters();
