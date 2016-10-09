###springmvc
---

**DispatcherServlet**

1 继承和实现关系

	dispatcherServlet --> FrameworkServlet --> HttpServletBean --> HttpServlet --> GenericServlet :Servlet, ServletConfig

Servlet = server + applet， 定义了一套网络请求的处理规范。
DispatcherServlet 本质上仍然是Servlet， 但是它不直接处理请求，而是分发到不同的控制器(后端handler)进行处理


2 HttpServlet

主要功能：重写service方法，提供基于http协议的request和response，将不同的请求方式路由到不同的处理方法。

这些方法只是模板方法，并不提供具体的实现