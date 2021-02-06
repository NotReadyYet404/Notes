# JavaScript

## 基本数据类型

### :one: Number

:man_student: JS中所有的数值类型都是Number，包括整数和浮点数

:o: typeof运算符可以检查数据类型，将数据类型以字符串的返回。**语法：typeof 变量名**;检查字符串时，返回string；检查数值时，返回number。

```javascript
var a = "123";
var b = 123;
console.log(typeof a);
console.log(typeof b);
```

:o: Number.MAX_VALUE是JS所能表示的数值的最大值(即1.7976931348623157e+308)。如果表示的数值超过这个数值便会等于Infinity，表示正无穷，当然Infinity或-Infinity也属于Number型。

:warning:Number.MIN_VALUE是JS的最小正数(即5e-324)。

```javascript
console.log(Number.MAX_VALUE);
console.log(Number.MAX_VALUE * Number.MAX_VALUE);
console.log(typeof Infinity);
```

:o: JS的浮点运算机制处理的不够好，结果可能不精确。

```javascript
var a = 0.3;
var b = 0.2;
console.log(a + b);
```

### :two: Boolean

```javascript
var a = false;
var b = true;
```

### :three: Null

:man_student: 只有一个null值，专门用来表示一个为空的<font color=red>对象</font>。所以使用typeof检查时，会返回object。

```javascript
console.log(typeof null);
```

### :four: Undefined

:man_student: 只有一个undefined值，当声明一个变量却未给它赋值，它便会被赋值undefined。

```javascript
var a;
console.log(a);
```

### :five: String

### :six: 强制类型转换

#### :o: 将其他数据类型转换为String：

:one: 调用被转换数据类型的toString()方法(Null和Undefined这两个类型没有toString()方法)

```javascript
var a = 123;
var b = a.toString();
console.log(a);
console.log(b);
console.log(typeof a);
console.log(typeof b);
```

:two: 调用String()方法(可用于Null和Undefined类型,**并且不影响作为被转换变量的类型**)

```javascript
var a = 123;
var b = true;
var c = null;
var d = undefined;
console.log(String(a));
console.log(String(b));
console.log(String(c));
console.log(String(d));
console.log(typeof a);
console.log(typeof String(a));
```

#### :o: 将其他数据类型转换为Number

:one: 使用Number()方法(用法与String()方法一样)

:warning:非数字内容，空字符串等等将返回NaN

**true转换为1；false转换为0；null转换为0；undefined转换为NaN**

```javascript
var a = "123";
var b = true;
var c = null;
var d = undefined;
console.log(Number(a));
console.log(Number(b));
console.log(Number(c));
console.log(Number(d));
console.log(typeof Number(a));
console.log(typeof Number(b));
console.log(typeof Number(c));
console.log(typeof Number(d));
```

:two: 使用parseInt()或parseFloat()方法进行相对智能的转换**(先将参数转换为String之后在进行转换Number，如果转换String后无法转换Number则返回NaN)**

:man_student:**这两个方法都是取到第一个符合类型的便会终止，不再检查后面的字符串。**

```javascript
var a = "125px";
var b = "123.3";
var c = "1234px12";
var d = "255.23.1";
var e = 123.2;
console.log(parseInt(a));
console.log(parseFloat(b));
console.log(parseInt(c));
console.log(parseFloat(d));
console.log(parseInt(e));
```

:o: **加上第二个参数可按照相应进制转换相应的数值**

```javascript
var a = "013";
var b = "13";
console.log(parseInt(a, 10));
console.log(parseInt(a, 8));
console.log(parseInt(b, 8));
```

#### :o: 将其他数值转换为Boolean

**使用Boolean()方法**:(①Number中0和NaN为false其他全部为true；②String除了空串其余全是true；③Null和Undefined都是false；④Object为true)。

## 运算符

### :one: 算数运算符

#### :o: 任何数据类型做算术运算时(除与String相加)，都会将其他转换成Number再进行运算。

```javascript
var c = "123";
var d = true;
console.log(c / d);
console.log(typeof (c / d));
```

#### :o: 任何值和NaN运算结果都为NaN。

#### :o: 任何值和字符串相加都会转换为字符串，并进行拼串操作。

​	:o: 此为隐式操作，实质为浏览器自动调用String()方法。

```javascript
result1 = 1 + 2 + "3";
result2 = "1" + 2 + 3;
console.log("result1=" + result1);
console.log("result2=" + result2);
```

### :two: 一元运算符

:o: +转换为整数；-转换为负数；非Number类型先转换Number在转换正负。

### :three: 逻辑运算符

####  :o: &&和||运算的非Boolean类型运算

​		对于&&的非布尔值运算，先进行对非布尔值的布尔转换，第一个为true返回第二个；第一个为false返回第一个。

```javascript
var a = 5 && 6;
var b = 0 && 2;
var c = 2 && 0;
var d = NaN && 0;
var e = 0 && NaN;
console.log(a);
console.log(b);
console.log(c);
console.log(d);
console.log(e);
```

​		对于 || ，如果第一个值为true，则返回第一个值；如果第一个值为false，则返回第二个值。

```javascript
var a = 2 || 1;
var b = 2 || NaN;
var c = 2 || 0;

var d = NaN || 1;
var e = NaN || 0;
var f = "" || "hello";
var g = -1 || "你好";

console.log("2 || 1 = " + a);
console.log("2 || NaN = " + b);
console.log("2 || 0 = " + c);
console.log("NaN || 1 = " + d);
console.log("NaN || 0 = " + e);
console.log("\"\" || \"hello\" = " + f);
console.log("-1 || \"你好\" = " + g);
```

### :four: 关系运算符

#### :o: 对于非数值要先转换为数值；**任何值和NaN比较结果都是false**

```javascript
console.log("1 > true = " + (1 > true));
console.log("1 > \"0\" = " + (1 >= "0"));
console.log("10 < \"hello\" = " + (10 < "hello"));
```

#### :warning: 两侧都是字符串时，比较字符串的Unicode大小（含中文时没有意义）

```javascript
console.log("\"1\" < \"5\" = " + ("1" < "5"));
console.log("\"abc\" < \"b\" = " + ("bbc" < "b"));
```

#### :warning:两侧都是数字字符串时，会发生不可预知的结果。<font color=red>所以每当这种情况一定要对其中一个进行Number转型</font>

### :five: Unicode编码

#### :o: 在JS中输出Unicode编码使用"\uUnicode十六进制编码"

```javascript
console.log("\u0054");//输出T
console.log("\u2620");//输出💀
```

#### :o: 在网页中（即H5中）输出需要使用&#Unicode十进制编码加分号

```javascript

```

### :six: 相等运算符

#### :o: NaN不和任何值相等，包括他自己

#### :o: Undefined衍生自Null所以他俩相等。

#### :o: 一般两个不同数值类型是会转换成Number类型再比较是否相等

```javascript
console.log("hello" == true);
console.log("1" == true);
console.log("11" == 11);
console.log(1 == true);
```

#### :o: 全等(===)不会做自动类型转换，所以只要两个值的类型不一样则直接返回false

## 对象

### :one: 分类

#### :o: 内建对象

:man_student: 由ES标准中定义的对象，在任何的ES的实现中都可以使用。比如：String、Number、Boolean、Function、Object……

#### :o: 宿主对象

:man_student:由JS的运行环境提供的对象，目前主要指浏览器提供的对象。比如：BOM、DOM。

#### :o: 自定义对象

:man_student:由开发人员自己创建的对象。

### :two:自定义对象

#### :o: 创建对象

```javascript
方式一：对象名 = new Object();
方式二(常用)：var 对象名 = {
    属性名: 属性值,
    ……
};
方式三：var obj = Object.create(null);
```

#### :o: 添加属性

```javascript
对象名.属性名 = 属性值;
```

#### :o: 删除属性

```javascript
delete 对象名.属性名
```

#### :o: 属性详解

**属性名的命名方式相对灵活没有固定的规则**，**<font color=red>但如果不符合标识符的规则则需要如下形式，且属性名加双引号</font>**

```javascript
对象名[属性名]
var s = "hello";
obj = new Object();
obj[s] = "你好";
console.log(obj);
```

**使用<font color=red>in</font>运算符检查一个对象中是否含有某个属性，有则返回true，无则返回false**

```javascript
属性名(以字符串的形式表示) in 对象名
```

#### :o: 对象字面量

:man_student:一个简易高校的创建对象的方式。

```javascript
var 对象名 = {[属性1名:属性1值],……[属性n名:属性n值]}
```

### 枚举对象的属性名或属性值

#### ① Object.keys方法

:man_student:获取参数对象的所有属性名，以数组形式返回

```javascript
//Object.keys(对象名);
var obj = {
    name: 'Tom',
    age: 10,
    gender: 'male',
    speak: function () {
        console.log(this.gender);
    }
};
var keys = Object.keys(obj);
for (var i = 0; i < keys.length; i++) {
    console.log(keys[i]);
}
```

#### ② Object.values方法

:man_student:获取参数对象的所有属性值，以数组的形式返回

```javascript
//Object.values(对象名);
var obj = {
    name: 'Tom',
    age: 10,
    gender: 'male',
    speak: function () {
        console.log(this.gender);
    }
};
var values = Object.values(obj);
for (var i = 0; i < values.length; i++) {
    console.log(values[i]);
}
```

#### ③ Object.entries方法

:man_student:获取对象数组的所有的属性名和属性值，以二维数组形式返回

```javascript
//Object.entries(对象名);
var obj = {
    name: 'Tom',
    age: 10,
    gender: 'male',
    speak: function () {
        console.log(this.gender);
    }
};
var attributes = Object.entries(obj);
for (var i = 0; i < attributes.length; i++) {
    console.log(attributes[i][0] + ": " + attributes[i][1]);
}
```

#### ④ for in遍历(常用)

```javascript
var obj = {
    name: 'Tom',
    age: 10,
    gender: 'male',
    speak: function () {
        console.log(this.gender);
    }
};
for (var i in obj) {
    console.log(i + ": " + obj[i]);
}
```



### :warning: window对象

浏览器会自动创建window对象，script标签内所有对象都是window的属性。

var声明的变量会在所有代码执行前执行。

使用函数声明的方式声明的函数会首先被声明。

### Math对象

#### ① PI属性

:man_student:圆周率

```javascript
console.log(Math.PI);
```

#### ② ceil方法

:man_student:对参数向上取整

```javascript
console.log(Math.ceil(Math.PI));
```

#### ③ floor方法

:man_student: 对参数向下取整

```javascript
console.log(Math.floor(Math.PI));
```

#### ④ round方法

:man_student: 对参数进行四舍五入，取整

```javascript
console.log(Math.round(Math.PI));
```

#### ⑤ pow方法

:man_student:求一个数的多少次幂

```javascript
var num = 10;
console.log(Math.pow(num, 3));
```

#### ⑥ max和min方法(参数不可为数组)

:man_student: 求数据的最大值：Math.max(值1， 值2，值3，……)；

```javascript
var res = Math.max(1, 0, 7, 3, 2);
console.log(res);
```

:man_student:求数据的最小值：Math.min(值1， 值2， 值3，值4，……)；

```javascript
var res = Math.min(1, 0, 7, 3, -2);
console.log(res);
```

#### ⑦ abs方法

:man_student:Math.abs(数据)：求数据的绝对值

```javascript
var num = -3;
var res = Math.abs(num);
console.log(res);
```

#### ⑧ sqrt()方法

:man_student:Math.sqrt(数据)：求数据的算数平方根

```javascript
var num = 4;
var res = Math.sqrt(num);
console.log(res);
```

#### :exclamation: random方法

:man_student: Math.random()：返回0-1的随机小数，包含0但不包含1。

```javascript
console.log(Math.random());
```

:man_student:parseInt(Math.random() * (最大值+1 - 最小值) + 最小值)：生成n-m的随机整数，包含n和m。

```javascript
//求1-5的随机数
console.log(parseInt(Math.random() * (5 + 1 - 1) + 1));
```

### 日期和时间对象

#### ① 创建时间日期对象

:man_student: var 对象名称 = new Date()：创建系统当前的日期和时间对象

```javascript
var date = new Date();
console.log(date);
```

:man_student:var 对象名称 = new Date(日期时间字符串)：将指定时间日期字符转换为时间日期对象

```javascript
var date_str = '2000-2-16 14:30:44';
var birthday = new Date(date_str);
console.log(birthday);
```

结果：

![](F:\学习\前端\JavaScript_Notes\日期时间字符串转日期时间对象.png)

:man_student: var 对象名 = new Date(毫秒值)：返回距离1970年1月1日0时0分0秒(非东八区)的时间点

```javascript
var date = new Date(1000);
console.log(date);
```

#### ② getFullYear方法

:man_student:日期时间对象.getFullYear()：获取对象的年份，以Number类型返回。

```javascript
var date = new Date();
var year = date.getFullYear();
console.log(year);
console.log(typeof year);
```

#### ③ getMonth方法

:man_student:日期时间对象.getMonth()：返回的月份，:exclamation:是0-11，0表示一月，11代表12月

```javascript
var date = new Date();
var month = date.getMonth();
console.log(month);
```

#### ④ getDate方法

:man_student:日期对象.getDate()：返回日。

```javascript
var date = new Date();
var day = date.getDate();
console.log(day);
```

#### ⑤ getDay方法

:man_student:日期对象.getDay()：返回星期，:exclamation:返回值为0-6，0表示星期日

```javascript
var date = new Date();
var day = date.getDay();
console.log(day);
```

#### ⑥ getHours方法

:man_student:日期时间对象.getHours()：返回小时

```javascript
var date = new Date();
var hour = date.getHours();
console.log(hour);
```

#### ⑦ getMinutes方法

:man_student:日期时间对象.getMinutes()：返回分钟

```javascript
var date = new Date();
var minutes = date.getMinutes();
console.log(minutes);
```

#### ⑧ getSeconds方法

```javascript
var date = new Date();
var seconds = date.getSeconds();
console.log(seconds);
```

#### ⑨ 获取日期时间的字符串形式

:man_student:日期时间对象.toLocalString()：获取日期和时间，以字符串返回

```javascript
var date = new Date();
var date_str = date.toLocaleString();
console.log(date_str);
console.log(typeof date_str);
```

:man_student:日期时间对象.toLocalDateString()：获取日期字符串

```javascript
var date = new Date();
var date_str = date.toLocaleDateString();
console.log(date_str);
console.log(typeof date_str);
```

:man_student:日期时间对象.toLocaleTimeString()：获取时间字符串

```javascript
var date = new Date('2000-2-16 3:00:00');
var time_str = date.toLocaleTimeString();
console.log(time_str);
```



## 函数

函数也是一个对象，只不过函数内可以封装一些功能（代码）

### 创建函数

#### ① new方式创建函数(不要允许定义前调用)

```javascript
var 函数名 = new Function('参数1', '参数2', '参数3', ……, '参数n');//不管有多少个参数，最后一个是函数体，其他的是形参。
var fun = new Function('num1', 'num2', 'console.log(num1 + num2)');
fun(1, 33);
```

#### ② 函数声明方式创建函数(允许定义前调用)

```javascript
function 函数名([形参1,形参2,……形参n]){
    语句……
}//可在声明前调用
//创建打印"This is my second function"的函数
func();
function func(){
    console.log("This is my second function");
}
```

#### ③ 使用函数表达式来创建函数(允许定义前调用)

```javascript
var 函数名 = function([形参1, 形参2, ……形参n]){
	语句……
}
//不能再定义之前调用
//！fun();
var fun = function() {
    console.log('hello world');
}

```

####  ④ 立即执行函数(或匿名自执行函数)

```javascript
(function(a, b){
 console.log(a + b);
 })(1, 2);
```

#### 匿名函数

:man_student: 没有函数名称的函数，可以和事件相结合，常用格式：

HTML元素.on事件名称 = function(){

​     ……

};

```javascript
//为页面中的div节点添加点击事件，当点击div时，在控制台打印5个hello

//写在body内的script标签内
//获取页面中的div
var myDiv = document.querySelector('div');
//为div添加点击事件
myDiv.onclick = functionn() {
    for(var i = 1; i <=5; i++) {
        console.log('hello');
    }
};
```



---

#### 回调函数

:man_student: 如果一个函数被当作另一函数的参数，则作为参数的这个函数就是回调函数。通常是匿名函数。

```javascript
var arr = [1, 2, 3, 4, 5, 6, 33, 47];
// 数组filter方法：作用是从数组中过滤符合条件的数组元素，返回值有这些符合条件的
// 元素组成的新数组。格式：数组名称.filter(function(val){return 条件;});
var res = arr.filter(function(val) {
    return val > 5;
});
console.log(res);
```



---

:exclamation: 定义形参时不需要加var

:exclamation: 全局变量与局部变量重名时，全局变量会被屏蔽，想使用就必须window.变量名或this.变量名

#### arguments对象

:man_student:该对象是函数内部的一个对象，只能在函数内使用。用来管理传来的数据，即实参。

:man_student: 他是伪数组类型，管理实参时也是用下标的方式对实参进行编号。还包含length和callee属性

arguments.length：实参个数

arguemts.callee：该属性实际是所在函数的引用，类似java的this。常与用来实现递归。

```javascript
function add(num1, num2) {
    console.log(arguments);
    
    console.log(arguments[0]);
    console.log(arguments[1]);
    console.log(arguments[2]);
    //Array.isArray(参数);
    //是数组返回true, 不是数组就返回false
    console.log(Array.isArray(arguments));
}
```

:exclamation:arguments告诉我们：当实参个数确定时，可以定义形参；但当不确定时可以不定义形参，直接通过arguments对象管理。

```javascript
//求和，但不确定是多少个数的和
function add() {
    var sum = 0;
    for (var i = 0; i < arguments.length; i++) {
        sum += arguments[i];
    }
    return sum;
}
console.log(add(1,2 , 44, 99, 123));
console.log(add(7, 47));
```

:warning:Javascript没有重载函数机制，如果两个函数名相同，则后定义的会覆盖前定义的。但可以使用arguments对象模拟重载。

```javascript
function add() {
    if(arguments.length == 2) {
        console.log("这是两个形参:" + (arguments[0] + arguments[1]));
    }
    else if(arguments.length == 3){
        console.log("这是三个形参:" + (arguments[0] + arguments[1] + arguments[2]));
    }
}
add(1, 2);
add(47, 47, 47);
```



## 数组

### 数组的分类

#### ① 按下标分类：一维、二维、多维数组

1. 一维数组：下标为一个的数组，如arr[下标]
2. 二维数组：下标为两个的数组，如arr\[下标][下标]
3. 多维数组：下标为大于等于3的数组，如arr\[下标]\[下标][下标]

#### ② 按下标的类型分类：索引型数组、关联性数组

1. 索引型数组：数组元素下标为数值型，如arr[0]
2. 关联型数组：数组元素下标为字符串型，如arr["num"]

### 数组的创建

#### :one:new方式(不常用)

```javascript
var 数组名 = new Array();
//创建一个空数组
var arr = new Array();
//创建一个长度为三的数组
var arr = new Array(3);
//创建一个长度为4的数组并分别赋值2、6、1、8
var arr = new Array(2, 6, 1, 8);
```

```javascript
//创建二维数组

var ArrayObj = new Array();    //创建数组对象
for (var i = 0; i < length; i++) {
    ArrayObj[i] = new Array();    //在每一个数组元素内再定义一个数组
}
```



#### :four:自变量创建数组

```javascript
//创建一维数组
var 数组名 = [值1，值2，值3，……值n];
//创建一个空数组
var arr = [];
//创建一个长度为1的数组并为元素赋值为4
var arr = [4];
//创建一个长度为4的数组并分别赋值2、6、1、8
var arr = [2, 6, 1, 8];
```

```javascript
//创建二维数组
var 数组名 = [[值1, 值2, 值3], [值4, 值5, ]]
```



#### :o:数组是存储在堆中的，所以数组是引用类型数据

```javascript
var arr = [1, 2, 3, 4];
var num;
num = arr[0];
console.log(num);
num = 100;
console.log(arr[0]);
num = arr;
num[0] = 12;
console.log(arr[0]);
```

#### 删除数组都某个元素

```javascript
//只是删除值，但数组空间(长度)不变
var arr = [0, 2, 3, 4, 5];
delete arr[2];
console.log(arr);
```

结果

<img src="./delete数组元素.png"/>

#### 增加数组元素

```javascript
//方式一
数组名[下标] = 元素值;
var arr = [1, 2, 3];
arr[5] = 8;
```

结果：

![](F:\学习\前端\JavaScript_Notes\数组增加元素方式一.png)

```javascript
//方式二，注意新的长度要大于原有长度
数组名.length = 新的长度;
var arr = [1, 2, 3];
arr.length = 7;
console.log(arr);
```

结果：

![](F:\学习\前端\JavaScript_Notes\数组增加元素方式二.png)



### 遍历数组元素

#### ① for in循环遍历数组元素

```javascript
var arr = [1, 2, 3, 4, 5];
//in使得每次循环将数组的下标一次赋给变量sub
for (var sub in arr){
    console.log(arr[sub]);
}
```

#### ② for of遍历数组元素

```javascript
var arr = [1, 2, 3, 4, 5, 6];
//与for in加数组不同的是for of加数组每次循环是依次将数组元素赋给变量value的
for (var value of arr){
    console.log(value);
}
```



### 数组对象的常用方法

#### ① join方法

:man_student:：作用是将数组转换为字i符串

```javascript
//分隔符可以省略，转化时数组元素将默认以逗号分隔
数组名.join("分隔符");

var arr = ['a', 'b', 'c', 'z', 'f'];
var str = arr.join();
console.log(str);
str = arr.join("&");
console.log(str);
str = arr.join("");
console.log(str);
```

#### ② indexOf方法和lastIndexOf方法

:man_student:indexOf的作用是在数组中查找指定的值，找到返回其下标并终止查找，否则返回-1。

```javascript
//数组名.indexOf(查找值,[起始下标]);

var arr = [10, 20, 30, 40, 50, 60, 70,80, 40, 100];
var res;
res = arr.indexOf(40);
console.log(res);
res = arr.indexOf(40, 4);
console.log(res);
```

:man_student:与indexOf唯一的区别是lastInexOf是从后往前找，其余的作用，格式什么的都是完全一样。

```javascript
var arr = [10, 20, 30, 40, 50, 60, 70,80, 40, 100];
var res;
res = arr.lastIndexOf(40);
console.log(res);
res = arr.lastIndexOf(40, 1);
console.log(res);
res = arr.lastIndexOf(40, 3);
console.log(res);
```

####  ③ find方法和findIndex方法

:man_student:find方法：返回通过测试(函数内判断)的数组的第一个元素的值

```javascript
数组名字.fin(function(currentValue, index, arr));
currentValue:当前正在处理的数组元素；
index:当前元素的下标；
arr:当前数组的引用
         
var arr = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100];
//查找数组中大于50的元素
var res = arr.find(function(val, index, arr){
    return val > 50;
});
console.log(res);
//查找数组中大于50的元素且下标等于7的元素
res = arr.find(function (val, index){
    return (val > 50) && (index == 7);
});
console.log(res);
```

:man_student:findIndex方法：返回通过测试(函数内部判断)的数组的第一个元素的下标

```javascript
数组名字.findIndex(function(currentValue, index, arr){
    语句;
    ……
});

var arr = [10, 20, 30, 40, 50, 60, 70, 80, 90, 100];
//查找数组中大于50的元素的下标
var res = arr.find(function(val, index, arr){
    return val > 50;
});
console.log(res);
```

#### ④ forEach方法遍历数组

:man_student::属于数组对象的一个方法，既可以可以遍历数组元素也可以元素下标

```javascript
var arr = [1, 2, 3, 4, 5, 6];
arr.forEach(function (element, index){
    console.log("a[" + index + "]" + " = " + element);
});
```

####  ⑤ map方法

:man_student:遍历数组的所有元素，返回一个新数组，新数组中的元素为原始数组的调用函数处理后的值，不会对空数组检测

```javascript
数组名.map(function (currentValue, index, arr){
    语句;
    ……;
});

//使b数组的元素是a数组元素的十倍
var a = [0, 2, 3, 4, 5, 6, 7, 8, 9, 10];
b = a.map(function (val, index, arr){
    return val * 10;
});
console.log(b);
```

#### ⑥ push、pop、unshift、shift方法

:man_student:push:在数组尾部增加元素并返回数组新的长度

```javascript
数组名.push(值1, 值2, 值3, ……);

//给arr数组增加100，200，300这三个值
var arr = [1, 2, 3, 4];
var l = arr.push(100, 200, 300);
console.log(arr);
console.log(l);
```

:man_student:pop：删除数组尾部的一个元素，返回被删除的元素

```javascript
数组名.pop();

var arr = [1, 2, 3, 4, 5];
var element = arr.pop();
console.log(element);
console.log(arr);
```

:man_student:unshift：在数组头部添加元素，返回新数组的长度

```javascript
数组名.unshift(值1, 值2, 值3, ……);

var arr = [1, 2, 3, 4, 5];
var length = arr.unshift(6, 7, 8);
console.log(arr);
console.log(length);
```

:man_student:shift：在数组头部删除元素，返回被删除的元素

```javascript
数组名.shift();

var arr = [1, 2, 3, 4, 5];
var element = arr.shift();
console.log(arr);
console.log(element);
```

#### ⑦ slice方法

:man_student:从数组中截取指定元素，并用这些元素组成新的数组返回

```javascript
数组名.slice(begin, end);
begin:开始下标；
end:结束下标；
不截取end下标对应的元素；
省略begin表示从头开始截取，省略end表示截取到尾，都省略表示复制数组

var arr = [1, 2, 3, 4, 5, 6];
var new_arr = arr.slice(2, 4);
console.log(new_arr);
```

#### ⑧ some、every、includes方法

:man_student:some：用于检测数组中的元素是否满足指定条件(函数提供)。有则返回true否则返回false

```javascript
数组名.some(function(currentValue, index, arr){
    语句;
    ……;
});

//确认arr数组中是否含有大于3的元素
var arr = [1, 2, 3, 4, 5, 6];
var ishave = arr.some(function(val, index, arr){
    return val > 3;
});
console.log(ishave);
//探索一下some方法
ishave = arr.some(function(val, index, arr){
    return  val * 10;
});
console.log(ishave);
```

:man_student: every：检查数组所有元素是否都符合指定条件(通过函数提供)

```javascript
数组名.every(function(val, index, arr){
   语句;
   ……;
});

var arr = [1, 2, 3, 4, 5];
//检查数组是否所有元素都大于4
var isGreater = arr.every(function (val, index, array){
    return val > 4;
});
console.log(isGreater);
//探索every方法
isGreater = arr.every(function (val, index, array){
    return 1;
});
console.log(isGreater);
```

:man_student: includes：检测数组中是否含有指定的值。有则返回true，无则返回false。

```javascript
数组名.includes(值, 起始下标);

var arr = [1, 2, 3, 4, 5, 6];
var ishave3 = arr.includes(3);
var is3 = arr.includes(3, 1);
console.log(ishave3);
console.log(is3);
```

#### ⑨ sort方法

:man_student:对数组元素转换为字符型然后进行排序；返回排序后的数组；原数组不受影响。

```javascript
默认：
数组名.sort();

针对非字符型数组(尤其是Number和对象型):
数组名.sort(function(a, b){
    语句;
    ……;
});
a:当前元素
b:下个元素
考虑一下为什么要这样

//探索
var arr = [1, 0, 13, 2, 7, 15];
var new_arr = arr.sort();
console.log(new_arr);
//升序
new_arr = arr.sort(function (a, b){
    return a - b;
});
console.log(new_arr);
//降序
new_arr = arr.sort(function (a, b){
    return b - a;
});
console.log(new_arr);

//探索
new_arr = arr.sort(function(a, b){
    return true;
});
console.log(new_arr);
```

#### ⑩ splice方法

:man_student:对数组做增删改操作

```javascript
增：
数组名.splice(插入位置的下标, 0, 值1, 值2, ……);
var arr = [1, 2, 3, 4, 5];
arr.splice(3, 0, 100, 300, 33);
console.log(arr);

删：
数组名.splice(删除的位置下标, 删除的个数);
arr.splice(3, 2);
console.log(arr);
arr.splice(2, 1);
console.log(arr);

改：
数组名.splice(替换位置开始的下标, 替换的个数, 替换后的值[或值1, 值2, ……]);
console.log(arr);
arr.splice(1, 2, 3);
console.log(arr);
arr.splice(1, 1, 100, 2, 4);
console.log(arr);
```

#### ⑪ reduce和reduceRight方法

:man_student:reduce：接受一个函数，这个函数遍历数组，第一个参数既是参数也是函数的返回值；数组受影响。

:man_student:reduceRight：与reduce作用相同但是方向是从右到左。

```javascript
数组名.reduce(function(prev, currentValue, cerrentIndex, arr){
    语句;
    ……;
}, 初始值);
注意：
如果设置初始值，那么第一次调用函数时，prev的值就是这个初始值，currentValue为数组第一个元素，currentIndex自然为0；
若不设置则prev为数组的一个元素值，currentValue为数组第二个元素值，currentIndex为1。

//求和
var arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
var result = arr.reduce(function(prev, currentValue, currentIndex, arr){
    console.log("prev:" + prev);
    console.log("currentValue:" + currentValue);
    console.log("currentIndex:" + currentIndex);
    console.log("arr:" + arr);
    return prev + currentValue;
});
console.log("arr:" + arr);
console.log("result:" + result);

result = arr.reduce(function(prev, currentValue, currentIndex, arr){
    console.log("prev:" + prev);
    console.log("currentValue:" + currentValue);
    console.log("currentIndex:" + currentIndex);
    console.log("arr:" + arr);
    return prev + currentValue;
}, 100);
console.log("arr:" + arr);
console.log("result:" + result);

//拼接字符串
var arr = ['a', 'b', 'c', 'd', 'e'];
var string = arr.reduce(function(prev, cValue, cIndex, array){
    return prev + cValue;
});
console.log(string);
```

## 字符串

### 字符串的管理

:man_student:字符串中字符的管理方式类似与数组，也就是说每个字符有自己的下标，从0开始，至字符串的长度-1

```javascript
var str = 'hello world';
console.log("--------------for循环遍历--------------");
for (var i = -1; i < str.length; i++) {
    console.log(str[i]);
}
console.log("--------------for in遍历--------------");
for (var i in str) {
    console.log(str[i]);
}
console.log("-------------for of遍历---------------");
for (var i of str) {
    console.log(i);
}
```

:warning:字符串一旦创建不可被改变，像如下操作都是无效的

```javascript
var str = 'qwewejk`2321312312';
//操作无效
str[0] = 'a';
str[20] = '#';
delete str[2];

console.log(str);
```

### 字符串对象的创建

#### ① 构造方法创建

```javascript
var str = new String("hello");
```

#### ② 字面量形式

```javascript
var 字符串名称 = '字符串';

//探索
var str = 'hello';
console.log(typeof str, str);
console.log(str.length);
```

:exclamation: 基本数据类型的字符串变量之所以能够调用字符串对象的属性和方法，是因为调用这些属性和方法的那一刻，后台会自动将基本类型的字符串包装成字符串对象，调用完后，又将其转换回来。

### 常用字符串函数

#### ① concat方法

:man_student: 字符串1.concat(字符串2, 字符串3, ……字符串n)：拼接字符串。

```javascript
var str1 = 'hello';
var str2 = 'world';
var str = str1.concat(' ', str2, ' !');
console.log('str: ' + str);
console.log('str1: ' + str1);
console.log('str2: ' + str2);
```

#### ② slice、substring和substr方法截取字符串

:man_student: 字符串.slice(begin, end)：从begin下标开始至end下标之前的字符串截取。

```javascript
var str = 'hello world !';
console.log(str.slice(1, 3));
console.log(str.slice());
console.log(str.slice(2));
```

:man_student: 字符串.substring(begin, end)：如slice。但slice支持下标为负数(-1表示最后一个字符下标，从右往左)。

```javascript
var str = 'hello world !';
console.log(str.substring(2, 4));
console.log(str.slice(-5, -1));
```

:man_student: 字符串.substr(begin, count)：begin表示开始下标，count表示截取个数。

```javascript
var str = 'hello world';
console.log(str.substr(3, 4));
```

#### ③ indexOf和lastIndexOf方法

:man_student: 字符串.indexOf('要查找的子串', [begin])：找到则返回下标，否则返回-1

```javascript
var str = 'hello world!';
console.log(str.indexOf('llo'));
```

:man_student: lastIndexOf方法与indexOf方法唯一区别时从右往左查找。

```javascript
var str = 'hello world';
console.log(str.lastIndexOf('lo'));
console.log(str.lastIndexOf('ol'));
```

#### ④ trim方法

:man_student:字符串.trim()：删除字符串左右两端的空格

```javascript
var str = '    hello world    ';
console.log(str.trim());
```

#### ⑤ toUpperCase和toLowerCase方法

:man_student: 字符串.toUpperCase()：将字符串转化为大写。

:man_student: 字符串.toLowerCase()：将字符串转化为小写。

```javascript
var str = 'hello world';
var upper = str.toUpperCase();
console.log(upper);
var lower = upper.toLowerCase();
console.log(lower);
```

#### ⑥ match、search、replace和split方法

:man_student: 字符串.match(子串)：将结果封成数组返回。

```javascript
var str = 'hello world';
console.log(str.match('l'));
```

:man_student: 字符串.search(子串)：与index类似

```javascript
var str = 'hello world';
console.log(str.search('l'));
```

:man_student: 字符串.replace(旧子串, 替换串)：替换

```javascript
var str = 'hello world';
var res = str.replace('e', 'a');
console.log(res);
var allRes = str.replaceAll('l', 'y');
console.log(allRes);
```

:man_student: 字符串.split([arguments])：将字符串拆分，并将拆分的子串作为数组元素封装成数组。

```javascript
var str = 'hello world';
//一、无参，则是将整个字符串作为一个数组元素封装。
var arr_str = str.split();
console.log('split(): ' + arr_str);
//二、有参，查找到子串参数，将参数左右子串作为数组元素封装。
arr_str = str.split('e');
console.log('split(argument)' + arr_str);
//三、参数为空串，将数组每个字符分别作为数组元素封装。
arr_str = str.split('');
console.log('split(empty string):' + arr_str);
```

#### ⑦ ES6、ES7新增方法：includes、startsWith、repeat、padStart、padEnd

:man_student: 字符串.includes('字符串')：查找到则返回true，没有则返回false

```javascript
var str = 'hello world';
console.log(str.includes('llo'));
console.log(str.includes('a'));
```

:man_student: 字符串.startsWith('字符串')：若字符串以参数字符串开头，则返回true，否则返回false。

```javascript
var str = 'hello world';
console.log(str.startsWith('hel'));
console.log(str.startsWith('asb'));
console.log(str.endsWith('ld'));
```

:man_student: 字符串.repeat(int)：将字符串重复参数次返回。

```javascript
var str = 'hello'
var repeat_str = str.repeat(3);
console.log(repeat_str);
```

:man_student: 字符串.padStarts(length, substring)：字符串长度大于等于length则返回原字符串，否则就用substring在左侧扩展至长度至length返回。

:man_student: 字符串.padEnd(length, substring)：同padStarts，只不过是从右侧扩展。

```javascript
var str = 'hello';
var padStart = str.padStart(8, 'a');
console.log(padStart);
var padEnd = str.padEnd(10, 'bc');
console.log(padEnd);
```

### 字符串编码方式

#### ① btoa和aotb方法

:man_student: btoa(string)：将二进制或字符串以BASE64的编码方式返回。

```javascript
var str = 'hello';
var Base64str = btoa(str);
console.log(Base64str);
```

:man_student: atob(string)：将BASE64的编码方式的字符串转换回原来的字符。

```javascript
var str = 'hello';
var res = btoa(str);
console.log(res);
res = atob(res);
console.log(res);
```

#### ② encodeURIComponent和decodeURIComponent方法

```javascript
var str = '?name=张三&age=10&gender=男';
//利用encodeURIComponent()对字符串str进行编码
var res = encodeURIComponent(str);
console.log(res);
//利用decodeURIComponent()对字符串进行解码
res = decodeURIComponent(res);
console.log(res);
```

---

## DOM

### :one: DOM定义

:man_student:DOM (Document Object Model), 文档对象模型，规定了操作文档和文档内容的API，不是一个对象。主要使用document对象操作文档内容。

:man_student: DOM的观点是文档就是一个节点树。而节点又分为：

- 元素节点：指的是HTML文档中的标签。
- 属性节点：标签的属性名和属性值。
- 文本节点：标签的文本内容。
- 注释节点：HTML注释。
- 文档节点：整个HTML文档就是一个文档节点。

:exclamation: 所有节点都是对象模型，所有节点都包含如下属性：

- nodeType：节点类型

  - 若为元素节点其值为 1
  - 若为属性节点其值为 2
  - 若为文本节点其值为 3
  - 若为注释节点其值为 8
  - 若为文档节点其值为 9

- nodeName：节点名称

  - 若为元素节点其值为 元素名称
  - 若为属性节点其值为 属性名称
  - 若为文本节点其值为 #text
  - 若为注释节点其值为 #comment
  - 若为文档节点其值为 #document

- nodeValue：表示节点值

  - 若为元素节点其值为 null
  - 若为属性节点其值为 属性值
  - 若为文本节点其值为 文本内容
  - 若为注释节点其值为 注释内容
  - 若为文档节点其值为 null

- ```javascript
  <body>
      <div id="box" title="hello">我是一个div节点</div><!-- 这是一个注释 -->
  	<script>
          // 元素节点
          var obj = document.querySelector("#box");
  		console.log(obj.nodeType);
  		console.log(obj.nodeName);
  		console.log(obj.nodeValue);
  		// 属性节点
  		var attr = obj.getAttributeNode('id');
  		console.log(attr.nodeType);
  		console.log(attr.nodeName);
  		console.log(attr.nodeValue);
  		// 文本节点
  		var txt = obj.firstChild;
  		console.log(txt.nodeType);
  		console.log(txt.nodeName);
  		console.log(txt.nodeValue);
  		// 注释节点
  		var comment =  obj.nextSibling;
  		console.log(comment.nodeType);
  		console.log(comment.nodeName);
  		console.log(comment.nodeValue);
  		// 文档节点
  		console.log(document.nodeType);
  		console.log(document.nodeName);
  		console.log(document.nodeValue);
  	</script>
  </body>
  ```

### :two: 元素节点

#### ① 元素节点的获取

1. getElementById()：通过标签的<font color=red>id属性值</font>获取元素

   ```javascript
   <body>
       <div id="box" title="hello">I'm a node</div><!--this is a comment-->
       <div id="bubox" title="world">you are a node</div>
       <script>
           var div1 = document.getElementById("box");
           var div2 = document.getElementById("bubox");
           console.log(div1);
           console.log(div2);
       </script>
   </body>
   ```

2. getElementsByTagName()：通过<font color=red>标签名</font>获取元素(返回值是数组)。

   ```javascript
   
   ```

   