    title: Windows环境搭建Red5流媒体服务器指南
    date: 2018-06-10 11:22:02
    tags: [ Gradle , b, c]
    description: Windows环境搭建Red5流媒体服务器指南
---

##测试环境：Windows 7

**一、**   **下载安装程序**

1. red5-server 下载地址

https://github.com/Red5/red5-server/releases

 

1. JDK 下载地址

http://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html

 

1. red5示例（如oflaDemo）下载地址，要FQ

http://red5.googlecode.com/svn/java/example/trunk/

 

1. flowplayer下载地址

https://codeload.github.com/flowplayer/flash/zip/release_3_2_18

http://releases.flowplayer.org/flowplayer.rtmp/flowplayer.rtmp-3.2.13.swf

 

**二、**   **安装JDK**

 

**三、**   **设置Java环境变量**

1)       在桌面用鼠标右键点击“计算机”，在弹出的菜单中选择“属性”选项，弹出“系统属性”窗口；

2)       在“系统属性”窗口，点击“高级”切换到高级系统设置Tab，然后点击

“环境变量”按钮，弹出“环境变量”窗口；

3)       在“环境变量”窗口，点击用户变量或者系统变更区域的“新建”按钮，弹出新建变量窗口，然后输入“变量名”：JAVA_HOME，　“变量值”：C:\Program Files\Java\jdk1.8.0_51。

​    注：“变量值”这一栏主要填写的是你安装JDK的路径，这里根据个人的情况可能会有所不同。

 

4)       上步结束之后，双击系统变量中的“Path”，在弹出的编辑系统变量窗口，

在“变量值”一栏的最前面添加如下的路径：

​    %Java_Home%\bin;%Java_Home%\jre\bin;

​    也可以用完全路径，如：C:\Program Files\Java\jdk1.8.0_51\\bin;

 

**四、**   **安装red5**

把下载的red5安装包解压（本指南下载的是Zip安装包），复制到要安装的目录，如F:\red5\Test\red5-server-1.0.5

 

**五、**   **设置red5环境变量**

根据设置Java环境变量的方法，添加red5_home和ClassPath

 

变量名：red5_home

变量值：F:\red5\Test\red5-server-1.0.5  （此处要根据你的安装目录调整）

 

变量名：ClassPath

变量值：.  （不配置此变量，或者此变更的值不是“.”，red5启动的过程会抛异常）

 

**六、**   **启动red5**

双击“red5.bat”文件，启动red5。

 

**七、**   **测试red5是否部署成功**

在浏览器中输入http://localhost:5080/，可成功打开，表示red5部署成功。

 

八、测试应用

将下载的oflaDemo.war文件解压后，放到red5部署目录中的webapps目录，如F:\red5\Test\red5-server-1.0.5\webapps。本指南测试时将目录名改成了oflaDemo2。

oflaDemo.war下载地址: http://pan.baidu.com/s/1hqAPl6O

 

重新启动red5服务器。

然后在浏览器中访问http://localhost:5080/oflaDemo2/，成功打开后，播放页面中的视频，如果顺利播放，表示应用部署成功。

 

注：如果在其它机器访问，将localhost改成服务器的IP即可。

 

**九、**   **在其它机器用FlowPlayer测试red5服务器上的视频播放**

将测试示例拷到要测试的机器，修改示例中的red5服务器地址和视频文件名称，在浏览器上打开测试示例中的flowplayer.html文件，看视频是否正常播放。

测试示例下载地址：http://pan.baidu.com/s/1dD8n8jf