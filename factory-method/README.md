---
layout: pattern
title: Factory Method
folder: factory-method
permalink: /patterns/factory-method/
pumlid: NSZB3G8n30N0Lg20n7UwCOxPP9MVx6TMT0zdRgEvjoazYeRrMmMsFuYChtmqr7Y6gycQq8aiQr3hSJ7OwEGtfwBUZfas0shJQR3_G2yMBFkaeQYha4B-AeUDl6FqBm00
categories: Creational
tags:
 - Java
 - Difficulty-Beginner
 - Gang Of Four
---

## Also known as
Virtual Constructor

## Intent
定义创建对象的接口，但让子类决定实例化哪个类。 工厂方法让班级推迟实例化到子类。
Define an interface for creating an object, but let subclasses
decide which class to instantiate. Factory Method lets a class defer
instantiation to subclasses.

## Explanation
Real world example
> 铁匠制造武器。 精灵需要精灵武器和兽人需要兽人武器。 根据手头的顾客，召唤正确类型的铁匠。
> Blacksmith manufactures weapons. Elves require Elvish weapons and orcs require Orcish weapons. Depending on the customer at hand the right type of blacksmith is summoned.

In plain words
> 它提供了一种将实例化逻辑委托给子类的方法。
> It provides a way to delegate the instantiation logic to child classes.

Wikipedia says
> 在基于类的编程中，工厂方法模式是一种创建模式，它使用工厂方法来处理创建对象的问题，而无需指定将创建的对象的确切类别。这是通过调用一个工厂方法创建对象来完成的，这个方法要么在接口中指定，要么由子类实现，要么在基类中实现，并且可以被派生类重写，而不是通过调用构造函数。
> In class-based programming, the factory method pattern is a creational pattern that uses factory methods to deal with the problem of creating objects without having to specify the exact class of the object that will be created. This is done by creating objects by calling a factory method—either specified in an interface and implemented by child classes, or implemented in a base class and optionally overridden by derived classes—rather than by calling a constructor.

 **Programmatic Example**
> 以上面的铁匠例子。 首先，我们有一个铁匠接口和一些实现
Taking our blacksmith example above. First of all we have a blacksmith interface and some implementations for it

```
public interface Blacksmith {
  Weapon manufactureWeapon(WeaponType weaponType);
}

public class ElfBlacksmith implements Blacksmith {
  public Weapon manufactureWeapon(WeaponType weaponType) {
    return new ElfWeapon(weaponType);
  }
}

public class OrcBlacksmith implements Blacksmith {
  public Weapon manufactureWeapon(WeaponType weaponType) {
    return new OrcWeapon(weaponType);
  }
}
```
现在随着顾客来到正确类型的铁匠被召唤并要求制造武器
Now as the customers come the correct type of blacksmith is summoned and requested weapons are manufactured

```
Blacksmith blacksmith = new ElfBlacksmith();
blacksmith.manufactureWeapon(WeaponType.SPEAR);
blacksmith.manufactureWeapon(WeaponType.AXE);
// Elvish weapons are created
```

## Applicability
Use the Factory Method pattern when
使用工厂方法模式
* a class can't anticipate the class of objects it must create
* 一个类无法预测它必须创建的对象的类
* a class wants its subclasses to specify the objects it creates
* 一个类想让它的子类指定它创建的对象
* classes delegate responsibility to one of several helper subclasses, and you want to localize the knowledge of which helper subclass is the delegate
* 类将责任委派给几个助手子类之一，并且您想本地化哪些助手子类是委托的知识

## Known uses

* [java.util.Calendar](http://docs.oracle.com/javase/8/docs/api/java/util/Calendar.html#getInstance--)
* [java.util.ResourceBundle](http://docs.oracle.com/javase/8/docs/api/java/util/ResourceBundle.html#getBundle-java.lang.String-)
* [java.text.NumberFormat](http://docs.oracle.com/javase/8/docs/api/java/text/NumberFormat.html#getInstance--)
* [java.nio.charset.Charset](http://docs.oracle.com/javase/8/docs/api/java/nio/charset/Charset.html#forName-java.lang.String-)
* [java.net.URLStreamHandlerFactory](http://docs.oracle.com/javase/8/docs/api/java/net/URLStreamHandlerFactory.html#createURLStreamHandler-java.lang.String-)
* [java.util.EnumSet](https://docs.oracle.com/javase/8/docs/api/java/util/EnumSet.html#of-E-)
* [javax.xml.bind.JAXBContext](https://docs.oracle.com/javase/8/docs/api/javax/xml/bind/JAXBContext.html#createMarshaller--)

## Credits

* [Design Patterns: Elements of Reusable Object-Oriented Software](http://www.amazon.com/Design-Patterns-Elements-Reusable-Object-Oriented/dp/0201633612)
