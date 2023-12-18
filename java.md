# static 

> **特点**
>
> * 数据共享
> * 不属于对象，属于类
> * 随着类加载 优于对象存在

| JavaBean类 | 描述一类事物                                     |
| ---------- | ------------------------------------------------ |
| 测试类     | 检测类是否书写正确，main()入口                   |
| 工具类     | 不描述任何事物的类，处理一类事物  私有化构造方法 |

# 静态方法

- **静态方法只能访问静态**
- **非静态可以访问所有**
- **静态方法无this 关键字（this 表示当前调用者的地址值） 非静态 有默认this 由java 虚拟机提供**

# 继承

```java
public class 子类 extends 父类
```

- **Java 单继承 不可多继承 可多层继承**
- **每个类都直接或者间接继承于 Object**

| 构造方法 | 非私有   不能 | private  不能  |
| -------- | ------------- | -------------- |
| 成员变量 | 非私有   能   | private  能    |
| 成员方法 | 非私有   能   | private   不能 |

## 继承中： 

- 成员变量的访问特点   就近原则（先在局部位置找，**本类成员位置找（this），父类成员位置找(super)，**逐级往上。）

- 成员方法的访问：就近原则

  方法重写

  * **@Override 重写注解**  

  * 方法尽量和父类一致  只有被添加到虚方法表中的才可以重写

  

构造方法的访问

- 父类中的构造方法不会被子类继承 **但是可以通过super调用变量  子类构造第一行默认有一个super**
- 子类中所有的构造方法默认先访问父类中的无参构造，再执行自己。

## this 、 super

this: 理解为一个变量 ，表示当前调用者的地址值 （访问本类构造）

super: 代表父类存储空间（访问父类构造）

# 多态

**前提：**

**继承 父类引用子类对象 方法重写** （父类类型 对象行为  = 子类对象）

**同一继承树下不同对象的针对同一行为的不同表现**

- 调用成员变量的特点:编译看左边，运行也看左边

- 调用成员方法的特点:编译看左边，运行看右边

  多态弊端：不可以使用子类的特有方法（强制类型转换，在调用子类方法）**if (a  instanceof  Dog  d)**

## 包

- 包就是文件夹,用来管理各种不同功能的Java类
- 公司域名反写+包的作用，需要全部英文小写，见名知意
- **全类名: 包名+类名**

### final修饰符 

**修饰方法，不能被重写  修饰类 不能被重写  修饰变量 变成常量**

### 常量

final 修饰的变量为基本类型：变量存储的数据值不会发生改变

​                              **引用类型：变量存储的地址值不能改变，对象内部可以变**

### 权限修饰符

private < 默认/缺省 <protected < public

实际开发只用 private public

### 代码块

局部代码块

构造代码块

静态代码块

- 格式: static{}
- 特点:需要通过static关键字修饰，随着类的加载而加载，并且自动触发、只执行一次
- 使用场景:在类加载的时候，做一些**数据初始化**的时候使用.

## 抽象类

- 抽取共性时，无法确定方法体,就把方法定义为抽象的。
- 强制让子类按照某种格式重写。
- 抽象方法所在的类，必须是抽象类。
- **抽象类不能实例化**   实际作用：当创建子类时给属性赋值
- abstract

## 接口

**就是一种规则**  **对行为的抽象**

- public **interface** api{}
- **接口不能实例化**
- 接口和类是实现关系 public class 类名 implements api {}

注：接口可单实现，多实现  public **interface** api1，api2{}  实现类可以继承类的同时继承多个接口 public class 类名 extends 夫 implements api {}

**接口中的成员特点：**

- 成员：只能是常量 默认修饰符：public static fianl
- 无构造
- 成员方法：只能是抽象方法 默认：public abstract 

接口中静态方法

```java
格式： public  static 返回值类型 方法名(参数列表){
    
}
```

静态方法只能通过接口名调用 不能通过实现类或者对象名调用

私有方法

```java
格式：prvite static 返回值类型 方法名(参数列表){
    
}
```

### 设配器设计模式

当一个接口中抽象方法过多，但是我只要使用其中一部分的时候，就可以适配器设计模式

1. 编写中间类XXXAdapter,实现对应的接口
2. 对接口中的抽象方法进行空实现
3. 让真正的实现类继承中间类,并重写需要用的方法
4. 为了避免其他类创建适配器类的对象，中间的适配器类
5. 用abstract进行修饰

## 内部类

**在一个类中再定义一个类**

| 内部类的访问特点                         |
| ---------------------------------------- |
| 内部类可以直接访问外部类的成员，包括私有 |
| 外部类要访问内部类的成员，必须创建对象   |

<img src=".\images\内部类.png" style="zoom:40%;" />

### 匿名内部类

隐藏了名字的内部类，可以写在成员位置，也可以写在局部位置。

```java
new Swim() {   // 类名或者接口
    @Override
    public void swim() {
        System.out.println("sd");
    }
};
```

- 当方法的参数是接口或者类时，以接口为例，可以传递这个接口的实现类对象，
- 如果实现类只要使用一次，就可以用匿名内部类简化代码。

## 包装类

**基本数据类型对应的对象**

JDK5 以后 增加自动装箱 自动拆箱

int integer成员方法

```java
integer.toBinaryString()  16

integer.toOvctalString()  8

integer.toHexString()   2
    // 在类型转换时，参数只能是数字
    // 8 中包装类，除Character有对应的parseXXX方法，进行类型转换
```

**约定： 以后不管什么输入都使用nextLine**

### 集合进阶

 ![image-20231204210645824](C:\Users\tlian\AppData\Roaming\Typora\typora-user-images\image-20231204210645824.png)

#### Collection

​		Collection 是单例集合的接口  它的功能是全部单例集合都可以继承使用

| 方法名称                            | 说明 |
| ----------------------------------- | ---- |
| public boolean add(E e)             | 添加 |
| public void clear()                 | 清空 |
| public boolean remove(E e)          | 删除 |
| public boolean contains(Object obj) | 包含 |
| public boolean isEmpty()            | 为空 |
| public int size()                   | 长度 |

```java
 Collection<String> coll = new ArrayList<>();

        // 1.添加元素
        // 如果往list系列集合添加数据 那么方法永远返回true 因为list集合允许元素重复
        // 如果往Set系列集合中添加数据 set数据不允许重复
        coll.add("sss");
        System.out.println(coll);

        // Collection 里面定义的是共性的方法 此时不能通过索引删除 只能通过对象删除
        // 返回值为Boolean
        coll.add("ass");
        boolean result = coll.remove("ass");
        System.out.println(result);

        // 包含
        // 底层是依赖equal方法判断是否存在
        // so 自定义对象需要重写equals
```

### 迭代器遍历

**迭代器在Java中的类是Iterator,迭代器是集合专用的遍历方式。**

| Collection集合获取迭代器 |                                                           |
| ------------------------ | --------------------------------------------------------- |
| Iterator<E> iterator( )  | 返回迭代器对象， 默认指向当前集合的0索引                  |
| boolean hasNext( )       | 判断当前位置是否有元素，有元素返回true ,没有元素返回false |
| E next()                 | 取取当前位置的元素，并将迭代器对象移向下一个位置。        |

<img src=".\images\迭代器.png" style="zoom:40%;" />

### 增强for遍历

- 增强for的底层就是迭代器，为了简化迭代器的代码书写的。
- 它是JDK5之后出现的，其内部原理就是一个Iterator迭代器
- 所有的单列集合和数组才能用增强for进行遍历。

```
for(String s:list){
	s = "q";
}    // 这里的s只是一个变量 不会修改listd
```

### ArrayList集合地层原理

- 利用空参创建的集合，在底层创建一个默认长度为0的数组
- 添加第一个元素时，底层会 创建一个新的长度为10的数组
- 存满时，会扩容1.5倍

### LinkedList集合

![LinkList](.\images\LinkList.png)

## 泛型<伪>

- 泛型:是JDK5中引入的特性，可以在编译阶段约束操作的数据类型，并进行检查。
- 泛型的格式: <数据类型>
- 注意:泛型只能支持引用数据类型。

<img src=".\images\泛型.png" alt="fx" style="zoom:70%;" />

### Set 系列集合

> * **无序**:存取顺序不一致
> * **不重复**:可以去除重复
> * **无索引**:没有带索引的方法，所以不能使用普通for循环遍历，也不能通过索引来获取元素

Set 集合的实现类

- HashSet:  无序、不重复、无索引
- LinkedHashSet:  有序、不重复、无索引
- TreeSet:  可排序、不重复、无索引

**Set接口中的方法.上基本上与Collection的API一致。**

**哈希值**

![](.\images\哈希值.png)

### HashSet地层原理

- HashSet集合底层采取哈希表存储数据
- 哈希表是一种对于增删改查数据性能都较好的结构

#### 哈希表组成

- JDK8之前:数组+链表.
- JDK8开始:数组+链表+红黑树

![](.\images\HashSet.png)

- JDK8以后，当链表长度超过8，而且数组长度大于等于64时，自动转换为红黑树
- 如果集合中存储的是自定义对象，必须要重写hashCode和equals方法

### LinkedHashSet底层原理

![](.\images\LinkHashList.png)

**默认使用HashSet**

## TreeSet

![](.\images\treeSet.png)

## 双列集合

![](.\images\双列集合的特点.png)

Map api

![](.\images\Map_api.png)

## HashMape的底层原理

- HashMap是Map里面的一个实现类。
- 没有额外需要学习的特有方法，直接使用Map里面的方法就可以了。
- **特点都是由键决定的:无序、不重复、无索引**
- **HashMap跟HashSet底层原理是一模一样的，都是哈希表结构.**

> - **依赖hashCode方法和equals方法保证键的唯一**
> - 如果键存储的是自定义对象， 需要重写hashCode和equals方法
> - 如果值存储自定义对象，不需要重写hashCode和equals方法

```java
public class A03_HashMapDemo1 {
    public static void main(String[] args) {
        HashMap<Student,String> hm = new HashMap<>();

        Student s1 = new Student("zhansan",22);
        Student s2 = new Student("limix",22);
        Student s3 = new Student("wangwu",23);

        // 添加元素
        hm.put(s1,"江苏");
        hm.put(s2,"重庆");
        hm.put(s3,"山东");

        // 遍历集合
        Set<Student>  keys = hm.keySet();
        for(Student s : keys){
            String value = hm.get(s);
            System.out.println(s + "=" + value);
        }

        System.out.println("------------------------");

        Set<Map.Entry<Student,String>> entries = hm.entrySet();
        for(Map.Entry<Student,String> entry : entries){
            Student key = entry.getKey();
            String value = entry.getValue();
            System.out.println(key + "=" +value);
        }
        System.out.println("------------------------");
        // lamber
        hm.forEach((Student,s) -> System.out.println(Student + "=" + s));

    }
}
```



## LinkedHashMap

![](.\images\LinkedHashMap.png)

## TreeMap

![](.\images\treeMap.png)

```java
public class A01_TreeMapDemo {
    public static void main(String[] args) {
        TreeMap<Integer,String> tm = new TreeMap<>(new Comparator<Integer>() {
            @Override
            public int compare(Integer o1, Integer o2) {
                // o1 当前要添加的元素
                // o2 表示已经在红黑树中存在的元素
                return o1 - o2;
            }
        });

        tm.put(3,"雷碧");
        tm.put(4,"九个核桃");
        tm.put(5,"康师傅");

        System.out.println(tm);
    }
}
```

# p11~p19 先跳过

**ctrl alt v  自动生成变量**

## 可变参数

- 可变参数本质上就是一个数组,

- 作用:在形参中接收多个数据

- 格式:数据类型...参数名称

- 注意事项:

- **形参列表中可变参数只能有一 个**

- **可变参数必须放在形参列表的最后面**

  

## Collections  集合工具类

![](.\images\collection_Api.png)

```java
public class CollectionDemo1 {
    public static void main(String[] args) {
        ArrayList<Integer> list = new ArrayList<>();
        Collections.addAll(list,10,23,43,435,45,45,6);
        Collections.sort(list);
        System.out.println(list);
    }
}
```

```java
public class RandomRollCall {
    public static void main(String[] args) {
        // 70% 男 30% 女

        // 创建集合
        ArrayList<Integer> list = new ArrayList<>();
        Collections.addAll(list, 1, 1, 1, 1, 1, 1);
        Collections.addAll(list, 0, 0, 0);
        //打乱集合中的数据
        Collections.shuffle(list);
        // 随机抽取
        Random rand = new Random();
        int index = rand.nextInt(list.size());
        int number = list.get(index);
        System.out.println(number);

        //创建两个集合存男女名字
        ArrayList<String> boyList = new ArrayList<>();
        ArrayList<String> girlList = new ArrayList<>();

        Collections.addAll(boyList,"饭桶","小米","小明","小流","方桶","珠穆朗玛峰","肚子痛");
        Collections.addAll(girlList,"理想城","理财","sy","小蔡");

        //判断抽取
        if(number == 1){
            // boy
            int boyIndex = rand.nextInt(boyList.size());
            String name = boyList.get(boyIndex);
            System.out.println(name);
        }else {
            // girl
            int girlIndex = rand.nextInt(girlList.size());
            String name = girlList.get(girlIndex);
            System.out.println(name);
        }

    }
}
```

![](.\images\不可变集合.png)



## Stream流

![](.\images\Stream.png)



## 方法引用

把已经有的方法拿过来用,当做函数式接口中抽象方法的方法体

> - **需要有函数式接口**
> - **被引用方法必须已经存在**
> - 被引用方法的形参和返回值需要跟抽象方法保持一致
> - 被引用方法的功能要满足当前的需求
> - **格式:   类名 ：：方法**

```java
public class FunctionDemo1 {
    public static void main(String[] args) {
        // 静态方法引用

        //1. 创建集合并添加元素
        ArrayList<String> list = new ArrayList<>();

        Collections.addAll(list, "1", "2", "3", "4", "5", "6");

        // 2. 变为int型
        list.stream().map(new Function<String, Integer>() {
            @Override
            public Integer apply(String s) {
                int i = Integer.parseInt(s);
                return i;
            }
        }).forEach(s -> System.out.println(s));

        // 方法需要已经存在
        //方法的形参和返回值需要跟抽象方法的形参和返回值保持一致
        //方法的功能需要把形参的字符串转换成整数
        list.stream().map(Integer::parseInt).forEach(s -> System.out.println(s));
    }
}
```

### 引用成员方法

格式:对象: :成员方法

> ①其他类:其他类对象::方法名
> ②本类: this: :方法名      
> ③父类: super: :方法名    

```java
public class FunctionDemo2 {
    public static void main(String[] args) {
        // 1.创建集合
        ArrayList<String> list = new ArrayList<>();
        // 2.添加数据
        Collections.addAll(list, "张无忌", "周芷若", "赵敏", "张强", "张三丰");
        // 3.过滤数据<只要以"张"开头,而且名字是三个字>
        list.stream().filter(s -> s.startsWith("张"))
                .filter(s -> s.length() == 3)
                .forEach(s -> System.out.println(s));

        list.stream().filter(new Predicate<String>() {
            @Override
            public boolean test(String s) {
                return  s.startsWith("张") && s.length() == 3;

            }
        }).forEach(s -> System.out.println(s));

        // 方法引用
        StringOperation so = new StringOperation();
        list.stream().filter(so::stringJudge).forEach(s -> System.out.println(s));

        // 本类引用
        StringOperation so2 = new StringOperation();
        list.stream().filter(new FunctionDemo2()::stringJudge).forEach(s -> System.out.println(s));
    }
    public boolean stringJudge(String s){
        return s.startsWith("张") && s.length() == 3;
    }
}
```

**P43-p51跳过**



## 异常

![异常](.\images\异常.png)

#### 异常处理方式

**JVM默认处理**

> - 把异常的名称，异常原因及异常出现的位置等信息输出在了控制台
> - 程序停止执行，下面的代码不会再执行

**自己处理**(当代码出现异常可以让程序继续执行)

```java
try{
   可能出现的异常
}catch (异常类名 变量名){
    异常处理
}finall{
    一定会执行，除非JVM 停止运行
}
```

![](.\images\异常处理.png)

![](.\images\Throwbale.png)



## File

- File对象就表示一个路径，可以是文件的路径、也可以是文件夹的路径
- 这个路径可以是存在的，也允许是不存在的

![](.\images\File.png)



![](.\images\file成员方法.png)

![](.\images\file成员方法2.png)



![](.\images\file成员方法(获取并遍历).png)



## IO流

![](.\images\IO流.png)



### IO 流的分类

![](.\images\IO流分类.png)

##### 纯文本文件

![](.\images\什么是纯文本文件.png)

##### IO流体系

![](.\images\IO流体系.png)

##### **FileOutputStream**

​	操作本地文件的字节输出流，可以把程序中的**数据写到本地**文件中。

- 细节1:参数是字符串表示的路径或者是File对象都是可以的
- 细节2:如果文件不存在会创建一个新的文件，但是要保证父级路径是存在的。.
- 细节3:**如果文件已经存在，则会清空文件**
  -   两个问题（既然会清空文件我怎么去**续写**？ 写入数据又怎么实现**换行**？）
    -  如果想要续写，打开续写开关即可
       默认false:表示关闭续写，此时创建对象会清空文件
       手动传递true:表示打开续写，此时创建对象不会清空文件
    - 换行加入一个回车

![](.\images\FileOuptStream写数据.png)

##### FileInputStream

操作本地文件的字节输入流，可以把本地文件中的**数据读取到程序**中来。

输入流:文件不存在，报错?

> 因为创建出来的文件是没有数据的，没有任何意义。
> 所以Java就没有设计这种无意义的逻辑，文件不存在直接报错。

**读到文件末尾了，read方法返回-1。** **(read每次读取时移动指针的 循环体再读取一次得到的数据不对)**

```java
int flags;
        while ((flags = fis.read()) != -1) {
            System.out.println(flags);
        }
```

![](.\images\FileInputStream读多个字节.png)

### 字符集

![](.\images\ASCII.png)

![](.\images\字符对比.png)

![](.\images\Unicode.png)

##### 为什么乱码

> 字节流: 一次读取一个字节
>
>  编码和解码时的方式不统一

## 字符流

![](.\images\字符流.png)



### IO完整体系

![](.\images\IO体系II.png)

### 字节缓冲流

​	原理:底层自带了长度为8192的缓冲区提高性能

![](.\images\缓冲流.png)

### 转换流

![](.\images\转换流.png)

### 序列化流/对象操作流

​	**可以把Java的对象写到本地文件**

### 反序列化流

​	**可以把序列化到本地文件中的对象，读取到程序中来**

### 打印流

​	**打印流一般是指: PrintStream, PrintWriter两个类**

- 打印流只操作文件目的地，不操作数据源
- 特有的写出方法可以实现，数据原样写出

特有的写出方法,

- 可以实现自动刷新，自动换行
- 打印一次数据=写出+换行+刷新

### 解压缩流



## Commons-io

Commons-io是apache开源基金组织提供的一-组有关I0操作的开源工具包。
作用:**提高I0流的开发效率**。



### Hutool 工具包      [入门和安装 (hutool.cn)](https://hutool.cn/docs/#/)

![](.\images\Hutool.png)

## 线程

线程是操作系统能够进行运算调度的最小单位。它被包含在**进程**之中，是进程中的实际运作单位。

简单理解:**应用软件中互相独立，可以同时运行的功能**

### 并发和并行

并发：在同一时刻，有多个指令在单个CPU上**交替**执行

并行：在同一时刻，有多个指令在多个CPU上**同时**执行

### 多线程的实现方式

1. 继承Thread类的方式进行实现

   ```java
   public class ThreadDemo1 {
       public static void main(String[] args) {
           /*
               多线程启动方式一:
               1. 自定义类继承Thread
               2. 重写run方法
               3. 创建子类对象 并启动线程
            */
           MyThread t1 = new MyThread();
           MyThread t2 = new MyThread();
   
           t1.setName("MyThread1");
           t2.setName("MyThread2");
           // 开启线程
           t1.start();
           t2.start();
       }
   }
   ```

2. 实现Runnable接口的方式进行实现

   ```java
   public class ThreadDemo2 {
       public static void main(String[] args) {
           /*
           多线程的第二二种启动方式:
           1.自己定义一一个类实现Runnable接口
           2.重写里面的run方法
           3.创建自己的类的对象
           4.创建-一个Thread类的对象，并开启线程
            */
   
           // 创建MyRun的对象
           MyRun myRun = new MyRun();
           // 创建线程对象
           Thread t1 = new Thread(myRun);
           Thread t2 = new Thread(myRun);
   
           // 设置名字
           t1.setName("myRun1");
           t2.setName("myRun2");
   
           // 开启线程
           t1.start();
           t2.start();
       }
   }
   ```

   

3. 利用Callable接口和Future接口方式实现

```java
public class ThreadDemo3 {
    public static void main(String[] args) throws ExecutionException, InterruptedException {
        /*
        多线程的第三种实现方式:
        特点:可以获取到多线程运行的结果
            1创建一个类MyCallable实现Callable接口
            2.重写call (是有返回值的，表示多线程运行的结果)
            3.创建MyCallable的对象( 表示多线程要执行的任务)
            4.创建Future的对象(作用管理多线程运行的结果)
         */

        // 创建MyCallable 对象
        MyCallable mc = new MyCallable();
        // 创建FutureTask 对象 （作用：管理多线程运行结果）
        FutureTask<Integer> ft = new FutureTask<>(mc);
        // 创建线程对象
        Thread t1 = new Thread(ft);
        // 启动线程
        t1.start();

        // 管理多线程运行结果
        Integer re = ft.get();
        System.out.println(re);
    }
}
```

**多线程对比**

![](.\images\多线程实现对比.png)

### 多线程常见方法

![](.\images\多线程成员方法.png)

### 线程生命周期

![](.\images\生命周期.png)

### 同步代码块

**把操作共享数据的代码锁起来**

- 锁默认打开，有一个线程进去了，锁自动关闭
- 里面的代码全部执行完毕，线程出来，锁自动打开

**方法：**

就是把**synchronized关键字**加到方法上

![](.\images\同步方法特点.png)

### 等待唤醒机制（生产者和消费者）

![](.\images\等待与唤醒.png)



### 等待唤醒机制(阻塞队列方式实现)

![](.\images\阻塞队列.png)

### 线程状态

![](.\images\线程状态.png)

### 线程池

![](.\images\线程池.png)

```java
public class MythreadDemo {
    public static void main(String[] args) {
        /**
         * ThreadPoolExecutor threadPoolExecutor = new ThreadPoolExecutor
         * (核心线程数量,最大线程数量,空闲线程最大存活时间，任务队列,创建线程工厂, 任务的拒绝策略);
         * 参数一:核心线程数量           不能小于0
         * 参数二:最大线程数            不能小于0，最大数量>=核心线程数量
         * 参数三:空闲线程最大存活时间    不能小于0
         * 参数四:时间单位             用TimeUnit指定
         * 参数五:任务队列              不能为null
         * 参数六:创建线程工厂           不能为null
         * 参数七:任务的拒绝策略         不能为null
         */

        ThreadPoolExecutor pool = new ThreadPoolExecutor(
                3,
                6,
                60,
                TimeUnit.SECONDS,
                new ArrayBlockingQueue<>(3),
                Executors.defaultThreadFactory(),
                new ThreadPoolExecutor.AbortPolicy()
        );
    }
}
```

