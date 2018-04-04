# 前言
总结以Java开源技术栈为中心的面试题，从上层语言逐步深入到整个计算机结构中：）
# 目录
* [J2SE](#j2se)
* [J2EE](#j2ee)
* [DesignPattern](#designpattern)
* [JVM](#jvm)
* [Android](#android)
* [DataBase](#database)
* [OperationSystem](#operationsystem)
* [ComputerArchitecture](#computerarchitecture)
* [Network](#network)
* [Algorithm](#algorithm)

# J2SE
> 1.J2SE什么?

J2SE是Java 2 Standard Edition,J2SE就是Java2的标准版，主要用于桌面应用软件的编程.

> 2 抽象类接口区别(加入java1.8新特性)

<details>
<summary>展开查看答案</summary>

1. 接口能够多实现，而抽象类只能单独被继承，其本质就是，一个类能继承多个接口，而只能继承一个抽象类。

2. 方法上，抽象类的方法可以用abstract 和public或者protect修饰。而接口默认为public abttact 修饰。

3. 抽象类的方法可以有需要子类实现的抽象方法，也可以有具体的方法。而接口在老版本的jdk中，只能有抽象方法，但是Java8版本的接口中，接口可以带有默认方法。

4. 属性上，抽象类可以用各种各样的修饰符修饰。而接口的属性是默认的public static final

5. 抽象类中可以含有静态代码块和静态方法，而接口不能含有静态方法和静态代码块。

6. 抽象类可以含有构造方法，接口不能含有构造方法。

7. 设计层面上，抽象类表示的是子类“是不是”属于某一类的子类，接口则表示“有没有”特性“能不能”做这种事。如飞机和鸟都能飞，但是他们在设计上实现一个Fly接口，实现fly()方法。远比两个类继承飞行物抽象类好得多。因为，飞机和鸟有太多的属性不一样。

8. 设计层面上，另外一点，抽象类可以是一个模板，因为可以自己带集体方法，所以要加一个实现类都能有的方法，直接在抽象类中写出并实现就好，接口在以前的版本则不行。新版本Java8才有默认方法。

9. 既然说到Java 8 那么就来说明，Java8中的接口中的默认方法是可以被多重继承的。而抽象类不行。

10. 另外，接口只能继承接口。而抽象类可以继承普通的类，也能继承接口和抽象类。


</details>

# J2EE
# DesignPattern
> 1.策略模式是什么

[策略模式](https://github.com/StopWorld/StopInterview/tree/master/Design_Pattern/Strategy_Pattern)

# JVM
# Android
[Android基础](https://github.com/StopWorld/StopInterview/tree/master/Android/Basics)
# DataBase
# OperationSystem
# ComputerArchitecture
# Network
# Algorithm
