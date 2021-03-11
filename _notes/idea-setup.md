

git clone https://github.com/apache/jmeter.git


JMeter5.2开始，使用gradle代替了原来ant
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



run GUI
```
  ./gradlew runGui
```

build
```
  ./gradlew build
```

## Debug in IntelliJ

http://benjaminhuanghuang.blogspot.com/2020/09/how-to-run-build-debug-jmeter-in.html

GUI entry: 
```
  java/org/apache/jmeter/NewDriver.java
```
