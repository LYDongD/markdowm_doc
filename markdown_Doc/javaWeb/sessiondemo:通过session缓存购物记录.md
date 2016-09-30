###Sessiondemo:通过session缓存购物记录
---
1 __使用maven构建web项目__

_Q1：_  jsp文件放在哪里可以通过/{projectName}/...的Url直接访问?

	从maven-archetype生成的目录来开，index.jsp默认妨碍web-inf/下，可在该路径下放jsp页面：sessionJsp/xxx.jsp，访问路径将为：/{projectName}/sessionJsp/xxx.jsp
	
*Q2：*   jsp文件的书写格式
	
	首行：<%@...%> ，通过import属性导入java的package
	次行：<!DOCTYPE html...>声明html规范
	主体: <%...%> 内嵌java代码
	视图：<html>...</html> 生成页面结构
	其他：<%=...%>可取java变量的值
	
2 **使用session缓存商品购买数量**

关于session的缓存机制，可以参考文章：
<http://blog.csdn.net/rongwenbin/article/details/51784517>

3 **使用maven插件热部署war到tomcat上**

 集成tomcat插件:mvn tomcat7:deploy/run

 详见：<http://www.cnblogs.com/alexck/archive/2013/11/13/3421922.html>
 

 
 
		
	
	

	

