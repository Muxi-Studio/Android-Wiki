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
这篇文档中的单词做一个word count，并且需要进行排序：<br>
example:

原文 ： to be or not to be is a question
```
a  1
be 2 
.
. 
to 2
.
```

### 几点注意事项
- wordCount 中的单词应该全是小写的。 比如 hamlet 和 Hamlet 应该视作一个单词处理。
- 这个lab的评分标准是按照程序的运行时间拟定的，运行时间越长得分越低
- 必须使用Stream 去进行流处理 
- 并行流处理？

### 代码格式
- 在提交的jar包中，真正进行wordcount的 java 类名应命名为 WordCount 进行wordCount 的函数 应命名为 wordCountStream() （或者 继承接口的方式？？）

tips: 我们应当从那几点削减运行的时间<br>
- 读取文件的方法？ 使用尽量高效率的读取算法
- 字符分割的算法 还是使用原生类
- wordcount 的 算法？ 如何优化?
- 内存方面随意使用

## 提交流程

- 命令行中使用``ssh ubuntu@132.232.255.156`` 登录上 石泽远的云服务器，密码是TXszypride666 
- 将本地的完成的结果 打包为jar 文件，通过`` sudo scp -r xxx.jar（你的jar的名字） ubuntu@132.232.255.156:kolibreath/javaStream``目录下面
- 运行``java Test ~/kolibreath/javaStream/xxx.jar`` 获取运行结果