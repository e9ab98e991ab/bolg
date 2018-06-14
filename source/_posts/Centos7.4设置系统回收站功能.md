    title: Centos7.4设置系统回收站功能
    date: 2018-03-10 11:22:02
    tags: [ Centos , b, c]
    description: Centos7.4设置系统回收站功能详解
---

linux rm删除文件之后，恢复就比较麻烦了，即使恢复了，文件名格式都变成一串数字了。

修改root用户的环境变量

```
vim ~/.bashrc
```

注释第5行的别名

```
#alias rm='rm -i'1
```

最后一行添加如下内容

```
mkdir -p ~/.trash
alias rm=trash
alias r=trash
alias rl='ls ~/.trash'
alias ur=undelfile
undelfile()
{
  mv -i ~/.trash/$@ ./
}
trash()
{
  mv $@ ~/.trash/
}

cleartrash()
{
    read -p "clear sure?[n]" confirm
    [ $confirm == 'y' ] || [ $confirm == 'Y' ]  && /bin/rm -rf ~/.trash/*
}12345678910111213141516171819
```

重新加载环境变量

source ~/.bashrc

使用命令ll -a查看目录，发现多了目录.trash，这个目录是用来存在删除的文件

```
drwxr-xr-x.  2 root root       4096 Jun  4 11:31 .trash1
```

删除一个文件

```
[root@localhost ~]# rm percona-xtrabackup_2.2.3.orig.tar.gz1
```

查看目录，发现删除的文件在回收站目录

```
[root@localhost ~]# ll .trash/
total 33780
-rw-r--r--. 1 root root 34584359 Jun  2 09:39 percona-xtrabackup_2.2.3.orig.tar.gz123
```

如果需要清空回收站文件 
使用以下命令

```
[root@localhost ~]# cleartrash
clear sure?[n]y12
```

再次查看，发现空了。

```
[root@localhost ~]# ll .trash/
total 0
123
```

虽然rm用别名定义了，但是可以是用绝对路径删除文件 
比如 
`/bin/rm 1.txt` 
它是不会保存到.trash目录的。

如果需要定义自动清理7天删除的文件 
可以写一个脚本

```
#!/bin/bash

find /root/.trash -ctime 7 -type f -name "*" -exec /bin/rm {} \;123
```

然后在任务计划里面调用一下就可以了。

如果Linux除了root用户，还有其他用户需要登陆服务器,也想他们使用回收站机制 
可以修改系统环境变量

```
vi /etc/profile1
```

最后一行添加

```
mkdir -p ~/.trash
alias rm=trash
alias r=trash
alias rl='ls ~/.trash'
alias ur=undelfile
undelfile()
{
  mv -i ~/.trash/$@ ./
}
trash()
{
  mv $@ ~/.trash/
}

cleartrash()
{
    read -p "clear sure?[n]" confirm
    [ $confirm == 'y' ] || [ $confirm == 'Y' ]  && /bin/rm -rf ~/.trash/*
}12345678910111213141516171819
```

重新加载环境变量

```
source /etc/profile1
```

创建普通用户测试

```
useradd a1
```

设置密码

```
passwd a1
```

登陆Linux 
查看目录，发现会创建.trash目录

```
[a@localhost ~]$ ll -a
total 24
drwx------. 3 a    a    4096 Jun  4 11:45 .
drwxr-xr-x. 5 root root 4096 Jun  4 11:44 ..
-rw-r--r--. 1 a    a      18 Oct 16  2014 .bash_logout
-rw-r--r--. 1 a    a     176 Oct 16  2014 .bash_profile
-rw-r--r--. 1 a    a     124 Oct 16  2014 .bashrc
drwxrwxr-x. 2 a    a    4096 Jun  4 11:45 .trash12345678
```

创建一个空文件

```
[a@localhost ~]$ touch 1.txt1
```

删除文件

```
[a@localhost ~]$ rm 1.txt1
```

查看回收站目录，发现多了一个文件

```
[a@localhost ~]$ ll .trash/
total 0
-rw-rw-r--. 1 a a 0 Jun  4 11:45 1.txt
```