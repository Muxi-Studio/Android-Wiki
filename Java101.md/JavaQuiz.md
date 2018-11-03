# Java 学习过程中的一些quiz

## Java 基础部分
1. 输入两个数，要求能够输出这两个数的最大公约数和最小公倍数。
2. 将数组作为参数传递给一个方法，该方法将这个数组的元素全部显示出来。
3. 使用Java 手写一个快速排序/归并排序/堆排序
4. 用LinkedList(Java的一种数据结构)实现一个Stack 和 一个Queue（Stack 不使用JDK中的Stack类 Queue不是JDK中的接口 需要自己实现）
5. 自己使用接口完成一个``回调函数``，情景： 每个超级英雄又不一样的超能力，神奇女侠会飞行和神力，蝙蝠侠有洞察力等等..要求英雄Hero和 能力Power，能力作为一个接口，各个英雄是抽象类Hero的子类。 要求不同的英雄的能力 在使用的时候，``usePower()`` 有不同的表现``usePower()``是接口中的一个方法

## Java 多线程部分

# 动手实现Java数据结构

原生类库，可以用，但是没必要
- 实现一个ArrayList 增删查改
- 实现一个LinkedList 链表
- 实现一个二叉树 
- 实现一个二叉查找树
- 实现一个二叉查找树
- 实现一个最优二叉查找树
- 实现一个Stack 和 Queue 
 

# 读程序题

```


    import java.util.Scanner;

    public class Purchase {

    private double groundPrice;
    private int groundCount;
    private int numberBought;
    private String name;

    public void setName(String newName) {
        name = newName;
    }

    public void setPrice(int count, double costForCount) {
        if ((count <= 0) || (costForCount <=  0)) {
            System.out.println("");
            System.exit(0);
        } else {
            groundCount = count;
            groundPrice = costForCount;
        }
    }

    public void setNumberBought(int number) {
        if (number <= 0) {
            System.out.println("");
            System.exit(0);
        } else
            numberBought = number;
    }

    public void readInput() {
        Scanner keyboard = new Scanner(System.in);
        System.out.println("Enter name of item you are purchasing: ");
        name = keyboard.nextLine();
        System.out.println("Enter price of item as two numbers.");
        System.out.println("For example, 3 for $2.99 is entered as");
        System.out.println("3 2.99");
        System.out.println("Enter price of item as two numbers, now:");
        groundCount = keyboard.nextInt();
        groundPrice = keyboard.nextDouble();
        while (groundCount <= 0 && groundPrice <= 0) {
            System.out.println("Both numvers must be positive. Try again.");
            System.out.println("Enter price of item as two numbers.");
            System.out.println("For example, 3 for $2.99 is entered as");
            System.out.println("3 2.99");
            System.out.println("Enter price of item as two numbers, now:");
            groundCount = keyboard.nextInt();
            groundPrice = keyboard.nextDouble();
        }

        System.out.println("please enter the number bought");
        numberBought = keyboard.nextInt();
        while (numberBought <= 0) {
            System.out.println("");
            System.out.println("");
            numberBought = keyboard.nextInt();
        }
        writeOutput();
    }

    public void writeOutput() {
        System.out.println(numberBought + " " + name);
        System.out.println("at " + groundCount + "for $" + groundPrice);
    }

    public String getName() {
        return name;
    }

    public double getTotalCost() {
        return ((groundPrice / groundCount) * numberBought);
    }

    public double getUnitCost() {
        return (groundPrice / groundCount);
    }

    public int getNumberBought() {
        return numberBought;
    }

（1）变量 groundCount、 groundPrice、numberBought 分别代表什么？

（2）总结上述代码中出现的类的特点(如信息是如何传递的之类,越多越好)

（3）你认为这个程序是用来做什么的？

（4） 写一个调用purchase类实现其功能的主函数

```
