# Configuration Files


## Main Configuration Files

Apache HTTP Server 通过在文本文档中配属指令(directives)来进行配置. 主配置文件(main configuration file)通常为httpd.conf. 这个文件的位置在编译时设置, 并且可以通过```-f```参数进行指定. 此外, 其他的配置文件通过```Include```指令添加. ```Include```指令支持通配符以包括多个文件. 配置文件中可以配置任意的指令(directive). 主配置文件修改后在httpd重启或启动后起效. 

Server也会读取一个定义MIME文件类型的文件. 这个文件的文件名有```TypeConfig```指令指定, 默认为mime.types.

## 配置文件语法规则
1. 一条指令一行， "\\"将下一行接续  
2. 参数用空格分割。如果参数内有空格，则参数必须用引号。  
3. 配置文件中，指令大小写不敏感。不过参数通常为大小写敏感。  
4. "\#"在一行开头为注释。注释和指令不能写在一行里.行前的空格会被忽略, 可以缩进对齐.  
5. 使用```Define```指令设置的变量和Shell的环境变量可以通过${VAR}进行引用.   
	1. 如果VAR没有定义，则会保留${VAR}并且在log中进行警告.   
	2. ```Define```指令会将将同名的环境变量覆盖.  
	3. 变量名不能包含":"  
	4. 使用RewriteMap指令避免命名冲突    
6. 只有Server启动前的环境变量会被引用展开。配置文件内设置的环境变量--例如使用```SetEnv```指令设置的--会在使用时展开.  
7. 普通的配置文件最大为16M, .htaccess文件最大为8190字节.  
8. 使用```apachectl configtest```测试配置文件语法  

## Modules

* Apache HTTP Server 是模块化的服务器。核心服务只包含基本的功能。扩展功能通过加载模块实现。  
	1. 默认情况下，编译时仅包含基本的模块集. 动态加载的模块(dynamically loaded modules)被分割编译, 通过```LoadModule```指令进行加载. 否则，Server需要在编译时添加／去掉模块.  
	2. 配置依赖于某个模块的指令时，可以用```<IfModule>```块。```<IfModle>```并不是必须的，不过很多时候这会掩盖你丢失重要模块的事实.  

命令行```-l```参数可以看到编译进Server的模块。```-M```参数可以看到当前加载的模块.


## 指令的作用域(Scope of Directives)

主配置文件中的指令会影响整个Server. 如果想配置Server的末裔部分, 可以将指令配置在```<Directory>```, ```<DirectoryMatch>```, ```<File>```, ```<FileMatch>```, ```<Location>```, ```<LocationMatch>```段内. 这些段(section)将指令的影响范围控制在指定的文件系统或URL内. 这些段可以嵌套, 以达到一个合适的粒度.

服务器也可以作为模拟多个不同web站点(website), 这称之为"虚拟主机(Virtual Hosting)". 指令同样可以通过```<VirtualHost>```段将作用范围限制在虚拟主机内.

指令可以配置在这些段内，但是某些指令在段内并不起作用。

## .htaccess File

* Apache HTTP Server 可以通过分布在web tree中的.htaccess文件管理分散的配置.  
	* .htaccess文件名可以通过```AccessFileName```指令进行配置.   
	* 配置在.htaccess文件中的指令其作用域为.htaccess文件所在目录及子目录。  
	* .htaccess语法与主配置文件语法一致  
	* .htaccess会在每次请求时读入，其修改立即起效  
	* Server管理员可以通过在主配置文件中配置```AllowOverride```指令配置.htaccess可以使用的指令  

