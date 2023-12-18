# Maven

Apache Maven是一个项目管理和构建工具，它基于项目对象模型(POM)的概念,通过一小段描述信息来管理项目的构建。

- 方便的依赖管理
- 统一的项目结构
- 标准的项目构建流程

![](.\images\Maven 架构.png)

#### 依赖配置

![](.\images\依赖配置.png)

#### 依赖范围

![](.\images\依赖范围.png)

#### 生命周期

![](.\images\Maven生命周期.png)

## SpringBoot

### 三层架构

![](.\images\spring_三层架构.png)

### 分层耦合

- 内聚:软件中各个功能模块内部的功能联系。
- 耦合:衡量软件中各个层/模块之间的依赖、关联的程度。
- 软件设计原则:**高内聚低耦合**。

![](.\images\spring_分层解耦.png)

## MySQL

关系型数据库(RDBMS) : 建立在关系模型基础上，由多张相互连接的**二维表**组成的数据库。

- 使用表存储数据，格式统一,便于维护
- 使用SQL语言操作，标准统一，使用方便，可用于复杂查询

#### **通用语法**

- SQL语句可以单行或多行书写，以**分号结尾**。
- SQL语句可以使用空格/缩进来增强语句的可读性。
- MySQL数据库的SQL语句**不区分大小写**。

#### SQL分类

![](.\images\sql四大语句.png)

### 事务

事务是一组操作的集合,它是一个不可分割的工作单位。事务会把所有的操作作为一个整体起向系统提交或撤销操作请求,即这些
**操作要么同时成功，要么同时失败。**

默认MySQL的事务是自动提交的，也就是说，当执行一条DML语句, **MySQL会立即隐式的提交事务。**

#### 事物控制

- 开启事务: start transaction; / begin ;
- 提交事务: commit;
- 回滚事务: rollback;

#### 索引

**索引(index) 是帮助数据库高效获取数据的数据结构**

优点

- 提高数据查询的效率，降低数据库的I0成本。
- 通过索引列对数据进行排序，降低数据排序的成本，降低CPU消耗。

缺点

- 索引会占用存储空间。
- 索引大大提高了查询效率，同时却也降低了insert、update、delete的效率。


#### 索引结构

多路平衡搜索树

![](.\images\B+Tree.png)

### MyBatis

MyBatis是一款优秀的持久层框架，用于**简化JDBC的开发。**

![](.\images\mybatis准备.png)

```java
spring.datasource.driver-class-name-com.mysql.cj.jdbc.Driver
spring.datasource.url=jdbc:mysql://localhost:3306/honey2024
spring.datasource.username=root
spring.datasource.password=123456
    
# 配置Mybatis输出日志位置，输出到控制台
mybatis.configuration.log-impl= org.apache.ibatis.logging.stdout.StdOutImpl
```

### JDBC

![](.\images\jdbc vs mybatis.png)

### 数据库链接池

- 数据库连接池是个容器，负责分配、管理数据库连接(Connection)
- 它允许应用程序重复使用一个现有的数据库连接，而不是再重新建立一个
- 释放空闲时间超过最大空闲时间的连接，来避免因为没有释放连接而引起的数据库连接遗漏

### lomok

Lombok是一个实用的Java类库,能通过注解的形式自动生成构造器、getter/setter. equals、 hashcode、 toString等方法,并可以自动化生成日志变量，简化java开发、提高效率。

![](.\images\lomok.png)

### XML映射文件

**规范**

- XML映射文件的名称与Mapper接口名称一致,并且将XML映射文件和Mapper接口放置在相同包下(同包同名)。
- XML映射文件的namespace属性为Mapper接口全限定名一致。
- XML映射文件中sql语句的id与Mapper接口中的方法名一致， 并保持返回类型一致。

![](.\images\msql_xml.png)

**使用Mybatis的注解，主要是来完成一些简单的增删改查功能。如果需要实现复杂的SQL功能，建议使用XML来配置映射**
**语句。**

### 动态SQL

随着用户的输入或外部条件的变化而变化的SQL语句，我们称为动态SQL。

![](D:\Desktop\typoraNote\images\动态sql_if.png)

![](.\images\foreach_sql.png)

```xml
<sql>: 定义可重用的SQL片段。
<include>: 通过属性refid,指定包含的sql片段。
```

### 阿里云OSS

阿里云对象存储OSS ( Object Storage Service) ,是一款海量、安全、低成本、高可靠的云存储服务。使用OSS,您可以通
过网络随时存储和调用包括文本、图片、音频和视频等在内的各种文件。

### 登录校验

![](.\images\登录校验.png)

#### 会话技术

- **会话**:用户打开浏览器,访问web服务器的资源，**会话建立,直到有一方断开连接 ,会话结束。**在一次会话中 可以包含多次请求和响应。
- **会话跟踪**: 一种维护浏览器状态的方法,服务器需要识别多次请求是否来自于同一浏览器,以便在同一一次会话的多次请求间**共享数据**。
- **会话跟踪方案**:
  - 客户端会话跟踪技术: Cookie
  - 服务端会话跟踪技术: Session
  - 令牌技术

![](.\images\Cookie.png)

#### jwt

JSON Web Token (https://jwt.io/)

![](.\images\jwt.png)
