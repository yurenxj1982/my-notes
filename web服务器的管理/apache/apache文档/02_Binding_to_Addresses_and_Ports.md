# Binding to Address and Ports

## Listen指令
* 使用Listen指令设置监听的地址-端口组合.   
	* 如果Listen指令只设置了端口, 则监听所有地址上的此端口.  
	* 如果IP地址和端口都设置了, 则监听指定地址上的端口.  
* 可以设置多个地址端口对  
* 可以指定协议的监听端口
例如:

```
Listen 80
Listen 8000
```

```
Listen 192.168.0.1:80
Listen 192.168.0.2:8000
```

```
Listen 192.168.0.1:8433 https
```

## How This Works With Virtual Hosts

* Listen 指令在Virtual Host段不起作用。
* <VirtualHost>可以对不同的地址端口对指定不同的行为。  
	* 首先，在整个Server设置Virtual Host监听的地址、端口
	* 然后，在<VirtualHost>段设置指定地址、端口进行的动作。




