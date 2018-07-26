    title: springBoot利用Idea打包部署
    date: 2018-06-19
    tags: [springBoot,Artifacts,idea]
    description: springBoot利用Idea打包部署
---

**1,在项目上鼠标右键 --> Open Module Settings**


![img](/springBoot利用Idea打包部署/998529-20160929164617969-1066189780.png)

**2, Artifacts --> + --> JAR --> From modules with dependencies...**

**![img](/springBoot利用Idea打包部署/998529-20160929165026906-589079232.png)**

**3, Main Class是你这个项目(脚本)的主方法,就是要运行的类,选一个**

**![img](/springBoot利用Idea打包部署/998529-20160929165136203-124464870.png)**

**4,如下图,设置 META-INF/MANIFEST.MF**

**!!!!!切记,不能用默认的(起码我用默认的是不成功的)!!!!!**

![img](/springBoot利用Idea打包部署/998529-20160929165409344-54984498.png)

**6,选中你这个项目的根目录,一定要放在根目录下**

![img](/springBoot利用Idea打包部署/998529-20160929165602922-1728699131.png)

**7,设置完是这样子的,关于 JAR files from libraries的两个选项:**

**选中第一个的话,打完包后是一个jar包**

**选中第二个的话,打完包后是一个jar包,外带你项目所用的jar包,个人推荐第二个**

**![img](/springBoot利用Idea打包部署/998529-20160929165729844-141512479.png)**

**8,设置完后就可以点OK了**

**9,这个页面, Build on make打上勾,其他的不一样也没事**

**![img](/springBoot利用Idea打包部署/998529-20160929170231656-2012788781.png)**

**10,最后一步, Build Artifacts... --> XXX.jar --> Build**

**![img](/springBoot利用Idea打包部署/998529-20160929170405078-2125381157.png)**

![img](/springBoot利用Idea打包部署/998529-20160929170504891-1525363776.png)

**11,复制这里的路径去找jar包就行**

**![img](/springBoot利用Idea打包部署/998529-20160929170637047-1227588275.png)**

 