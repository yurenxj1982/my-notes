# Getting Started

## URL - Uniform Resource Locator

典型的URL例如 http://www.apache.org/docs/current/getting-started.html?arg=value   
包括以下几个部分  

* protocol - 协议 (例如: http)  
* servername - 服务器名称(例如: www.apache.org)  
* URL-path - URL路径(例如: /docs/current/getting-started.html)  
* query string - 查询字串(例如: ?arg=value)  


## Clients, Servers

* Client 使用特定的协议连接 Server, 通过URL-path**请求(request)**资源  
	* URL-path可以表示多种在服务器上的资源。也许是一个文件（像 getting-started.html), 也许是一个处理器(handler), 也许某一种程序文件(例如index.php).  

* Server 将**响应(response)**返回给Client。响应通常包括一个**状态码(status code)**, 以及可选的**响应体(response body)**.  
	* 状态码指示请求是否成功。如果失败，指明失败的状态. 这将告诉client如何处理响应. 可能的状态码参阅[HTTP Server Wiki](https://wiki.apache.org/httpd/CommonHTTPStatusCodes)  

## Configuration File and Directives

Apache HTTP Server 通过简单的文本文档进行配置.
为了方便管理，配置一般被分割到多个小文件中。这些小文件通过_Include_指令被加载进来.  

### 指令位置
* 对于全局设置的指令，应该放在配置文件的<Directory>,<Location>,<VirtualHost>等字段之外
* 对于指定目录(directory)的指令，应该放在<Directory>下.


## Web Site Content
Web Site Content可以简单的概括为**静态内容(static content)**和**动态内容(dynamic content)**.

- Static Content包括像HTML文件, Image文件, CSS文件, 以及其他的定位于文件系统上的文件. DocumentRoot指令指示了部署位置。DocumentRoot可以在全局设置，也可以在VirtualHost中进行设置。 
	- index.html: 如果某一目录作为请求而没有指定具体文件，则当前目录下的index.html就会被作为默认响应
- Dynamic Content指的是在请求时生成的内容，或者一个请求到另一个请求期间会改变的内容。有多种方法可以生成动态内容。如handlers，CGI programs.

## Log File
- ErrorLog 指令指定error log所在位置。
