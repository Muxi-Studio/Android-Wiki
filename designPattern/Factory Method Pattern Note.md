## 定义
> 工厂方法模式：定义一个用于创建对象的接口，让子类决定哪一个类实例化。工厂方法模式让一个类的实例化延迟到其子类。工厂方法模式又称为工厂模式或者多态工厂模式。

## 适用场景
1. 客户端不需要其所需要的对象的类，只需要知道对应的工厂即可。
2. 抽象工厂通过其子类来指定创建哪个对象，运行时，子类对象覆盖父类对象，使得程序更容易扩展。

## 结构图
![Factory Method](http://oq8w2ddi6.bkt.clouddn.com/dp:factory.png)

## 实例

```java
//抽象产品
interface Logger{
  void writeLog();
}

//具体产品
class DatabaseLogger implements Logger{
  @Override
  public void writeLog(){
    System.out.println("数据库日志记录");
  }
}


class FileLogger implements Logger{
  @Override
  public void writeLog(){
    Systme.out.println("文件日志记录");
  }
}

//抽象工厂
interface LoggerFactory{
  Logger createLogger();
}

//具体工厂
class DatabaseLoggerFactory implements LoggerFactory{
  @Override
  public Logger createLogger(){
    return new DatabaseLogger();
  }
}


class FileLoggerFactory implements LoggerFactory{
  @Override
  public Logger createLogger(){
    return new FileLogger();
  }
}


public class Client{
  public static void main(String[] args){
    LoggerFactory factory;
    Logger logger;
    factory = new DatabaseLoggerFactory();
    logger = factory.createLogger();
    logger.writeLog();
  }
}
```

## 工厂方法模式总结
### 优点
1. 在工厂方法模式中，工厂方法用来创建客户所需要的产品，用户只需要关心所需产品对应的工厂，无需关心创建细节，甚至无需知道具体产品类的类名。
2. 基于工厂角色和产品角色的多态性设计是工厂方法模式的关键。工厂能够自主确定创建何种产品对象，而如何创建这个对象的细节则完全封装在具体工厂内部。
3. 同时当加入新产品时，无需修改抽象工厂和抽象产品提供的接口，也无需修改具体的工厂和具体的产品类，只需要添加相应的具体工厂和具体产品即可，拓展性较好，符合开闭原则。


### 缺点
1. 添加新产品编写新的具体产品类和对应的具体工厂类，有更多的类需要编译和运行，会给系统带来额外的开销。
2. 因为具有较好的可拓展性，在客户端代码中均使用抽象层进行定义，增加了系统的抽象性和理解难度。

