# Math

| 方法名 |                        说明                        |
| :----: | :------------------------------------------------: |
|  abs   |           小bug(-2147483648 无对应正数)            |
|  ceil  | 向上取整（向正无穷大方向获取距离最近的整数），进一 |
| floor  |                      向下取整                      |
| round  |                      四舍五入                      |
|  pow   |                         幂                         |
|  sqrt  |                        开根                        |
|  max   |                                                    |
| random |          doubl返回值随机数 范围[0.0,1,0)           |

<img src="D:\Desktop\typoraNote\images\mi.png" style="zoom:40%;" />

# System

### 1970.1.1 00:00:00:00  算C语言生日

**1s = 1000 ms**

| exit()              | 终止Java虚拟机         |
| ------------------- | ---------------------- |
| currentTimeMillis() | 获取当前系统时间（ms） |
| arraycopy           | 数组拷贝               |

# Runtime

| getRuntime          | 当前系统运行的环境对象             |
| ------------------- | ---------------------------------- |
| exit                | 停止虚拟机                         |
| availableProcessors | 获取CPU线程数                      |
| maxMeory            | JVM能从系统中获取总内存大小  byte  |
| totalMeory          | JVM已经从系统中获取总内存大小 byte |
| freeMeory           | JVm剩余内存大小 byte               |
| exec                | 运行CMD                            |

# Object

**顶级父类无有参构造因为他无成员变量**

| toString | 返回该对象的字符串形式 |
| -------- | ---------------------- |
| equals   | 比较两个对象是否相等   |
| clone    | 对象拷贝               |

**一般父类方法不满足需要重写**

1. 重写0bject中的clone方法

2. 让javabean类实现Cloneable接口

3. 创建原对象并调用clone就可以了。

   浅克隆 object
   不管对象内部的属性是基本数据类型还是引用数据类型，都完全拷贝过来

   深克隆

   基本数据类型拷贝过来
   字符串复用
   引用数据类型会重新创建新的

## objects

| equals  | 先做非空判断，再比较对象    |
| ------- | --------------------------- |
| isNull  | 判断是否为NULL 是返回True   |
| nonNull | 判断是否为null 是返回 flase |

### BigInteger

GMT	 格林尼治时间

UTC  世界标准时间

中国标准 UTC + 8h
