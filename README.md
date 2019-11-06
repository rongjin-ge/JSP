# JSP技术
JSP是Java Server Page的缩写,是Servlet的扩展,其作用是简化网站创建过程和维护动态网站.

# JSP生成HTML页面
* **当Servlet容器接收到客户端的要求访问特定JSP文件的请求时,容器按照以下流程来处理：**
* 1.查找与JSP文件对应的Servlet,如果已经存在,就调用它的服务方法.
* 2.如果与JSP文件对应的Servlet还不存在,就解析文件系统中的JSP文件,把它翻译成Servlet源文件,接着把Servlet源文件翻译成Servlet类,然后再初始化并运行        Servlet.
* **在Web应用处于运行时的情况下,如果原始的JSP文件被更新,多数Servlet容器能检测到所做的更新,既而自动生成新的Servlet源文件,然后再运行新生成的Servlet.**
* **Tips：Tomcat把由JSP生成的Servlet源文件和类文件放于<CATALINA_HOME>/work目录下.**

# JSP语法
在JSP文件中除了可以直接包含HTML文本,还可以包含以下内容：
* JSP指令
* JSP声明
* java程序片段(Scriptlet)
* java表达式
* JSP隐含对象

* **一.JSP指令**  
  JSP指令用来设置和整个JSP网页相关的属性,如网页的编码方式和脚本语言.JSP指令的一般语法形式为:  
<%@ 指令名 属性="值" > 
  常用的3种指令为page、include、taglib
* 1.page指令(略) 
* 2.include指令  
  <%@ include file="目标文件绝对URL或相对URL" %>  
  Tips: include指令来包含其它文件被看作静态包含.

# JSP生命周期
  //todo

# 请求转发
  //todo
  
# 包含(静态包含和动态包含)
---
* **1. 静态包含(include指令)**  
  * <%@ include file="目标文件绝对URL或相对URL" %> 
  * Tomcat解析include指令流程：  
    1.解析源文件.在解析<%@ include file="目标文件" %>时,把目标文件的所有源代码融合到源文件;  
    2.把融合后的jsp源文件翻译为Servlet源文件,再把它编译为Servlet类.  
    3.初始化与源文件对应的Servlet,再运行它的服务方法.  
    Tips：目标文件如果是JSP文件,那么该JSP文件可以访问在源文件中定义的局部变量,因为实际上,JSP源文件和JSP目标文件对应同一个Servlet.  
    
* **2. 动态包含(include标签)**  
  * <jsp:include page="目标文件绝对URL或相对URL" %>  
  * Tomcat解析include标签流程：  
    1.解析源文件并把它翻译为Servlet源文件.<jsp:include page="目标文件" %>会被翻译为如下程序代码:
    
```html
   org.apache.jasper.runtime.JspRuntimeLibrary.include(request, response, "目标文件", out, false);
```

   2.把Servlet源文件编译成Servlet类.  
   3.初始化Servlet,运行它的服务方法.  
   4.Servlet服务方法调用JspRuntimeLibrary.include(...)方法,解析目标文件,把它翻译为Servlet源文件,再编译成Servlet类,接着初始化该Servlet并调用它的服务方法.  
   5.当Servlet容器执行完JspRuntimeLibrary.include(...)方法后,继续执行源文件对应的Servlet的服务方法中的后续代码.  
   Tips: include标签可以包含JSP表达式,如：<jsp:include page="<%=VarName %/>" />,如果改为<%@include file="<%=VarName %/>" %>,那么Servlet容器会把字符串<%=VarName %/>的字面内容直接理解为一个目标组件的URL,而由于找不到相应的目标组件,会报错.










  

