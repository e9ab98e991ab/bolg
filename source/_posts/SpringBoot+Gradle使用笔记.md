    title: springboot+Gradle使用笔记
    date: 2018-03-10 11:22:02
    tags: [ springboot , Gradle, 笔记]
    description: Gradle使用笔记
---

#生成 gradle 结构树

```gradle
gradlew dependencies
```

## springboot gradle 构建多模块项目

#### 第一步 在主项目中 **settings.gradle** 文件，引入子模块 

```gradle
includeFlat 'modules' 
```

#### 第二步 在主项目中 build.gradle文件，引入子模块 

```gradle
compile project(':modules')
```
#####注

[^1]: includeFalt 导入同目录下的library包
[^2]: inclode 导入父类下面所有子类library包

## springboot gradle 中导入jar包

```gradle
1、需要在项目与src同级的目录下创建libs 在libs下放jar包
2、在build.gradle配置：dependencies { compile files('lib/ojdbc-14.jar')}
3、dependencies { compile fileTree(dir:'libs',include:['*.jar'])}
```

