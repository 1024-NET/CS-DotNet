issues：

Delegate是个什么？

为什么要使用Delegate？

怎么使用Delegate？

----

What？

首先我会通过一个简单的Person类和Thread、Delegate的源码进行对比分析来学习Delegate是什么？
世界万物都可以抽象为对象，都有类型，那么函数也可以，函数是由返回值和方法名还有参数组成的动态表达式，那么我们怎么来区分函数的不同？
就可以通过函数返回值和参数（参数的类型、个数）来区分，所以返回值和参数相同的一类函数（不包括函数名）就规定为一种类型的函数，我们在
.NET中可以用委托Delegate来表示这类函数，就类比用Person类来表示不同种类（肤色）的人，只是Delegate是.NET自带的已经定义好的类类型（
抽象类），所以可以通过delegate void xDelegate(); xDelegate d = new xDelegate(Method_Name)；创建一个方法对象的实例，相当于d为引用（或者C里面的函数指针）指向该类方法（所有存在或者
还未声明的该方法类型相同的方法）的地址（C语言里面我们用方法名表示一个函数在内存中的起始地址），而不仅仅是只指向Methread_Name这
一个方法，Delegate是一种针对方法的数据类型（比如String是字符串的数据类型，只是String比较特殊），
对比Person p = new Person(skin_Color)；我们通过Person p = new Person(identity_Num)；在中国可以通过身份证号码指向特定的那个人，那我们怎么指向一个特定的方法呢？......
我们还可以通过查看Delegate的源码（https://source.dot.net）了解更多。结合Thread，Thread t = new Thread(Method_Name);一个线程就是用来执行一个单独的方法，
用Delegate来定义一个类型的所有方法，Thread就用来执行这类方法中特定的一个方法，Method_Name是一个ThreadStart（自定定义的委托：public delegate void ThreadStart();）类型的函数。


Why？

通过委托调用函数，可以跨区域、跨线程、跨对象。
由于C#是面向对象的语言，加上对类和成员默认访问权限(public、private、protected、internal)，不同类型对象之间是无法进行成员变量的直接访问（与C语言不通，可以直接通过函数指针进行调用）.



How？
