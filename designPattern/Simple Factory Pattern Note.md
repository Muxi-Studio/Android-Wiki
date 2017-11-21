## 实例

```java
//抽象产品类
public interface Chart{
  void display();
}


//具体产品类
public class HistogramChart implements Chart{
  
  public HistogramChart(){
    System.out.println("create HistogramChart");
  }
  
  public void display(){
    System.out.println("display HistogramChart");
  }
}


public class PieChart implements Chart{
  
  public PieChart(){
    System.out.println("create PieChart");
  }
  
  public void display(){
    System.out.println("display PieChart");
  }
}


//工厂类
public class ChartFactory{
  
  public static Chart getChart(String type){
    Chart chart = null;
    if (type.equals("histogram"){
      chart = new HistogramChart();
    } else if (type.equals("pie"){
      chart = new PieChart();
    }
    
    return chart;
  }
}



public class Client{
  public static void main(String[] args){
    Chart chart;
    chart = ChartFactory.getChart("histogram");
    chart = ChartFactory.getChart("pie");
  }
}
```

## 简单工厂模式总结
### 优点
1. 简单工厂模式实现了对象创建和使用的分离。
2. 客户端无需知道所创建的具体产品类的类名，只需要知道具体产品类所对应的参数即可。
3. 通过引入配置文件，可以在不修改任何客户端代码的情况下更换和增加新的具体产品类

### 缺点
1. 由于工厂类集中了所有产品的创建逻辑，职责过重
2. 系统拓展困难
3. 由于使用了静态工厂方法，造成工厂角色无法形成基于继承的等级结构

### 适用场景
1. 工厂类负责创建的对象比较少
2. 客户端只知道传入工厂类的参数，对于如何创建对象并不关心

