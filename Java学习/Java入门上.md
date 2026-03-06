```cmd
javac HelloWorld.java // 得到HelloWorld.class
java HelloWorld // 运行
```

**Java SE、Java ME和Java EE**

**Java运行在虚拟机(JVM)中，只需要安装不同操作系统平台上的虚拟机即可**

**JDK(Java Development Jit)包含JVM、核心类库和开发工具**

**JRE(Java Runtime Environment)包含JVM、核心类库和运行工具**

**单行注释// 多行注释 文档注释**

**字面量**

- 整数类型 默认是int类型
- 小数类型
- 字符串类型
- 字符类型
- 布尔类型 true false
- 空类型 null (字符串形式打印)

**二进制0b开头 八进制0开头 十六进制0x开头**

**A对应65 a对应97**

**基本数据类型**

- byte
- short
- int
- long 可以在数据值后面加一个L
- float 数据值后面需要加一个F作为后缀
- double
- char
- boolean

**输入**

```java
import java.util.Scanner;

Scanner sc = new Scanner(System.in);
int a = sc.nextInt();
System.out.println(a);
```

**项目结构**

- module
- package
- class

**整数运算只能得到整数**

**隐式转换（自动类型提升）**

- 取值范围小的转成取值范围大的，**byte->short->int->long->float->double**
- **byte short char**三种类型的数据在运算的时候，都会先提升为**int**，然后再进行运算

**强制转换**

- 把一个取值范围大的数值赋值给取值范围小的变量，必须**强制转换**
- 例子

  ```java
  int a = 300;
  byte b = (byte) a;
  ```

**字符串的‘+’操作**

- 当出现字符串时，变为字符串连接符
- 从左到右依次操作

**短路逻辑运算符**

- &&就是短路与，两个逻辑运算符就是短路操作

**无符号右移>>>**

**switch用法**

- 用法一

  ```java
  switch (表达式) {
      case 字面量,字面量:
          执行语句;
          break;
      default:
          执行语句;
          break;
  }
  ```
- 用法二

  ```java
  switch (表达式) {
      case 字面量,字面量 -> {
          执行语句;
      }
      default -> {
          执行语句;
      }
  }
  ```

**随机数**

```java
import java.util.Random;

Random r = new Random();
int a = r.nextInt(10); // 0 ~ 9
```

**数组**

- 数组的静态格式化

  ```java
  // 完整格式
  int[] array = new int[]{1, 2, 3};
  // 简化格式
  int[] array = {1, 2, 3}
  System.out.println(array); // 打印地址值
  System.out.println(array.length); // 数组长度
  
  // 二维数组
  int[][] array = {{1, 2, 3}, {4, 5, 6, 7, 8}};
  ```
- 数组的动态初始化

  ```java
  int[] array = new int[10]; // 虚拟机会给出默认的初始化值
  // 整数类型和小数类型默认是0
  // 字符类型默认是'/u000' 空格
  // 布尔类型默认是false
  // 引用数据类型默认是"null"
  
  // 二维数组
  int[][] array = new int[3][5];
  ```
- 数组的内存图，数组的内容存放在**堆**中，数组地址存放在**栈**中
- 方法重载的条件只跟方法参数有关，跟返回类型无关

**Javabean类**

- 用来描述一类事物的类，不写main方法
- 一个Java文件可以定义多个class类，只能有一个是public修饰，而且public修饰的类名必须是代码文件名

**测试类**

- 编写main方法，使用Javabean类

**封装**

- 对象代表什么，就需要封装对应的数据，并提供数据对应的行为

**就近原则**

```java
public class GirlFriend {
  private int aget;
    public void method() {
      int age = 10;
      System.out.println(age); // 就近原则 所以是10
      System.out.println(this.age) // 0
    }
}
```

**构造方法**

- 创建对象的时候由虚拟机调用构造方法，不能手动调用
- 每创建一次对象，就会调用一次构造方法
- 如果定义了构造方法，系统将不再提供默认的构造方法

**标准JavaBean类**

- 成员变量使用private修饰
- 至少提供无参构造方法和带全部参数的构造方法
- 提供每一个成员变量对应的set和get方法

**this的原理**

- 表示调用者的地址值，用来区分局部变量和成员变量

**String构造**

```java
String s1 = "abcd"; // 在StringTable中开辟空间，可以复用
char[] charArr = {'a', 'b', 'c', 'd'};
String s2 = new String(charArr); // 在堆空间中开辟新的空间
byte[] byteArr = {97, 98, 99, 100};
String s3 = new String(byteArr);
System.out.println(s1==s2); // false 引用数据类型比较的是地址值

// 方法
s1.subString(1, 3);
s1.charAt(2);
s1.replace('a', 'b');
```

**StringBuilder**

```java
StringBuilder sb = new StringBuilder("abc");
sb.append("abc");
sb.reverse();
String s = sb.toString(); // 转换为String
// 在拼接和反转的时候使用StringBuilder
// sb.capacity() 容量
// 如果放不下会进行扩容，原来的容量*2+2，如果还不够，以实际长度为准
```

**StringJoiner**

```java
StringJoiner sj = new StringJoiner(", ", "[", "]");
int[] arr = {1, 2, 3};
for (int i = 0; i < arr.length; i ++ )
    sj.add(arr[i] + "");
System.out.println(sj.toString()); // [1, 2, 3]
```

**字符串拼接的底层原理**

- 如果没有变量参与，都是字符串相加，会复用串池中的字符串
- 如果有变量参与，会在内存中创建新的字符串，浪费内存

**集合**

```java
ArrayList<String> list = new ArrayList<>();
list.add("aaa");
list.add("bbb");
list.add("ccc");
list.remove("aaa"); // true
list.remove(0); // bbb
list.set(0, "aaa"); // ccc
list.get(0); // aaa
sout(list.size()); // 1
ArrayList<Interger> list = new ArrayList<>(); // 集合不能包装基本数据类型，所以需要包装
```

**工具类**

- 只是做一些事情的类
- 私有化构造方法
- 其它方法为静态方法，方便使用类名调用

**static注意事项**

- 静态方法只能访问静态变量和静态方法
- 非静态方法都能访问
- 静态方法不能使用**this**关键字

**继承**

- 父类的构造方法都不能继承，成员变量都可以继承，非private非static非final方法可以继承
- 子类重写父类方法，形参列表必须与父类一致，重写方法前加@Override，访问权限必须大于等于父类，返回值类型必须小于等于父类，**只有继承的方法可以重写**
- 子类构造方法首先调用父类的**无参构造**，调用super()

**多态**

- 调用成员变量，编译看左边，运行看左边
- 调用成员方法，编译看左边，**运行看右边**，可以转换类型然后调用子类方法

  ```java
  // 判断类型
  if (a instanceof Dog)
  if (a instanceof Dog d) // 如果是类型Dog，转换之后变量名为
  ```

**导包规则**

- 在使用同一个包中的类时，不需要导包
- 使用java.lang包中的类时，不需要导包

**final**

- 修饰类，不能继承
- 修饰方法，不能重写
- 修饰变量，不能修改，注意如果修饰引用数据类型，地址值不能变化，但是内部属性值可以改变

  ```java
  final int A = 1;
  A = 3; // 报错，不能改变
  
  final int[] ARR = {1, 2, 3};
  ARR[0] = 1; // 可以改变
  ```

**权限修饰符**

|修饰符 |同一个类中 |同一个包中其他类 |不同包下的子类 |不同包下的无关类 |
|:---:|:---:|:---:|:---:|:---:|
|private |√ |   |   |   |
|空着不写 |√ |√ |   |   |
|protected |√ |√ |√ |   |
|public |√ |√ |√ |√ |

**构造代码块（被淘汰）**

- 把多个构造方法中重复的代码抽取出来，在创建本类对象的时候会先执行构造代码块然后再执行构造方法

**静态代码块**

- 随着类的加载而加载的，**并且只执行一次**，用于数据初始化

  ```java
  static {
      // 代码块
  }
  ```

**抽象类和抽象方法**

- 抽象类不能实例化
- 抽象类不一定有抽象方法，有抽象方法的类一定是抽象类
- 可以有构造方法
- 抽象类的子类要么重写所有抽象方法要么是抽象类

```java
public abstract class Person {
    public abstract void work();
}
```

**接口**

- 成员变量只能是常量，默认修饰符**public static final**
- 方法已经可以定义方法体了，**默认修饰符public abstract**
- 接口可以多继承
- 默认方法，使用关键字default修饰，不是默认方法，不强制被重写
- 静态方法，不能被重写，**只能通过接口名调用**
- 私有方法，可以静态，可以默认
- 接口多态，方法参数是接口，编译看左边，运行看右边

```java
public insterface Swim {
    public abstract void swim();

    public default void show() {
        sout("hello");
    }

    public static void show1() {
        sout("hello!");
    }
}
```

**内部类**

- 成员内部类

  ```java
  public class Outer {
      private int a = 10;
  
      public class Inner {
          public void show() {
              sout(Outer.this.a); // 访问外部类的变量
          }
      }
  
      private Class Inner1 {
  
      }
  
      public Inner1 getInstance() {
          return new Inner1();
      }
  }
  Outer.Inner oi = new Outer().new Inner(); // 获取成员内部类
  Outer o = new Outer();
  o.getInstance(); // 使用外部类方法来返回内部类对象
  ```
- 静态内部类

  ```java
  public class Outer {
      int a = 10;
      static class Inner {
          public void show1() { 
              Outer o = new Outer();
              sout(o.a);
          } 
          public static void show2() { 
          }
      }
  } 
  Outer.Inner oi = new Outer.Inner(); // 这里的new作用于Inner()
  oi.show1(); // 非静态方法，先创建对象，再调用 
  Outer.Inner.show2(); // 静态方法，通过类名调用
  ```
- 局部内部类

  ```java
  public class Outer {
      public void show() {
          class Inner { // 局部内部类
  
          }
      }
  }
  ```
- 匿名内部类（重要，前三个了解）

  ```java
  public interface Swim() {
      public abstract void swim();
  }
  new Swim() {
      @Override
      public void swim() {
          sout("游泳");
      }
  }
  ```

**常用API**

```java
// Math
Math.abs(-1); // 绝对值
Math.ceil(12.34); // 13 向上取整
Math.floor(-12.24); // -13 向下取整
Math.round(12.34); // 12 四舍五入
Math.max(20, 30); // 30 较大值
Math.min(20, 30); // 20 较小值
Math.pow(2, 3); // 8 a的b次幂
Math.sqrt(4); // 2 平方根
Math.cqrt(8); // 2 立方根
Math.random(); // [0, 1.0)

// System
System.exit(0); // 正常停止 底层源码就是下面的runtime.exit(0)
System.currentTimeMillis(); // 当前系统的时间毫秒值形式 long类型
System.arraycopy(数据源数组，起始索引，目的地数组，起始索引，拷贝个数);

// Runtime
Runtime r = Runtime.getRuntime();
r.exit(0); // 停止虚拟机
r.maxMemory(); // 总内存大小，单位byte
r.totalMemory(); // 已经获得的内存大小
r.freeMemory(); // 剩余内存大小
r.exec("dir"); // 执行cmd命令

// Object
Object.toString(); // 返回地址值
Object.equals(); // 比较地址值
Object.clone(); // 需要在类中重写clone方法，实现Cloneable接口，然后就可以克隆了
// 深克隆 基本数据类型复制，字符串复用，其它引用数据类型复制地址
// Objects
Objects.equals(s1, s2); // 会先判断s1是否为null，然后再调用equals方法
Objects.isNull(s1); // 判断是否为null
Objects.nonNull(s1); // 和上面结果相反

// BigInteger
BigInteger(num, new Random()); // 0到2^num-1的随机数
BigInteger("123456"); // 参数必须是整数字符串
BigInteger("100", 2); // 4 第二个是进制
BigInteger.valueOf(100); // 范围不能超过long的范围，在-16到16进行优化
// 使用add进行相加，但是会产生新的BigInteger对象
BigInteger.intValue(); // 转换为int类型

// BigDecimal
BigDecimal(0.01); // 有可能不精确
BigDecimal("0.01); // 精确，建议使用
BigDecimal.valueOf(0.01); // 精确
// 会将每一个字符存进来，用字节表示
```

**正则表达式**

- 具体规则不用记
- 本地爬虫

```java
import java.util.regex.Pattern;
import java.util.regex.Matcher;

String str = "Java是一门编程语言，Java8";
Pattern p = Pattern.compile("Java\\d{0, 2}"); // 正则表达式对象
Matcher m = p.matcher(str); // 文本匹配器对象
boolean b = m.find(); // 如果有匹配对象，则返回true
String s1 = m.group(); // 取出匹配字符串 Java

// 第二次读取
b = m.find();
String s2 = m.group(); // Java8
```


