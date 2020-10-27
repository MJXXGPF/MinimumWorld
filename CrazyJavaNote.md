# 1.数据类型和运算符

## 1.1 数据类型分类

### 1.1.1基本类型：

- 整数类型   byte  short int long   字节数分别位1	2 	4 	8    默认为int
- 字符类型  char  字节数为2
- 浮点类型  float double   字节数分别为  4 8     默认为double
- 布尔类型  boolean   字节数为1

### 1.1.2引用类型：

- String

## 1.2 基本数据类型的转化

### 1.2.1 自动类型转化

- 数值范围小的可以向数值范围大的进行转化，反之不行,会产生溢出问题

  ```java
  public class AutoConversion
  {
  	public static void main(String[] args)
  	{
  		int a  = 6;
  		// int可以自动转换为float类型
  		float f = a;
  		// 下面将输出6.0
  		System.out.println(f);
  		// 定义一个byte类型的整数变量
  		byte b = 9;
  		// 下面代码将出错，byte型不能自动类型转换为char型
  		// char c = b;
  		// 下面是byte型变量可以自动类型转换为double型
  		double d = b;
  		// 下面将输出9.0
  		System.out.println(d);
  	}
  }
  ```

- 基本类型与字符串进行连接,基本类型会转化为字符串类型

  ```java
  public class PrimitiveAndString
  {
  	public static void main(String[] args)
  	{
  		// 下面代码是错的，因为5是一个整数，不能直接赋给一个字符串
  		// String str1 = 5;
  		// 一个基本类型值和字符串进行连接运算时，基本类型值自动转换为字符串
  		String str2 = 3.5f + "";
  		// 下面输出3.5
  		System.out.println(str2);
  		// 下面语句输出7Hello!
  		System.out.println(3 + 4 + "Hello！");
  		// 下面语句输出Hello!34，因为Hello! + 3会把3当成字符串处理，
  		// 而后再把4当成字符串处理
  		System.out.println("Hello！" + 3 + 4);
  	}
  }
  
  ```

### 1.2.2 强制类型转化

- 强制类型转化类似于将一个大瓶子的水倒进小瓶子，若大瓶子里面的水过多，则会引起溢出问题

  ```java
  public class NarrowConversion
  {
  	public static void main(String[] args)
  	{
  		int iValue = 233;
  		// 强制把一个int类型的值转换为byte类型的值
  		byte bValue = (byte)iValue;//大-->小
  		// 将输出-23
  		System.out.println(bValue);
  		double dValue = 3.98;
  		// 强制把一个double类型的值转换为int
  		int tol = (int)dValue;
  		// 将输出3
  		System.out.println(tol);
  	}
  }
  ```

### 1.2.3 表达式类型的自动提升

- 当一个算术表达式中包含多个基本类型的值时，整个算术表达式数据类型将会自动提升

  ```java
  public class AutoPromote
  {
  	public static void main(String[] args)
  	{
  		// 定义一个short类型变量
  		short sValue = 5;
  		// 下面代码将出错：表达式中的sValue将自动提升到int类型，
  		// 则右边的表达式类型为int，将一个int类型赋给short类型的变量将发生错误。
  		// sValue = sValue - 2;
  		byte b = 40;
  		char c = 'a';
  		int i = 23;
  		double d = .314;
  		// 右边表达式中在最高等级操作数为d（double型）
  		// 则右边表达式的类型为double型,故赋给一个double型变量
  		double result = b + c + i * d;
  		// 将输出144.222
  		System.out.println(result);
  		int val = 3;
  		// 右边表达式中2个操作数都是int，故右边表达式的类型为int
  		// 因此，虽然23/3不能除尽，依然得到一个int整数
  		int intResult = 23 / val;
  		System.out.println(intResult); // 将输出7
  		// 输出字符串Hello!a7
  		System.out.println("Hello!" + 'a' + 7);
  		// 输出字符串104Hello!
  		System.out.println('a' + 7 + "Hello!");
  	}
  }
  
  ```

## 1.3 运算符

### 1.3.1 位运算符

- 按位与  &

  ```java
  System.out.println(5 & 9); // 将输出1   (00101)&(01001)=00001=1
  ```

- 按位或 |

  ```java
  System.out.println(5 | 9); // 将输出13   (00101)|(01001)=01101=13
  ```

- 按位非 ~

  ```java
  System.out.println(~-5); // 将输出4
  ```

- 按位异或 ^

  ```java
  System.out.println(~-5); // 将输出4
  ```

- 左移  <<  右边空出来的部分补0

  ```java
  System.out.println(5 << 2); // 输出20   左移一位相当于乘2
  ```

- 右移  >>   左边空出来的部分补符号位

  ```java
  System.out.println(-5 >> 2); // 输出-2    右移一位相当于除2
  ```

- 无符号右移  >>>   左边空出来的部分补0

  ```java
  System.out.println(-5 >>> 2); // 输出1073741822
  ```

  

### 1.3.2 逻辑运算符

- &&  短路与
- &   不短路与
- ||  短路或
- |  不短路或
- ！非运算符
- ^  异或

#  2.流程控制和数组

## 2.1流程控制

- switch语句后的expression表达式只可以是byte short char int四个整数类型和Strin、枚举类型
- for循环语句的循环迭代语句（i++）没有和循环体放在一起，所以即使使用continue语句来结束本次循环，循环体依然执行

## 2.2 数组

### 2.2.1 数组的初始化

- 静态初始化

  ```java
  int arr[]={1,2,3,4,5};
  ```

- 动态初始化

  ```
  int arr[]=new int[5];//默认整型数组的值为0
  ```

### 2.2.2 使用数组

- 使用数组的length属性，可以得到数组的长度

  ```java
  int arr[]=new int[5];
  System.out.println(arr.length);//属性没有（）
  ```

- foreach强化版循环遍历数组

  ```java
  public class ForEachTest
  {
  	public static void main(String[] args)
  	{
  		String[] books = {"轻量级Java EE企业应用实战" ,
  		"疯狂Java讲义",
  		"疯狂Android讲义"};
  		// 使用foreach循环来遍历数组元素，
  		// 其中book将会自动迭代每个数组元素
  		for (String book : books)
  		{
  			System.out.println(book);
  		}
  	}
  }
  ```

### 2.2.3 数组的深入理解

- 数组的引用是一个局部变量，存在于栈中；数组对象存在于堆中;

  ```java
  int arr[]=new int[5];//arr就是一个引用，new int[5]在堆中产生了一个数组对象
  ```

- 二维数组本质上还是一维数组，只不将原来的数组元素的基本类型改成了引用类型，每个引用类型的数组元素又指向一个一维数组

  ```java
  int arr[][]=new int[3][4];
  arr[0]=new int[1];//第一维数组创建的第二维数组元素个数可以不一样
  arr[1]=new int[2];
  arr[2]=new int [3];
  ```

### 2.2.4 操作数组的工具类Arrays

- 代码举例

  ```java
  public class ArraysTest
  {
  	public static void main(String[] args)
  	{
  		// 定义一个a数组
  		int[] a = new int[]{3, 4 , 5, 6};
  		// 定义一个a2数组
  		int[] a2 = new int[]{3, 4 , 5, 6};
  		// a数组和a2数组的长度相等，每个元素依次相等，将输出true
  		System.out.println("a数组和a2数组是否相等："
  			+ Arrays.equals(a , a2));
  		// 通过复制a数组，生成一个新的b数组
  		int[] b = Arrays.copyOf(a, 6);
  		System.out.println("a数组和b数组是否相等："
  			+ Arrays.equals(a , b));
  		// 输出b数组的元素，将输出[3, 4, 5, 6, 0, 0]
  		System.out.println("b数组的元素为："
  			+ Arrays.toString(b));
  		// 将b数组的第3个元素（包括）到第5个元素（不包括）赋为1
  		Arrays.fill(b , 2, 4 , 1);
  		// 输出b数组的元素，将输出[3, 4, 1, 1, 0, 0]
  		System.out.println("b数组的元素为："
  			+ Arrays.toString(b));
  		// 对b数组进行排序
  		Arrays.sort(b);//默认升序
  		// 输出b数组的元素，将输出[0, 0, 1, 1, 3, 4]
  		System.out.println("b数组的元素为："
  			+ Arrays.toString(b));
  	}
  }
  
  ```

# 3.面向对象（上）

## 3.1 类和对象

### 3.1.1 定义类

- 类中三种最常见的成员：构造器、Field（属性）和方法
- 三种权限修饰符：public protected default private  可见性依次减小
- 构造器是一个特殊的方法，没有返回值（不能用void修饰），名字和类名一样

### 3.1.2 对象的产生和使用

- 创建对象的根本途径是构造器，通过new关键字来调用构造器
- 一个类中可以含有多个不同参数的构造器，如果没有自己写构造器，系统将提供一个默认的构造器，但是如果自己有定义构造器，则系统不再提供默认的构造器

### 3.1.3 对象、引用、指针

```java
Person p=new Person();
Person p1=p;
Person p2=p;
```

- p p1 p2称为引用变量，new Person（）会产生一个实际的对象，这里，引用就相当于C里的指针
- 引用变量存在于栈中，对象存在于堆中
- 一个对象可以有多个引用变量指向它
- 若一个对象没有任何引用变量指向它，则将会被Java的垃圾回收机制回收

### 3.1.4 对象的this引用

- this关键字总是指向调用该方法的对象

  ```java
  public class Dog
  {
  	// 定义一个jump()方法
  	public void jump()
  	{
  		System.out.println("正在执行jump方法");
  	}
  	// 定义一个run()方法，run()方法需要借助jump()方法
  	public void run()
  	{
  //		Dog d = new Dog();
  //		d.jump();
  		// 使用this引用调用run()方法的对象
  		this.jump();
  		System.out.println("正在执
                             行run方法");
  	}
  }
  ```

- 在静态方法中不能使用this关键字，因为这个关键字无法指向合适的对象

  ```java
  public class StaticAccessNonStatic
  {
  	public void info()
  	{
  		System.out.println("简单的info方法");
  	}
  	public static void main(String[] args)
  	{
  		// 因为main()方法是静态方法，而info()是非静态方法，
  		// 调用main()方法的是该类本身，而不是该类的实例，
  		// 因此省略的this无法指向有效的对象
  		info();
  	}
  }
  
  ```

## 3.2 方法详解

### 3.2.1 方法的所属性

- 方法在逻辑上要么属于类，要么属于对象
- 方法必须存在于类中，不能独立存在
- 同一个类的一个方法调用另外一个方法时，如果调方法是普通方法，则默认使用this作为调用者；如果被调方法是静态方法，则默认使用类作为调用者。总之，表面上看起来某些方法可以被独立执行，但实际上还是使用this或者类来作为调用者
- 使用static修饰的方法既可以用类作为调用者来使用，也可以使用对象作为调用者来使用

### 3.2.2 方法的参数传递机制

- Java中只有值传递这一种参数传递方式
- 对于交换swap()函数，如果传递的是两个基本类型，则主函数中的两个数值没有发生改变；但是如果传递的是引用类型，则会导致数值发生变化；因为对于基本类型，是复制了变量本身；但对于引用类型，复制的是引用变量，虽然有两个引用变量，但是这两个引用变量指向的对象是一样的，因此一个引用对对象属性的重新赋值都会引起对象的值的变化。

### 3.2.3形参个数可变的方法

- 在**最后一个**形参的类型后加上三点（...）

  ```java
  public class Varargs
  {
  	// 定义了形参个数可变的方法
  	public static void test(int a , String... books)
  	{
  		// books被当成数组处理
  		for (String tmp : books)
  		{
  			System.out.println(tmp);
  		}
  		// 输出整数变量a的值
  		System.out.println(a);
  	}
  	public static void main(String[] args)
  	{
  		// 调用test方法
  		test(5 , "疯狂Java讲义" , "轻量级Java EE企业应用实战");
  	}
  }
  ```

### 3.2.4  方法重载

- 同一个类中方法名相同，参数列表不同

- 方法返回值类型、修饰符等与方法重载没有任何关系

  ```java
  public class Overload
  {
  	// 下面定义了两个test()方法，但方法的形参列表不同
  	// 系统可以区分这两个方法，这种被称为方法重载
  	public void test()
  	{
  		System.out.println("无参数");
  	}
  	public void test(String msg)
  	{
  		System.out.println("重载的test方法 " + msg);
  	}
  	public static void main(String[] args)
  	{
  		Overload ol = new Overload();
  		// 调用test()时没有传入参数，因此系统调用上面没有参数的test()方法。
  		ol.test();
  		// 调用test()时传入了一个字符串参数，
  		// 因此系统调用上面带一个字符串参数的test()方法。
  		ol.test("hello");
  	}
  }
  ```

## 3.3 成员变量和局部变量

### 3.3.1 成员变量和局部变量

- 成员变量指的是在类范围里定义的变量   包括实例Field和类Field  
- 局部变量指的是在方法里定义的变量  包括形参  方法中定义的局部变量  代码块中定义的局部变量
- 成员变量无需初始化，本身会有一个默认值，比如整型默认值为0，布尔型默认值为false
- 如果方法里的局部变量与成员变量同名，局部变量会覆盖成员变量，若想访问成员变量可以采用this

### 3.3.2 成员变量的初始化和内存中的运行机制

- 当系统加载类或创建该类的实例时，系统会自动为成员变量分配内存空间，并在分配内存空间后，自动为成员变量指定初始值
- 对于静态变量，值加载一次，即使创建一个类的多个对象，静态变量只在第一次创建时被初始化，静态变量被多个对象共享使用

### 3.3.3  局部变量的初始化和内存中的运行机制

- 局部变量定义后，必须经过显示初始化以后才能使用，系统不会为局部变量执行初始化
- 局部变量不属于任何类和实例
- 如果一个局部变量是一个引用类型的变量，则保存的是一个地址
- 成员变量使用的几种情形：
  - 需要定义的变量是用于描述某个类或某个对象的固有信息
  - 某个类需要以一个变量来保存该类或者实例运行时的状态信息
  - 某个信息需要在某个类的多个方法之间进行共享

## 3.4 类的继承

### 3.4.1 继承的特点

- 通过继承，子类可以获得父类的属性和方法，但不能获得父类的构造器
- Java只支持单继承

### 3.4.2 重写父类的方法

- 子类包含与父类同名方法的现象称为方法重写或方法覆盖
- 方法重写原则：
  - 方法名相同
  - 形参列表相同
  - 子类方法返回的类型<=父类方法返回的类型
  - 子类方法抛出的异常<=父类方法抛出的异常
  - 子类方法的访问权限>=父类方法的访问权限

- 要想在子类重写的方法中访问父类的方法，可以使用super关键字

### 3.4.3 调用父类的构造器

- 子类不会获得父类的构造器，但是子类构造器里面可以调用父类构造器的初始化代码
- 当调用子类构造器来初始化子类对象之前，父类构造器总会在子类构造器之前执行
- 创建任何对象总是从该类所在继承树最顶层的构造器开始执行，任何依次向下执行，最后才是类的构造器

## 3.5 多态

- 当编译时类型和运行时类型不一致时就可能产生多态

  ```java
  class BaseClass
  {
  	public int book = 6;
  	public void base()
  	{
  		System.out.println("父类的普通方法");
  	}
  	public void test()
  	{
  		System.out.println("父类的被覆盖的方法");
  	}
  }
  public class SubClass extends BaseClass
  {
  	//重新定义一个book实例变量隐藏父类的book实例变量
  	public String book = "轻量级Java EE企业应用实战";
  	public void test()
  	{
  		System.out.println("子类的覆盖父类的方法");
  	}
  	public void sub()
  	{
  		System.out.println("子类的普通方法");
  	}
  	public static void main(String[] args)
  	{
  		// 下面编译时类型和运行时类型完全一样，因此不存在多态
  		BaseClass bc = new BaseClass();
  		// 输出 6
  		System.out.println(bc.book);
  		// 下面两次调用将执行BaseClass的方法
  		bc.base();
  		bc.test();
  		// 下面编译时类型和运行时类型完全一样，因此不存在多态
  		SubClass sc = new SubClass();
  		// 输出"轻量级Java EE企业应用实战"
  		System.out.println(sc.book);
  		// 下面调用将执行从父类继承到的base()方法
  		sc.base();
  		// 下面调用将执行从当前类的test()方法
  		sc.test();
  		// 下面编译时类型和运行时类型不一样，多态发生
  		BaseClass ploymophicBc = new SubClass();
  		// 输出6 —— 表明访问的是父类对象的实例变量
  		System.out.println(ploymophicBc.book);
  		// 下面调用将执行从父类继承到的base()方法
  		ploymophicBc.base();
  		// 下面调用将执行从当前类的test()方法
  		ploymophicBc.test();
  		// 因为ploymophicBc的编译类型是BaseClass，
  		// BaseClass类没有提供sub方法,所以下面代码编译时会出现错误。
  		// ploymophicBc.sub();
  	}
  }
  ```

- 引用变量时父类类型，对象是子类类型时，访问成员变量时访问的是父类的成员变量，当调用共同的方法时，调用的时子类的方法

## 3.6 初始化块

### 3.6.1 使用初始化块

- 在创建Java对象时，系统先调用初始化块，再调用构造器

```java
public class Person
{
	// 下面定义一个初始化块
	{
		int a = 6;
		if (a > 4)
		{
			System.out.println("Person初始化块：局部变量a的值大于4");
		}
		System.out.println("Person的初始化块");
	}
	// 定义第二个初始化块
	{
		System.out.println("Person的第二个初始化块");
	}
	// 定义无参数的构造器
	public Person()
	{
		System.out.println("Person类的无参数构造器");
	}
	public static void main(String[] args)
	{
		new Person();
	}
}

/*输出：
Person初始化块：局部变量a的值大于4
Person的初始化块
Person的第二个初始化块
Person类的无参数构造器
*/
```

### 3.6.2 静态初始化块

- 静态初始化块比普通初始化块先执行
- 系统在类初始化阶段执行静态初始化块而不是在创建对象时才执行
- 静态初始化块和静态变量相似，只加载一次

# 4 面向对象下

## 4.1 包装类

- | 基本数据类型 | 包装类   |
  | ------------ | -------- |
  | byte         | Byte     |
  | short        | Short    |
  | int          | Integer  |
  | long         | Long     |
  | char         | Charcter |
  | float        | Float    |
  | double       | Double   |
  | boolean      | Boolean  |

- 自动装箱与自动拆箱

  ```java
  public class AutoBoxingUnboxing
  {
  	public static void main(String[] args)
  	{
  		// 直接把一个基本类型变量赋给Integer对象
  		Integer inObj = 5;
  		// 直接把一个boolean类型变量赋给一个Object类型的变量
  		Object boolObj = true;
  		// 直接把一个Integer对象赋给int类型的变量
  		int it = inObj;
  		if (boolObj instanceof Boolean)
  		{
  			// 先把Object对象强制类型转换为Boolean类型，再赋给boolean变量
  			boolean b = (Boolean)boolObj;
  			System.out.println(b);
  		}
  	}
  }
  /*
  int只能自动装箱成Integer类型，Integer也只能自动拆箱成int
  */
  ```

- 基本类型变量与字符串之间的转化

  - 字符串----->基本数据类型    parseXxx(String s)    (parseInt(String s))
  - 基本数据类型------>字符串    valueOf()

  ```java
  public class Primitive2String
  {
  	public static void main(String[] args)
  	{
  		String intStr = "123";
  		// 把一个特定字符串转换成int变量
  		int it1 = Integer.parseInt(intStr);
  		int it2 = Integer.valueOf(intStr);
  		System.out.println(it2);
  		String floatStr = "4.56";
  		// 把一个特定字符串转换成float变量
  		float ft1 = Float.parseFloat(floatStr);
  		float ft2 = Float.valueOf(floatStr);
  		System.out.println(ft2);
  		// 把一个float变量转换成String变量
  		String ftStr = String.valueOf(2.345f);
  		System.out.println(ftStr);
  		// 把一个double变量转换成String变量
  		String dbStr = String.valueOf(3.344);
  		System.out.println(dbStr);
  		// 把一个boolean变量转换成String变量
  		String boolStr = String.valueOf(true);
  		System.out.println(boolStr.toUpperCase());
  	}
  }
  
  ```

## 4.2 处理对象

### 4.2.1 打印对象1和toString方法

- toString方法用来实现这样一个功能：当程序员之间打印该对象时，系统将会输出该对象的“自我描述信息”

- Object提供的toString方法总是返回该对象实现类的“类名+@+hashcode”值，所以一般情况下我们会重写toString方法，按照自己的需求打印信息

- toString方法无需显示调用，当使用System.out.println(对象)就是在使用;

  ```java
  class Apple
  {
  	private String color;
  	private double weight;
  	public Apple(){	}
  	//提供有参数的构造器
  	public Apple(String color , double weight)
  	{
  		this.color = color;
  		this.weight = weight;
  	}
  
  	// color的setter和getter方法
  	public void setColor(String color)
  	{
  		this.color = color;
  	}
  	public String getColor()
  	{
  		return this.color;
  	}
  
  	// weight的setter和getter方法
  	public void setWeight(double weight)
  	{
  		this.weight = weight;
  	}
  	public double getWeight()
  	{
  		return this.weight;
  	}
  
  	// 重写toString方法，用于实现Apple对象的"自我描述"
  	public String toString()
  	{
  		return "一个苹果，颜色是：" + color
  			+ "，重量是：" + weight;
  	}
  
  //	public String toString()
  //	{
  //		return "Apple[color=" + color + ",weight=" + weight + "]";
  //	}
  
  }
  public class ToStringTest
  {
  	public static void main(String[] args)
  	{
  		Apple a = new Apple("红色" , 5.68);
  		// 打印Apple对象
  		System.out.println(a);
  	}
  }
  ```

 ### 4.2.2  ==和equals方法

- ==一般比较的使两个变量的地址，对于基本数据类型而言，大小一样则地址一样，所以区别不大，但是对于引用类型而言，则需要严格区别地址和内容

- ==比较两个字符串的情形

  ```java
  public class StringCompareTest{
  public static void main(String args[])
  {
      //s1直接引用常量池中的"疯狂Java"
      String s1="疯狂Java";
      String s2="疯狂";
      String s3="Java";
      //s4后面的字符串可以在编译时就确定下来
      //s4直接引用常量池中的"疯狂Java"
      String s4="疯狂"+"Java";
      //s4后面的字符串可以在编译时就确定下来
      //s4直接引用常量池中的"疯狂Java"
       String s5="疯"+"狂"+"Java";
      //s6后面的字符串值不能在编译时就确定下来
      //不能引用常量池中的字符串
      String s6=s2+s3;
      //使用new调用构造器将会创建一个新的String对象
      //s7引用堆内存中新创建的String对象
      String s7=new String("疯狂Java");
      System.out.println(s1==s4);//true
       System.out.println(s1==s5);//true
       System.out.println(s1==s6);//false
       System.out.println(s1==s7);//false
  }
  }
  ```

- equals

  - String重写了equals方法，因此对应两个字符串变量而言，使用equals比较的是两个字符串的内容

  - equals是Object类提供的一个实例方法，如果使用equals方法的对象没有重写equals方法，其作用与==一样用来判断地址是否相等

  - 重写equals方法的实例

    ```java
    class Person
    {
    	private String name;
    	private String idStr;
    	public Person(){}
    	public Person(String name , String idStr)
    	{
    		this.name = name;
    		this.idStr = idStr;
    	}
    	// 此处省略name和idStr的setter和getter方法。
    	// name的setter和getter方法
    	public void setName(String name)
    	{
    		this.name = name;
    	}
    	public String getName()
    	{
    		return this.name;
    	}
    
    	// idStr的setter和getter方法
    	public void setIdStr(String idStr)
    	{
    		this.idStr = idStr;
    	}
    	public String getIdStr()
    	{
    		return this.idStr;
    	}
    	// 重写equals()方法，提供自定义的相等标准
    	public boolean equals(Object obj)
    	{
    		// 如果两个对象为同一个对象
    		if (this == obj)
    			return true;
    		// 只有当obj是Person对象
    		if (obj != null && obj.getClass() == Person.class)
    		{
    			Person personObj = (Person)obj;
    			// 并且当前对象的idStr与obj对象的idStr相等才可判断两个对象相等
    			if (this.getIdStr().equals(personObj.getIdStr()))
    			{
    				return true;
    			}
    		}
    		return false;
    	}
    }
    public class OverrideEqualsRight
    {
    	public static void main(String[] args)
    	{
    		Person p1 = new Person("孙悟空" , "12343433433");
    		Person p2 = new Person("孙行者" , "12343433433");
    		Person p3 = new Person("孙悟饭" , "99933433");
    		// p1和p2的idStr相等，所以输出true
    		System.out.println("p1和p2是否相等？"
    			+ p1.equals(p2));
    		// p2和p3的idStr不相等，所以输出false
    		System.out.println("p2和p3是否相等？"
    			+ p2.equals(p3));
    	}
    }
    ```

## 4.3 类成员

### 4.3.1 理解类成员

- static关键字修饰的成员就是类成员，类成员属于整个类，而不属于单个对象

- 类成员既可以通过类来访问，也可以通过类的对象来访问

- 即使一个对象为null,依然可以访问类成员

  ```java
  public class NullAccessStatic
  {
  	private static void test()
  	{
  		System.out.println("static修饰的类方法");
  	}
  	public static void main(String[] args)
  	{
  		// 定义一个NullAccessStatic变量，其值为null
  		NullAccessStatic nas = null;
  		// 使用null对象调用所属类的静态方法
  		nas.test();
  	}
  }
  //打印结果为：“static修饰的类方法”
  ```

### 4.3.2 单例类

- 如果一个类始终只能创建一个实例，则这个类被称为单例类

  ```java
  class Singleton
  {
  	// 使用一个类变量来缓存曾经创建的实例
  	private static Singleton instance;
  	// 将构造器使用private修饰，隐藏该构造器
  	private Singleton(){}
  	// 提供一个静态方法，用于返回Singleton实例
  	// 该方法可以加入自定义的控制，保证只产生一个Singleton对象
  	public static Singleton getInstance()
  	{
  		// 如果instance为null，表明还不曾创建Singleton对象
  		// 如果instance不为null，则表明已经创建了Singleton对象，
  		// 将不会重新创建新的实例
  		if (instance == null)
  		{
  			// 创建一个Singleton对象，并将其缓存起来
  			instance = new Singleton();
  		}
  		return instance;
  	}
  }
  public class SingletonTest
  {
  	public static void main(String[] args)
  	{
  		// 创建Singleton对象不能通过构造器，
  		// 只能通过getInstance方法来得到实例
  		Singleton s1 = Singleton.getInstance();
  		Singleton s2 = Singleton.getInstance();
  		System.out.println(s1 == s2); // 将输出true
  	}
  }
  ```

## 4.4 final修饰符

- final修饰变量时，表示该变量一旦获得了初始值就不可以被改变

- final修饰的成员变量必须由程序员显示地指定初始值

- final修饰局部变量时，既可以在定义的时候指定默认值，也可以在后面的代码中对该final变量赋值，但只能一次

- final修饰基本变量时，不能对基本类型的变量重新赋值，因此基本类型的变量不能被改变，但对于引用类型变量而言，对象可以发生改变

  ```java
  class Person
  {
  	private int age;
  	public Person(){}
  	// 有参数的构造器
  	public Person(int age)
  	{
  		this.age = age;
  	}
  	// 省略age的setter和getter方法
  	// age的setter和getter方法
  	public void setAge(int age)
  	{
  		this.age = age;
  	}
  	public int getAge()
  	{
  		return this.age;
  	}
  }
  public class FinalReferenceTest
  {
  	public static void main(String[] args)
  	{
  		// final修饰数组变量，iArr是一个引用变量
  		final int[] iArr = {5, 6, 12, 9};
  		System.out.println(Arrays.toString(iArr));
  		// 对数组元素进行排序，合法
  		Arrays.sort(iArr);
  		System.out.println(Arrays.toString(iArr));
  		// 对数组元素赋值，合法
  		iArr[2] = -8;
  		System.out.println(Arrays.toString(iArr));
  		// 下面语句对iArr重新赋值，非法
  		// iArr = null;
  		// final修饰Person变量，p是一个引用变量
  		final Person p = new Person(45);
  		// 改变Person对象的age实例变量，合法
  		p.setAge(23);
  		System.out.println(p.getAge());
  		// 下面语句对p重新赋值，非法
  		// p = null;
  	}
  }
  ```

### 4.4.1final方法

- final修饰的方法不能被重写，如果不希望子类重写父类额某个方法，可以使用final方法

- 重写父类的private final方法

  ```java
  public class PrivateFinalMethodTest
  {
  	private final void test(){}
  }
  class Sub extends PrivateFinalMethodTest
  {
  	// 下面方法定义将不会出现问题
  	public void test(){}
  }
  ```

### 4.4.2final类

- final修饰类不能有子类
- java.lang.Math就是一个final类，他不可以有子类

## 4.5 抽象类

- 抽象方法和抽象类必须使用abstract关键字来定义

- 有抽象方法的类只能被定义成抽象类，但是抽象类里面可以没有抽象方法

- 抽象类不能被实例化,只能当作父类被其他子类继承，继承抽象类的子类必须要实现抽象父类里面所有的方法

  ```java
  public abstract class Shape
  {
  	{
  		System.out.println("执行Shape的初始化块...");
  	}
  	private String color;
  	// 定义一个计算周长的抽象方法
  	public abstract double calPerimeter();
  	// 定义一个返回形状的抽象方法
  	public abstract String getType();
  	// 定义Shape的构造器，该构造器并不是用于创建Shape对象，
  	// 而是用于被子类调用
  	public Shape(){}
  	public Shape(String color)
  	{
  		System.out.println("执行Shape的构造器...");
  		this.color = color;
  	}
  	// 省略color的setter和getter方法
  	public void setColor(String color)
  	{
  		this.color = color;
  	}
  	public String getColor()
  	{
  		return this.color;
  	}
  }
  ```

- abstract和final不能同时修饰，abstract和static也不能同时修饰

## 4.6 接口

### 4.6.1 接口的定义

- 定义接口不再使用class关键字，而是使用interface关键字

- 一个接口可以继承多个父接口，但是不能继承类

- 接口的修饰符可以是public或省略，省略时采用包权限访问控制符，只有在相同包结构下才可以访问接口

- 接口里面只能有抽象方法，不能有静态方法

- 接口里面的Field只能是常量

  ```java
  public interface Output{
      //接口里定义的Field只能是常量
      int MAX_CACHE_LINE =50;
      //接口里定义的只能是public的抽象实例方法
      void out();
      void getData(String msg);
  }
  ```

### 4.6.2 接口的继承

- 接口完全支持多继承

- 子接口拓展某个父类接口，将会获得父接口里定义的所有的抽象方法、常量Field等

  ```java
  interface InterfaceA
  {
  	int PROP_A = 5;
  	void testA();
  }
  interface InterfaceB
  {
  	int PROP_B = 6;
  	void testB();
  }
  interface InterfaceC extends InterfaceA, InterfaceB
  {
  	int PROP_C = 7;
  	void testC();
  }
  public class InterfaceExtendsTest
  {
  	public static void main(String[] args)
  	{
  		System.out.println(InterfaceC.PROP_A);
  		System.out.println(InterfaceC.PROP_B);
  		System.out.println(InterfaceC.PROP_C);
  	}
  }
  
  ```

  

### 4.6.3 接口的使用

- 接口不能用于创建实例，但是可以用于声明引用类型变量
- 一个类可以实现一个或多个接口，使用implements关键字
- 实现接口的类必须完全实现这些接口里所定义的全部的抽象方法

### 4.6.4 接口的抽象类

- 相同点：
  - 接口和抽象类都不能被实例化
  - 接口和抽象类都可以包含抽象方法，实现接口或继承抽象类的普通子类都必须实现这些抽象方法

- 不同点：
  - 接口体现的是一种规范，抽象类体现的是一种模板设计
  - 接口可以实现多个，但是类只能是单继承
  - 接口里面只能含有抽象方法，但是抽象类里面可以有普通方法

## 4.7 内部类

### 4.7.1 非静态内部类

- 没有使用static修饰的成员内部类是非静态内部类

- 非静态内部类可以直接访问外部类的private成员

- 外部类不能直接访问内部类的成员，若要访问则需要显示地创建内部类对象来访问

- 非静态内部类访问变量的查找顺序：方法内-->内部类-->外部类

  ```java
  public class Cow
  {
  	private double weight;
  	// 外部类的两个重载的构造器
  	public Cow(){}
  	public Cow(double weight)
  	{
  		this.weight = weight;
  	}
  	// 定义一个非静态内部类
  	private class CowLeg
  	{
  		// 非静态内部类的两个实例变量
  		private double length;
  		private String color;
  		// 非静态内部类的两个重载的构造器
  		public CowLeg(){}
  		public CowLeg(double length , String color)
  		{
  			this.length = length;
  			this.color = color;
  		}
  		// 下面省略length、color的setter和getter方法
  		public void setLength(double length)
  		{
  			this.length = length;
  		}
  		public double getLength()
  		{
  			return this.length;
  		}
  		public void setColor(String color)
  		{
  			this.color = color;
  		}
  		public String getColor()
  		{
  			return this.color;
  		}
  		// 非静态内部类的实例方法
  		public void info()
  		{
  			System.out.println("当前牛腿颜色是："
  				+ color + ", 高：" + length);
  			// 直接访问外部类的private修饰的成员变量
  			System.out.println("本牛腿所在奶牛重：" + weight);   //①
  		}
  	}
  	public void test()
  	{
  		CowLeg cl = new CowLeg(1.12 , "黑白相间");
  		cl.info();
  	}
  	public static void main(String[] args)
  	{
  		Cow cow = new Cow(378.9);
  		cow.test();
  	}
  }
  ```

- 非静态内部类里面不能定义静态成员(静态方法、静态Field、静态初始化块)，如下代码会发生编译错误

  ```java
  public class InnerNoStatic
  {
  	private class InnerClass
  	{
  		/*
  		下面三个静态声明都将引发如下编译错误:
  		非静态内部类不能有静态声明
  		*/
  		static
  		{
  			System.out.println("==========");
  		}
  		private static int inProp;
  		private static void test(){}
  	}
  }
  ```

### 4.7.2 静态内部类

- 使用static修饰的内部类称为静态内部类

- 静态内部类是外部类的一个静态成员

- 静态内部类不能访问外部类的实例成员，只能访问外部类的静态成员（静态只能访问静态的原则）

  ```java
  public class StaticInnerClassTest
  {
  	private int prop1 = 5;
  	private static int prop2 = 9;
  	static class StaticInnerClass
  	{
  		// 静态内部类里可以包含静态成员
  		private static int age;
  		public void accessOuterProp()
  		{
  			// 下面代码出现错误：
  			// 静态内部类无法访问外部类的实例变量
  //			System.out.println(prop1);
  			// 下面代码正常
  			System.out.println(prop2);
  		}
  	}
  }
  ```

- 外部类不能直接访问静态内部类的成员，但是可以通过类名或静态内部类的对象来访问

  ```java
  public class AccessStaticInnerClass
  {
  	static class StaticInnerClass
  	{
  		private static int prop1 = 5;
  		private int prop2 = 9;
  	}
  	public void accessInnerProp()
  	{
  		// System.out.println(prop1);
  		// 上面代码出现错误，应改为如下形式：
  		// 通过类名访问静态内部类的类成员
  		System.out.println(StaticInnerClass.prop1);
  		// System.out.println(prop2);
  		// 上面代码出现错误，应改为如下形式：
  		// 通过实例访问静态内部类的实例成员
  		System.out.println(new StaticInnerClass().prop2);
  	}
  }
  ```

### 4.7.3 使用内部类

- 在外部类内部使用内部类（静态或非静态）

- 在外部类以外使用非静态内部类----先创建外部类对象再创建内部类对象

  ```java
  class Out
  {
  	// 定义一个内部类，不使用访问控制符，
  	// 即只有同一个包中其他类可访问该内部类
  	class In
  	{
  		public In(String msg)
  		{
  			System.out.println(msg);
  		}
  	}
  }
  public class CreateInnerInstance
  {
  	public static void main(String[] args)
  	{
  		Out.In in = new Out().new In("测试信息");
  		/*
  		上面代码可改为如下三行代码：
  		使用OutterClass.InnerClass的形式定义内部类变量
  		Out.In in;
  		创建外部类实例，非静态内部类实例将寄存在该实例中
  		Out out = new Out();
  		通过外部类实例和new来调用内部类构造器创建非静态内部类实例
  		in = out.new In("测试信息");
  		*/
  	}
  }
  ```

- 在外部内以外使用静态内部类，因为是静态的，所以不需要创建静态内部类对象，只需创建外部类对象

  ```java
  class StaticOut
  {
  	// 定义一个静态内部类，不使用访问控制符，
  	// 即同一个包中其他类可访问该内部类
  	static class StaticIn
  	{
  		public StaticIn()
  		{
  			System.out.println("静态内部类的构造器");
  		}
  	}
  }
  public class CreateStaticInnerInstance
  {
  	public static void main(String[] args)
  	{
  		StaticOut.StaticIn in = new StaticOut.StaticIn();
  		/*
  		上面代码可改为如下两行代码：
  		使用OutterClass.InnerClass的形式定义内部类变量
  		StaticOut.StaticIn in;
  		通过new来调用内部类构造器创建静态内部类实例
  		in = new StaticOut.StaticIn();
  		*/
  	}
  }
  
  ```



- 静态内部类只需要使用外部类即可调用构造器，非静态内部类则需要使用外部类对象来调用构造器

### 4.7.4 局部内部类

- 在方法里面定义的内部类称为局部内部类

- 若需要使用局部内部类定义变量、创建实例或派生子类，都只能在局部内部类所在的方法里面进行

  ```java
  public class LocalInnerClass
  {
  	public static void main(String[] args)
  	{
  		// 定义局部内部类
  		class InnerBase
  		{
  			int a;
  		}
  		// 定义局部内部类的子类
  		class InnerSub extends InnerBase
  		{
  			int b;
  		}
  		// 创建局部内部类的对象
  		InnerSub is = new InnerSub();
  		is.a = 5;
  		is.b = 8;
  		System.out.println("InnerSub对象的a和b实例变量是："
  			+ is.a + "," + is.b);
  	}
  }
  ```

### 4.7.5 匿名内部类

- 匿名内部类适合于那种只需要一次使用的类

- 匿名内部类必须继承一个父类或实现一个接口，但是只能继承一个父类或实现一个接口

- 匿名内部类不能是抽象类

- 匿名内部类不能定义构造器

  ```java
  interface Product
  {
  	public double getPrice();
  	public String getName();
  }
  public class AnonymousTest
  {
  	public void test(Product p)
  	{
  		System.out.println("购买了一个" + p.getName()
  			+ "，花掉了" + p.getPrice());
  	}
  	public static void main(String[] args)
  	{
  		AnonymousTest ta = new AnonymousTest();
  		// 调用test()方法时，需要传入一个Product参数，
  		// 此处传入其匿名实现类的实例
  		ta.test(new Product()
  		{
  			public double getPrice()
  			{
  				return 567.8;
  			}
  			public String getName()
  			{
  				return "AGP显卡";
  			}
  		});
  	}
  }
  ```

## 4.8 枚举类

- 枚举类可以实现一个或多个接口

- 枚举类不能派生子类

- 枚举类的构造器只能用private修饰

- 枚举类的所有实例必须在枚举类的第一行显示列出

  ```java
  public enum Operation
  {
  	PLUS
  	{
  		public double eval(double x , double y)
  		{
  			return x + y;
  		}
  	},
  	MINUS
  	{
  		public double eval(double x , double y)
  		{
  			return x - y;
  		}
  	},
  	TIMES
  	{
  		public double eval(double x , double y)
  		{
  			return x * y;
  		}
  	},
  	DIVIDE
  	{
  		public double eval(double x , double y)
  		{
  			return x / y;
  		}
  	};
  	// 为枚举类定义一个抽象方法
  	// 这个抽象方法由不同的枚举值提供不同的实现
  	public abstract double eval(double x, double y);
  	public static void main(String[] args)
  	{
  		System.out.println(Operation.PLUS.eval(3, 4));
  		System.out.println(Operation.MINUS.eval(5, 4));
  		System.out.println(Operation.TIMES.eval(5, 4));
  		System.out.println(Operation.DIVIDE.eval(5, 4));
  	}
  }
  ```

  

# 5 Java集合

## 5.1 Java集合概述

- 集合类也称容器类，集合类位于java.util包下
- 数组元素既可以时基本类型的值，也可以是对象，但是集合只能保存对象
- 集合类主要由两个接口派生：Collection接口和Map接口
- Collection
  - Set
    - EnumSet
    - SortedSet
    - HashSet---->LinkedHashSet
  - Queue
    - Deque
    - PriorityQueue
  - List
    - ArrayList
    - LinkedList
    - Vector----->Stack
- Map
  - HashMap------LinkedHashMap
  - HashTable-----Properties
  - SortedMap-----TreeMap

## 5.2 Collection和Iterator接口

- Collection接口是List、Set、Queue接口的父接口

  ```java
  public class CollectionTest
  {
  	public static void main(String[] args)
  	{
  		Collection c = new ArrayList();
  		// 添加元素
  		c.add("孙悟空");
  		// 虽然集合里不能放基本类型的值，但Java支持自动装箱
  		c.add(6);
  		System.out.println("c集合的元素个数为:" + c.size()); // 输出2
  		// 删除指定元素
  		c.remove(6);
  		System.out.println("c集合的元素个数为:" + c.size()); // 输出1
  		// 判断是否包含指定字符串
  		System.out.println("c集合的是否包含\"孙悟空\"字符串:"
  			+ c.contains("孙悟空")); // 输出true
  		c.add("轻量级Java EE企业应用实战");
  		System.out.println("c集合的元素：" + c);
  		Collection books = new HashSet();
                                                                                        		books.add("轻量级Java EE企业应用实战");
  		books.add("疯狂Java讲义");
  		System.out.println("c集合是否完全包含books集合？"
  			+ c.containsAll(books)); // 输出false
  		// 用c集合减去books集合里的元素
  		c.removeAll(books);
  		System.out.println("c集合的元素：" + c);
  		// 删除c集合里所有元素
  		c.clear();
  		System.out.println("c集合的元素：" + c);
  		// 控制books集合里只剩下c集合里也包含的元素
  		books.retainAll(c);
  		System.out.println("books集合的元素:" + books);
  	}
  }
  ```

### 5.2.1 使用Iterator接口遍历集合元素

- Iterator接口里定义的三个重要方法

  - boolean hasNext():如果被迭代的集合元素还没有被遍历，则返回true
  - Object next():返回集合里的下一个元素
  - void remove():删除集合里上一次next方法返回的元素

  ```java
  public class IteratorTest
  {
  	public static void main(String[] args)
  	{
  		// 创建集合、添加元素的代码与前一个程序相同
  		Collection books = new HashSet();
  		books.add("轻量级Java EE企业应用实战");
  		books.add("疯狂Java讲义");
  		books.add("疯狂Android讲义");
  		// 获取books集合对应的迭代器
  		Iterator it = books.iterator();
  		while(it.hasNext())
  		{
  			// it.next()方法返回的数据类型是Object类型，因此需要强制类型转换
  			String book = (String)it.next();
  			System.out.println(book);
  			if (book.equals("疯狂Java讲义"))
  			{
  				// 从集合中删除上一次next方法返回的元素
  				it.remove();
  			}
  			// 对book变量赋值，不会改变集合元素本身
  			book = "测试字符串";   //①
  		}
  		System.out.println(books);
  	}
  }
  ```

- Collection集合里面的元素不能被改变，只有通过Iterator的remove方法删除上一次next方法返回的集合元素才可以，不能用集合本身去删除

  ```java
  public class IteratorErrorTest
  {
  	public static void main(String[] args)
  	{
  		// 创建集合、添加元素的代码与前一个程序相同
  		Collection books = new HashSet();
  		books.add("轻量级Java EE企业应用实战");
  		books.add("疯狂Java讲义");
  		books.add("疯狂Android讲义");
  		// 获取books集合对应的迭代器
  		Iterator it = books.iterator();
  		while(it.hasNext())
  		{
  			String book = (String)it.next();
  			System.out.println(book);
  			if (book.equals("疯狂Android讲义"))
  			{
  				// 使用Iterator迭代过程中，不可修改集合元素,下面代码引发异常
  				books.remove(book);
  			}
  		}
  	}
  }
  
  ```

### 5.2.2 使用foreac循环遍历集合元素

```java
public class ForeachTest
{
	public static void main(String[] args)
	{
		// 创建集合、添加元素的代码与前一个程序相同
		Collection books = new HashSet();
		books.add(new String("轻量级Java EE企业应用实战"));
		books.add(new String("疯狂Java讲义"));
		books.add(new String("疯狂Android讲义"));
		for (Object obj : books)
		{
			// 此处的book变量也不是集合元素本身
			String book = (String)obj;
			System.out.println(book);
			if (book.equals("疯狂Android讲义"))
			{
				// 下面代码会引发ConcurrentModificationException异常
				books.remove(book);     //①
			}
		}
		System.out.println(books);
	}
}
```

## 5.3 Set集合

- Set集合不允许含有相同的元素

- Set判断两个对象是否相同使用的是equals方法

  ```java
  public class SetTest{
      public static void main(String args[])
      {
          Set books=new HashSet();
          //添加一个字符串对象
          books.add(new String("hello"));
          //再次添加一个字符串对象
          //因为两个字符串对象通过equals方法比较相等，所以添加失败，返回false
          boolean result= books.add(new String("hello"));
          System.out.println(result+"--->"+books);
      }
  }
  ```

### 5.3.1 HashSet类

- HashSet是Set接口的典型实现
- 不能保证元素的排列顺序
- HashSet不是同步的
- HashSet判断两个元素相等的标准是两个对象通过equals方法比较相等，并且两个对象的hashCode()方法返回值也相等
- 重写hashCode()方法的基本规则
  - 同一个对象多次调用hasgCode()方法应该返回相同的值
  - 若两个对象通过equals方法比较时返回true,这两个对象的hashCode()方法应返回相等的值
  - 对象中用作equals()方法比较标准的Field,都应该用来计算hashCode()的值
- 如果向一个HashSet中添加了一个可变对象后，后面又修改了该对象的值，则可能会导致set中有两个相同的元素

### 5.3.2 LinkedHashSet类

- 能够使用链表来维护元素的次序，使得元素看起是以插入的顺序保存的

  ```java
  public class LinkedHashSetTest
  {
  	public static void main(String[] args)
  	{
  		LinkedHashSet books = new LinkedHashSet();
  		books.add("疯狂Java讲义");
  		books.add("轻量级Java EE企业应用实战");
  		System.out.println(books);
  		// 删除 疯狂Java讲义
  		books.remove("疯狂Java讲义");
  		// 重新添加 疯狂Java讲义
  		books.add("疯狂Java讲义");
  		System.out.println(books);
  	}
  }
  ```

### 5.3.3 TreeSet

- 确保集合元素处于排序状态

  ```java
  public class TreeSetTest
  {
  	public static void main(String[] args)
  	{
  		TreeSet nums = new TreeSet();
  		// 向TreeSet中添加四个Integer对象
  		nums.add(5);
  		nums.add(2);
  		nums.add(10);
  		nums.add(-9);
  		// 输出集合元素，看到集合元素已经处于排序状态
  		System.out.println(nums);
  		// 输出集合里的第一个元素
  		System.out.println(nums.first()); // 输出-9
  		// 输出集合里的最后一个元素
  		System.out.println(nums.last());  // 输出10
  		// 返回小于4的子集，不包含4
  		System.out.println(nums.headSet(4)); // 输出[-9, 2]
  		// 返回大于5的子集，如果Set中包含5，子集中还包含5
  		System.out.println(nums.tailSet(5)); // 输出 [5, 10]
  		// 返回大于等于-3，小于4的子集。
  		System.out.println(nums.subSet(-3 , 4)); // 输出[2]
  	}
  }
  ```

- 自然排序
  - TreeSet自动调用集合元素的compareTo(Object obj)的方法来比较元素之间的大小关系---->升序
  - TreeSet集合中添加的应该是同一个类的对象
  - 如果加入TreeSet集合中的对象是自己定义的对象，则需要将该类**实现Comparable接口**

```java
class Z implements Comparable
{
	int age;
	public Z(int age)
	{
		this.age = age;
	}
	// 重写equals()方法，总是返回true
	public boolean equals(Object obj)
	{
		return true;
	}
	// 重写了compareTo(Object obj)方法，总是返回1
	public int compareTo(Object obj)
	{
		return 1;
	}
}
public class TreeSetTest2
{
	public static void main(String[] args)
	{
		TreeSet set = new TreeSet();
		Z z1 = new Z(6);
		set.add(z1);
		// 第二次添加同一个对象，输出true，表明添加成功
		System.out.println(set.add(z1));    //①
		// 下面输出set集合，将看到有两个元素
		System.out.println(set);
		// 修改set集合的第一个元素的age变量
		 ((Z)(set.first())).age = 9;
		// 输出set集合的最后一个元素的age变量，将看到也变成了9
		System.out.println(((Z)(set.last())).age);
	}
}
```

- 定制排序

  - 在创建TreeSet对象时，提供一个Comparator对象与该TreeSet集合关联

  ```java
  class M
  {
  	int age;
  	public M(int age)
  	{
  		this.age = age;
  	}
  	public String toString()
  	{
  		return "M [age:" + age + "]";
  	}
  }
  public class TreeSetTest4
  {
  	public static void main(String[] args)
  	{
  		// 此处Lambda表达式的目标类型是Comparator
  		TreeSet ts = new TreeSet((o1 , o2) 
  		{
  			M m1 = (M)o1;
  			M m2 = (M)o2;
  			// 根据M对象的age属性来决定大小，age越大，M对象反而越小
  			return m1.age > m2.age ? -1
  				: m1.age < m2.age ? 1 : 0;
  		});
  		ts.add(new M(5));
  		ts.add(new M(-3));
  		ts.add(new M(9));
  		System.out.println(ts);
  	}
  }
  
  ```

### 5.3.4 各Set实现类的性能分析

- HashSet的性能总是比TreeSet好，因为TreeSet需要额外的红黑树算法来维护集合元素的次序
- 只有当需要一个保持排序的Set时，才应该使用TreeSet,否则都应该使用HashSet
- Set集合的实现类HashSet、TreeSet、EnumSet都是线程不安全的

## 5.4 List集合

### 5.4.1 List接口

- List是有序集合

  ```java
  public class ListTest
  {
  	public static void main(String[] args)
  	{
  		List books = new ArrayList();
  		// 向books集合中添加三个元素
  		books.add(new String("轻量级Java EE企业应用实战"));
  		books.add(new String("疯狂Java讲义"));
  		books.add(new String("疯狂Android讲义"));
  		System.out.println(books);
  		// 将新字符串对象插入在第二个位置
  		books.add(1 , new String("疯狂Ajax讲义"));
  		for (int i = 0 ; i < books.size() ; i++ )
  		{
  			System.out.println(books.get(i));
  		}
  		// 删除第三个元素
  		books.remove(2);
  		System.out.println(books);
  		// 判断指定元素在List集合中位置：输出1，表明位于第二位
  		System.out.println(books.indexOf(new String("疯狂Ajax讲义"))); //①
  		//将第二个元素替换成新的字符串对象
  		books.set(1, new String("疯狂Java讲义"));
  		System.out.println(books);
  		//将books集合的第二个元素（包括）
  		//到第三个元素（不包括）截取成子集合
  		System.out.println(books.subList(1 , 2));
  	}
  }
  ```

### 5.4.2 Vector实现类

- Vector集合是线程安全的

- Vector还提供了一个Stack子类，用于模拟栈

  - Object peek(): 返回栈中的第一个元素，但是不pop出栈
  - Object pop(): 返回栈中的第一个元素，并将该元素pop出栈
  - void push(Object item): 将一个元素入栈，最后一个进栈的元素位于栈顶

  ```java
  public class VectorTest{
      public staic void main(String args[])
      {
          Stack s=new Stack();
          s.push(1);
          s.puhs(2);
          s.push(3);
          System.out.println(s.peek());
          System.out.println(s.pop());
      }
  }
  ```

- 数组或指定个数的对象转化为List集合-----asList(Object...a)方法-----**固定长度，不能增加或删除**

  ```java
  public class FixedSizeList
  {
  	public static void main(String[] args)
  	{
  		List fixedList = Arrays.asList("疯狂Java讲义"
  			, "轻量级Java EE企业应用实战");
  		// 获取fixedList的实现类，将输出Arrays$ArrayList
  		System.out.println(fixedList.getClass());
  		// 使用方法引用遍历集合元素
  		fixedList.forEach(System.out::println);
  		// 试图增加、删除元素都会引发UnsupportedOperationException异常
  		fixedList.add("疯狂Android讲义");
  		fixedList.remove("疯狂Java讲义");
  	}
  }
  ```

## 5.5 Queue集合

### 5.5.1 PriorityQueue实现类

- 队列中的元素不是按加入时的顺序排列的，而是根据队列元素的大小进行排序的

- 所以从j进出的顺序角度来说，并不是先进先出

  ```java
  public class PriorityQueueTest
  {
  	public static void main(String[] args)
  	{
  		PriorityQueue pq = new PriorityQueue();
  		// 下面代码依次向pq中加入四个元素
  		pq.offer(6);
  		pq.offer(-3);
  		pq.offer(20);
  		pq.offer(18);
  		// 输出pq队列，并不是按元素的加入顺序排列
  		System.out.println(pq); // 输出[-3, 6, 18, 20]
  		// 访问队列第一个元素，其实就是队列中最小的元素：-3
  		System.out.println(pq.poll());
  	}
  }
  ```

- 两种排序方式------和TreeSet的排序要求一致
  - 自然排序：进行自然排序的对象的类必须实现了Comparable接口
  - 定制排序：在创建PriorityQueue时，传入一个Comparator对象

### 5.5.2 LinkedList实现类

- 可以当成双端队列来使用

- 可以当作栈来使用

- 实现了Deque接口

  ```java
  public class LinkedListTest
  {
  	public static void main(String[] args)
  	{
  		LinkedList books = new LinkedList();
  		// 将字符串元素加入队列的尾部
  		books.offer("疯狂Java讲义");
  		// 将一个字符串元素加入栈的顶部
  		books.push("轻量级Java EE企业应用实战");
  		// 将字符串元素添加到队列的头部（相当于栈的顶部）
  		books.offerFirst("疯狂Android讲义");
  		// 以List的方式（按索引访问的方式）来遍历集合元素
  		for (int i = 0; i < books.size() ; i++ )
  		{
  			System.out.println("遍历中：" + books.get(i));
  		}
  		// 访问、并不删除栈顶的元素
  		System.out.println(books.peekFirst());
  		// 访问、并不删除队列的最后一个元素
  		System.out.println(books.peekLast());
  		// 将栈顶的元素弹出“栈”
  		System.out.println(books.pop());
  		// 下面输出将看到队列中第一个元素被删除
  		System.out.println(books);
  		// 访问、并删除队列的最后一个元素
  		System.out.println(books.pollLast());
  		// 下面输出：[轻量级Java EE企业应用实战]
  		System.out.println(books);
  	}
  }
  ```

### 5.5.3 几种List实现类的比较

- ArrayList以数组的形式保存集合中的元素，因此随机访问集合元素时有较好的性能
- LinkedList内部以链表的形式来保存集合中的元素，因此随机访问集合元素时性能较差，但是删除、增加集合元素时性能较好

## 5.6 Map

- 常用方法
  - void clear(): 删除该Map对象中所有的key-value键值对
  - boolean containsKey(Object key): 查询Map中是否包含指定的key,有则返回true
  - boolean containsValue(Object value): 查询Map中是否包含指定的value,有则返回true
  - Set entrySet():返回Map中包含的key-value组成的Set集合
  - Object get(Object key):返回指定key所对应的value值
  - Set keySet():返回Map中key的集合

### 5.6.1 HashMap和Hashtable实现类

- 二者区别：

  - Hashtable是一个线程安全的Map实现，HashMap不安全
  - Hashtable不允许使用null作为key和value,但是HashMap允许

- HashMap举例

  ```java
  public class NullInHashMap
  {
  	public static void main(String[] args)
  	{
  		HashMap hm = new HashMap();
  		// 试图将两个key为null的key-value对放入HashMap中
  		hm.put(null , null);
  		hm.put(null , null);    // ①
  		// 将一个value为null的key-value对放入HashMap中
  		hm.put("a" , null);    // ②
  		// 输出Map对象
  		System.out.println(hm);
  	}
  }
  ```

- Hashtable举例

  ```java
  class A
  {
  	int count;
  	public A(int count)
  	{
  		this.count = count;
  	}
  	// 根据count的值来判断两个对象是否相等。
  	public boolean equals(Object obj)
  	{
  		if (obj == this)
  			return true;
  		if (obj != null && obj.getClass() == A.class)
  		{
  			A a = (A)obj;
  			return this.count == a.count;
  		}
  		return false;
  	}
  	// 根据count来计算hashCode值。
  	public int hashCode()
  	{
  		return this.count;
  	}
  }
  class B
  {
  	// 重写equals()方法，B对象与任何对象通过equals()方法比较都返回true
  	public boolean equals(Object obj)
  	{
  		return true;
  	}
  }
  public class HashtableTest
  {
  	public static void main(String[] args)
  	{
  		Hashtable ht = new Hashtable();
  		ht.put(new A(60000) , "疯狂Java讲义");
  		ht.put(new A(87563) , "轻量级Java EE企业应用实战");
  		ht.put(new A(1232) , new B());
  		System.out.println(ht);
  		// 只要两个对象通过equals比较返回true，
  		// Hashtable就认为它们是相等的value。
  		// 由于Hashtable中有一个B对象，
  		// 它与任何对象通过equals比较都相等，所以下面输出true。
  		System.out.println(ht.containsValue("测试字符串")); // ① 输出true
  		// 只要两个A对象的count相等，它们通过equals比较返回true，且hashCode相等
  		// Hashtable即认为它们是相同的key，所以下面输出true。
  		System.out.println(ht.containsKey(new A(87563)));   // ② 输出true
  		// 下面语句可以删除最后一个key-value对
  		ht.remove(new A(1232));    //③
  		System.out.println(ht);
  	}
  }
  ```

### 5.6.2 LinkedHashMap实现类

- 使用链表来维护Map的迭代顺序

- 能够保证迭代的顺序和key-value插入的顺序一致

  ```java
  public class LinkedHashMapTest
  {
  	public static void main(String[] args)
  	{
  		LinkedHashMap scores = new LinkedHashMap();
  		scores.put("语文" , 80);
  		scores.put("英文" , 82);
  		scores.put("数学" , 76);
  		// 调用forEach方法遍历scores里的所有key-value对
  		scores.forEach((key, value) -> System.out.println(key + "-->" + value));
  	}
  }
  ```

## 5.7 操作集合的工具类：Collections

- static void reverse(List list):反转指定List集合中元素额顺序

- staic void shuffle(List list):对List集合元素进行随机排序

- static void sort(List list):对List集合中的元素进行升序排序

- static void sort(List list,Comparator c):根据Comparator产生的顺序对List集合元素进行排序

- static swap(List list,int i,int j):交换List集合中i处和j处的元素

  ```java
  public class SortTest
  {
  	public static void main(String[] args)
  	{
  		ArrayList nums = new ArrayList();
  		nums.add(2);
  		nums.add(-5);
  		nums.add(3);
  		nums.add(0);
  		System.out.println(nums); // 输出:[2, -5, 3, 0]
  		Collections.reverse(nums); // 将List集合元素的次序反转
  		System.out.println(nums); // 输出:[0, 3, -5, 2]
  		Collections.sort(nums); // 将List集合元素的按自然顺序排序
  		System.out.println(nums); // 输出:[-5, 0, 2, 3]
  		Collections.shuffle(nums); // 将List集合元素的按随机顺序排序
  		System.out.println(nums); // 每次输出的次序不固定
  	}
  }
  ```

  ```java
  public class SearchTest
  {
  	public static void main(String[] args)
  	{
  		ArrayList nums = new ArrayList();
  		nums.add(2);
  		nums.add(-5);
  		nums.add(3);
  		nums.add(0);
  		System.out.println(nums); // 输出:[2, -5, 3, 0]
  		System.out.println(Collections.max(nums)); // 输出最大元素，将输出3
  		System.out.println(Collections.min(nums)); // 输出最小元素，将输出-5
  		Collections.replaceAll(nums , 0 , 1); // 将nums中的0使用1来代替
  		System.out.println(nums); // 输出:[2, -5, 3, 1]
  		// 判断-5在List集合中出现的次数，返回1
  		System.out.println(Collections.frequency(nums , -5));
  		Collections.sort(nums); // 对nums集合排序
  		System.out.println(nums); // 输出:[-5, 1, 2, 3]
  		//只有排序后的List集合才可用二分法查询，输出3
  		System.out.println(Collections.binarySearch(nums , 3));
  	}
  }
  ```

  

# 6 泛型

## 6.1 泛型入门

- 编译时不检查类型的异常

  ```java
  public class ListErr
  {
  	public static void main(String[] args)
  	{
  		// 创建一个只想保存字符串的List集合
  		List strList = new ArrayList();
  		strList.add("疯狂Java讲义");
  		strList.add("疯狂Android讲义");
  		// "不小心"把一个Integer对象"丢进"了集合
  		strList.add(5);     // ①
  		strList.forEach(str -> System.out.println(((String)str).length())); // ②
          //对5进行强制数据类型转化时会引发ClassCastException异常
          
  	}
  }
  ```

- 使用泛型

  ```java
  public class GenericList
  {
  	public static void main(String[] args)
  	{
  		// 创建一个只想保存字符串的List集合
  		List<String> strList = new ArrayList<String>();  // ①
  		strList.add("疯狂Java讲义");
  		strList.add("疯狂Android讲义");
  		// 下面代码将引起编译错误
  //		strList.add(5);    // ②
  		strList.forEach(str -> System.out.println(str.length())); // ③
  	}
  }
  ```

## 6.2 深入泛型

### 6.2.1 定义泛型接口、类

```java
public class Apple<T>
{
	// 使用T类型定义实例变量
	private T info;
	public Apple(){}
	// 下面方法中使用T类型来定义构造器
	public Apple(T info)
	{
		this.info = info;
	}
	public void setInfo(T info)
	{
		this.info = info;
	}
	public T getInfo()
	{
		return this.info;
	}
	public static void main(String[] args)
	{
		// 由于传给T形参的是String，所以构造器参数只能是String
		Apple<String> a1 = new Apple<>("苹果");
		System.out.println(a1.getInfo());
		// 由于传给T形参的是Double，所以构造器参数只能是Double或double
		Apple<Double> a2 = new Apple<>(5.67);
		System.out.println(a2.getInfo());
	}
}

```

### 6.2.2 从泛型类派生子类

- 使用泛型接口、父类时不能再包含类型形参，必须指定确定类型

  ```java
  public class A extends Apple<T>{}   //错误写法，T应该被换成具体的数据类型
  ```

- 重写泛型父类的方法时，必须要注意T类型形参一致

  ```java
  public class A1 extends Apple<String>
  {
  	// 正确重写了父类的方法，返回值
  	// 与父类Apple<String>的返回值完全相同
  	public String getInfo()
  	{
  		return "子类" + super.getInfo();
  	}
  	/*
  	// 下面方法是错误的，重写父类方法时返回值类型不一致
  	public Object getInfo()
  	{
  		return "子类";
  	}
  	*/
  }
  ```

- 使用泛型类时如果没有传入实际的类型参数，则可能会出错

  ```java
  public class A2 extends Apple
  {
  	// 重写父类的方法
  	public String getInfo()
  	{
  		// super.getInfo()方法返回值是Object类型，
  		// 所以加toString()才返回String类型
  		return super.getInfo().toString();
  	}
  }
  ```

# 7 异常处理

## 7.1 异常处理机制

### 7.1.1 使用try...catch捕获异常

```java
String inputStr = null;
		// br.readLine()：每当在键盘上输入一行内容按回车，
		// 用户刚刚输入的内容将被br读取到。
		while ((inputStr = br.readLine()) != null)
		{
			try
			{
				// 将用户输入的字符串以逗号作为分隔符，分解成2个字符串
				String[] posStrArr = inputStr.split(",");
				// 将2个字符串转换成用户下棋的坐标
				int xPos = Integer.parseInt(posStrArr[0]);
				int yPos = Integer.parseInt(posStrArr[1]);
				// 把对应的数组元素赋为"●"。
				if (!gb.board[xPos - 1][yPos - 1].equals("╋"))
				{
					System.out.println("您输入的坐标点已有棋子了，"
						+ "请重新输入");
					continue;
				}
				gb.board[xPos - 1][yPos - 1] = "●";
			}
			catch (Exception e)
			{
				System.out.println("您输入的坐标不合法，请重新输入，"
					+ "下棋坐标应以x,y的格式");
				continue;
			}

			gb.printBoard();
			System.out.println("请输入您下棋的坐标，应以x,y的格式：");
		}
    }
```

### 7.2.2 异常类的继承体系

- try块后面可以有多个catch块，多个catch块中的异常范围必须时从小到大

  ```java
  public class DivTest
  {
  	public static void main(String[] args)
  	{
  		try
  		{
  			int a = Integer.parseInt(args[0]);
  			int b = Integer.parseInt(args[1]);
  			int c = a / b;
  			System.out.println("您输入的两个数相除的结果是：" + c );
  		}
  		catch (IndexOutOfBoundsException ie)
  		{
  			System.out.println("数组越界：运行程序时输入的参数个数不够");
  		}
  		catch (NumberFormatException ne)
  		{
  			System.out.println("数字格式异常：程序只能接受整数参数");
  		}
  		catch (ArithmeticException ae)
  		{
  			System.out.println("算术异常");
  		}
  		catch (Exception e)
  		{
  			System.out.println("未知异常");
  		}
  	}
  }
  ```

- try后面的{}不可以省略，哪怕只有1行语句

### 7.2.3 访问异常信息

- getMessage():返回该异常的详细描述字符串

- printStackTrace():将该异常的跟踪栈信息输出到标准错误输出

- printStackTrace(PrintStream s):将该异常的跟踪栈信息输出到指定输出流

- getStackTrace():返回该异常的跟踪栈信息

  ```java
  public class AccessExceptionMsg
  {
  	public static void main(String[] args)
  	{
  		try
  		{
  			FileInputStream fis = new FileInputStream("a.txt");
  		}
  		catch (IOException ioe)
  		{
  			System.out.println(ioe.getMessage());
  			ioe.printStackTrace();
  		}
  	}
  }
  ```

### 7.2.4 使用finally回收资源

- 不管try块中的代码是否出现异常，也不管哪一个catch块被执行，甚至在try块或者catch块执行了return语句，finally块总会被执行
- 如果没有try块，后面的catch和finally块也不能有
- 如果有try块，后面的catch和finally块都是可选的，二者至少有一个

## 7.2 使用throws声明抛出异常

- 当前方法不知道如何处理这种类型的异常，该异常应该由上一级调用者处理

- 如果main方法也不知道如何处理这种类型的异常，也可以使用throws抛出，该异常将交给JVM处理

  ```java
  public class ThrowsTest2
  {
  	public static void main(String[] args)
  		throws Exception
  	{
  		// 因为test()方法声明抛出IOException异常，
  		// 所以调用该方法的代码要么处于try...catch块中，
  		// 要么处于另一个带throws声明抛出的方法中。
  		test();
  	}
  	public static void test()throws IOException
  	{
  		// 因为FileInputStream的构造器声明抛出IOException异常，
  		// 所以调用FileInputStream的代码要么处于try...catch块中，
  		// 要么处于另一个带throws声明抛出的方法中。
  		FileInputStream fis = new FileInputStream("a.txt");
  	}
  }
  ```

- 使用throws抛出异常时要注意子类抛出的异常访问<=父类抛出的异常

  ```java
  public class OverrideThrows
  {
  	public void test()throws IOException
  	{
  		FileInputStream fis = new FileInputStream("a.txt");
  	}
  }
  class Sub extends OverrideThrows
  {
  	// 子类方法声明抛出了比父类方法更大的异常
  	// 所以下面方法出错
  	public void test()throws Exception
  	{
  	}
  }
  ```

## 7.3 使用throw抛出异常

- throw用于自行抛出异常

- throw抛出的不是一个异常类，而是一个异常实例

  ```java
  public class AuctionException extends Exception
  {
  	// 无参数的构造器
  	public AuctionException(){}       //①
  	// 带一个字符串参数的构造器
  	public AuctionException(String msg)    //②
  	{
  		super(msg);
  	}
  }
  ```

  ```java
  public class AuctionTest
  {
  	private double initPrice = 30.0;
  	// 因为该方法中显式抛出了AuctionException异常，
  	// 所以此处需要声明抛出AuctionException异常
  	public void bid(String bidPrice)
  		throws AuctionException
  	{
  		double d = 0.0;
  		try
  		{
  			d = Double.parseDouble(bidPrice);
  		}
  		catch (Exception e)
  		{
  			// 此处完成本方法中可以对异常执行的修复处理，
  			// 此处仅仅是在控制台打印异常跟踪栈信息。
  			e.printStackTrace();
  			// 再次抛出自定义异常
  			throw new AuctionException("竞拍价必须是数值，"
  				+ "不能包含其他字符！");
  		}
  		if (initPrice > d)
  		{
  			throw new AuctionException("竞拍价比起拍价低，"
  				+ "不允许竞拍！");
  		}
  		initPrice = d;
  	}
  	public static void main(String[] args)
  	{
  		AuctionTest at = new AuctionTest();
  		try
  		{
  			at.bid("df");
  		}
  		catch (AuctionException ae)
  		{
  			// 再次捕捉到bid方法中的异常。并对该异常进行处理
  			System.err.println(ae.getMessage());
  		}
  	}
  }
  ```

# 8.输入/输出

## 8.1 File类

- File类可以通过使用文件路径字符串来创建File实例，该文件路径字符串既可以是绝对路径，也可以是相对路径
- 访问文件名相关的方法
  - String getName():返回此File对所表示的文件名或路径名
  - String getPath():返回此File对象所对应的路径名
  - File getAbsoluteFile()：返回此File对象所对应的绝对路径所对应的File对象
- 文件检测相关方法
  - boolean exists():判断File对象所对应的文件或目录是否存在
  - boolean isFile():判断File对象所对应的是否是文件，而不是目录

## 8.2 理解Java的IO流

### 8.2.1 流的分类

- 输入流和输出流
  - 输入流：只能从中读取数据
  - 输出流：只能向其写入数据
  - 从文件中读取内容----输入流     将内容写到文件中------输出流
- 字符流和字节流
  - 字节流操作的是8位的字节
  - 字符流操作的是16位的字符
- 节点流和处理流
  - 可以从/向一个特定的IO设备读/写数据的流，称为节点流
  - 处理流用于对一个已存在的流进行连接或封装

## 8.2.2 流的4个**抽象**基类

- InputStream/Reader:所有输入流的基类，前者是字节输入流，后者是字符输入流
- OutStream/Writer:所有输出流的基类，前者是字节输出流，后者是字符输出流

## 8.3 字节流和字符流

### 8.3.1 InputStream和Reader

- InputStream中的三个方法：

  - int read():从输入流中读取单个字节
  - int read(byte b[]):从输入流中读取最多b.length个字节的数据，并保存在字节数组中
  - int read(byte b[],int off,int len):从输入流中最多读取len个字节的数据，在数组b中从off位置开始存放

- Reader中的三个方法：

  - int read():从输入流中读取单个字符
  - int read(char buf[]):从输入流中最多读取buf.length个字符的数据，存储在buf数组中
  - int read(char buf[],int off,int len):从输入流中最多读取len个字符的数据，将其保存在buf数组中，存储时从off位置开始

  ```java
  public class FileInputStreamTest
  {
  	public static void main(String[] args) throws IOException
  	{
  		// 创建字节输入流
  		FileInputStream fis = new FileInputStream(
  			"FileInputStreamTest.java");
  		// 创建一个长度为1024的“竹筒”
  		byte[] bbuf = new byte[1024];
  		// 用于保存实际读取的字节数
  		int hasRead = 0;
  		// 使用循环来重复“取水”过程
  		while ((hasRead = fis.read(bbuf)) > 0 )
  		{
  			// 取出“竹筒”中水滴（字节），将字节数组转换成字符串输入！
  			System.out.print(new String(bbuf , 0 , hasRead ));
  		}
  		// 关闭文件输入流，放在finally块里更安全
  		fis.close();
  	}
  }
  
  ```

### 8.3.2 OutStream和Writer

- void write(int c):将指定的字节/字符输出到输出流中
- void write(byte[]/char[] buf):将字节数组/字符数组输出到指定输出流中
- void write(byte[]/char [] buf,int off,int len):将字节数组/字符数组中从off位置开始长度为len的字节/字符输出到输出流中
- void write(String str):将字符串中的字符输出到指定输出流中
- void write(String str,int off,int len):将str字符串里从off位置开始长度为len的字符输出到指定输出流中

```java
public class FileWriterTest
{
	public static void main(String[] args)
	{
		try(
			FileWriter fw = new FileWriter("poem.txt"))
		{
			fw.write("锦瑟 - 李商隐\r\n");
			fw.write("锦瑟无端五十弦，一弦一柱思华年。\r\n");
			fw.write("庄生晓梦迷蝴蝶，望帝春心托杜鹃。\r\n");
			fw.write("沧海月明珠有泪，蓝田日暖玉生烟。\r\n");
			fw.write("此情可待成追忆，只是当时已惘然。\r\n");
		}
		catch (IOException ioe)
		{
			ioe.printStackTrace();
		}
	}
}
```

## 8.4 对象序列化

### 8.4.1 序列化的含义和意义

- 对象的序列化指将一个Java对象写入IO流中，与此对应的是，对象的反序列化指的是从IO流中恢复该Java对象
- 某个类如果是可序列化的，需要实现以下两个接口之一：
  - Serializable
  - Externalizable

### 8.4.2 使用对象流实现序列化

```java
public class Person
	implements java.io.Serializable
{
	private String name;
	private int age;
	// 注意此处没有提供无参数的构造器!
	public Person(String name , int age)
	{
		System.out.println("有参数的构造器");
		this.name = name;
		this.age = age;
	}
	// 省略name与age的setter和getter方法

	// name的setter和getter方法
	public void setName(String name)
	{
		this.name = name;
	}
	public String getName()
	{
		return this.name;
	}

	// age的setter和getter方法
	public void setAge(int age)
	{
		this.age = age;
	}
	public int getAge()
	{
		return this.age;
	}
}
```

```java
public class WriteObject
{
	public static void main(String[] args)
	{
		try(
			// 创建一个ObjectOutputStream输出流
			ObjectOutputStream oos = new ObjectOutputStream(
				new FileOutputStream("object.txt")))
		{
			Person per = new Person("孙悟空", 500);
			// 将per对象写入输出流
			oos.writeObject(per);
		}
		catch (IOException ex)
		{
			ex.printStackTrace();
		}
	}
}
```

```java
public class ReadObject
{
	public static void main(String[] args)
	{
		try(
			// 创建一个ObjectInputStream输入流
			ObjectInputStream ois = new ObjectInputStream(
				new FileInputStream("object.txt")))
		{
			// 从输入流中读取一个Java对象，并将其强制类型转换为Person类
			Person p = (Person)ois.readObject();
			System.out.println("名字为：" + p.getName()
				+ "\n年龄为：" + p.getAge());
		}
		catch (Exception ex)
		{
			ex.printStackTrace();
		}
	}
}
```

# 9 多线程

## 9.1 线程概述

###  9.1.1 线程和进程

- 进程是系统进行资源分配和调度的基本单位
- 进程的三个特征：
  - 独立性
  - 动态性
  - 并发性
- 线程是进程的组成部分，一个进程可以有多个线程
- 归纳起来可以说：操作系统可以同时执行多个任务，每个任务就是进程；进程可以同时执行多个任务，每个任务就是线程

### 9.1.2 多线程的优势

- 线程比进程具有更高的性能
- 进程之前不能共享内存，但是线程之间共享内存非常容易
- 系统创建进程时需要为该进程重新分配系统资源，但创建线程的代价小得多

## 9.2 线程的创建和启动

### 9.2.1 继承Thread类创建线程类

- 定义Thread的子类，并重写该类的ruun()方法

- 创建Thread子类的实例，创建线程对象

- 调用线程对象的start()方法来启动该线程

  ```java
  public class FirstThread extends Thread
  {
  	private int i ;
  	// 重写run方法，run方法的方法体就是线程执行体
  	public void run()
  	{
  		for ( ; i < 100 ; i++ )
  		{
  			// 当线程类继承Thread类时，直接使用this即可获取当前线程
  			// Thread对象的getName()返回当前该线程的名字
  			// 因此可以直接调用getName()方法返回当前线程的名
  			System.out.println(getName() +  " " + i);
  		}
  	}
  	public static void main(String[] args)
  	{
  		for (int i = 0; i < 100;  i++)
  		{
  			// 调用Thread的currentThread方法获取当前线程
  			System.out.println(Thread.currentThread().getName()
  				+  " " + i);
  			if (i == 20)
  			{
  				// 创建、并启动第一条线程
  				new FirstThread().start();
  				// 创建、并启动第二条线程
  				new FirstThread().start();
  			}
  		}
  	}
  }
  ```

- 使用Thread类的方法来创建线程类时，多个线程之间无法共享线程类的实例变量

### 9.2.2 实现Runnable接口创建线程类

- 定义Runnable的接口的实现类，并重写该接口的run()方法

- 创建Runnable实现类的实例，并以此实例作为Thread的target来创建Thread对象

- 调用线程对象的start()方法来启动线程

  ```java
  public class SecondThread implements Runnable
  {
  	private int i ;
  	// run方法同样是线程执行体
  	public void run()
  	{
  		for ( ; i < 100 ; i++ )
  		{
  			// 当线程类实现Runnable接口时，
  			// 如果想获取当前线程，只能用Thread.currentThread()方法。
  			System.out.println(Thread.currentThread().getName()
  				+ "  " + i);
  		}
  	}
  
  	public static void main(String[] args)
  	{
  		for (int i = 0; i < 100;  i++)
  		{
  			System.out.println(Thread.currentThread().getName()
  				+ "  " + i);
  			if (i == 20)
  			{
  				SecondThread st = new SecondThread();     // ①
  				// 通过new Thread(target , name)方法创建新线程
  				new Thread(st , "新线程1").start();
  				new Thread(st , "新线程2").start();
  			}
  		}
  	}
  }
  ```

- 采用Runnable接口的方式创建的多个线程可以共享进程的实例属性

### 9.2.3 使用Callable创建线程

- Callable提供了一个call()方法作为线程执行体，但call()方法比run()方法更加强大

  - call()方法可以有返回值
  - call()方法可以声明抛出异常

- 创建并启动有返回值的进程步骤：

  - 创建Callable接口的实现类。并实现call()方法，该方法有返回值

  - 创建Callable实现类的实例，使用Future类来包装Callable对象，该FutureTask对象封装了该Callable对象call()方法的返回值

  - 使用FutureTask对象作为Thread对象的target创建并启动线程

  - 调用FutureTask对象的get方法来获得子线程执行结束以后的返回值

    ```java
    public class ThirdThread implements Callable<Integer>
    {    
        public Integer call()
        {
            int i=0;
            
            for ( ; i < 100 ; i++ )
    			{
    				System.out.println(Thread.currentThread().getName()
    					+ " 的循环变量i的值：" + i);
    			}
    			// call()方法可以有返回值
    			return i;
            
        }
    	public static void main(String[] args)
    	{
    		// 创建Callable对象
    		ThirdThread rt = new ThirdThread();
    		// 先使用Lambda表达式创建Callable<Integer>对象
    		// 使用FutureTask来包装Callable对象
    		FutureTask<Integer> task = new FutureTask<Integer>(rt);
    		
    		for (int i = 0 ; i < 100 ; i++)
    		{
    			System.out.println(Thread.currentThread().getName()
    				+ " 的循环变量i的值：" + i);
    			if (i == 20)
    			{
    				// 实质还是以Callable对象来创建、并启动线程
    				new Thread(task , "有返回值的线程").start();
    			}
    		}
    		try
    		{
    			// 获取线程返回值
    			System.out.println("子线程的返回值：" + task.get());
    		}
    		catch (Exception ex)
    		{
    			ex.printStackTrace();
    		}
    	}
    }
    
    ```

### 9.2.4 创建进程的三种方式对比

- 实现Runnable接口和实现Callable接口的方式基本相同，所有可以归为一种方式
- 实现接口创建多线程的方式与继承Thread类的方式的区别
  - 线程类只是实了Runnable接口或Callable接口，还可以继承其他类
  - 实现接口的方式下，多个线程可以共享一个target对象，适合处理多个相同线程来处理同一份资源的情况
  - 如果需要访问当前进程，必须要使用Thread.currentThread()方法
- 一般推荐采用Runable接口、Callable接口的方式来创建多线程

## 9.3 线程的生命周期

 ### 9.3.1 新建和就绪状态

- 使用new关键字创建一个线程以后，该线程就处于新建状态
- 当线程对象调用了start()方法后，线程就处于就绪状态

### 9.3.2 运行和阻塞状态

- 若就绪状态的线程获得了CPU，开始执行run()方法了，则该线程处于运行状态
- 如果线程调用sleep()方法，进程会进入阻塞状态
- 使用stop()方法可以结束进程，使进程处于死亡状态，不用对处于死亡状态的方法再次调用start()方法

## 9.4 控制线程

### 9.4.1 join线程

- 当某个程序在执行中调用其他线程的join方法时，调用线程将被阻塞，直到被join()方法加入的join线程执行完毕为止

  ```java
  public class JoinThread extends Thread
  {
  	// 提供一个有参数的构造器，用于设置该线程的名字
  	public JoinThread(String name)
  	{
  		super(name);
  	}
  	// 重写run()方法，定义线程执行体
  	public void run()
  	{
  		for (int i = 0; i < 100 ; i++ )
  		{
  			System.out.println(getName() + "  " + i);
  		}
  	}
  	public static void main(String[] args)throws Exception
  	{
  		// 启动子线程
  		new JoinThread("新线程").start();
  		for (int i = 0; i < 100 ; i++ )
  		{
  			if (i == 20)
  			{
  				JoinThread jt = new JoinThread("被Join的线程");
  				jt.start();
  				// main线程调用了jt线程的join()方法，main线程
  				// 必须等jt执行结束才会向下执行
  				jt.join();
  			}
  			System.out.println(Thread.currentThread().getName()
  				+ "  " + i);
  		}
  	}
  }
  ```

### 9.4.2 线程睡眠：sleep

- 使用sleep()方法可以让当前正在执行的线程暂停一段时间，并进入阻塞状态

  ```java
  public class SleepTest
  {
  	public static void main(String[] args)
  		throws Exception
  	{
  		for (int i = 0; i < 10 ; i++ )
  		{
  			System.out.println("当前时间: " + new Date());
  			// 调用sleep方法让当前线程暂停1s。
  			Thread.sleep(1000);
  		}
  	}
  }
  ```

### 9.4.3 线程让步  yield

- yield()方法和sleep()方法类似，但是yield()方法不会阻塞该进程，只会使该线程转入就绪状态

  ```java
  public class YieldTest extends Thread{
      public YieldTest(String name)
      {
          super(name);
      }
      //定义run()方法作为线程执行体
      public void run()
      {
          for(int i=0;i<50;i++)
              
              Sysout.out.println(getName()+" "+i);
          if(i==20)
          {
              Thread.yield();
          }
      }
      public static void main(String args[]) throws Exception
      {
          //启动两个并发线程
          YiedTest yt1=new YieldTest("高级");
          //将yt1线程设置成最高优先级
         // yt1.setPriority(Thread.MAX_PRIORITY);
          yt1.start();
          YieldTest yt2=new YieldTest("低级");
          //将yt2线程设置成最低优先级
         // yt2.setPriority(Thread.MIN_PRIORITY);
          yt2.start();
          
      }
  }
  ```

### 9.4.4 改变线程优先级

- 优先级高的线程获得较多的执行机会，优先级低的进程则获得较少的执行机会

- Thread提供的优先级静态常量：

  - MAX_PRIORITY:   10
  - MIN_PRIORITY:     1
  - NORM_PRIORITY:  5

  ```java
  public class PriorityTest extends Thread
  {
  	// 定义一个有参数的构造器，用于创建线程时指定name
  	public PriorityTest(String name)
  	{
  		super(name);
  	}
  	public void run()
  	{
  		for (int i = 0 ; i < 50 ; i++ )
  		{
  			System.out.println(getName() +  ",其优先级是："
  				+ getPriority() + ",循环变量的值为:" + i);
  		}
  	}
  	public static void main(String[] args)
  	{
  		// 改变主线程的优先级
  		Thread.currentThread().setPriority(6);
  		for (int i = 0 ; i < 30 ; i++ )
  		{
  			if (i == 10)
  			{
  				PriorityTest low  = new PriorityTest("低级");
  				low.start();
  				System.out.println("创建之初的优先级:"
  					+ low.getPriority());
  				// 设置该线程为最低优先级
  				low.setPriority(Thread.MIN_PRIORITY);
  			}
  			if (i == 20)
  			{
  				PriorityTest high = new PriorityTest("高级");
  				high.start();
  				System.out.println("创建之初的优先级:"
  					+ high.getPriority());
  				// 设置该线程为最高优先级
  				high.setPriority(Thread.MAX_PRIORITY);
  			}
  		}
  	}
  }
  ```

## 9.5 线程同步

### 9.5.1 同步代码块

- 同步代码块语法格式

  ```java
  synchronized(obj)
  {
  ...
      //此处的代码就是同步代码块
  }
  ```

  - 任何时刻只能由一个线程可以获得对同步监视器的锁定，当同步代码块执行完成后，该线程会释放对该同步监视器的锁定
  - Java程序允许使用任何对象作为同步监视器

  ```java
  public class Account
  {
  	// 封装账户编号、账户余额的两个成员变量
  	private String accountNo;
  	private double balance;
  	public Account(){}
  	// 构造器
  	public Account(String accountNo , double balance)
  	{
  		this.accountNo = accountNo;
  		this.balance = balance;
  	}
  	// 此处省略了accountNo和balance的setter和getter方法
  
  	// accountNo的setter和getter方法
  	public void setAccountNo(String accountNo)
  	{
  		this.accountNo = accountNo;
  	}
  	public String getAccountNo()
  	{
  		return this.accountNo;
  	}
  
  	// balance的setter和getter方法
  	public void setBalance(double balance)
  	{
  		this.balance = balance;
  	}
  	public double getBalance()
  	{
  		return this.balance;
  	}
  
  	// 下面两个方法根据accountNo来重写hashCode()和equals()方法
  	public int hashCode()
  	{
  		return accountNo.hashCode();
  	}
  	public boolean equals(Object obj)
  	{
  		if(this == obj)
  			return true;
  		if (obj !=null
  			&& obj.getClass() == Account.class)
  		{
  			Account target = (Account)obj;
  			return target.getAccountNo().equals(accountNo);
  		}
  		return false;
  	}
  }
  ```

  ```java
  public class DrawThread extends Thread
  {
  	// 模拟用户账户
  	private Account account;
  	// 当前取钱线程所希望取的钱数
  	private double drawAmount;
  	public DrawThread(String name , Account account
  		, double drawAmount)
  	{
  		super(name);
  		this.account = account;
  		this.drawAmount = drawAmount;
  	}
  	// 当多条线程修改同一个共享数据时，将涉及数据安全问题。
  	public void run()
  	{
  		// 使用account作为同步监视器，任何线程进入下面同步代码块之前，
  		// 必须先获得对account账户的锁定——其他线程无法获得锁，也就无法修改它
  		// 这种做法符合：“加锁 → 修改 → 释放锁”的逻辑
  		synchronized (account)
  		{
  			// 账户余额大于取钱数目
  			if (account.getBalance() >= drawAmount)
  			{
  				// 吐出钞票
  				System.out.println(getName()
  					+ "取钱成功！吐出钞票:" + drawAmount);
  				try
  				{
  					Thread.sleep(1);
  				}
  				catch (InterruptedException ex)
  				{
  					ex.printStackTrace();
  				}
  				// 修改余额
  				account.setBalance(account.getBalance() - drawAmount);
  				System.out.println("\t余额为: " + account.getBalance());
  			}
  			else
  			{
  				System.out.println(getName() + "取钱失败！余额不足！");
  			}
  		}
  		// 同步代码块结束，该线程释放同步锁
  	}
  }
  ```

### 9.5.2 同步方法

- 同步方法就是使用synchronized关键字来修饰某个方法
- 对于同步方法，无需显示指定同步监视器，同步方法的同步监视器是this,也就是该对象本身

## 9.6 线程通信

- 使用synchronized修饰的同步方法，因为该类的默认实例this就是同步监视器，所以可以在同步方法中直接调用这3个方法
- 对于synchronized修饰的同步代码块，同步监视器是synchronzied后括号里面的对象，所以必须使用该对象调用这3个方法
  - wait():导致当前线程等待，直到其他线程调用该同步监视器的notify()方法或notifyAll()方法来唤醒该进程
  - notify():唤醒在此同步监视器上等待的单个线程
  - notifyAll():唤醒在此同步监视器上等待的所有线程