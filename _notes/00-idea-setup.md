

git clone https://github.com/apache/jmeter.git


JMeter5.2开始，使用gradle代替了原来ant, 网上看到的文章都是ant版本的
With Apache JMeter 5.2 the sources have been migrated to Git.


按照JMeter官方文档
Building JMeter
  - https://jmeter.apache.org/building.html

  - https://github.com/apache/jmeter/blob/master/CONTRIBUTING.md#intellij


```
Open the build.gradle.kts file with IntelliJ IDEA and choose "Open as Project"

Make sure "Create separate module per source set" is selected

Make sure "Use default gradle wrapper" is selected

In the "File already exists" dialogue, choose "Yes" to overwrite

In the "Open Project" dialogue, choose "Delete Existing Project and Import"
```

但是我Open `build.gradle.kts` 时并无UI弹出让我选择 "Create separate module per source set", 
搜到 一篇文章 "When I import a grade build file into IDEA it doesn’t give me a pop up to change the settings"
https://www.reddit.com/r/IntelliJIDEA/comments/d2hso3/when_i_import_a_grade_build_file_into_idea_it/

再搜索到
https://krjura.wordpress.com/2020/08/03/intellij-idea-disable-create-separate-module-per-source-set/


## build
```
  ./gradlew build
```
build后jmeter自身的核心jar放在lib\ext下，由jmeter自己加载



## run GUI
```
  ./gradlew runGui
```





## Debug in IntelliJ

http://benjaminhuanghuang.blogspot.com/2020/09/how-to-run-build-debug-jmeter-in.html


由于制成品的jmeter在jmeter\bin启动，工作路径也就是jmeter\bin，因此代码中会取上层目录为项目路径，

而在IDE下启动，工作路径为jmeter，因此启动报错。解决的办法有两种，一种是修改源码 
java/org/apache/jmeter/NewDriver.java
```
  JMETER_INSTALLATION_DIRECTORY="/Users/bhuang/study/jmeter";
```
另一种是在启动时加参数 -Djmeter.home=jmeter项目路径


GUI entry: 
```
  java/org/apache/jmeter/NewDriver.java
```
找jemeter的本地安装路径，这里对mac的操作系统作了特别处理。
找到安装路径后，这里开始筛选bin里面的jar包，然后使用DynamicClassLoader加载。
设置新的系统属性，加载类org.apache.jmeter.JMeter，执行”start“方法。jmeter启动。
