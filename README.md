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

* **JSP指令


