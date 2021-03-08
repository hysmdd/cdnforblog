---
title: Java 设计模式-1
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://www.zhengyuanyuan520.com
categories: Java
date: 2020-10-20 20:40:00
comments: true
---

1.设计模式原则 

2.设计模式分类 

3.常用设计模式

4.工厂模式定义

5.工厂模式类图 

6.工厂模式示例 

7.工厂模式应用

8.抽象工厂模式定义 

9.抽象工厂模式类图 

10.抽象工厂模式示例 

11.抽象工厂模式应用 

12.工厂方法模式、抽象工厂模式区别

<!-- more -->



# 什么是设计模式

在软件工程中，设计模式是对软件设计中普遍存在的各种问题，所提出的解决方案。

换句话说，设计模式是一套被反复使用、多数人知晓的、经过分类的、代码设计的经验的总结。使用设计模式是为了可重用代码，让代码更容易被他人理解，保证代码可靠性。

# 设计模式原则

## 开闭原则

开闭原则的意思是：`对扩展开放，对修改封闭`。在程序需要进行扩展的时候，不能去修改或影响原有的代码，实现一个热插拔的效果。简言之，是为了使程序的扩展性更好，易于维护和升级。想要达到这样的效果，我们需要使用接口和抽象类。

## 里氏代换原则

里氏代换原则是面向对象设计的基本原则之一。 里氏代换原则中说，任何基类可以出现的地方，子类一定可以出现。里氏代换原则是继承复用的基石，只有当子类可以替换掉基类，且软件单位的功能不受到影响时，基类才能真正被复用，而且子类也能够在基类的基础上增加新的行为。里氏代换原则是对开闭原则的补充。实现开闭原则的关键步骤就是抽象化，而基类与子类的继承关系就是抽象化的具体实现，所以里氏代换原则是对实现抽象化的具体步骤的规范。

## 依赖倒转原则

这个原则是开闭原则的基础，核心内容：针对接口编程，高层模块不应该依赖底层模块，二者都应该依赖抽象而不依赖于具体。

## 接口隔离原则

这个原则的意思是：使用多个隔离的接口，比使用单个庞大的接口要好。其目的在于降低耦合度。由此可见，其实设计模式就是从大型软件架构出发，便于升级和维护软件的设计思想。它强调低依赖、低耦合。

## 单一职责原则

类的职责要单一，不能将太多的职责放在一个类中。

可能有的人会觉得单一职责原则和前面的接口隔离原则很相似，其实不然。其一，单一职责原则原注重的是职责；而接口隔离原则注重对接口依赖的隔离。其二，单一职责原则主要约束的是类，其次才是接口和方法，它针对的是程序中的实现和细节；而接口隔离原则主要约束接口，主要针对抽象，针对程序整体框架的构建。

## 最少知道原则

最少知道原则也叫迪米特法则，就是说：一个实体应当尽量少的与其他实体之间发生相互作用，使得系统功能模块相对独立。

一个对象应该对其他对象保持最少的了解。类与类之间的关系越密切，耦合度越大，当一个类发生改变时，对另一个类的影响也越大。如果两个类不必彼此直接通信，那么这两个类就不应当发生直接的相互作用。如果其中一个类需要调用另一个类的某一个方法的话，可以通过第三者转发这个调用。所以在类的设计上，每一个类都应当尽量降低成员的访问权限。

## 合成复用原则

合成复用原则就是在一个新的对象里通过关联关系（组合关系、聚合关系）来使用一些已有的对象，使之成为新对象的一部分；新对象通过委派调用已有对象的方法达到复用功能的目的。简而言之，尽量多使用`组合/聚合`的方式，尽量少使用甚至不使用继承关系。

# 设计模式分类

通常来说设计模式分为三大类：

- **创建型模式**，共 5 种：工厂模式、抽象工厂模式、单例模式、建造者模式、原型模式。
- **结构型模式**，共 7 种：适配器模式、装饰器模式、代理模式、外观模式、桥接模式、组合模式、享元模式。
- **行为型模式**，共 11 种：策略模式、模板方法模式、观察者模式、迭代子模式、责任链模式、命令模式、备忘录模式、状态模式、访问者模式、中介者模式、解释器模式。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020190940.png)

# 什么是工厂模式

> 工厂模式（Factory Pattern）的意义就跟它的名字一样，在面向对象程序设计中，工厂通常是一个用来创建其他对象的对象。工厂模式根据不同的参数来实现不同的分配方案和创建对象。

在工厂模式中，我们在创建对象时不会对客户端暴露创建逻辑，并且是通过使用一个`共同的接口`来指向新创建的对象。例如用工厂来创建 `人` 这个对象，如果我们需要一个男人对象，工厂就会为我们创建一个男人；如果我们需要一个女人，工厂就会为我们生产一个女人。

工厂模式通常分为：

- 普通工厂模式
- 多个工厂方法模式
- 静态工厂方法模式

# 普通工厂模式

刚刚我们说到，用工厂模式来创建人。先创建一个男人，他每天都“吃饭、睡觉、打豆豆”，然后我们再创建一个女人，她每天也“吃饭、睡觉、打豆豆”。

我们以普通工厂模式为例，在 project 目录下新建一个`FactoryTest.java`。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020191237.png)

```java
// 二者共同的接口
interface Human{
    public void eat();
    public void sleep();
    public void beat();
}

// 创建实现类 Male
class Male implements Human{
    public void eat(){
        System.out.println("Male can eat.");
    }
    public void sleep(){
        System.out.println("Male can sleep.");
    }
    public void beat(){
        System.out.println("Male can beat.");
    }
}
//创建实现类 Female
class Female implements Human{
    public void eat(){
        System.out.println("Female can eat.");
    }
    public void sleep(){
        System.out.println("Female can sleep.");
    }
    public void beat(){
        System.out.println("Female can beat.");
    }
}

// 创建普通工厂类
class HumanFactory{
    public Human createHuman(String gender){
        if( gender.equals("male") ){
           return new Male();
        }else if( gender.equals("female")){
           return new Female();
        }else {
            System.out.println("请输入正确的类型！");
            return null;
        }
    }
}

// 工厂测试类
public class FactoryTest {
    public static void main(String[] args){
        HumanFactory factory = new HumanFactory();
        Human male = factory.createHuman("male");
        male.eat();
        male.sleep();
        male.beat();
    }
}
```

## 编译运行

```powershell
javac FactoryTest.java
java FactoryTest
```

## 运行结果

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020193135.png)

# 多个工厂方法模式

普通工厂模式就是上面那样子了，那么多个工厂方法模式又有什么不同呢？在普通工厂方法模式中，如果传递的字符串出错，则不能正确创建对象。多个工厂方法模式是提供多个工厂方法，分别创建对象。

```java
package 设计模式;

//两者共同的接口
interface Human {
	public void eat();

	public void sleep();

	public void beat();
}

//创建实现类Male
class Male implements Human {
	public void eat() {
		System.out.println("Male can eat.");
	}

	public void sleep() {
		System.out.println("Male can sleep.");
	}

	public void beat() {
		System.out.println("Male can beat.");
	}
}

//创建实现类Female
class Female implements Human {
	public void eat() {
		System.out.println("Female can eat.");
	}

	public void sleep() {
		System.out.println("Female can sleep.");
	}

	public void beat() {
		System.out.println("Female can beat.");
	}
}

//多个工厂方法
class HumanFactory {
	public Male CreateMale() {
		return new Male();
	}

	public Female createFemale() {
		return new Female();
	}
}

//工厂测试类
public class FactoryTest2 {
	public static void main(String args[]) {
		HumanFactory factory = new HumanFactory();
		Human maleHuman = factory.CreateMale();
		maleHuman.eat();
		maleHuman.sleep();
		maleHuman.beat();
	}
}
```

## 编译运行

```
javac FactoryTest2.java
java FactoryTest2
```

## 运行结果

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020194538.png)

# 静态工厂方法模式

将上面的多个工厂方法模式里的方法置为静态的，不需要创建实例，直接调用即可。

```java
package 设计模式;

//两者共同的接口
interface Human {
	public void eat();

	public void sleep();

	public void beat();
}

//创建实现类Male
class Male implements Human {
	public void eat() {
		System.out.println("Male can eat.");
	}

	public void sleep() {
		System.out.println("Male can sleep.");
	}

	public void beat() {
		System.out.println("Male can beat.");
	}
}

//创建实现类Female
class Female implements Human {
	public void eat() {
		System.out.println("Female can eat.");
	}

	public void sleep() {
		System.out.println("Female can sleep.");
	}

	public void beat() {
		System.out.println("Female can beat.");
	}
}

//多个工厂方法
class HumanFactory{
 public static Male createMale() {
     return new Male();
 }
 public static Female createFemale() {
     return new Female();
 }
}

//工厂测试类
public class FactoryTest2 {
 public static void main(String[] args){
     Human male = HumanFactory.createMale();
     male.eat();
     male.sleep();
     male.beat();
 }
}
```

总结：凡是出现了大量的产品需要创建，并且具有共同的接口时，可以通过工厂方法模式进行创建。在以上的三种模式中，第一种如果传入的字符串有误，不能正确创建对象，第三种相对于第二种，不需要实例化工厂类，所以，大多数情况下，我们会选用第三种——静态工厂方法模式。

# 什么是抽象工厂模式

抽象工厂模式（Abstract Factory Pattern）是一种软件开发设计模式。抽象工厂模式提供了一种方式，可以将一组具有同一主题的单独的工厂封装起来。如果比较抽象工厂模式和工厂模式，我们不难发现前者只是在工厂模式之上增加了一层抽象的概念。抽象工厂是一个父类工厂，可以创建其它工厂类。所以我们也叫它 “工厂的工厂”。

# 抽象工厂模式类图

“女娲娘娘”只有一个，而我们的工厂却可以有多个，因此在这里用作例子就不合适了。作为“女娲娘娘”生产出来的男人女人们，那就让我们来当一次吃货吧。（吃的东西总可以任性多来一点）

现在，假设我们有 A、B 两个厨房。每个厨房拥有的餐具和食品都不一样，但是用户搭配使用的方式，比如刀子和苹果、杯子和牛奶等等，我们假设是一致的。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020200923.png)

```java
package 抽象工厂模式;

//抽象食物
interface Food{
	public String getFoodName();
}

//抽象餐具
interface TableWare{
	public String getToolName();
}
//抽象工厂
interface KitchenFactory{
	public Food getFood();
	public TableWare getTableWare();
}

//具体食物 Apple 的定义如下
class Apple implements Food{
	@Override
	public String getFoodName() {
		return "apple";
	}
}

//具体餐具 Knife 的定义如下
class Knife implements TableWare{
	@Override
	public String getToolName() {
		return "knife";
	}
}

//以具体工厂 AKitchen 为例
class AKitchen implements KitchenFactory{
	@Override
	public Food getFood() {
		return new Apple();
	}
	@Override
	public TableWare getTableWare() {
		return new Knife();
	}
}

//吃货要开吃了
public class Foodaholic {
	public void eat(KitchenFactory kitchenFactory) {
		System.out.println("A foodaholic is eating " + kitchenFactory.getFood().getFoodName() + " with " + kitchenFactory.getTableWare().getToolName());
	}
	
	public static void main(String[] args) {
		Foodaholic foodaholic = new Foodaholic();
		KitchenFactory kitchenFactory = new AKitchen();
		foodaholic.eat(kitchenFactory);
		
	}
	
}
```

## 编译运行

```
javac Foodaholic.java
java Foodaholic
```

## 运行结果

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020203200.png)

抽象工厂模式特别适合于这样的一种产品结构：产品分为几个系列，在每个系列中，产品的布局都是类似的，在一个系列中某个位置的产品，在另一个系列中一定有一个对应的产品。这样的产品结构是存在的，这几个系列中同一位置的产品可能是互斥的，它们是针对不同客户的解决方案，每个客户都只选择其一。

# 工厂方法模式、抽象工厂模式区别

工厂方法模式、抽象工厂模式，傻傻分不清楚。

为了解释得更清楚，先介绍两个概念：

- **产品等级结构**：比如一个抽象类是食物，其子类有苹果、牛奶等等，则抽象食物与具体食物名称之间构成了一个产品等级结构。食物是抽象的父类，而具体的食物名称是其子类。
- **产品族**：在抽象工厂模式中，产品族是指由同一个工厂生产的，位于不同产品等级结构中的一组产品。如 AKitchen 生产的苹果、刀子，苹果属于食物产品等级结构中，而刀子则属于餐具产品等级结构中。而 BKitchen 可能生成另一组产品，如牛奶、杯子。

因此工厂方法模式、抽象工厂模式最大的区别在于：

工厂方法模式：针对的是 **一个产品等级结构**。

抽象工厂模式：针对 **多个产品等级结构**。

# 什么是适配器模式

顾名思义，适配器模式（Adapter Pattern）当然是用来适配的啦。当你想使用一个已有的类，但是这个类的接口跟你的又不一样，不能拿来直接用，这个时候你就需要一个适配器来帮你了。

这就好像你兴冲冲地跑去香港，买了个港版的 iPhone6，充电器插头拿回家一看，不能用啊。这时候你多么需要买一个转接头适配器...

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020223507.png)

你去香港旅游，买的 iPhone6 的充电器插头是英标的，它是那种三脚是方形的插头。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020223608.png)

而咱们国标的插头是两只脚，即使是三只脚的插头也和英标不一样。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020223722.png)

为了方便，这里我们就假设国标插头就只是两只脚的插头吧。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020223745.png)

好的，目标明确，英标三只脚插头充电，国标两只脚插头充电。你家很富，有很多插座可以充电。

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/20201020223805.png)

在国内的家中只能用国标接口进行充电。

```java

// 国标插头
public interface CnPluginInterface {
    void chargeWith2Pins();
}

// 实现国标插座的充电方法
public class CnPlugin implements CnPluginInterface {
    public void chargeWith2Pins() {
        System.out.println("charge with CnPlugin");
    }
}

// 在国内家中充电
public class Home {  
    private CnPluginInterface cnPlugin;

    public Home() { }

    public Home(CnPluginInterface cnPlugin) {
        this.cnPlugin = cnPlugin;
    }

    public void setPlugin(CnPluginInterface cnPlugin) {
        this.cnPlugin = cnPlugin;
    }

    // 充电
    public void charge() {
        // 国标充电
        cnPlugin.chargeWith2Pins();
    }
}

// 国标测试类
public class CnTest {
    public static void main(String[] args) {
        CnPluginInterface cnPlugin = new CnPlugin();
        Home home = new Home(cnPlugin);
        // 会输出 “charge with CnPlugin”
        home.charge();
    }
}
```

然而，当把 iPhone6 带回来时，因为与家里的插座不匹配，所以需要一个适配器。这个适配器必须满足以下条件：

> 1. 插头必须符合国内标准的接口，否则的话还是没办法插到国内插座中。
> 2. 在调用上面实现的国标接口进行充电时，提供一种机制，将这个调用转到对英标接口的调用 。

这就要求：

> 1. 适配器必须实现原有的旧的接口。
> 2. 适配器对象中持有对新接口的引用，当调用旧接口时，将这个调用委托给实现新接口的对象来处理，也就是在适配器对象中组合一个新接口。

```java
// 英标插头
public interface EnPluginInterface {
    void chargeWith3Pins();
}

// 实现英标插座的充电方法
public class EnPlugin implements EnPluginInterface {
    public void chargeWith3Pins() {
        System.out.println("charge with EnPlugin");
    }
}

//适配器
public class PluginAdapter implements CnPluginInterface {
     private EnPluginInterface enPlugin;

     public PluginAdapter(EnPluginInterface enPlugin) {
         this.enPlugin = enPlugin;
 }

 // 这是重点，适配器实现了国标的插头，然后重写国标的充电方法，在国标的充电方法中调用英标的充电方法
 @Override
public void chargeWith2Pins() {
    enPlugin.chargeWith3Pins();
     }
}

// 适配器测试类
public class AdapterTest {
    public static void main(String[] args) {
        EnPluginInterface enPlugin = new EnPlugin();
        Home home = new Home();
        PluginAdapter pluginAdapter = new PluginAdapter(enPlugin);
        home.setPlugin(pluginAdapter);
        // 会输出 “charge with EnPlugin”
        home.charge();
    }
}
```

# 适配器模式的三个特点

- 适配器对象实现原有接口
- 适配器对象组合一个实现新接口的对象（这个对象也可以不实现一个接口，只是一个单纯的对象）
- 对适配器原有接口方法的调用被委托给新接口的实例的特定方法