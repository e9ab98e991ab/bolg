    title: 腾讯云Nginx错误
    date: 2018-03-10 11:22:02
    tags: [ Centos , b, c]
    description: 阿里云ECS在CentOS 6.9中使用Nginx提示： Address family not supported by protocol)的解决方法
---

阿里云ECS在CentOS 6.9中使用Nginx提示：nginx: [emerg] socket() [::]:80 failed (97: Address family not supported by protocol)的解决方法
说明：

1、[::]:80这个是IPv6的地址。

2、阿里云截至到今天还不支持IPv6。

解决方式：

1、普通解决方式：开启IPv6的支持，不过这个方法在阿里云行不通。

vim /etc/nginx/conf.d/default.conf
#找到并替换为以下：
listen 80;
listen [::]:80 ipv6only=on default_server;
2、极端方式：直接屏蔽IPv6，全部服务器都适用。

vim /etc/nginx/conf.d/default.conf
#找到并替换为以下：
listen 80;
#listen [::]:80 default_server;
最后直接在命令行下执行nginx即可启动成功。