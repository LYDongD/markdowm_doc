###MongoDB之开始
---
1 homebrew下载套件的安装目录
	
	Homebrew 会将套件安装到独立目录，并将文件软链接至 /usr/local 
	

2 使用homebrew下载mongodb遇到的问题

***Q**：Permission denied - /usr/local/etc/openssl*

当前用户没有操作path: /usr/local/的权限

**A**：

sudo chown -R "$USER": admin /usr/local
sudo chown "$USER" /data/db

sudo: 使用root权限操作
chown: 设置path下操作权限

***Q **如何连接mongodb并进入终端交互模式？*

**A：**

	1 创建dataPath: 创建data/db作为mongodb的数据输出路径 mkdir -p data/db
	2 连接mongodb: mongodb --dbpath data/db --port=27000， 可以不指定--dbpath,默认为data/db, 可以不指定端口，默认为27017
	3 另外打开终端，通过命令mongo进入交互模式
	
**mongodb的bin路径自动添加到$PATH当中，无需另外手动添加即可使用相关命令**

***Q：** 如何以指定的app打开某个文件*

**A：** open -a + app_path + file_path



3 连接mongodb

	mongo 120.76.223.75:27017/admin -u admin -p
	
	输入密码
	
	mongo + 【ip : port/database】 -u 【account】 -p
	
4 常用命令

	show databases
	use + [database]
	show collections
	db.[collection].find()

	



