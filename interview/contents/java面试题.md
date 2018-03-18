# java面试题汇总

熟练掌握java是很关键的，大公司不仅仅要求你会使用几个api，更多的是要你熟悉源码实现原理，甚至要你知道有哪些不足，怎么改进，还有一些java有关的一些算法，设计模式等等。

### 一、java基础面试知识点

* java中==和equals和hashCode的区别
* int、char、long各占多少字节数
  >* int 4字节,char 2个字节(java采用unicode来表示编码,通常gbk/gb2312是2个字节，utf-8是3个字节),long 8个字节
  * java char 在内存中只会使用 unicode 编码，所有其他编码只可能是在转换成 byte[] 之后才能具体体现。
  + utf-8 编码作为优化单字节文字的方案，在多字节文字中效果反而是变差的。就难中文来举例，使用 utf-16 进行编码时（也就是 java char 实际编码），只需要占用 2 byte。而在使用 utf-8 编码时，因为需要多几个 bit 来做标记位，反而需要占用 3 byte。这也就是为什么基于 utf-16 的 java char 存储中文的效果要比 utf-8 优秀。Unicode是一种字符集(charset)，用两个字节就能囊括世界上所有的文字集合。UTF-8是一种编码方式(encoding)，是Unicode的一种表现方式。
  + 在一个Java文件(该文件为UTF-8编码)里面写上这样一句话
  char a = '猿';编译后生成的class文件会把'猿'转化成Unicode的两字节。理解字符集和字符编码的区别，有助于题主理解这些问题.

* int与integer的区别
  > int是基本数据类型,Integer是包装类,相互转换装箱拆箱
* 谈谈对java多态的理解
  > 所谓多态就是指程序中定义的引用变量所指向的具体类型和通过该引用变量发出的方法调用在编程时并不确定，而是在程序运行期间才确定，即一个引用变量倒底会指向哪个类的实例对象，该引用变量发出的方法调用到底是哪个类中实现的方法，必须在由程序运行期间才能决定。因为在程序运行时才确定具体的类，这样，不用修改源程序代码，就可以让引用变量绑定到各种不同的类实现上，从而导致该引用调用的具体方法随之改变，即不修改程序代码就可以改变程序运行时所绑定的具体代码，让程序可以选择多个运行状态，这就是多态性。
* String、StringBuffer、StringBuilder区别
  > String：字符串常量，字符串长度不可变。
  <br>StringBuffer：字符串变量（Synchronized，即线程安全）
  <br>StringBuilder：字符串变量（非线程安全）。在内部，StringBuilder对象被当作是一个包含字符序列的变长数组。Jdk5.0引入.
* 什么是内部类？内部类的作用
  > 内部类是指在一个外部类的内部再定义一个类。内部类作为外部类的一个成员，并且依附于外部类而存在的。内部类可为静态，可用protected和private修饰（而外部类只能使用public和缺省的包访问权限）。内部类主要有以下几类：成员内部类、局部内部类、静态内部类、匿名内部类.
* 抽象类和接口区别
  > 抽象类和接口都不能被实例化,抽象类有实函数
* 抽象类的意义
  >
* 抽象类与接口的应用场景
* 抽象类是否可以没有方法和属性？
* 接口的意义
* 泛型中extends和super的区别

* 父类的静态方法能否被子类重写

* 进程和线程的区别
* final，finally，finalize的区别
* 序列化的方式
* Serializable 和Parcelable 的区别
* 静态属性和静态方法是否可以被继承？是否可以被重写？以及原因？
* 静态内部类的设计意图
* 成员内部类、静态内部类、局部内部类和匿名内部类的理解，以及项目中的应用
* 谈谈对kotlin的理解
* 闭包和局部内部类的区别
* string 转换成 integer的方式及原理


### 二、java深入源码级的面试题（有难度）

* 哪些情况下的对象会被垃圾回收机制处理掉？
* 讲一下常见编码方式？
* utf-8编码中的中文占几个字节；int型几个字节？
  > utf-8中文占3个字节,int类型占4个字节

* 静态代理和动态代理的区别，什么场景使用？
* Java的异常体系
* 谈谈你对解析与分派的认识。
* 修改对象A的equals方法的签名，那么使用HashMap存放这个对象实例的时候，会调用哪个equals方法？
* Java中实现多态的机制是什么？
* 如何将一个Java对象序列化到文件里？
* 说说你对Java反射的理解
* 说说你对Java注解的理解
* 说说你对依赖注入的理解
* 说一下泛型原理，并举例说明
* Java中String的了解
* String为什么要设计成不可变的？
* Object类的equal和hashCode方法重写，为什么？


### 三、数据结构

* 常用数据结构简介
* 并发集合了解哪些？
* 列举java的集合以及集合之间的继承关系
* 集合类以及集合框架
* 容器类介绍以及之间的区别（容器类估计很多人没听这个词，Java容器主要可以划分为4个部分：List列表、Set集合、Map映射、工具类（Iterator迭代器、Enumeration枚举类、Arrays和Collections），具体的可以看看这篇博文 [Java容器类](http://alexyyek.github.io/2015/04/06/Collection/)）

* List,Set,Map的区别
> List里面的元素相当于数组,Set里面的元素不会重复,Map里面的元素是key,value类型的键值对

* List和Map的实现方式以及存储方式
* HashMap的实现原理
* HashMap数据结构？
* HashMap源码理解
* HashMap如何put数据（从HashMap源码角度讲解）？
* HashMap怎么手写实现？
* ConcurrentHashMap的实现原理
* ArrayMap和HashMap的对比
* HashTable实现原理
* TreeMap具体实现
* HashMap和HashTable的区别
* HashMap与HashSet的区别
* HashSet与HashMap怎么判断集合元素重复？
* 集合Set实现Hash怎么防止碰撞
* ArrayList和LinkedList的区别，以及应用场景
* 数组和链表的区别
* 二叉树的深度优先遍历和广度优先遍历的具体实现
* 堆的结构
>

* 堆和树的区别

* 堆和栈在内存中的区别是什么(解答提示：可以从数据结构方面以及实际实现方面两个方面去回答)？

* 什么是深拷贝和浅拷贝

* 手写链表逆序代码
> Java反转单链表实战 http://hanhailong.com/2016/02/25/Java%E5%8F%8D%E8%BD%AC%E5%8D%95%E9%93%BE%E8%A1%A8%E5%AE%9E%E6%88%98/

* 讲一下对树，B+树的理解

* 讲一下对图的理解

* 判断单链表成环与否？

* 链表翻转（即：翻转一个单项链表）

* 合并多个单有序链表（假设都是递增的）


### 四、线程、多线程和线程池

* 开启线程的三种方式？
> 继承Thread,实现Runnable接口,实现Callable接口
  * run是执行体, call是Callable的执行体, start方法是执行线程
  * 采用实现Runnable、Callable接口的方式创见多线程时，优势是：线程类只是实现了Runnable接口或Callable接口，还可以继承其他类。在这种方式下，多个线程可以共享同一个target对象，所以非常适合多个相同线程来处理同一份资源的情况，从而可以将CPU、代码和数据分开，形成清晰的模型，较好地体现了面向对象的思想。劣势是：编程稍微复杂，如果要访问当前线程，则必须使用Thread.currentThread()方法。  
  使用继承Thread类的方式创建多线程时优势是：编写简单，如果需要访问当前线程，则无需使用Thread.currentThread()方法，直接使用this即可获得当前线程。劣势是：线程类已经继承了Thread类，所以不能再继承其他父类。
  http://blog.csdn.net/longshengguoji/article/details/41126119

* 线程和进程的区别？
> 进程和线程就是这样的背景出来的，两个名词不过是对应的CPU时间段的描述，名词就是这样的功能。进程就是包换上下文切换的程序执行时间总和 = CPU加载上下文+CPU执行+CPU保存上下文线程是什么呢？  
https://www.zhihu.com/question/25532384

* 为什么要有线程，而不是仅仅用进程？
> 早期：在ＯＳ中一直都是以进程作为能拥有资源和独立运行的基本单位．后来人们又提出了比进程更小的能独立运行的基本单位－线程（Ｔｈｒｅａｄｓ），试图通过它来提高系统内程序并发执行的程序，从而进一步提高系统的吞吐量．后来多处理机系统得到迅速发展，线程能比进程更好的提高程序的并发执行程序，充分发挥多处理机的优越性．如果说：在操作系统中引入进程的目的，是为了使多个程序能并发执行，以提高资源的利用率和系统的吞吐量，那么在操作系统中再引入线程，则是为了减少程序在并发执行时所付出的时空开销，使ＯＳ具有更好的并发行
（进程的两个基本属性：１，进程是一个可拥有资源的独立单位 ２，进程同时又是一个可独立调度和分派的基本单位）所以进程才能成为一个独立运行的基本单位．从而也就构成了进程并发执行的基础　然而，为了能并发执行，系统还必须进行一下一系列的操作．．．．http://blog.csdn.net/msdnwolaile/article/details/52106242

* run()和start()方法区别

* 如何控制某个方法允许并发访问线程的个数？
* 在Java中wait和sleep方法的不同；
* 谈谈wait/notify关键字的理解
* 什么导致线程阻塞？
* 线程如何关闭？
* 讲一下java中的同步的方法
* 数据一致性如何保证？
* 如何保证线程安全？
* 如何实现线程同步？
* 两个进程同时要求写或者读，能不能实现？如何防止进程的同步？
* 线程间操作List
* Java中对象的生命周期
* Synchronized用法
* synchronize的原理
* 谈谈对Synchronized关键字，类锁，方法锁，重入锁的理解
* static synchronized 方法的多线程访问和作用
* 同一个类里面两个synchronized方法，两个线程同时访问的问题
* volatile的原理
* 谈谈volatile关键字的用法
* 谈谈volatile关键字的作用
* 谈谈NIO的理解
* synchronized 和volatile 关键字的区别
* synchronized与Lock的区别
* ReentrantLock 、synchronized和volatile比较
* ReentrantLock的内部实现
* lock原理
* 死锁的四个必要条件？
* 怎么避免死锁？
* 对象锁和类锁是否会互相影响？
* 什么是线程池，如何使用?
* Java的并发、多线程、线程模型
* 谈谈对多线程的理解
* 多线程有什么要注意的问题？
* 谈谈你对并发编程的理解并举例说明
* 谈谈你对多线程同步机制的理解？
* 如何保证多线程读写文件的安全？
* 多线程断点续传原理
* 断点续传的实现



----

### 并发编程有关知识点（这个是一般Android开发用的少的，所以建议多去看看）：

平时Android开发中对并发编程可以做得比较少，Thread这个类经常会用到，但是我们想提升自己的话，一定不能停留在表面，,我们也应该去了解一下java的关于线程相关的源码级别的东西。


**学习的参考资料如下：**

> Java 内存模型

* [java线程安全总结](http://www.iteye.com/topic/806990)
* [深入理解java内存模型系列文章](http://ifeve.com/java-memory-model-0/)

> 线程状态：

* [一张图让你看懂JAVA线程间的状态转换](https://my.oschina.net/mingdongcheng/blog/139263)

> 锁：

* [锁机制：synchronized、Lock、Condition](http://blog.csdn.net/vking_wang/article/details/9952063)
* [Java 中的锁](http://wiki.jikexueyuan.com/project/java-concurrent/locks-in-java.html)

> 并发编程：

* [Java并发编程：Thread类的使用](http://www.cnblogs.com/dolphin0520/p/3920357.html)
* [Java多线程编程总结](http://blog.51cto.com/lavasoft/27069)
* [Java并发编程的总结与思考](https://www.jianshu.com/p/053943a425c3#)
* [Java并发编程实战-----synchronized](http://www.cnblogs.com/chenssy/p/4701027.html)
* [深入分析ConcurrentHashMap](http://www.infoq.com/cn/articles/ConcurrentHashMap#)
