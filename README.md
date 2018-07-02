# Node

## 简单的http服务 

1. 加载 `http` 模块

	 	const http = require('http');

2. 使用 `http.createServer()` 方法创建一个 `web` 服务器

		const server = http.createServer();

3. 注册 `request` 请求事件，当客服端请求过来，就会自动触发服务器的 `request` 请求事件，然后执行第二个参数：回调处理

		server.on('request', function(request, response) { 
			//返回数据，同时结束请求
			response.end('收到请求');
		})

4. 绑定端口号，启动服务器

		server.listen(3000, function() {
			console.log('服务器启动成功了，可以通过 http://127.0.0.1:3000/ 来进行访问');
		})

### 可以简写成

		const http = require('http');
		const server = http.createServer();
		
		server.on('request', function(request, response) { 
			//返回数据，同时结束请求
			response.end('收到请求');
		})
		.listen(3000, function() {
			console.log('服务器启动成功了，可以通过 http://127.0.0.1:3000/ 来进行访问');
		})

### 或者

		const http = require('http');
		http.createServer(function(request, response) { 
		    //返回数据，同时结束请求
		    response.end('收到请求');
		})
		.listen(5000, function() {
		    console.log('服务器启动成功了，可以通过 http://127.0.0.1:3000/ 来进行访问');
		})
    
## 简单使用 express

1. 加载模块 `express` 
	
		const express = require('express');

2. 创建服务器应用程序

		const app = express();

3. 配置路由

		app.get('/', function(req, res) {
			res.send('index');
		});

4. 绑定端口号，启动服务器

		app.listen(3000, function() {
			console.log('服务器启动成功了，可以通过 http://127.0.0.1:3000/ 来进行访问');
		});

### 提供静态资源服务
	
	//公开指定目录，可以直接通过 /public/xxx 的方式访问 public 目录中所有的资源
	app.use('/public', express.static('./public'));
