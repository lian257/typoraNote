# Java Web

**Asynchronous JavaScript and XML**

### JS基本语法

- 区分大小写
- 行尾分号可有可无
- 大括号表示代码块

### **输出语句**

- 使用window.alert()写入警告框
- 使用document.write()写入HTML输出
- 使用console.log()写入浏览器控制台

### **变量**

- JavaScript中用var关键字(variable 的缩写)来声明变量。
- JavaScript是一门弱类型语言，**变量可以存放不同类型的值**。

### **数据类型**

JavaScript中分：原始和引用数据类型

原始：number:数字(整数、小数、NaN(Not a Number)) | string |boolean | null |undefined

![](.\images\运算符.png)

### 函数

语法：JavaScript函数通过**function关键字**进行定义

```javascript
1.方式一
function functionName(参数1,参数2..){
//要执行的代码
}
2.方式二
var functionName = function (参数1,参数2..){
//要执行的代码
}
```

- **形式参数不需要类型**。因为JavaScript是弱类型语言
- ​        **返回值也不需要定义类型**，可以在函数内部直接使用return返回即可
  - **JS中，函数调用可以传递任意个数的参数 但是只接收定义的参数**



## JS对象

### **Array**

**JavaScript中的数组相当于Java中集合,数组的长度是可变的,而JavaScript是弱类型,所以可以存储任意的类型的数据。**

| forEach( ) | 遍历数组中的每个有值的元素，并调用一次传入的函数 |
| :--------: | :----------------------------------------------: |
|  push( )   |    将新元素添加到数组的末尾，并返回新的长度。    |
| splice( )  |                从数组中删除元素。                |

**ES6箭头函数：(.....)  => {....}**   简化书写

```javascript
//forEach:遍历数组中有值的元素
arr.forEach (function (e) {
console.log(e)
})

arr. forEach((e) =>{
  console.log(e)  
})
```

### String

| charAt( )   | 返回在指定位置的字符。                   |
| ----------- | ---------------------------------------- |
| index0f( )  | 检索字符串。                             |
| trim( )     | 去除字符串两边的空格                     |
| substring() | 提取字符串中两个指定的索引号之间的字符。 |

### JavaScript自定义对象

![](.\images\js自定义对象.png)

### JSON

- 概念: JavaScript Object Notation, JavaScript对 象标记法。
- **JSON是通过JavaScript对象标记法书写的文本。**
- 由于其语法简单，层次结构鲜明，**现多用于作为数据载体**,在网络中进行数据传输。

![](.\images\json.png)

### BOM

概念: Browser Object Model**浏览器对象模型,允许JavaScript与浏览器对话，JavaScript 将浏览器的各个组成部分封装为对象。**

组成：

Window: 浏览器窗口对象        Navigator: 浏览器对象        Screen: 屏幕对象    History: 历史记录对象   Location: 地址栏对象

![](.\images\浏览器窗口对象.png)



### DOM

![](.\images\DOM.png)

![](.\images\DOM_1.png)

### JS事件监听

- 事件: HTML事件是发生在HTML元素上的“事情” 。比如:
  - 按钮被点击
  - 鼠标移动到元素上
  - 按下键盘按键
- **事件监听: JavaScript可以在事件被侦测到时执行代码。**

![](.\images\事件绑定.png)

### 常见事件

![](.\images\常见事件.png)

## VUE

- 框架:是一个半成品软件,是一套可重用的、通用的、软件基础代码模型。基于框架进行开发，更加快捷、更加高效。
- **Vue是一套前端框架，免除原生JavaScript中的DOM操作，简化书写**。
- 基于MVVM(Model-View-View-Model)思想，**实现数据的双向绑定，将编程的关注点放在数据上。**

![](.\images\MVVM.png)

**插值表达式**

**形式：{{表达式}}**

#### **常见指令**

![](.\images\Vue 常见指令.png)

![](.\images\vue 常见指令-1.png)

### Vue生命周期

![](.\images\Vue生命周期.png)

### Ajax

- 概念: Asynchronous JavaScript And XML，**异步的JavaScript和XML**。

- 作用:

  - **数据交换:**通过Ajax可以给服务器发送请求，并获取服务器响应的数据。

  - **异步交互**:可以在**不重新加载**整个页面的情况下，与服务器交换数据并更新部分网页的技术,如:搜索联想,用户名是否可用的校验

### Axios

- 介绍: **Axios对原生的Ajax进行了封装，简化书写,快速开发。**
- 官网: https://www.axios-http.cn/

### vue-cli

- 介绍: **Vue-cli是Vue官方提供的一个脚手架，用于快速生成一个Vue的项目模板。.**
- Vue-cli提供了如下功能:
  - 统一的目录结构
  - 本地调试
  - 热部署
  - 单元测试
  - 集成打包上线
- 依赖环境: NodeJS

```java
// vue项目创建
vue ui
```

### vue项目-目录接口

![](.\images\vue项目接口.png)

### Vue项目-端口配置

![](.\images\Vue端口配置.png)

### Vue文件

![](.\images\vue组成.png)

### ElementUI组件

**安装**：[组件 | Element](https://element.eleme.cn/#/zh-CN/component/installation)

main.js

```javascript
import ElementUI from 'element-ui';
import 'element-ui/lib/theme-chalk/index.css';
Vue.use(ElementUI);
```

