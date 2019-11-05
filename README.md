# JSP技术
JSP是Java Server Page的缩写,是Servlet的扩展,其作用是简化网站创建过程和维护动态网站.

# JSP生成HTML页面
  当Servlet容器接收到客户端的要求访问特定JSP文件的请求时,容器按照以下流程来处理：
* 1.查找与JSP文件对应的Servlet,如果已经存在,就调用它的服务方法.
* 2.如果与JSP文件对应的Servlet还不存在,就解析文件系统中的JSP文件,把它翻译成Servlet源文件,接着把Servlet源文件翻译成Servlet类,然后再初始化并运行        Servlet.
