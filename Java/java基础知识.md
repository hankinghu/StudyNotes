### 1、作用域public,private,protected,以及不写时的区别 

| 作用域 | 当前类 | 同一package |子孙类 |其他package|
| :------------ |:---------------:|:---------------:|:---------------:|:---------------:|
| public    | √ | √ |√|√|
| protected | √ |√| √| ×|
| friendly | √  | √ |×|×|
| private | √|× |×|×|



### 2、Anonymous Inner Class (匿名内部类) 是否可以extends(继承)其它类，是否可以implements(实现)interface(接口)  
答：匿名的内部类是没有名字的内部类。不能extends(继承) 其它类，但一个内部类可以作为一个接口，由另一个内部类实现 
### 3、Static Nested Class 和 Inner Class的不同 
答：Nested Class （一般是C++的说法），Inner Class (一般是JAVA的说法)。Java内部类与C++嵌套类最大的不同就在于是否有指向外部的引用上。注： 静态内部类（Inner Class）意味着1创建一个static内部类的对象，不需要一个外部类对象，2不能从一个static内部类的一个对象访问一个外部类对象
### 4、&和&&的区别 
答：&是位运算符，表示按位与运算，&&是逻辑运算符，表示逻辑与（and
### 5、Collection 和 Collections的区别
答：Collection是集合类的上级接口，继承与他的接口主要有Set 和List.  Collections是针对集合类的一个帮助类，他提供一系列静态方法实现对各种集合的搜索、排序、线程安全化等操作
### 6、序列化与反序列化的作用：

对象的序列化主要有两种用途：<br>
1） 把对象的字节序列永久地保存到硬盘上，通常存放在一个文件中；<br>
2） 在网络上传送对象的字节序列。<br>

 

因为不对对象序列化的化容易出现很多问题，所以引入了序列化解决了这些问题。<br>

 

对象序列化包括如下步骤：<br>
1） 创建一个对象输出流，它可以包装一个其他类型的目标输出流，如文件输出流；<br>
2） 通过对象输出流的writeObject()方法写对象。<br>
对象反序列化的步骤如下：<br>
1） 创建一个对象输入流，它可以包装一个其他类型的源输入流，如文件输入流；<br>
2） 通过对象输入流的readObject()方法读取对象。<br>
下面让我们来看一个对应的例子，类的内容如下：<br>

 

serialVersionUID作用： <br>
       序列化时为了保持版本的兼容性，即在版本升级时反序列化仍保持对象的唯一性。<br>
有两种生成方式：<br>
       一个是默认的1L，比如：private static final long serialVersionUID = 1L;<br>
       一个是根据类名、接口名、成员方法及属性等来生成一个64位的哈希字段，比如：<br>
       private static final   long     serialVersionUID = xxxxL;<br>

当你一个类实现了Serializable接口，如果没有定义serialVersionUID，Eclipse会提供这个提示功能告诉你去定义 。<br>
### 7、final, finally, finalize的区别。 
　　final 用于声明属性，方法和类，分别表示属性不可变，方法不可覆盖，类不可继承。
finally是异常处理语句结构的一部分，表示总是执行。
### 8、final
 * 根据程序上下文环境，Java关键字final有“这是无法改变的”或者“终态的”含义，它可以修饰非抽象类、非抽象类成员方法和变量。你可能出于两种理解而需要阻止改变：设计或效率。
 * final类不能被继承，没有子类，final类中的方法默认是final的。
 * final方法不能被子类的方法覆盖，但可以被继承。
 * final成员变量表示常量，只能被赋值一次，赋值后值不再改变。
 * final不能用于修饰构造方法。
 * 注意：父类的private成员方法是不能被子类方法覆盖的，因此private类型的方法默认是final类型的。
 
####final类
        final类不能被继承，因此final类的成员方法没有机会被覆盖，默认都是final的。在设计类时候，如果这个类不需要有子类，类的实现细节不允许改变，并且确信这个类不会载被扩展，那么就设计为final类。
####final方法
        如果一个类不允许其子类覆盖某个方法，则可以把这个方法声明为final方法。
        使用final方法的原因有二：
        第一、把方法锁定，防止任何继承类修改它的意义和实现。
        第二、高效。编译器在遇到调用final方法时候会转入内嵌机制，大大提高执行效率。
####final变量（常量）
        用final修饰的成员变量表示常量，值一旦给定就无法改变！
        final修饰的变量有三种：静态变量、实例变量和局部变量，分别表示三种类型的常量。
        从下面的例子中可以看出，一旦给final变量初值后，值就不能再改变了。
        另外，final变量定义的时候，可以先声明，而不给初值，这中变量也称为final空白，无论什么情况，编译器都确保空白final在使用之前必须被初始化。但是，final空白在final关键字final的使用上提供了更大的灵活性，为此，一个类中的final数据成员就可以实现依对象而有所不同，却有保持其恒定不变的特征。
####final参数
        当函数参数为final类型时，你可以读取使用该参数，但是无法改变该参数的值
二、static

* static表示“全局”或者“静态”的意思，用来修饰成员变量和成员方法，也可以形成静态static代码块，但是Java语言中没有全局变量的概念。

* 被static修饰的成员变量和成员方法独立于该类的任何对象。也就是说，它不依赖类特定的实例，被类的所有实例共享。只要这个类被加载，Java虚拟机就能根据类名在运行时数据区的方法区内定找到他们。因此，static对象可以在它的任何对象创建之前访问，无需引用任何对象。

* 用public修饰的static成员变量和成员方法本质是全局变量和全局方法，当声明它类的对象市，不生成static变量的副本，而是类的所有实例共享同一个static变量。
 
* static变量前可以有private修饰，表示这个变量可以在类的静态代码块中，或者类的其他静态成员方法中使用（当然也可以在非静态成员方法中使用--废话），但是不能在其他类中通过类名来直接引用，这一点很重要。实际上你需要搞明白，private是访问权限限定，static表示不要实例化就可以使用，这样就容易理解多了。static前面加上其它访问权限关键字的效果也以此类推。
 
* static修饰的成员变量和成员方法习惯上称为静态变量和静态方法，可以直接通过类名来访问，访问语法为：
类名.静态方法名(参数列表...) 
类名.静态变量名
        用static修饰的代码块表示静态代码块，当Java虚拟机（JVM）加载类时，就会执行该代码块（用处非常大，呵呵）。
 
#### 1、static变量
        按照是否静态的对类成员变量进行分类可分两种：一种是被static修饰的变量，叫静态变量或类变量；另一种是没有被static修饰的变量，叫实例变量。两者的区别是：
        对于静态变量在内存中只有一个拷贝（节省内存），JVM只为静态分配一次内存，在加载类的过程中完成静态变量的内存分配，可用类名直接访问（方便），当然也可以通过对象来访问（但是这是不推荐的）。
        对于实例变量，没创建一个实例，就会为实例变量分配一次内存，实例变量可以在内存中有多个拷贝，互不影响（灵活）。
 
#### 2、静态方法
        静态方法可以直接通过类名调用，任何的实例也都可以调用，因此静态方法中不能用this和super关键字，不能直接访问所属类的实例变量和实例方法(就是不带static的成员变量和成员成员方法)，只能访问所属类的静态成员变量和成员方法。因为实例成员与特定的对象关联！这个需要去理解，想明白其中的道理，不是记忆！！！
        因为static方法独立于任何实例，因此static方法必须被实现，而不能是抽象的abstract。
### static和final一块用表示什么
        static final用来修饰成员变量和成员方法，可简单理解为“全局常量”！
        对于变量，表示一旦给值就不可修改，并且通过类名可以访问。
        对于方法，表示不可覆盖，并且可以通过类名直接访问。
       
        特别要注意一个问题：
        对于被static和final修饰过的实例常量，实例本身不能再改变了，但对于一些容器类型（比如，ArrayList、HashMap）的实例变量，不可以改变容器变量本身，但可以修改容器中存放的对象，这一点在编程中用到很多。

### 如果要对一个特别大的（如100位）数进行相加，在java中如何计算：
[相关链接](http://ly5633.iteye.com/blog/1218724)  
在Java中针对比较大的数字，有大数类型来进行表示。即BigInteger和BigDecimal两个类。
以BigDecimal为例：
```java
BigDecimal bigDecimalA = new BigDecimal("1234567890123456789012345678901");
        BigDecimal bigDecimalB = new BigDecimal("1234567890123456789012345678902");
        // 加  +
        bigDecimalA = bigDecimalA.add(bigDecimalB);
        // 减  -
        bigDecimalA = bigDecimalA.subtract(bigDecimalB);
        // 乘  *
        bigDecimalA = bigDecimalA.multiply(bigDecimalB);
        // 除  /
        bigDecimalA = bigDecimalA.divide(bigDecimalB);
        ```
        // ......其他的类似，API里很详细，不再赘述了。
