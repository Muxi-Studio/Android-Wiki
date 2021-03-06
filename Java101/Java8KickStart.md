# Java 8 kick start!


##  完成这个lab之前 你需要掌握的：

- Java 泛型机制
- Java 匿名内部类
- Java Scanner 类 
- Java 文件流

因为Java8 是目前在最新的版本中使用的最为广泛的一种jdk 版本， 所以掌握其中的新鲜的卖点是非常重要和关键的。
关于Java8的特性，可以参考[这篇文章(http://www.importnew.com/11908.html#lambdaAndFunctional)

## 需要掌握的要点的笔记

<br>
为了便于同学们了解和学习函数式编程或者说使用一些类似于使用了函数式编程思想的库，我们的主要焦点在Java8 提供的lamda 和 Stream 这两个特性上。
<br>

要求：

## 
使用Java8 Stream api 尽可能快速的将[hamlet.txt](https://gist.github.com/provpup/2fc41686eab7400b796b) 
这篇文档中的单词做一个``letter count``，并且需要进行排序：<br>

``letter count``: 一段话中出现的字母的次数： 不包括空格或者其他标点符号,大写字母小写字母一起处理,并且排序
example:

原文 ： I am Batman
```
 a 3
 b 1
 ..
 m 2
```

### 几点注意事项
- ``letter Count`` 中的单词应该全是小写的。 比如 ``hamlet`` 和 ``Hamlet`` 应该视作一个单词处理。
- 这个lab的评分标准是按照程序的运行时间拟定的，运行时间越长得分越低
- 必须使用Stream 去进行流处理 
- 并行流处理 会提高效率吗？
- 如何读取 文档的速度最快呢？

### 代码格式
- 在提交的jar包中，真正进行wordcount的 java 类名应命名为 ``LetterCount`` 进行``letter count`` 的函数 应命名为 ``letterCount`` 

tips: 我们应当从那几点削减运行的时间<br>
- 提交的时候是提交的一个jar 文件 这个jar将会通过 测试程序进行测试，主要测试``已经编译好的class文件``运行时间 
- 读取文件的方法？ 使用尽量高效率的读取算法
- 字符分割的算法 还是使用原生类
- wordcount 的 算法？ 如何优化?
- 怎么通过数据结构优化
- 内存方面随意使用

## 提交流程

- 命令行中使用``ssh ubuntu@132.232.255.156`` 登录上 石泽远的云服务器，密码是TXszypride666 
- 你的class文件的名称为``LetterCount``
- 将本地的完成的结果 变成.class 文件，通过``  scp LetterCount.class ubuntu@132.232.255.156:kolibreath/xxx``目录下面,自己去创建一个自己的目录，比如我创建的目录的名称是``kolibreathExample`` 可以调用已经有的``hamlet.txt``的路径，也可以自己将自己的hamlet.txt上传，说明这一点是需要规避找不到文件的异常
- 运行``java -jar wordCount.jar  xxxxx`` 获取运行结果
xxxxx是你的class 文件的路径
<br>
wordCount.jar 在/home/ubuntu/kolibreath 路径下

> hints
- 可以参考我写的代码，在``kolibreathExample``下，不一定正确 
- 用来测试的jar 是用反射调用你的函数，函数名称不正确会错误