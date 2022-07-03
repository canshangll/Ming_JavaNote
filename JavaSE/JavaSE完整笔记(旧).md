# 						   **Java开发**笔记

## Java简述和开发基本

#### Java开发细节

```java
1、Java源文件.Java为扩展名。源文件的基本组成部分是类（class）
2、区分大小写
3、Java应用程序的执行入口是main()方法
4、一个源文件中最多只能有一个public类，其他不限，可以将main方法写在非public类中，然后运行非public类，这样入口方法就是非public的main方法
5、声明为public的主类要与文件名一致
6、源文件使用utf-8编码
```

#### Java转义字符

```java
Java常用转义字符：
    1） \t：一个制表位，实现对齐的功能
    2） \n：换行符
    3） \\：一个\
    4） \":一个"
    5) \':一个'
    6） \r:一个回车
```

## Java变量

#### 数据类型

![java数据类型](E:\java\笔记\image\java数据类型.png)

#### 整数类型

```java
1、Java各整数类型有固定的范围和字段长度，不受具体OS[操作系统]的影响，保证了Java程序的可移植性
2、Java的整型常量（具体值）默认为int型，声明long后加'ｌ'或'L'
3、Java程序中变量常声明为int型
```

#### 浮点类型

```java
1、与整数类型类似，Java浮点类型有固定的返回和字段长度，不受具体OS的影响。[float4个字节 double是8个字节]
2、Java浮点型常量默认是double型
3、浮点型使用陷阱：2.7和8.1/3比较
```

#### 布尔类型：boolean

```java
1、boolean类型数据只允许取值true和false，无null
2、boolean类型占一个字节
3、适用于逻辑运算，一般用于程序流程控制语句
```

#### 字符类型（char）

```java
1、字符类型表示单个字符，字符类型是char，char是两个字节（可以存放汉字），多个字符我们用字符串String。
2、字符常量用（''）括起来的单个字符
3、允许使用转义字符'\'
4、Java中，char的本质是一个整数,在输出时，是unicode码对应的字符。
5、Java中，可以直接给char赋一个整数，然后输出，会按照对应Unicode字符输出:如：[97]
6、Java中，char类型是可以进行运算的，相当于一个整数，因为它都对应有Unicode码。
    
 ============字符类型本质探讨===============
 1、字符型存储到计算机中，需要将字符对应的码值（整数）找出来，比如'a'
    存储：'a'==>码值97==>二进制==>存储
    读取：二进制=>97===>'a'=>显示
 2、字符和码值的对应关系是通过字符编码表决定好的(规定好的)
```

#### 编码介绍

![java字符类型char4](E:\java\笔记\image\java字符类型char4.png)

![javaASCII码介绍](E:\java\笔记\image\javaASCII码介绍.png)

![JavaUnicode编码介绍](E:\java\笔记\image\JavaUnicode编码介绍.png)

![javaUTF-8编码介绍](E:\java\笔记\image\javaUTF-8编码介绍.png)

#### 基本数据类型转换

![java基本数据类型的转换1](E:\java\笔记\image\java基本数据类型的转换1.png)

##### 自动类型转换注意和细节

```java
1、有多种类型的数据混合运算时，系统首先自动将所有数据转换成容量最大的那种数据类型，然后再进行计算
2、（byte,short）和char之间不会相互转换。
3、byte,short,char 三者可以计算
4、boolean不参与转换
5、自动提升原则：表达式结果的类型自动提升为 操作数中最大的类型
```

##### 强制类型转换

```java
1、将容量大的数据类型转换为容量小的数据类型，使用时要加上强制转换符()，但可能造成精度降低或溢出，格外要注意。
2、强制符号只针对于最近的操作数有效，往往会使用小括号提升优先级
3、char类型可以保存int的常量值，但不能保存int的变量值，需要强转
4、byte和short类型在进行运算时，当做int类型处理
```

##### 基本数据类型和String类型的转换

```java
基本类型转String类型语法:将基本类型的值+""
String通过基本类型的包装类调用parseXX方法
==========注意事项===========    
在将String类型转换成基本数据类型时，要确保String类型能够转成有效的数据。如果格式不正确，会抛出异常。
```

#### Java API 文档

中文在线文档：（https://www.matools.com）

```java
1、PI(应用程序编程接口)是Java提供的基本编程接口。
2、包->类->方法
```



## 运算符

#### 运算符介绍

```java
运算符是一种特殊的符号，用以表示数据的运算、赋值和比较等。
1、算术运算符 2、赋值运算符 3、关系运算符（比较运算符） 4、逻辑运算符 5、位运算符[需要二进制基础] 6、三元运算符
```

#### 算术运算符

![java算术运算符](E:\java\笔记\image\java算术运算符.png)

#### 关系运算符（比较运算符）

```java
关系运算符的结果都是boolean型，要么是true，要么是false
关系表达式 经常用在if结构的条件中或循环结构的条件中
```

![java关系运算符（比较运算符）2](E:\java\笔记\image\java关系运算符（比较运算符）2.png)

#### 逻辑运算符

```java
用于连接多个条件（多个关系表达式），最终的结果也是一个boolean值
```

![java逻辑运算符2](E:\java\笔记\image\java逻辑运算符2.png)

```java
逻辑运算符规则：
1、a&b:&叫逻辑与：规则：当a和b同时为true，则结果为true，否则为false
2、a&&b:&&叫短路与：规则：当a和b同时为true，则结果为true，否则为false
3、a|b:|叫逻辑或，规则：当a和b，有一个为true，则结果为true，否则为false
4、a||b:||叫短路或，规则：当a和b，有一个true，则结果为true，否则为false
5、!a:叫取反，或者非运算。当a为true，则结果为false，当a为false时，结果为true
6、a^b：叫逻辑异或，当a和b不同时，则结果为true，否则为false
```

![java逻辑运算符4](E:\java\笔记\image\java逻辑运算符4.png)

![java逻辑运算符5](E:\java\笔记\image\java逻辑运算符5.png)

![java逻辑运算符6](E:\java\笔记\image\java逻辑运算符6.png)



#### 赋值运算符

```java
赋值运算符就是将某个运算后的值，赋给指定的变量。
```

![Java赋值运算符2](E:\java\笔记\image\Java赋值运算符2.png)



#### 三元运算符

```java
基本语法：
    条件表达式？表达式1：表达式2；
1、如果条件表达式为true，运算后的结果时表达式1；
2、如果条件表达式为false，运算后的结果是表达式2；
```

![Java三元运算符2](E:\java\笔记\image\Java三元运算符2.png)



#### 运算符优先级

![Java运算符的优先级](E:\java\笔记\image\Java运算符的优先级.png)

#### 标识符的命名规则和规范

![Java标识符的命名规则](E:\java\笔记\image\Java标识符的命名规则.png)

![Java标识符命名规范](E:\java\笔记\image\Java标识符命名规范.png)



#### 关键字

![Java关键字1](E:\java\笔记\image\Java关键字1.png)

![Java关键字2](E:\java\笔记\image\Java关键字2.png)



#### 保留字

![Java保留字1](E:\java\笔记\image\Java保留字1.png)

#### ==导入包==

```java
import java.util.Scanner;//导入Util包的Scanner类
```

#### 进制

```java
对于整数，有四种方式：
1、二进制：0，1，满2进1.以0b或0B开头。
2、十进制：0-9，满10进1.
3、八进制：0-7，满8进1.以数字0开头表示。
4、十六进制：0-9及A（10）-F(15)，满16进1.以0x或0X开头表示。
```

![Java进制2](E:\java\笔记\image\Java进制2.png)

##### 二进制转换成十进制

![Java二进制转换成十进制](E:\java\笔记\image\Java二进制转换成十进制.png)

##### 八进制转换成十进制

![Java八进制转换成十进制](E:\java\笔记\image\Java八进制转换成十进制.png)

##### 十六进制转换成十进制

![Java十六进制转换成十进制](E:\java\笔记\image\Java十六进制转换成十进制.png)

##### 十进制转换成二进制

![Java十进制转换成二进制](E:\java\笔记\image\Java十进制转换成二进制.png)

##### 十进制转换成八进制

![Java十进制转换成八进制](E:\java\笔记\image\Java十进制转换成八进制.png)

##### 十进制转换成十六进制

![Java十进制转换成十六进制](E:\java\笔记\image\Java十进制转换成十六进制.png)

##### 二进制转换成八进制

![Java二进制转换成八进制](E:\java\笔记\image\Java二进制转换成八进制.png)

##### 二进制转换成十六进制

![Java二进制转换成十六进制](E:\java\笔记\Java二进制转换成十六进制.png)

##### 八进制转换成二进制

![Java八进制转换成二进制](E:\java\笔记\image\Java八进制转换成二进制.png)

##### 十六进制转换成二进制

![Java十六进制转换成二进制](E:\java\笔记\image\Java十六进制转换成二进制.png)

##### 二进制在运算中的说明

![Java二进制在运算中的说明](E:\java\笔记\image\Java二进制在运算中的说明.png)

#### 原码、反码、补码

```java
1、二进制位是符号位：0表示正数，1表示负数
2、正数的原码，反码，补码都一样
3、负数的反码=它的原码符号位不变，其他位取反（0->1,1->0）
4、负数的补码=它的反码+1，负数的反码=负数的补码-1
5、0的反码，补码都是0
6、java没有无符号数，换言之，java中的数都是有符号的
7、在计算机运算的时候，都是以补码的方式来运算的。
8、当我们看运算结果的时候，要看他的原码
```



#### 位运算符

```java
java中有7个位运算（&、|、^、~、>>、<<和>>>）
1、按位与&:两位全为1，结果为1，否则为0
2、按位或|：两位有一个为1，结果为1，否则为0
3、按位异或^：两位一个为0，一个为1，结果为1，否则为0
4、按位取反~：~-2=? ~2=? 2|3=? 2^3=?
```

##### 位运算符（&）

![Java位运算(&)](E:\java\笔记\image\Java位运算(&).png)

##### 位运算符（~）

![Java位运算(~)](E:\java\笔记\image\Java位运算(~).png)

![Java位运算(算术左移右移)](E:\java\笔记\image\Java位运算(算术左移右移).png)



## 流程控制结构

##### 程序流程控制介绍

```java
1、顺序控制
2、分支控制
3、循环控制
```

##### 顺序控制

![java顺序控制](E:\java\笔记\image\java顺序控制.png)



##### 分支控制if-else

![Java分支控制2](E:\java\笔记\image\Java分支控制2.png)

![Java分支控制3](E:\java\笔记\image\Java分支控制3.png)

![Java分支控制4](E:\java\笔记\image\Java分支控制4.png)

##### 嵌套分支

![Java嵌套分支](E:\java\笔记\image\Java嵌套分支.png)

##### switch分支结构

![Javaswitch分支结构](E:\java\笔记\image\Javaswitch分支结构.png)

```java
switch注意事项和细节讨论
1、表达式数据类型，应和case后的常量类型一致，或者是可以自动转换可以相互比较的类型，比如输入的是字符，而常量是int
2、switch（表达式）中表达式的返回值必须是：（byte,short,int,char,enum[枚举],String）
3、case子句中的值必须是常量，而不能是变量
4、default子句是可选的，当没有匹配的case时，执行default
5、break语句用来在执行完一个case分支后使程序跳出switch语句块；如果没有写break，程序会顺序执行到switch结尾，除非遇到break；
```

##### for循环控制

![Javafor循环控制1](E:\java\笔记\image\Javafor循环控制1.png)

```java
注意事项和细节说明
1、循环条件是返回一个布尔值的表达式
2、循环初始值可以有多条初始化语句，但要求类型一样，并且中间用逗号隔开，循环变量迭代也可以有多条变量迭代语句，中间用逗号隔开。
```

##### while循环控制

![Javawhile循环控制1](E:\java\笔记\image\Javawhile循环控制1.png)

```java
注意事项和细节说明
1、循环条件是返回一个布尔值的表达式
2、while循环是先判断再执行语句
```

##### do..while循环控制

![Javado..while循环控制1](E:\java\笔记\image\Javado..while循环控制1.png)

```Java
注意事项和细节说明
1、循环条件是返回一个布尔值的表达式
2、do..while循环是先执行，在判断，因此它至少执行一次
```
##### 多重控制

![Java多重循环控制1](E:\java\笔记\image\Java多重循环控制1.png)

##### 跳转控制语句-break

![Java跳转控制语句-break](E:\java\笔记\image\Java跳转控制语句-break.png)

![Java跳转控制语句-break例题](E:\java\笔记\image\Java跳转控制语句-break例题.png)

##### 跳转控制语句-continue

![Java跳转控制语句-continue](E:\java\笔记\image\Java跳转控制语句-continue.png)

![Java跳转控制语句-continue案例](E:\java\笔记\image\Java跳转控制语句-continue案例.png)

##### 跳转控制语句-return

![Java跳转控制语句-return](E:\java\笔记\image\Java跳转控制语句-return.png)



## 数组

![Java数组](E:\java\笔记\image\Java数组.png)

##### 数组的使用-动态初始化1

![Java数组的使用-动态初始化1](E:\java\笔记\image\Java数组的使用-动态初始化1.png)

##### 数组的使用-动态初始化2

![Java数组的使用-动态初始化2](E:\java\笔记\image\Java数组的使用-动态初始化2.png)

##### 数组的使用-静态初始化

![Java数组的使用-静态初始化](E:\java\笔记\image\Java数组的使用-静态初始化.png)

##### 数组的使用注意事项和细节

![Java数组使用注意事项和细节](E:\java\笔记\image\Java数组使用注意事项和细节.png)

##### 数组的赋值机制

![Java数组赋值机制1](E:\java\笔记\image\Java数组赋值机制1.png)

![Java数组赋值机制2](E:\java\笔记\image\Java数组赋值机制2.png)

##### 排序

![Java排序介绍](E:\java\笔记\image\Java排序介绍.png)

##### 冒泡排序法

![Java冒泡排序法](E:\java\笔记\image\Java冒泡排序法.png)

##### 查找

![Java查找](E:\java\笔记\image\Java查找.png)

##### 二维数组的使用

![Java二位数组的使用](E:\java\笔记\image\Java二位数组的使用.png)

![Java二维数组的内存布局](E:\java\笔记\image\Java二维数组的内存布局.png)

##### 二维数组的内存布局

![Java二维数组的内存布局](E:\java\笔记\image\Java二维数组的内存布局.png)



## 面向对象编程（基础部分）

##### 类与对象示意图

![Java类与对象](E:\java\笔记\image\Java类与对象.png)

##### 类与对象的区别和联系

![Java类与对象的区别和联系](E:\java\笔记\image\Java类与对象的区别和联系.png)

##### 类和对象内存布局

![Java对象内存布局](E:\java\笔记\image\Java对象内存布局.png)

##### 属性变量

![Java属性（成员）变量](E:\java\笔记\image\Java属性（成员）变量.png)

##### 属性的注意事项和细节

![Java属性的注意事项和细节](E:\java\笔记\image\Java属性的注意事项和细节.png)

##### 对象分配机制

![Java对象分配机制](E:\java\笔记\image\Java对象分配机制.png)

##### 对象创建过程

![Java对象创建过程](E:\java\笔记\image\Java对象创建过程.png)

##### 成员方法

![Java成员方法](E:\java\笔记\image\Java成员方法.png)

##### 方法调用机制

![Java方法调用机制](E:\java\笔记\image\Java方法调用机制.png)

##### 成员方法的定义

![Java成员方法的定义](E:\java\笔记\image\Java成员方法的定义.png)

##### 成员方法的注意事项和使用细节

![Java成员方法的注意事项和使用细节1](E:\java\笔记\image\Java成员方法的注意事项和使用细节1.png)

![Java成员方法的注意事项和使用细节2](E:\java\笔记\image\Java成员方法的注意事项和使用细节2.png)

![Java成员方法的注意事项和使用细节3](E:\java\笔记\image\Java成员方法的注意事项和使用细节3.png)

##### 成员方法的传参机制

![Java成员方法的传参机制](E:\java\笔记\image\Java成员方法的传参机制.png)

##### 方法的递归调用

![Java方法的递归调用](E:\java\笔记\image\Java方法的递归调用.png)

##### 方法的递归规则

![Java方法的递归调用规则](E:\java\笔记\image\Java方法的递归调用规则.png)

##### 递归例题

```java
public class Migong {
    public static void main(String[] args) {
        
    	int[][] map = new int[8][7];
    	for(int i=0;i<7;i++){
    		map[0][i]=1;
    		map[7][i]=1;
    	}

    	for(int i=0;i<8;i++){
    		map[i][0]=1;
    		map[i][6]=1;
    	}
    	map[3][1]=1;
    	map[3][2]=1;
    	map[2][2]=1;
    	//输出当前的地图
    	for(int i =0;i<map.length;i++){
    		for (int j=0;j<map[i].length ;j++ ) {
    			System.out.print(map[i][j]+" ");
    		}
    		System.out.println();
    	}

    	T t1 = new T();
    	t1.findWay(map,1,1);
    	System.out.println("\n====找路的情况如下====");
    	for(int i=0;i<map.length;i++){
    		for(int j =0;j<map[i].length;j++){
    			System.out.print(map[i][j]+" ");
    		}
    		System.out.println();
    	}


    }
}

class T {

	public boolean findWay(int[][] map,int i,int j){
		if(map[6][5]==2){
			return true;
		}else{
			if(map[i][j]==0){
				map[i][j]=2;
				if(findWay(map,i+1,j)){
					return true;
				}else if(findWay(map,i,j+1)){
					return true;
				}else if(findWay(map,i-1,j)){
					return true;
				}else if(findWay(map,i,j-1)){
					return true;
				}else{
					map[i][j]=3;
					return false;
				}
			}else{
				return false;
			}
		}
	}
}
```

##### 方法重载

![Java方法重载1](E:\java\笔记\image\Java方法重载1.png)

##### 方法重载的注意事项和细节

![Java方法重载的注意事项和细节](E:\java\笔记\image\Java方法重载的注意事项和细节.png)

##### 可变参数

![Java可变参数](E:\java\笔记\image\Java可变参数.png)

##### 可变参数例题

![Java可变参数例题](E:\java\笔记\image\Java可变参数例题.png)

##### 可变参数注意事项和细节

![Java可变参数注意事项和使用细节](E:\java\笔记\image\Java可变参数注意事项和使用细节.png)

##### 作用域

![Java作用域](E:\java\笔记\image\Java作用域.png)

##### 作用域的注意事项和细节

![Java作用域的注意事项和细节1](E:\java\笔记\image\Java作用域的注意事项和细节1.png)

![Java作用域的注意事项和细节2](E:\java\笔记\image\Java作用域的注意事项和细节2.png)

##### 构造方法

![Java构造方法(构造器)说明](E:\java\笔记\image\Java构造方法(构造器)说明.png)

![Java构造方法(构造器)介绍](E:\java\笔记\image\Java构造方法(构造器)介绍.png)

##### 构造方法的使用

![Java构造方法的使用](E:\java\笔记\image\Java构造方法的使用.png)

##### 构造方法的注意事项和细节

![Java构造方法的注意事项和使用细节1](E:\java\笔记\image\Java构造方法的注意事项和使用细节1.png)

![Java构造方法的注意事项和使用细节2](E:\java\笔记\image\Java构造方法的注意事项和使用细节2.png)

##### this关键字的内存机制

![Javathis关键字的内存机制](E:\java\笔记\image\Javathis关键字的内存机制.png)

##### this关键字的注意事项和细节

![Javathis关键字的注意事项和使用细节](E:\java\笔记\image\Javathis关键字的注意事项和使用细节.png)



## 面向对象编程（中级部分）

##### 包

###### 包的作用及基本语法 

![Java包](E:\java\笔记\image\Java包.png)

###### 包的本质

![Java包的本质](E:\java\笔记\image\Java包的本质.png)

###### 包的命名规则及规范

![Java包的命名和规范](E:\java\笔记\image\Java包的命名和规范.png)

###### 常用的包

![Java常用的包](E:\java\笔记\image\Java常用的包.png)

###### 引入包

![Java引入包](E:\java\笔记\image\Java引入包.png)

###### 包的注意事项和使用细节

![Java包的注意事项和使用细节](E:\java\笔记\image\Java包的注意事项和使用细节.png)



##### 访问修饰符

![Java访问修饰符介绍](E:\java\笔记\image\Java访问修饰符介绍.png)

###### 访问修饰符的注意事项和使用细节

![Java访问修饰符及注意事项](E:\java\笔记\image\Java访问修饰符及注意事项.png)



##### 面向对象编程三大特征

```java
面向对象编程的三大特征：封装、继承和多态。
```

###### 封装

![Java封装](E:\java\笔记\image\Java封装.png)

```java
封装的理解及好处
1）隐藏实现细节：方法（连接数据库）<--调用（传入参数..）
2）可以对数据进行验证，保证安全合理
    Person{name,age}
	Person p = new Person();
	p.name = "jack";
	p.age = 1200;

封装的实现步骤（三步）
1）将属性进行私有化private 【不能直接修改属性】
2）提供一个公共的（public）set方法，用于对属性判断并赋值
    public void setXxx（类型 参数名）{//Xxx 表示某个属性
	//加入数据验证的业务逻辑
    属性 = 参数名;
}
3）提供一个公共的（public）get方法，用于获取属性的值
    public数据类型getXxx(){//权限判断，Xxx某个属性
    	return xx;
	}
```



###### 继承

![Java继承](E:\java\笔记\image\Java继承.png)

```java
继承的深入讨论/细节问题
1.子类继承了所有的属性和方法，但是私有属性和方法不能在子类直接访问，要通过公共的方法去访问
    
2.子类必须调用父类的构造器，完成父类的初始化
    
3.当创建子类对象时，不管使用子类的哪个构造器，默认情况下总会去调用父类的无参构造器，如果父类没有提供无参构造器，则必须在子类的构造器中用super去指定使用父类的哪个构造器完成对父类的初始化工作，否则，编译不会通过
    
4.如果希望指定去调用父类的某个构造器，则显式的调用一下：super(参数列表)
    
5.super在使用时，必须放在构造器第一行（super只能在构造器中使用）
    
6.super()和this()都只能放在构造器第一行，因此这两个方法不能共存在一个构造器
    
7.java所有类都是Object类的子类，Object时所有类的基类。
    
8.父类构造器的调用不限于直接父类！将一直往上追溯直到Object类（顶级父类）
    
9.子类最多只能继承一个父类（指直接继承），即Java中时单继承机制
    
10.不能滥用继承，子类和父类之间必须满足is-a的逻辑关系
```

##### *super关键字

```java
基本介绍
super代表父类的引用，用于访问父类的属性、方法、构造器

1.访问父类的属性，但不能访问父类的private属性，super.属性名

2.访问父类的方法，不能访问父类的private方法，super.方法名(参数列表)
    
3.访问父类的构造器：super(参数列表);只能放在构造器的第一句，只能出现一句！
    
super给编程带来的便利/细节
1.调用父类的构造器的好处(分工明确，父类属性由父类初始化，子类的属性由子类初始化)
    
2.当子类中有和父类中的成员(属性和方法)重名时，为了访问父类的成员，必须通过super。如果没有重名，使用super、this、直接访问是一样的效果！

3.super的访问不限于直接父类，如果爷爷类和本类中有同名的成员，也可以使用super去访问爷爷类的成员；如果多个基类（上级类）中都有同名的成员，使用super访问遵循的就近原则。A->B->C
```

###### super和this的比较

![Javasuper和this的比较](E:\java\笔记\image\Javasuper和this的比较.png)



##### 方法重写/覆盖(override)

![Java方法重写(覆盖)(override)](E:\java\笔记\image\Java方法重写(覆盖)(override).png)

###### 方法重写的注意事项和细节

![Java方法重写的注意事项和细节](E:\java\笔记\image\Java方法重写的注意事项和细节.png)

###### 方法重载和方法重写的比较

![Java方法重载和方法重写的比较](E:\java\笔记\image\Java方法重载和方法重写的比较.png)

##### *多态

```java
多态的具体体现
对象的多态（核心、重难点）
1.一个对象的编译类型和运行类型可以不一致
    
2.编译类型在定义对象时，就确定了，不能改变
    
3.运行类型时可以变化的
    
4.编译类型看定义时=号的左边，运行类型看=号的 右边
```

```java
多态的向上转型
前提：两个对象(类)存在继承关系
    
1.本质：父类的引用指向了子类的对象
    
2.语法：父类类型 引用名 = new 子类类型();

3.特点：编译类型看左边，运行类型看右边。
  可以调用父类中的所有成员（遵守访问权限），
  不能调用子类中的特有成员；
  最终运行效果看子类的具体实现！
    

多态的向下转型
1.语法： 子类类型 引用名 = (子类类型) 父类引用;

2.只能强转父类的引用，不能强转父类的对象
    
3.要求父类的引用必须指向的是当前目标类型的对象
    
4.可以调用子类类型中所有的成员
    
***
属性没有重写之说！属性的值看编译类型
    
instanceOf比较操作符，用于判断对象的类型是否为XX类型或XX类型的子类型
例：
class AA{}
class BB{}

class test{
	main（main方法下）{
        BB bb = new BB();
        Object obj1 = null;
        System.out.println(bb instanceof AA);
        System.out.println(bb instanceof obj1);
    }
}

    
```

![Java多态题例](E:\java\笔记\image\Java多态题例.png)

```java
Java的动态绑定机制****
1.当调用对象方法的时候，该方法会和该对象的内存地址/运行类型绑定
    
2.当调用对象属性时，没有动态绑定机制，哪里声明，哪里使用
例
public class Dya {
    public static void main(String[] args) {
        //a 的编译类型 A ，  运行类型 B
        A a  = new B();//向上转型
        System.out.println(a.sum());//40(为注释前) -> 30(注释后)
        System.out.println(a.sum1());//30(为注释前) -> 20(注释后)
    }
}

class A{//父类
    public int i = 10;
    public int sum(){
        return getI()+10;
    }
    public int sum1(){
        return i+10;
    }
    public int getI(){
        return i;
    }
}

class B extends A{//子类
    public int i = 20;
//    public int sum(){
//        return i+20;
//    }
    public int getI(){
        return i;
    }
//    public int sum1(){
//        return i+10;
//    }
}


```

```java
*多态数组
 数组的定义类型为父类类型，里面保存的实际元素类型为子类类型
 上代码：

例1
public class HomeWork01 {
    public static void main(String[] args) {
        Person[] persons = new Person[3];
        persons[0] = new Person("jack",10,"工人");
        persons[1] = new Person("tom",35,"老师");
        persons[2] = new Person("mary",29,"经理");

        for (int i = 0; i < persons.length; i++) {
            System.out.println(persons[i]);
        }

        Person tmp = null;
        for (int i = 0; i < persons.length-1; i++) {
            for (int j = 0; j < persons.length-1-i; j++) {
                if(persons[i].getAge()<persons[i+1].getAge()){
                    tmp = persons[i];
                    persons[i]=persons[i+1];
                    persons[i+1]=tmp;
                }
            }
        }
        for (int i = 0; i < persons.length; i++) {
            System.out.println(persons[i]);
        }

    }
}

class Person{
    private String name;
    private int age;
    private String job;

    Person(String name, int age, String job) {
        this.name = name;
        this.age = age;
        this.job = job;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String getJob() {
        return job;
    }

    public void setJob(String job) {
        this.job = job;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", age=" + age +
                ", job='" + job + '\'' +
                '}';
    }
}
输出结果：
Person{name='jack', age=10, job='工人'}
Person{name='tom', age=35, job='老师'}
Person{name='mary', age=29, job='经理'}
Person{name='tom', age=35, job='老师'}
Person{name='mary', age=29, job='经理'}
Person{name='jack', age=10, job='工人'}
    
    
    
例2
public class Person {//父类
    private String name;
    private int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String say(){//返回名字和年龄
        return name + "\t" + age+"\n";
    }
} 


public class Student extends Person{//子类
    private double score;
    
    public Student(String name,int age,double score) {
        super(name,age);
        this.score = score;
    }

    public double getScore() {
        return score;
    }

    public void setScore(double score) {
        this.score = score;
    }
    //重写父类say
    @Override
    public String say(){
        return "学生："+super.say()+" score=" + score+"\n" ;
    }
    //特有方法
    public void study(){
        System.out.printf("学生："+getName()+"正在学Java...");
    }
}

public class Teacher extends Person{//子类
    private double salary;

    public Teacher( String name,int age,double salary) {
        super(name,age);
        this.salary = salary;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
    //重写父类的say方法
    @Override
    public String say(){
        return "老师："+super.say()+" salary="+salary+"\n" ;
    }
    //特有方法
    public void teach(){
        System.out.printf("老师："+getName()+"正在讲课");
    }
}

main方法实现

public class PloyArray {
    public static void main(String[] args) {
        Person[] person = new Person[5];
        person[0] = new Person("jack",20);
        person[1] = new Student("kai",18,100);
        person[2] = new Student("mao",19,30.1);
        person[3] = new Teacher("chen",30,20000);
        person[4] = new Teacher("Yu",30,25000);

        for (int i = 0; i < person.length; i++) {
            System.out.printf(person[i].say());
            if(person[i] instanceof Student){
                Student student = (Student)person[i];
                student.study();
                //合成一步  ((Student)person[i]).study();
            }else if(person[i] instanceof Teacher){
                Teacher teacher = (Teacher) person[i];
                teacher.teach();
            }else if(person[i] instanceof Person){
                Person person1 = person[i];
                person1.say();
            }else{
                System.out.printf("你的类型有误，请自己检查");
            }
        }
    }
}

结果：
    jack	20
学生：kai	18
 score=100.0
学生：kai正在学Java...学生：mao	19
 score=30.1
学生：mao正在学Java...老师：chen	30
 salary=20000.0
老师：chen正在讲课老师：Yu	30
 salary=25000.0
老师：Yu正在讲课    
```

```java
多态参数
方法定义的形参类型为父类类型，实参类型允许为子类类型
    
上代码：
    
public class Employee {//父类
    private String name;
    private double salary;

    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }

    public double getAnnual(){
        return 12 * salary;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public double getSalary() {
        return salary;
    }

    public void setSalary(double salary) {
        this.salary = salary;
    }
}

public class Manager extends Employee{//子类
    private double bonus;

    public Manager(String name, double salary,double bonus) {
        super(name, salary);
        this.bonus = bonus;
    }

    public double getBonus() {
        return bonus;
    }

    public void setBonus(double bonus) {
        this.bonus = bonus;
    }
    public void manage(){
        System.out.println("经理"+getName()+"is manageing");
    }

    @Override
    public double getAnnual() {
        return super.getAnnual()+bonus;
    }
}

public class Worker extends Employee{//子类
    public Worker(String name, double salary) {
        super(name, salary);
    }
    public void work(){
        System.out.println("普通员工"+getName()+"is working");
    }

    @Override
    public double getAnnual() {
        return super.getAnnual();
    }
}

main方法主类
public class PPter {
    public static void main(String[] args) {
        Worker tom = new Worker("tom",2500);
        Manager milan = new Manager("milan",5000,20000);
        PPter pPter = new PPter();
        pPter.showEmpAnnual(tom);
        pPter.showEmpAnnual(milan);
        pPter.testWork(tom);
        pPter.testWork(milan);

        "hello".equals("abc");
    }

    public void showEmpAnnual(Employee e){
        System.out.println(e.getAnnual());
    }

    public void testWork(Employee e){
        if (e instanceof Worker){
            ((Worker) e).work();//向下转型
        }else if (e instanceof Manager){
            ((Manager) e).manage();
        }else{
            System.out.printf("不做处理");
        }
    }
}

输出结果
30000.0
80000.0
普通员工tomis working
经理milanis manageing

```

###### 多态题例

```java
//父类
public class Person {
    private String name;
    private char gender;
    private int age;

    public Person(String name, char gender, int age) {
        this.name = name;
        this.gender = gender;
        this.age = age;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public char getEender() {
        return gender;
    }

    public void setEender(char gender) {
        this.gender = gender;
    }

    public int getAge() {
        return age;
    }

    public void setAge(int age) {
        this.age = age;
    }

    public String play(){
        return name+"爱玩";
    }

    public String basicInfo(){
        return "姓名：" + name + "\n年龄：" + age + "\n性别：" + gender;
    }

    @Override
    public String toString() {
        return "Person{" +
                "name='" + name + '\'' +
                ", gender=" + gender +
                ", age=" + age +
                '}';
    }
}

//子类
public class Student extends Person{
    private String stu_id;

    public Student(String name, char gender, int age, String stu_id) {
        super(name,gender,age);
        this.stu_id = stu_id;
    }

    public String getStu_id() {
        return stu_id;
    }

    public void setStu_id(String stu_id) {
        this.stu_id = stu_id;
    }

    public void study(){
        System.out.println(getName()+"承诺，我要好好学习");
    }

    @Override
    public String play() {
        return super.play()+"足球";
    }

    public void printInfo(){
        System.out.println("学生的信息：");
        System.out.println(super.basicInfo());
        System.out.println("学号："+stu_id);
        study();
        System.out.println(play());
    }

    @Override
    public String toString() {
        return "Student{" +
                "stu_id='" + stu_id + '\'' +
                '}' +super.toString();
    }
}

//子类
public class Teacher extends Person{
    private int workage;

    public Teacher(String name, char gender, int age, int workage) {
        super(name,gender,age);
        this.workage = workage;
    }

    public int getWorkage() {
        return workage;
    }

    public void setWorkage(int workage) {
        this.workage = workage;
    }

    public void teach(){
        System.out.println(getName()+"承诺，我会认真教学");
    }

    @Override
    public String play() {
        return super.play()+"象棋";
    }

    public void printInfo(){
        System.out.println("老师的信息：");
        System.out.println(super.basicInfo());
        System.out.println("学号："+workage);
        teach();
        System.out.println(play());
    }

    @Override
    public String toString() {
        return "Teacher{" +
                "workage=" + workage +
                '}' + super.toString();
    }
}

//主类
public class HomeWork13 {
    public static void main(String[] args) {
        Student student = new Student("小名", '男', 15, "0015222");
        student.printInfo();
        System.out.println("===============================");
        Teacher teacher = new Teacher("老余",'男',45,15);
        teacher.printInfo();

        Person[] person = new Person[4];
        person[0] = new Student("小名", '男', 15, "0015222");
        person[1] = new Student("小陈", '女', 16, "0015666");
        person[2] = new Teacher("老余",'男',45,15);
        person[3] = new Teacher("老邵",'男',49,25);

        HomeWork13 homeWork13 = new HomeWork13();
        homeWork13.bubbleSort(person);
        System.out.println("===============================");
        for (int i = 0; i < person.length; i++) {
            System.out.println(person[i].toString());
        }
        System.out.println("===============================");
        for (int i = 0; i < person.length; i++) {
            homeWork13.test(person[i]);
        }

    }

    public void bubbleSort(Person[] persons){
        Person tmp = null;
        for (int i = 0; i < persons.length-1; i++) {
            for (int j = 0; j < persons.length-1-i; j++) {
                if(persons[j].getAge() < persons[j+1].getAge()){
                    tmp=persons[j];
                    persons[j]=persons[j+1];
                    persons[j+1]=tmp;
                }
            }
        }
    }

    public void test(Person p){
        if (p instanceof Student){
            ((Student) p).study();
        }else if(p instanceof Teacher){
            ((Teacher) p).teach();
        }else{
            System.out.println("do nothing");
        }
    }
}
```

![Java多态题例](E:\java\笔记\image\Java多态题例.png)



##### Object类详解

###### equals方法

![JavaObject类-equals方法1](E:\java\笔记\image\JavaObject类-equals方法1.png)

![JavaObject类-equals方法2](E:\java\笔记\image\JavaObject类-equals方法2.png)

###### hashCode方法

###### ![JavahashCode方法](E:\java\笔记\JavahashCode方法.png)

###### toString方法

![JavatoString方法](E:\java\笔记\image\JavatoString方法.png)

###### finalize方法

![Javafinalize方法](E:\java\笔记\image\Javafinalize方法.png)



##### 断点调试（debug）

![Java断点调试(debug)](E:\java\笔记\image\Java断点调试(debug).png)

![Java断点调试快捷键](E:\java\笔记\image\Java断点调试快捷键.png)



## 面向对象编程（高级部分）

##### 类变量和类方法

```java
类变量也叫静态变量/静态属性，是该类的所有对象共享的变量，任何要给该类的对象去访问它时，取到的都是相同的值，同样任何一个该类的对象去修改它是，修改的也是同一个变量
   
定义类变量
访问修饰符 static 数据类型 变量名;

访问类变量
类名.类变量名【推荐】
或者 对象名.类变量名【静态变量的访问修饰符的访问权限和范围 和 普通属性是一样的。】
    
类变量与类方法的注意事项
1、类变量与实例变量区别：类变量是该类的所有对象共享的，而实例变量是每个对象独享的。
2、实例变量不能通过 类名.类变量名 方式访问。
3、类变量是在类加载时就初始化了，即使没有创建对象，只要类加载了，就可以使用类变量了。
4、类变量的生命周期时随类的加载开始，随着类消亡而销毁。
5、当方法中不涉及到任何和对象相关的成员，则可以将方法设计成静态方法，提高开发效率。
6、类方法和普通方法都是随着类的加载而加载，将结构信息存储在方法区：类方法中无this参数 普通方法中隐含着this的参数
7、类方法可以通过类名调用，也可以通过对象名调用。
8、普通方法和对象有关，需要通过对象名调用，比如对象名.方法名(参数),不能通过类名调用    
9、类方法中不允许使用和对象有关的关键字。普通方法可以
10、静态方法中只能访问静态变量或静态方法。
11、普通成员方法，既可以访问 普通变量(方法),也可以访问静态变量(方法)。    
```

##### main方法语法

![Javamain方法语法](E:\java\笔记\image\Javamain方法语法.png)

![Javamain方法语法1](E:\java\笔记\image\Javamain方法语法1.png)

##### 代码块

```Java
代码化块又称为初始化块，属于类中的成员[即 是类的一部分],类似于方法，将逻辑语句封装在方法体中，通过{}包围起来
但和方法不同，没有方法名，没有返回，没有参数，只有方法体，而且不用通过对象或类显式调用，而是加载类时，或创建对象时隐式调用。
语法：
[修饰符]{
    代码
};
代码块分为两类，使用static修饰的叫静态代码块，没有static修饰的，叫普通代码块/非静态代码块。
    
代码块的好处：相当于另外一种形式的构造器(对构造器的补充机制)，可以做初始化的操作

代码块的使用注意事项
1、静态代码块，作用就是对类进行初始化，而且它随着类的加载而执行，并且只会执行一次。普通代码块则每创建一个对象，就执行。
    
2、类什么时候被加载：①创建对象实例时(new)②创建子类对象实例，父类也会被加载③使用类的静态成员时(静态属性、静态方法)    
    
3、普通代码块，在创建对象实例时，会被隐式的调用。被创建一次，就会调用一次。如果只是使用类的静态成员时，普通代码块并不会执行。
小结：1、static代码块是类加载时，执行，只会执行一次。
    2、普通代码块时在创建对象时调用的，创建一次，调用一次
    3、类加载的3种情况
    
4、创建一个对象时，在一个类中调用顺序是：
    ①调用静态代码块和静态属性初始化(注意：静态代码块和静态属性初始化调用的优先级一样，如果有多个静态代码块和多个静态变量初始化，则按他们定义的顺序调用)
    ②调用普通代码块和普通属性的初始化(注意：普通代码块和普通属性初始化调用的优先级一样，如果有多个普通代码块和多个普通属性初始化，则按定义顺序调用)

5、创建一个子类对象时，他们的静态代码块，静态属性初始化，普通代码块，普通属性初始化，构造方法的调用顺序：
    ①父类的静态代码块和静态属性(优先级一样，按定义顺序执行)
    ②子类的静态代码块和静态属性(优先级一样，按定义顺序执行)
    ③父类的普通代码块和普通属性初始化(优先级一样，按定义顺序执行)
    ④父类的构造方法
    ⑤子类的普通代码块和普通属性初始化(优先级一样，按定义顺序执行)
    ⑥子类的构造方法

6、静态代码块只能直接调用静态成员(静态属性和静态方法)，普通代码块可以调用任意成员。
```

##### 单例设计模式

```java
单例（单个的实例）
1、所谓类的单例设计模式，就是采取一定的方法保证在整个的软件系统中，对某个类只能存在一个对象实例，并且该类只提供一个取得其对象实例的方法
2、单例模式有两种方式：1、饿汉式 2、懒汉式  
实现步骤：
    1、构造器私有化 =》 防止直接new
    2、类的内部创建对象
    3、向外暴露一个静态的公共方法
```

###### 饿汉式

```java
public class StaticlnnerClass01 {
    public static void main(String[] args) {
        Outer10 outer10 = new Outer10();
        outer10.m1();
        //外部其他类 使用静态内部类
        //方式一
        //因为静态内部类，是可以通过类名直接访问(前提是满足访问权限)
        Outer10.Inner10 inner10 = new Outer10.Inner10();
        inner10.say();
        //方式2
        //编写一个方法，可以返回一个静态内部类
        Outer10.Inner10 inner101 = outer10.getInter10();
        inner101.say();

        Outer10.Inner10 inner10_ = Outer10.getInter10_();
        inner10_.say();
    }
}

class Outer10{//外部类
    private int n1 = 10;
    private static String name = "张三";
    private static void cry(){}
    //Inner10就是静态内部类
    //1.放在外部类的成员位置
    //2.使用static 修饰
    //3.可以直接访问外部类的所有静态成员，包含私有的，但不能直接访问非静态成员
    //4.可以添加任意访问修饰符(public、protected、默认、private)，因为它的地位就是一个成员
    static class Inner10{
        private static String name = "里斯";
        public void say(){//就近原则
            System.out.println(name+" 外部类name= " + Outer10.name);
            cry();
        }
    }
    public void m1(){
        Inner10 inner10 = new Inner10();
        inner10.say();
    }
    public Inner10 getInter10(){
        return new Inner10();
    }
    public static Inner10 getInter10_(){
        return new Inner10();
    }
}
```

###### 懒汉式

```java
public class SingleTon02 {
    public static void main(String[] args) {
        Cat instance = Cat.getInstance();
        System.out.println(instance);

        Cat instance2 = Cat.getInstance();
        System.out.println(instance2);

        System.out.println(instance==instance2);//T
    }
}

//在程序运行中只创建一个Cat对象
//使用单例模式
class Cat {
    private String name;
    public static int n1 = 999;
    private static Cat cat;//默认是null
    //步骤
    //1.构造器私有化
    //2.定义一个static静态属性对象
    //3.提供一个public的static方法，可以返回一个Cat对象
    //4.懒汉式，只有当用户使用getInstance时，才返回cat对象，后面再次调用时，会返回上次调用的对象
    private Cat(String name) {
        this.name = name;
    }
    public static Cat getInstance(){

        if(cat == null){//如果还没有创建cat对象
            cat = new Cat("小花");
        }
        return cat;
    }
    @Override
    public String toString() {
        return "Cat{" +
                "name='" + name + '\'' +
                '}';
    }
}
```

饿汉式VS懒汉式

```java
1、二者最主要的区别在于创建对象的时机不同：饿汉式是在类加载就创建了对象实例，而懒汉式是在使用时才创建。
2、饿汉式不存在线程安全问题，懒汉式存在线程安全问题。
3、饿汉式存在浪费资源的可能。因为如果程序员一个对象实例都没有使用，那么饿汉式创建的对象就浪费了，懒汉式是使用时才创建，就不存在这个问题
4、在我们javaSE标准类中，java.lang.Runtime就是经典的单例模式    
```

单例设计模式小结

```java
1、单例模式的两种实现方式①饿汉式②懒汉式
2、饿汉式的问题：在类加载时候就创建，可能存在资源浪费问题
3、懒汉式的问题：线程安全问题。
```



##### final关键字

```java
final可以修饰类、属性、方法和局部变量。
1、当不希望类被继承时，可以用final修饰。
2、当不希望父类的某个方法被子类覆盖/重写(override)时，可以用final关键字修饰。
3、当不希望类的某个属性的值被修改，可以用final修饰
4、当不希望某个局部变量被修改，可以使用final修饰
5、一般来说，如果一个类已经是final类了，就没有必要再将方法修饰成final方法。
6、final方法不能修饰构造方法(构造器)
7、final和static往往搭配使用，效率更高，底层编译器做了优化处理。
8、包装类(Integer,Double,Float,Boolean等都是final)，String也是final类
    
final使用注意事项
1、final修饰的属性又叫常量
2、final修饰的属性在定义时，必须赋初值，并且以后不能再修改，赋值可以在如下位置之一：①定义时：如public final double TAX_PATE=0.08; ②在构造器中 ③在代码块中
3、如果final修饰的属性是静态的，则初始化的位置只能是①定义时 ②在静态代码块 不能在构造器中赋值。
4、final类不能继承，但是可以实例化对象
5、如果类不是final类，但是含有final方法，则该方法虽然不能重写，但是可以被继承    
```

##### 抽象类

```java
抽象类介绍
1、用abstract关键字来修饰一个类时，这个类就叫抽象类
    访问修饰符 abstract 类名{
	}
2、用abstract关键字来修饰一个方法时，这个方法就是抽象方法
    访问修饰符abstract返回类型 方法名(参数列表);//没有方法体
3、抽象类的价值更多作用是在于设计，是设计者设计好后，让子类继承并实现抽象类()
4、抽象类，是考官比较爱问的知识点，再框架和设计模式使用较多
    
抽象类使用的注意事项
1、抽象类不能被实例化
2、抽象类不一定要包含abstract方法。抽象类可以没有abstract方法
3、一旦类包含了abstract方法，则这个类必须声明为abstract
4、abstract只能修饰类和方法，不能修饰属性和其他的
5、抽象类可以有任意成员【因为抽象类还是类】
6、抽象类方法不能用主体，即不能实现
7、如果一个类继承了抽象类，则它必须实现抽象类的所有抽象方法，除非它自己也声明为abstract类。
8、抽象方法不能使用private、final和static来修饰，因为这些关键字都是和重写相违背的
```

###### 抽象类-模板设计模式

TestTemplate.java

```java
public class TestTemplate {
    public static void main(String[] args) {
        AA aa = new AA();
        aa.calculateTime();

        BB bb = new BB();
        bb.calculateTime();
    }
}
```

Template.java

```java
public abstract class Template {//抽象类-模板设计模式
    public abstract void job();//抽象方法
    public void calculateTime(){//实现方法，调用job方法
        //得到开始的时间
        long start = System.currentTimeMillis();
        job();
        long end = System.currentTimeMillis();
        System.out.println("任务执行时间："+ (end - start));
    }
}
```

AA.java

```java
public class AA extends Template{
    @Override
    public void job(){
        long num =0;
        for (long i = 0; i <= 800000; i++) {
            num += i;
        }
    }
}
```

BB.java

```java
public class BB extends Template{
    @Override
    public void job(){
        long num =0;
        for (long i = 0; i <= 800000; i++) {
            num *= i;
        }
    }
}
```



##### 接口

```java
接口介绍
接口就是给出一些没有实现的方法，封装到一起，到某个类要使用的时候，再根据具体情况把这些方法写出来。
语法
    interface 接口名{
    	//属性
    	//方法(1.抽象方法 2.默认实现方法 3.静态方法)
	}
	class 类名 implements 接口{
        自己属性;
        自己方法;
        必须实现的接口的抽象方法
    }
小结：
1、在jdk.7.0前接口里的所有方法都没有方法体，即都是抽象方法。
2、jdk8.0后接口可以有静态方法，默认方法，也就是说接口中可以有方法的具体实现
    
接口使用注意事项
1、接口不能被实例化
2、接口中所有的方法是 public方法，接口中抽象方法，可以不用abstract修饰：void aaa()实际上是 abstract void aa();
3、一个普通类实现接口，就必须将该接口的所有方法都实现。
4、抽象类实现接口，可以不用实现接口的方法
5、一个类同时可以实现多个接口
6、接口中的属性，只能是final的，而且是public static final 修饰符。比如：int a=1;实际上是 public static final a=1;(必须初始化)
7、接口中属性的访问形式:接口名.属性名
8、一个接口不能继承其他的类，但是可以继承多个别的接口：interface A extends B,C{}
9、接口的修饰符 只能是public和默认，这点和类的修饰符是一样的
```

###### 实现接口VS继承类

```java
接口和继承解决的问题不同：
	继承的价值主要在于：解决代码的复用性和可维护性。
    接口的价值主要在于：设计，设计好各种规范(方法),让其他类去实现这些方法。即更加灵活..
    
接口比继承更加灵活：
    接口比继承更加灵活，继承是满足is-a的关系，而接口只需满足like-a的关系。
    
接口在一定程度上实现代码解耦[即：接口规范性+动态绑定机制]    
```

###### 接口的多态传递

```java
public class InterfacePolyPass {
    public static void main(String[] args) {
        //接口类型的变量可以指向，实现了该接口的类的对象实例
        IG ig = new Teacher();
        //如果IG 继承了IH接口，而Teacher类实现了 IG接口
        //那么，实际上就相当于 Teacher 类也实现了 IH接口
        //这就是所谓的 接口多态多态传递现象
        IH ih = new Teacher();
    }
}
interface IH{
    void h1();
}
interface IG extends IH{
}
class Teacher implements IG{
    @Override
    public void h1() {
    }
}
```



##### ★★内部类★★

```java
基本介绍：
一个类的内部又完整的嵌套了另一个类结构。被嵌套的类称为内部类(inner class),嵌套其他类的类称为外部类(outer class)。是我们类的第五大成员(成员：[属性、方法、构造器、代码块、内部类])，内部类最大的特点就是可以直接访问私有属性，并且可以体现类与类之间的包含关系。

语法：
    class Outer{//外部类
        class Inner{//内部类
        }
    }
	class Other{//外部其他类
    }
```

###### 内部类分类

```java
定义在外部类局部位置上(比如方法内)：
    1、局部内部类(有类名)
    2、匿名内部类(没有类名)
定义在外部类的成员位置上：
    1、成员内部类(没用static修饰)
    2、静态内部类(使用static修饰)
```

###### 局部内部类

```java
说明：局部内部类是定义在外部类的局部位置，比如方法中，并且有类名。
    1、可以直接访问外部类的所有成员，包含私有化
    2、不能添加访问修饰符，因为它的地位就是一个局部变量。局部变量是不能使用修饰符的。但是可以使用final修饰，因为局部变量也可以使用final
    3、作用域：仅仅在定义它的方法或代码块中。
    4、局部内部类---访问--->外部类的成员[访问方式：直接访问]
    5、外部类---访问--->局部内部类的成员[访问方式：创建对象，在访问(注意：必须在作用域内)]
    6、外部其他类---不能访问--->局部内部类(因为 局部内部类地位是一个局部变量)
    7、如果外部类和局部内部类的成员重名时，默认遵循就近原则，如果想访问外部类成员，则可以使用(外部类名.this.成员) 去访问
    
代码案例：  
    
public class LocalInnerClass {
    public static void main(String[] args) {
        Outer02 outer02 = new Outer02();
        outer02.m1();
        System.out.println("Outer02的hashcode=" + outer02);
    }
}

class Outer02{//外部类
    private int n1 = 100;
    private void m2(){
        System.out.println("Outer m2()");
    }//私有方法
    public void m1(){//方法
        //1.局部内部类是定义在外部类的局部位置，通常在方法
        //3.不能添加访问修饰符，但是可以使用final修饰
        //4.作用域：仅仅在定义它的方法或代码块中
        final class Inner02{//局部内部类(本质仍然是一个类)
            //2.可以直接访问外部类的所有成员，包含私有的
            private int n1 = 800;
            public void f1(){
                //5.局部内部类可以直接访问外部类的成员，比如下面 外部类n1 和 m2()
                //7.如果外部类和局部内部类的成员重名时，默认遵循就近原则，如果想访问外部类成员，使用(外部类名.this.成员)去访问
                System.out.println("n1=" + n1 + " 外部类的n1=" + Outer02.this.n1);
                System.out.println("Outer02.this hashcode=" + Outer02.this);
                m2();
            }
        }
        //6.外部类在方法中，可以创建Inner02对象，然后调用方法即可
        Inner02 inner02 = new Inner02();
        inner02.f1();
    }
}    
```

###### ★★匿名内部类★★

```java
匿名内部类的使用
    1、本质是类 2、内部类 3、该类没有名字 4、同时还是一个对象
说明：匿名内部类是定义在外部类的局部位置，比如方法中，并且没有类名
    1、匿名内部类的基本语法：
    	new 类或接口(参数列表){
    		类体
		};
	2、匿名内部类是一个类的定义，同时它本身也是一个对象，从语法上看，它既有定义类的特征，也有创建对象的特征，因此可以调用匿名内部类方法。
	3、可以直接访问外部类的所有成员，包含私有的
    4、不能添加访问修饰符，因为它的地位就是一个局部变量
    5、作用域：仅仅在定义它的方法或代码块中
    6、匿名内部类---访问--->外部类成员[访问方式：直接访问]
        
代码案例：

public class AnonymousInnerClass {
    public static void main(String[] args) {
        Outer04 outer04 = new Outer04();
        outer04.method();
    }
}

class Outer04 {//外部类
    private int n1 = 10;//属性
    public void method() {//方法
        //基于接口的匿名内部类
        //1.需求：要使用IA接口，并创建对象
        //2.传统方式，是写一个类，实现该接口，并创建对象
        //3.需求：Tiger/Gog类只是使用一次，后面再不使用
        //4.可以使用匿名内部类来简化开发
        //5.tiger的编译类型 IA
        //6.tiger的运行类型 就是匿名内部类 Outer04$1
        /*
            我们看底层 会分配 类名 Outer04$1
            class Outer04$1 implements IA{
                @Override
                public void cry(){
                    System.out.println("老虎叫唤...");
                }
            }
        */
        //7.jdk底层在创建匿名内部类 Outer04$1，立即就创建了 Outer04$1实例，并且把地址返回给tiger
        //8.匿名内部类使用一次，就不能再使用
        IA tiger = new IA(){
            @Override
            public void cry() {
                System.out.println("老虎叫唤...");
            }
        };
        System.out.println("tiger的运行类型="+tiger.getClass());
        tiger.cry();
        tiger.cry();
        tiger.cry();

        //演示基于类的匿名内部类
        //1.father编译类型 Father
        //2.father运行类型 Outer04$1
        //3.底层会创建匿名内部类
        /*
            class Outer04$2 extends Father{
            }
         */
        //4.同时也直接返回了 匿名内部类 Outer04$2的对象
        //5.注意("jack")参数列表会传递给 构造器
        Father father = new Father("javk"){
            @Override
            public void test() {
                System.out.println("匿名内部类重写了test方法");
            }
        };
        System.out.println("father对象的运行类型="+father.getClass());//Outer04$2
        father.test();

        //基于抽象类的匿名内部类
        Animal animal = new Animal(){
            @Override
            void eat() {
                System.out.println("小狗吃骨头。。。。");
            }
        };
        animal.eat();
    }
}

interface IA {//接口
    public void cry();
}
//class Tiger implements IA {
//    @Override
//    public void cry() {
//        System.out.println("老虎叫唤...");
//    }
//}
//class Dog implements IA {
//    @Override
//    public void cry() {
//        System.out.println("小狗汪汪...");
//    }
//}

class Father{//类
    public Father(String name){//构造器
        System.out.println("接受到的name="+name);
    }
    public void test(){//方法
    }
}

abstract class Animal{//抽象类
    abstract void eat();
}


```

###### 成员内部类

```java
说明：成员内部类是定义在外部类的成员位置，并且没有static修饰。
    1、可以直接访问外部类所有成员，包含私有的
    2、可以添加任意访问修饰符(public、protected、默认、private),因为它的地位就是一个成员。
    3、作用域和外部类的其他成员一样，为整个类体，在外部类的成员方法中创建成员内部类对象，再调用方法。
    4、成员内部类---访问--->外部类成员(比如：属性)[访问方式：直接访问]
    5、外部类---访问--->成员内部类[访问方式：创建对象，再访问]
    6、外部其他类---访问--->成员内部类
    7、如果外部类和内部类的成员重名时，内部类访问的话，默认遵循就近原则，如果想访问外部类的成员，则可以使用(外部类名.this.成员)去访问
    
```

![Java成员内部类代码](E:\java\笔记\image\Java成员内部类代码.png)

###### 静态内部类

```java
说明：静态内部类是定义再外部类的成员位置，并且有static修饰
	1、可以直接访问外部类的所有静态成员，包含私有的，但不能直接访问非静态成员
	2、可以添加任意访问修饰符(public、protected、默认、private)，因为它的地位就是一个成员
	3、作用域：同其他的成员，为整个类体
	4、静态内部类---访问--->外部类(比如：静态属性)[访问方式：直接访问所有静态成员]
	5、外部类---访问--->静态内部类 访问方式：创建对象，再访问
    6、如果外部类和静态内部类的成员重名时，静态内部类访问时，默认遵循就近原则，如果想访问外部类的成员，则可以使用(外部类名.成员)去访问
    
代码案例：
    
public class StaticlnnerClass01 {
    public static void main(String[] args) {
        Outer10 outer10 = new Outer10();
        outer10.m1();
        //外部其他类 使用静态内部类
        //方式一
        //因为静态内部类，是可以通过类名直接访问(前提是满足访问权限)
        Outer10.Inner10 inner10 = new Outer10.Inner10();
        inner10.say();
        //方式2
        //编写一个方法，可以返回一个静态内部类
        Outer10.Inner10 inner101 = outer10.getInter10();
        inner101.say();

        Outer10.Inner10 inner10_ = Outer10.getInter10_();
        inner10_.say();
    }
}
class Outer10{//外部类
    private int n1 = 10;
    private static String name = "张三";
    private static void cry(){}
    //Inner10就是静态内部类
    //1.放在外部类的成员位置
    //2.使用static 修饰
    //3.可以直接访问外部类的所有静态成员，包含私有的，但不能直接访问非静态成员
    //4.可以添加任意访问修饰符(public、protected、默认、private)，因为它的地位就是一个成员
    static class Inner10{
        private static String name = "里斯";
        public void say(){//就近原则
            System.out.println(name+" 外部类name= " + Outer10.name);
            cry();
        }
    }
    public void m1(){
        Inner10 inner10 = new Inner10();
        inner10.say();
    }
    public Inner10 getInter10(){
        return new Inner10();
    }
    public static Inner10 getInter10_(){
        return new Inner10();
    }
}
```

###### 小结

```java
1、内部类有四种 局部内部类，匿名内部类，成员内部类，静态内部类
2、重点还是掌握 匿名内部类使用
	new 类/接口(参数列表){
    	//...
	};
3、成员内部类，静态内部类 是放在外部类成员位置，本质就是一个成员
```



##### 枚举

代码路径:

<u>E:\Android\lx\javastudy\chapter10\src\main\java\com\example\chapter11</u>

![Java枚举](E:\java\笔记\image\Java枚举.png)

![Java枚举实现方式](E:\java\笔记\image\Java枚举实现方式.png)

![Java自定义类实现枚举](E:\java\笔记\image\Java自定义类实现枚举.png)

![Java自定义类实现枚举小结](E:\java\笔记\image\Java自定义类实现枚举小结.png)

![Javaenum关键字实现枚举注意事项1](E:\java\笔记\image\Javaenum关键字实现枚举注意事项1.png)

![Javaenum常用方法应用](E:\java\笔记\image\Javaenum常用方法应用.png)

   

##### 注解

![Java注解的理解](E:\java\笔记\image\Java注解的理解.png)

![Java基本的Annotation介绍](E:\java\笔记\image\Java基本的Annotation介绍.png)

![JavaOverride使用说明](E:\java\笔记\image\JavaOverride使用说明.png)

![JavaDeprecated说明](E:\java\笔记\image\JavaDeprecated说明.png)

![Java@SuppressWarnings说明各种值](E:\java\笔记\image\Java@SuppressWarnings说明各种值.png)

![Java的元注解](E:\java\笔记\image\Java的元注解.png)

![JavaJDK的元注解-@Retention注解](E:\java\笔记\image\JavaJDK的元注解-@Retention注解.png)

![JavaJDK的元注解-@Target注解](E:\java\笔记\image\JavaJDK的元注解-@Target注解.png)

![JavaJDK的元注解-@Documented注解](E:\java\笔记\image\JavaJDK的元注解-@Documented注解.png)

![JavaJDK的元注解-@Inherited注解](E:\java\笔记\image\JavaJDK的元注解-@Inherited注解.png)



##### 异常

![Java异常介绍](E:\java\笔记\image\Java异常介绍.png)

![Java异常体系图小结](E:\java\笔记\image\Java异常体系图小结.png)

###### 常见运行时异常

![Java常见的运行时异常](E:\java\笔记\image\Java常见的运行时异常.png)

###### NullPointerException空指针异常

![JavaNullPointerException空指针异常](E:\java\笔记\image\JavaNullPointerException空指针异常.png)

###### ArithmeticException数学运算异常

![JavaArithmeticException数学运算异常](E:\java\笔记\image\JavaArithmeticException数学运算异常.png)

###### ArrayIndexOutBoundsException数组下标越界异常

![JavaArrayIndexOutBoundsException数组下标越界异常](E:\java\笔记\image\JavaArrayIndexOutBoundsException数组下标越界异常.png)

###### ClassCastException类型转换异常

![JavaClassCastException类型转换异常](E:\java\笔记\image\JavaClassCastException类型转换异常.png)

###### NumberFormatException异常

![JavaNumberFormatException异常](E:\java\笔记\image\JavaNumberFormatException异常.png)

###### 编译异常和异常处理

![Java编译异常](E:\java\笔记\image\Java编译异常.png)

![Java异常处理](E:\java\笔记\image\Java异常处理.png)

###### try-catch异常处理

![Javatry-catch异常处理](E:\java\笔记\image\Javatry-catch异常处理.png)

![Javatry-catch异常处理注意事项1](E:\java\笔记\image\Javatry-catch异常处理注意事项1.png)

![Javatry-catch异常处理注意事项2](E:\java\笔记\image\Javatry-catch异常处理注意事项2.png)

![Javatry-catch异常处理注意事项3](E:\java\笔记\image\Javatry-catch异常处理注意事项3.png)

![Javatry-catch异常处理小结](E:\java\笔记\image\Javatry-catch异常处理小结.png)

###### try-catch异常处理代码

```java
import java.util.Scanner;

public class TryCatchExercise {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        int num = 0;
        String inputStr = "";
        while (true){
            System.out.println("请输入一个整数");
            inputStr = scanner.next();
            try {
                num = Integer.parseInt(inputStr);//这里是可能抛出异常
                break;
            }catch (NumberFormatException e){
                System.out.println("你输入的不是一个整数");
            }
        }
        System.out.println("你输入的值是=" + num);

    }
}
```

###### thows异常处理

![Javathrows异常处理](E:\java\笔记\image\Javathrows异常处理.png)

![Javathrows异常处理注意事项](E:\java\笔记\image\Javathrows异常处理注意事项.png)

###### throws异常代码

```java
import java.io.FileInputStream;
import java.io.FileNotFoundException;

public class Throws01 {
    public static void main(String[] args) {

    }

    public void f1() throws FileNotFoundException,NullPointerException,ArithmeticException {
        //创建一个文件流对象
        //1、这里有一个异常 FileNotFoundException 编译异常
        //2、使用前面讲过的 try-catch-finally
        //3、使用throws，抛出异常，让调用f1方法的调用者(方法)处理
        //4、throws后面的异常类型可以是方法中产生的异常类型，也可以是它的父类
        //5、throws关键字后也可以是 异常列表，即可以抛出多个异常
        FileInputStream fis = new FileInputStream("D://aa.txt");
    }
}
```

###### 自定义异常

```java
public class CustomException {
    public static void main(String[] args) {
        int age = 180;
        //要求范围 18 - 120之间，否则抛出一个自定义异常
        if (!(age >= 18 && age <= 120)){
            //这里我们可以通过构造器，设置信息
            throw new AgeException("年龄需要在 18~120之间");
        }
        System.out.println("你的年龄范围正确.");
    }
}
//自定义一个异常
//一般情况下，我们自定义异常是继承 RuntimeException
//即把自定义异常做成 运行时异常，好处时，我们可以使用默认的处理机制

class AgeException extends RuntimeException {
    public AgeException(String message) {//构造器
        super(message);
    }
}
```

###### throw和throws的区别

![Javathrow和throws的区别](E:\java\笔记\image\Javathrow和throws的区别.png)



##### 包装类

![Java包装类](E:\java\笔记\image\Java包装类.png)

##### 包装类和基本数据的转换

![Java包装类和基本数据的转换](E:\java\笔记\image\Java包装类和基本数据的转换.png)

```java
public class wrapper01 {
    public static void main(String[] args) {
        //jdk5前是手动装箱和拆箱
        //手动装箱 int->Integer
        int n1 = 100;
        Integer integer = new Integer(n1);
        Integer integer1 = Integer.valueOf(n1);

        //手动拆箱
        //Integer -> int
        int i = integer.intValue();

        //jdk5后，就可以自动装箱和自动拆箱
        int n2 = 200;
        //自动装箱 int->Integer
        Integer integer2 = n2;//底层使用的是 Integer.valueOf(n2)
        //自动拆箱 Integer->int
        int n3 = integer2;//底层仍然使用的是 intValue()方法
    }
}
```

##### Integer类和Character类的常用方法

![JavaInteger类和Character类的常用方法](E:\java\笔记\image\JavaInteger类和Character类的常用方法.png)



##### String类

![JavaString类01](E:\java\笔记\image\JavaString类01.png)

![JavaString类两种创建String对象的区别](E:\java\笔记\image\JavaString类两种创建String对象的区别.png)

![JavaString的内存布局](E:\java\笔记\image\JavaString的内存布局.png)

![JavaString类intern方法](E:\java\笔记\image\JavaString类intern方法.png)

![Java字符串的特性](E:\java\笔记\image\Java字符串的特性.png)

##### String类常见方法

![JavaString类的常见方法说明](E:\java\笔记\image\JavaString类的常见方法说明.png)

![JavaString类的常见方法01](E:\java\笔记\image\JavaString类的常见方法01.png)

![JavaString类的常见方法02](E:\java\笔记\image\JavaString类的常见方法02.png)

##### StringBuffer类

![JavaStringBuffer类](E:\java\笔记\image\JavaStringBuffer类.png)

![JavaStringBufferVSString](E:\java\笔记\image\JavaStringBufferVSString.png)

![JavaStringBuffer的构造器](E:\java\笔记\image\JavaStringBuffer的构造器.png)

##### StringBuffer类的常见方法

![JavaStringBuffer类的常见方法](E:\java\笔记\image\JavaStringBuffer类的常见方法.png)

##### StringBuild类

![JavaStringBuilder类](E:\java\笔记\image\JavaStringBuilder类.png)

##### StringBuild类的常见方法

![JavaStringBuilder类的常用方法](E:\java\笔记\image\JavaStringBuilder类的常用方法.png)

##### String、StringBuffer、StringBuilder的比较

![JavaStringBuilder类对比](E:\java\笔记\image\JavaStringBuilder类对比.png)

![JavaString、StringBuffer、StringBuilder的选择](E:\java\笔记\image\JavaString、StringBuffer、StringBuilder的选择.png)

##### Math类常见方法

![JavaMath类常见方法](E:\java\笔记\image\JavaMath类常见方法.png)

##### Arrays类常见方法

![JavaArrays类常见方法1](E:\java\笔记\image\JavaArrays类常见方法1.png)

![JavaArrays类常见方法2](E:\java\笔记\image\JavaArrays类常见方法2.png)

![JavaArrays类常见方法3](E:\java\笔记\image\JavaArrays类常见方法3.png)

##### System类

![JavaSystem类](E:\java\笔记\image\JavaSystem类.png)

##### BigInteger类和BigDecimal类

![JavaBigInteger类和BigDecimal类](E:\java\笔记\image\JavaBigInteger类和BigDecimal类.png)

##### 日期类

![Java日期类1](E:\java\笔记\image\Java日期类1.png)

![Java日期类2](E:\java\笔记\image\Java日期类2.png)

![Java日期类3](E:\java\笔记\image\Java日期类3.png)

##### 第三代日期类常见方法

![Java第三代日期类常见方法](E:\java\笔记\image\Java第三代日期类常见方法.png)

##### DateTimeFormatter格式日期类

![Java日期类DateTimeFormatter格式日期类](E:\java\笔记\image\Java日期类DateTimeFormatter格式日期类.png)

##### Instant时间戳

![Java日期类Instant时间戳](E:\java\笔记\image\Java日期类Instant时间戳.png)

##### 第三代日期类更多方法

![Java第三代日期类更多方法](E:\java\笔记\image\Java第三代日期类更多方法.png)



##### ★★集合★★

```java
集合:
	1、可以动态保存任意多个对象，使用比较方便
    2、提供了一系列方便的操作对象的方法：add、remove、set、get等
    3、使用集合添加，删除新元素的示意代码-简洁了
```

###### 集合的框架体系

![Java集合的框架体系](E:\java\笔记\image\Java集合的框架体系.png)

###### Collection接口和常用方法

```java
Collection接口实现类的特点：
    public interface Collection<E> extends Iterable<E>
1.collection实现子类可以存放多个元素，每个元素可以是Object
2.有些Collection的实现类，可以存放重复的元素，有些不可以
3.有些Collection的实现类，有些是有序的(List),有些不是有序(Set)
4.Collection接口没有直接的实现子类，是通过它的子接口Set和List来实现的
    
Collection接口常用方法，以实现子类
1.add:添加单个元素
2.remove：删除指定元素
3.contains：查找元素是否存在
4.size:获取元素个数    
5.isEmpty:判断是否为空
6.clear：清空
7.addAll:添加多个元素    
8.containsAll:查找多个元素是否都存在
9.removeAll：删除多个元素    

代码：
import java.util.ArrayList;
import java.util.List;

public class CollectionMethod {
    @SuppressWarnings({"all"})
    public static void main(String[] args) {
        List list = new ArrayList();

        //add:添加单个元素
        list.add("jack");
        list.add(10);//list.add(new Integer(10))
        list.add(true);
        System.out.println("list="+list);

        //remove:删除指定元素
        //list.remove(0);//删除第一个元素
        list.remove(true);//指定删除某个元素
        System.out.println("list="+list);

        //contains：查找元素是否存在
        System.out.println(list.contains("jack"));//true

        //size:获取元素个数
        System.out.println(list.size());//2

        //isEmpty：判断是否为空
        System.out.println(list.isEmpty());//F

        //clear:清空
        list.clear();
        System.out.println("list=" + list);

        //addAll:添加多个元素
        ArrayList list2 = new ArrayList();
        list2.add("红楼梦");
        list2.add("三国演义");
        list.addAll(list2);
        System.out.println("list=" + list);

        //containsAll：查找多个元素是否都存在
        System.out.println(list.containsAll(list2));//T

        //removeAll:删除多个元素
        list.add("聊斋");
        list.removeAll(list2);
        System.out.println("list="+list);//[聊斋]
    }
}
```

###### Collection接口遍历元素方式1-使用Iterator(迭代器)

```java
java.util
接口 Iterator<E>
所有已知子接口： ListIterator<E>,XMLEventReader
所有已知实现类：BeanContextSupport.BCSIterator,EventReaderDelegate,Scanner
1.Iterator对象成为迭代器，主要用于遍历Collection集合中的元素。
2.所有实现了Collection接口的集合类都有一个iterator()方法，用以返回一个实现了Iterator接口的对象，即可以返回一个迭代器。
3.Iterator仅用于遍历集合，Iterator本身并不存放对象    
迭代器的执行原理
Iterator iterator = coll.iterator();//得到一个集合的迭代器
//hasNext():判断是否还有下一个元素
while(iterator.jasNext()){
    //next()作用：1.下移 2.将下移以后集合位置上的元素返回
    System。out.println(iterator.next())
}
Iterator接口的方法提示
在调用iterator.next()方法之前必须要调用iterator.hasNext()进行检测。若不调用，且下一条记录无效，直接调用it.next()会抛出NoSuchElementException异常
```

###### Collection接口遍历对象方式2-for循环增强

```java
增强for循环，可以替代iterator迭代器，特点：增强for就是简化版的iterator，本质一样。只能用于遍历集合或数组
基本语法
for(元素类型 元素名：集合名或数组名){
    访问元素
}
代码
import java.util.ArrayList;
import java.util.Collection;

public class CollectionFor {
    public static void main(String[] args) {
        Collection col = new ArrayList();

        col.add(new Book("三国演义","罗贯中",10.1));
        col.add(new Book("小李飞刀","古龙",5.1));
        col.add(new Book("红楼梦","曹雪芹",34.6));

        //1.使用增强for,在Collection集合
        //2.增强for,底层仍然是迭代器
        //3.增强for可以理解成就是简化版本的 迭代器遍历
        //4.快捷键方式 I
        for (Object book : col) {
            System.out.println("book=" + book);
        }

//        for (Object book : col) {
//            System.out.println("book=" + book);
//        }
        //增强for,也可以直接在数组使用
        int[] nums = {1,8,10,90};
        for (int i : nums){
            System.out.println("i=" + i);
        }
    }
}
```

###### List接口和常用方法

```java
List接口介绍
List接口是Collection接口的子接口
1、List集合类中元素有序(即添加顺序和取出顺序一致)、且可重复
2、List集合中的每个元素都有其对应的顺序索引，即支持索引
3、List容器中的元素都对应一个整数型的序号记载其在容器中的位置，可以根据序号存取容器中元素。
4、JDK API中List接口的实现类有：(常用:ArrayList、LinkedList和Vector)

List常用方法
List集合里添加了一些根据索引来操作集合元素的方法
1、void add(int index,Object ele):在index位置插入ele元素
2、boolean addAll(int index,Collection eles):从index位置开始将eles中的所有元素添加进来
3、Object get(int index):获取指定index位置的元素
4、int indexOf(Object obj):返回obj在集合中首次出现的位置
5、int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
6、Object remove(int index):移除指定index位置的元素，并返回此元素
7、Object set(int index,Object ele):设置指定index位置的元素为ele，相当于替换。
8、List subList(int fromIndex,int toIndex):返回从fromIndex到toIndex位置的子集合:返回的子集合 fromIndex <= subList < toIndex

代码    
import java.util.ArrayList;
import java.util.List;

public class ListMethod {
    public static void main(String[] args) {
        List list = new ArrayList();
        list.add("张三丰");
        list.add("贾宝玉");
        //void add(int index,Object ele):在index位置插入ele元素
        //在index = 1的位置插入一个对象
        list.add(1,"张三");
        System.out.println("list="+list);
        //boolean addAll(int index,Collection eles):从index位置开始将eles中的所有元素添加进来
        List list2 = new ArrayList();
        list2.add("jack");
        list2.add("mara");
        list.addAll(1,list2);
        System.out.println("list="+list);
        //Object get(int index):获取指定index位置的元素
        //int indexOf(Object obj):返回obj在集合中首次出现的位置
        System.out.println(list.indexOf("jack"));//1
        //int lastIndexOf(Object obj):返回obj在当前集合中末次出现的位置
        list.add("张三丰");
        System.out.println(list.lastIndexOf("张三丰"));//5
        //Object remove(int index):移除指定index位置的元素，并返回此元素
        list.remove(0);
        System.out.println("list=" + list);
        //Object set(int index,Object ele):设置指定index位置的元素为ele，相当于替换。
        list.set(1,"玛丽");
        System.out.println("list=" + list);
        //  List subList(int fromIndex,int toIndex):返回从fromIndex到toIndex位置的子集合
        //返回的子集合 fromIndex <= subList < toIndex
        List returnlist = list.subList(0,2);
        System.out.println("returnlist=" + returnlist);
    }
}
```

###### List排序练习

```java
import java.util.LinkedList;
import java.util.List;

public class Listexercise02 {
    public static void main(String[] args) {
        //List list = new ArrayList();//效果一样
        List list = new LinkedList();//效果一样
        //List list = new Vector();//效果一样
        list.add(new book("红楼梦","曹雪芹",100));
        list.add(new book("三国","罗贯中",280));
        list.add(new book("水浒","施耐庵",300));
        list.add(new book("史记","司马迁",123));
        list.add(new book("西游","吴承恩",70));

        //遍历
        for (Object o : list) {
            System.out.println(o);
        }

        //冒泡排序
        sort(list);
        System.out.println("==排序后==");
        for (Object o : list) {
            System.out.println(o);
        }
    }
    //静态方法
    public static void sort(List list){
        int listSize = list.size();
        for (int i = 0; i < listSize-1; i++) {
            for (int j = 0; j < listSize-1-i; j++) {
                //取出对象Book
                book book1 = (book)list.get(j);
                book book2 = (book)list.get(j+1);
                if (book1.getPrice() < book2.getPrice()){//交换
                    list.set(j,book2);
                    list.set(j+1,book1);
                }
            }
        }
    }

}

class book{
    private String name;
    private String author;
    private double price;

    public book(String name, String author, double price) {
        this.name = name;
        this.author = author;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }

    public String getAuthor() {
        return author;
    }

    public void setAuthor(String author) {
        this.author = author;
    }

    public double getPrice() {
        return price;
    }

    public void setPrice(double price) {
        this.price = price;
    }

    @Override
    public String toString() {
        return "名称："+name+"\t\t价格："+price+"\t\t作者："+ author;
    }
}

结果:
名称：红楼梦		价格：100.0		作者：曹雪芹
名称：三国		价格：280.0		作者：罗贯中
名称：水浒		价格：300.0		作者：施耐庵
名称：史记		价格：123.0		作者：司马迁
名称：西游		价格：70.0		作者：吴承恩
==排序后==
名称：水浒		价格：300.0		作者：施耐庵
名称：三国		价格：280.0		作者：罗贯中
名称：史记		价格：123.0		作者：司马迁
名称：红楼梦		价格：100.0		作者：曹雪芹
名称：西游		价格：70.0		作者：吴承恩

Process finished with exit code 0
```

###### ArrayList底层结构和源码分析

```java
ArrayList的注意事项
    1、permits all elements,including null,ArrayList可以加入null，并且多个
    2、ArrayList是由数组来实现数据存储的
    3、ArrayList基本等同于Vector，除了ArrayList是线程不安全(执行效率高)看源码.，在多线程情况下，不建议使用ArrayList
    
ArrayList的底层操作机制源码分析(重点，难点)
    1、ArrayList中维护了一个Object类型的数组elementData.
       transient Object[] elementData;//transient 表示瞬间，短暂的，表示该属性不会被序列号
	2、当创建ArrayList对象时，如果使用的是无参构造器，则初始elementData容量为0，第1次添加，则扩容elementData为10，如需要再次扩容elementData为1.5倍。
    3、如果使用的是指定大小的构造器，则初始elementData容量为指定大小，如果需要扩容，则直接扩容elementData为1.5倍
```

###### Vector底层结构和源码刨析

```java
Vector的基本介绍
1、Vector类的定义说明
    public class Vector<E>
    extends AbstractList<E>
    implements List<E>,RandomAccess,Cloneable,Serializeable
2、Vector底层也是一个对象数组，protected Object[] elementData;
3、Vector是线程同步的，即线程安全，Vector类的操作方法带有synchronized
    public synchronized E get(int index){
    	if(index >= elementCount)
            throw new ArrayIndexOutOfBoundsException(index);
    	return elementData(index);
	}
4、在开发中，需要线程同步安全时，考虑使用Vector
```

###### Vector和ArrayList的比较

![JavaVector底层结构和ArrayList的比较](E:\java\笔记\image\JavaVector底层结构和ArrayList的比较.png)

###### LinkdList底层结构

```java
LinkedList的全面说明
    1、LinkedList底层实现了双向链表和双端队列特点
    2、可以添加任意元素(元素可以重复)，包括null
    3、线程不安全，没有实现同步
    
LinkedList的底层操作机制
    1、LinkedList底层维护了一个双向链表
    2、LinkedList中维护了两个属性first和last分别指向 首节点和尾节点
    3、每个节点(Node对象)，里面又维护了prev、next、item三个属性，其中通过prev指向前一个，通过next指向后一个节点。最终实现双向链表。
    4、所以LinkedList的元素的添加和删除，不能通过数组完成的，相对来说效率较高。

LinkedList01 代码：

public class LinkedList01 {
    public static void main(String[] args) {
        //模拟一个简单的双向链表
        Node jack = new Node("jack");
        Node tom = new Node("tom");
        Node lh = new Node("老寒");

        //连接三个结点，形成双向链表
        //jack -> tom -> lh
        jack.next = tom;
        tom.next=lh;
        //lh -> tom -> jack
        lh.pre = tom;
        tom.pre = jack;

        Node first = jack;//让first引用指向jack,就是双向链表的头结点
        Node last = lh;//让last引用指向lh,就是双向链表的尾结点

        //从头到尾 遍历
        System.out.println("===从头到尾进行遍历====");
        while (true) {
            if (first == null){
                break;
            }
            //输出first信息
            System.out.println(first);
            first = first.next;
        }

        //从尾到头 遍历
        System.out.println("===从尾到头进行遍历====");
        while (true) {
            if (last == null){
                break;
            }
            //输出first信息
            System.out.println(last);
            last = last.pre;
        }

        //链表的添加对象/数据

        //1.先创建一个 Node结点，name 就是 smith
        Node smith = new Node("smith");
        smith.next = lh;
        smith.pre = tom;
        lh.pre = smith;
        tom.next = smith;

        //让first 再次指向jack
        first = jack;//让first引用指向jack,就是双向链表的头结点
        //从头到尾 遍历
        System.out.println("===从头到尾进行遍历====");
        while (true) {
            if (first == null){
                break;
            }
            //输出first信息
            System.out.println(first);
            first = first.next;
        }

        //让last 再次指向lh
        last = lh;//让last引用指向lh,就是双向链表的尾结点
        //从尾到头 遍历
        System.out.println("===从尾到头进行遍历====");
        while (true) {
            if (last == null){
                break;
            }
            //输出first信息
            System.out.println(last);
            last = last.pre;
        }
    }
}
//定义一个 Node类，Node 对象 表示双向链表的一个节点
class Node {
    public Object item; //真正存放数据的地方
    public Node next; //指向下一个结点
    public Node pre;  //指向上一个节点
    public Node(Object name) {
        this.item = name;
    }
    public String toString() {
        return "Node name=" + item;
    }
}    
输出结果：
===从头到尾进行遍历====
Node name=jack
Node name=tom
Node name=老寒
===从尾到头进行遍历====
Node name=老寒
Node name=tom
Node name=jack
===从头到尾进行遍历====
Node name=jack
Node name=tom
Node name=smith
Node name=老寒
===从尾到头进行遍历====
Node name=老寒
Node name=smith
Node name=tom
Node name=jack

Process finished with exit code 0

   
    
LinkedListCRUD 代码： 
    
import java.util.Iterator;
import java.util.LinkedList;

public class LinkedListCRUD {
    public static void main(String[] args) {

        LinkedList linkedList = new LinkedList();
        linkedList.add(1);
        linkedList.add(2);
        linkedList.add(3);

        System.out.println("linkedList=" + linkedList);

        //删除
        linkedList.remove();//默认删除的是第一个结点
        //linkedList.remove(2);
        System.out.println("linkedList="+linkedList);

        //修改某个结点对象
        linkedList.set(1,999);
        System.out.println("linkedList=" + linkedList);

        //得到某个结点对象
        //get(1) 是得到双向链表的第二个对象
        Object o = linkedList.get(1);
        System.out.println(o);//999

        //因为LinkedList 是 实现了 List接口，遍历方式
        System.out.println("===LinkeList遍历迭代器===");
        Iterator iterator = linkedList.iterator();
        while (iterator.hasNext()){
            Object next = iterator.next();
            System.out.println("next=" + next);
        }

        System.out.println("===LinkeList遍历迭代器增强for===");
        for (Object o1 : linkedList) {
            System.out.println("o1=" + o1);
        }
        System.out.println("===LinkeList遍历普通for===");
        for (int i = 0; i < linkedList.size(); i++) {
            System.out.println(linkedList.get(i));
        }

        /* 1.LinkedList linkedList = new LinkedList();
             public LinkedList() {}
           2.这时 linkeList 的属性 first = null last = null
           3.执行 添加
                public boolean add(E e) {
                    linkLast(e);
                    return true;
                }
         */
    }
}
输出结果：
linkedList=[1, 2, 3]
linkedList=[2, 3]
linkedList=[2, 999]
999
===LinkeList遍历迭代器===
next=2
next=999
===LinkeList遍历迭代器增强for===
o1=2
o1=999
===LinkeList遍历普通for===
2
999

Process finished with exit code 0

```

###### ArrayList和LinkedList比较

![JavaArrayList和LinkedList比较](E:\java\笔记\image\JavaArrayList和LinkedList比较.png)



###### Set接口

![JavaSet接口基本介绍](E:\java\笔记\image\JavaSet接口基本介绍.png)

![JavaSet接口的常用方法与遍历方式](E:\java\笔记\image\JavaSet接口的常用方法与遍历方式.png)

![JavaSet接口实现类-HashSet](E:\java\笔记\image\JavaSet接口实现类-HashSet.png)

![JavaHashSet底层机制说明](E:\java\笔记\image\JavaHashSet底层机制说明.png)

![JavaHashSet底层机制说明1](E:\java\笔记\image\JavaHashSet底层机制说明1.png)

![Set接口实现类-LinkedHashSet](E:\java\笔记\image\Set接口实现类-LinkedHashSet.png)

![JavaLinkedHashSet底层机制示意图](E:\java\笔记\image\JavaLinkedHashSet底层机制示意图.png)



###### Map接口

![JavaMap接口和常用方法](E:\java\笔记\image\JavaMap接口和常用方法.png)

![JavaMap接口的特点](E:\java\笔记\image\JavaMap接口的特点.png)

![JavaMap接口常用方法](E:\java\笔记\image\JavaMap接口常用方法.png)

![JavaMap接口遍历方法](E:\java\笔记\image\JavaMap接口遍历方法.png)



###### HashMap接口

![javaMap接口实现类-HashMap](E:\java\笔记\image\javaMap接口实现类-HashMap.png)

![JavaHashMap底层机制及源码剖析](E:\java\笔记\image\JavaHashMap底层机制及源码剖析.png)



###### Hashtable

![javaMap接口实现类-Hashtable](E:\java\笔记\image\javaMap接口实现类-Hashtable.png)



###### HashTable和HashMap对比

![JavaHashtable和HashMap对比](E:\java\笔记\image\JavaHashtable和HashMap对比.png)



###### Map接口实现类-Properties

![javaMap接口实现类-Properties](E:\java\笔记\image\javaMap接口实现类-Properties.png)



###### Collections工具类

![javaCollections工具类](E:\java\笔记\image\javaCollections工具类.png)

![javaCollections工具类2](E:\java\笔记\image\javaCollections工具类2.png)



###### 集合总结

![Java总结-开发中如何选择集合实现类](E:\java\笔记\image\Java总结-开发中如何选择集合实现类.png)



##### 泛型

```java
泛型的好处
    1、编译时，检查添加元素的类型，提高了安全性
    2、减少了类型转换的次数，提高效率
    
泛型的声明
    interface接口<T>{}和class类<K,V>{}
	说明：
    1、其中，T,K,V不代表值，而是表示类型。
    2、任意字母都可以。常用T表示，是Type的缩写
        
泛型的实例化：
    1、List<String> strList = new ArrayList<String>();
	2、Iterator<Customer> iterator = customers.iterator();

泛型使用的主要事项和细节
    1. interface List<T>o , public class HashSet<E>0..等等说明:T,E只能是引用类型
    2.在给泛型指定具体类型后，可以传入该类型或者其子类类型3．泛型使用形式
    3.泛型使用形式
        List<lnteger> list1 =new ArrayList<Integer>0);List<lnteger> list2 = new ArrayList<>0);[说明:]
		如果我们这样写List list3 = new ArrayList();默认给它的泛型是[<E>E就是Object]
	
自定义泛型类：
    基础语法：
        class 类名<T,R...>{//...表示可以有多个泛型成员
        }
	注意细节
        1、普通成员可以使用泛型(属性、方法)
        2、使用泛型的数组，不能初始化
        3、静态方法中不能使用类的泛型
        4、泛型类的类型，是在创建对象时确定的(因为创建对象时，需要指定确定类型)
        5、如果在创建对象时，没有指定类型，默认为Object

自定义泛型
    自定义泛型接口
        基本语法：interface 接口名<T,R...>{}
        注意事项
            1、接口中，静态成员也不能使用泛型(这个和泛型类规定一样)
            2、泛型接口的类型，在继承接口或者实现接口时确定
            3、没有指定类型，默认为Object
    自定义泛型方法
        基本语法：修饰符 <T,R..>返回类型 方法名(参数列表){}
		注意细节
            1、泛型方法，可以定义在普通类中，也可以定义在泛型类中
            2、当泛型方法被调用时，类型会确定
            3、public void eat(E e){}，修饰符后没有<T,R..> eat方法不是泛型方法，而是使用了泛型
            
泛型的继承和通配符
		1、泛型不具备继承性List<Object> list = new ArrayList<String>0);对吗?
        2、<?>︰支持任意泛型类型
        3、<? extends A>:支持A类以及A类的子类,规定了泛型的上限
        4、<? super A>:支持A类以及A类的父类，不限于直接父类，规定了泛型的下限
```



##### 绘图与事件处理机制

![Java绘图技术](E:\Java\笔记\image\Java绘图技术.png)

![Java绘图技术-Graphics类](E:\Java\笔记\image\Java绘图技术-Graphics类.png)

![Java事件处理机制](E:\Java\笔记\image\Java事件处理机制.png)

![Java事件处理机制深入理解](E:\Java\笔记\image\Java事件处理机制深入理解.png)

![Java事件处理机制事件类型](E:\Java\笔记\image\Java事件处理机制事件类型.png)

![Java事件处理机制-事件监听器接口](E:\Java\笔记\image\Java事件处理机制-事件监听器接口.png)



##### ★线程★

```java
创建线程的方式：
//    1、继承Thread类，重写run方法
//    2、实现Runnable接口，重写run方法
	
继承Thread VS 实现Runnable的区别
//    1、本质上没有区别，Thread类本身就实现了Runnable接口
//    2、实现Runnable接口方式更加适合多个线程共享一个资源的情况，并且避免了单继承的限制，建议使用Runnable。
    
线程终止
//    1、当线程完成任务后，会自动退出。
//    2、还可以通过使用变量来控制run方法退出的方式停止线程，即通知方式
    
线程常用方法
//    1、setName：设置线程名称，使之与参数name相同
//    2、getName：返回该线程的名称
//    3、start：使该线程开始执行；Java虚拟机底层调用该线程的start0方法
//    4、run：调用线程对象run方法
//    5、setPriority：更改线程的优先级
//    6、getPriority：获取线程的优先级
//    7、sleep：在指定的毫秒数内让当前正在执行的线程休眠(暂停执行)
//    8、interrupt：中断线程,但并没有真正的结束线程，所以一般用于中断正在休眠线程
//    9、yield:线程的礼让，让出cpu,让其他线程执行，但礼让的时间不确定，所以也不一定礼让成功。
//    10、join：线程的插队。插队的线程一旦插队成功，则肯定先执行完插入的线程所以的任务
    
用户线程和守护线程
//    1、用户线程：也叫工作线程，当线程的任务执行完或通知方式结束
//    2、守护线程：一般是为工作线程服务的，当所以的用户线程结束，守护线程自动结束
//    3、常见的守护线程：垃圾回收机制

线程的生命周期
//    JDK中用Thread.State枚举表示了线程的几种状态
    public static enum Thread.State extends Enum<Thread.State>
//线程状态：可以处以以下状态之一：
    NEW:尚未启动的线程处于此状态。
    RUNNABLE：在Java虚拟机中执行的线程处于此状态。
    BLOCKED：被阻塞等待监视器锁定的线程处于此状态。
    WAITING：正在等待另一个线程执行特定动作的线程处于此状态。
    TIMED_WAITING：正在等待另一个线程执行动作达到指定等待时间的线程处于此状态。
    TERMINATED：已推出的线程处于此状态。
    
Synchronized
	线程同步机制
//        1、在多线程编程，一些敏感数据不允许被多个线程同时访问，此时使用同步访问技术，保证数据在任何同一时刻，最多有一个线程访问，一保证数据的完整性。
//        2、线程同步，即当有一个线程在对内存进行操作时，其他线程都不可以对这个内存地址进行操作，直到该线程完成操作，其他线程才能对该内存地址进行操作。
	
    同步具体方法-Synchronized
//        1、同步代码块
        synchronized(对象){ //得到对象的锁，才能操作同步代码
        	//需要被同步代码;
    	}
//		2、synchronized还可以放在方法声明中，表示整个方法-为同步方法
		public synchronized void m(String name){
            //需要被同步的代码
        }            
        
互斥锁
//    1、每个对象都对应一个可称为"互斥锁"的标记，这个标记用来保证在任一时刻，只能有一个线程访问该对象。
//    2、关键字synchronized来与对象的互斥锁联系。当某个对象用synchronized修饰时，表明该对象在任一时刻只能由一个线程访问
//    3、同步的局限性：导致程序的执行效率要降低
//    4、同步方法(非静态的)的锁可以是this，也可以是其他对象(要求是同一个对象)
//    5、同步方法(静态的)的锁为当前类本身。
  
线程的死锁
//    多个线程都占用了对方的资源锁，但不肯相让，导致了死锁，在编程是一定要避免死锁的发生。
    
```



##### ★文件流/IO流★

###### 常用文件操作

```java
//创建文件对象相关构造器和方法
//相关方法
    new File(String pathname) //根据路径构建一个File对象
    new File(File parent,String child) //根据父目录文件+子路径构建
    new File(String parent,String child) //根据父目录+子路径创建
    createNewFile 创建文件
        //创建文件对象及相关方法
        File file = new File("e:\\news1.txt");
        System.out.println("文件名字："+file.getName());
        System.out.println("文件绝对路径："+file.getAbsolutePath());
        System.out.println("文件父目录："+file.getParent());
        System.out.println("文件大小（字节）："+file.length());
        System.out.println("文件是否存在："+file.exists());
        System.out.println("是否是一个文件："+file.isFile());
        System.out.println("是否是一个目录："+file.isDirectory());    
```

###### I/O流

```java
//原理
    1、I/O是Input/Output的缩写，I/O技术是非常实用的技术，用于处理数据传输，如读/写文件，网络通信等。
    2、Java程序中，对于数据的输入/输出操作以"流(stream)"的方式进行。
    3、java.io包下提供了各种"流"类和接口，用以获取不同种类的数据，并通过方法输入或输出数据
    4、输入input：读取外部数据(磁盘、光盘等存储设备的数据)到程序(内存)中。
    5、输出output：将程序(内存)数据输出到磁盘、光盘等存储设备中
```

```java
//流的分类
	1、按操作数据单位不同分为：字节流(8 bit)二进制文件，字符流(按字符)文本文件
    2、按数据流的流向不同分为：输入流，输出流
    3、按流的角色的不同分为：节点流，处理流/包装流
```

1、Java的IO流共涉及40多个类，实际上非常规则，都是从如上4个抽象基类派生的。

2、由这四个类派生出来的子类名称都是以其父类名作为子类名后缀。

| （抽象基类） |    字节流    | 字符流 |
| :----------: | :----------: | :----: |
|    输入流    | InputStream  | Reader |
|    输出流    | OutputStream | Writer |

```java
//InputStream:字节输入流
InputStream抽象类是所有类字节输入流的超类
常用子类
    1、FileInputStream：文件输入流
    2、BufferedInputStream：缓冲字节输入流
    3、ObjectInputStream：对象字节流入流
//OutputStream:字节输出流 相似
    
        String FilePath = "e:\\hello.txt";
        //字节数组
        byte[] buf = new byte[8];//一次读取8个字节
        int readLen = 0;
        FileInputStream fileInputStream = null;
        //创建 FileInputStream 对象，用于读取文件
        fileInputStream = new FileInputStream(FilePath);
        //从该输入流读取最多b.length字节的数据到字节数组。此方法将阻塞，直到某些输入可用
        //如果返回-1，表示读取完毕
        //如果读取正常，返回实际读取的字节数
        while ((readLen = fileInputStream.read(buf)) != -1){
            System.out.print(new String(buf,0,readLen));//显示
        }
```

```java
//FileReader和FileWriter
FileReader和FileWriter是字符流，按照字符来操作IO
FileReader相关方法:
	1、new FileReader(File/String)
    2、read:每次读取单个字符，返回该字符，如果到文件末尾返回-1
    3、read(char[]):批量读取多个字符到数组，返回读取到的字符数，如果到文件末尾返回-1
     相关API:
		1、new String(char[]):将char[]转换成String
        2、new String(char[],off,len):将char[]的指定部分转换成String
            
FileWriter常用方法:
	1、new FileWriter(File/String):覆盖模式，相当于流的指针在首端
    2、new FileWriter(File/String,true):追加模式，相当于流的指针在尾端
    3、write(int):写入单个字符
    4、write(char[]):写入指定数组
    5、write(char[],off,len):写入指定数组的指定部分
    6、write(String):写入整个字符串
    7、write(String,off,len):写入字符串的指定部分
    相关API:String类:toCharArray:将String转换成char[]
    注意:FileWriter使用后，必须要关闭(close)或刷新(flush),否则写入不到指定文件
        
    String filePath = "e://story.txt";
    FileReader fileReader = null;
    char[] buf = new char[100];
    int readlen = 0;
    //1、创建一个FileReader对象    
    fileReader = new FileReader(filePath);
    //读取 使用read(buf)  返回实际读取的字符数
    while ((readlen = fileReader.read(buf)) != -1){
    	System.out.print(new String(buf,0,buf.length));
    }
	if (fileReader != null){
    	try {
        	fileReader.close();
        } catch (IOException e) {
        	e.printStackTrace();
        }
     }
```

```java
//节点流和处理流
1、节点流可以从一个特定的数据源读写数据，如FileReader、FileWriter
2、处理流(也叫包装流)是"连接"在已存在的流(节点流或处理流)之上，为程序提供更为强大的读写功能，如BufferedReader、BufferedWriter
//区别和联系
1、节点流是底层流/低级流，直接跟数据源相接
2、处理流(包装流)包装节点流，既可以消除不同节点流的实现差异，也可以提供更方便的方法来完成输入输出。
3、处理流(也叫包装流)对节点流进行包装，使用了修饰器设计模式，不会直接与数据源相连[模拟修饰器设计模式]
//处理流的功能主要体现在以下两个方面
1、性能的提供:主要以增加缓冲的方式来提供输入输出的效率。
2、操作的便捷:处理流可能提供了一系列便捷的方法来一次输入输出大批量的数据，使用更加灵活方便。
```

```java
//处理流-BufferedReader和BufferedWriter
BufferedReader和BufferedWriter属于字符流，是按照字符来读取数据的，关闭时，只需要关闭外层流即可

BufferedInputStream是字节流，在创建BufferedInputStream时，会创建一个内部缓冲区数组
BufferOutputStream是字节流，实现缓冲的输出流，可以将多个字节写入底层输出流中，而不必对每次字节写入调用底层系统
        String filePath = "e:\\Java\\lx\\ChangeChar.java";
        //创建bufferedReader
        BufferedReader bufferedReader = new BufferedReader(new FileReader(filePath));
        //读取
        String line;//按行读取，效率高
        //1. bufferedReader.readLine() 按行读取文件
        //2. 当返回null时，表示文件读取完毕
        while ((line = bufferedReader.readLine()) != null) {
            System.out.println(line);
        }
        //关闭流，这里注意，只需关闭 BufferedReader,因为底层会自动的去关闭， 节点流
        //FileReader
        bufferedReader.close();
```

```java
//对象流-ObjectInputStream和ObjectOutputStream
1、功能:提供了对基本类型或对象类型的序列化和反序列化的方法
2、ObjectOutputStream 提供 序列化功能
3、ObjectInputStream 提供 反序列化功能

//序列化和反序列化
1、序列化就是在保存数据时，保存数据的值和数据类型
2、反序列化就是在恢复数据时，恢复数据的值和数据类型
3、需要让某个对象支持序列化机制，则必须让其类是可序列化的，为了让某个类是可序列化的，该类必须实现如下两个接口之一：
    ->Serializable //这是一个标记接口，没有方法
    ->Externalizable //该接口有方法需要实现，因此我们一般实现上面的 Serializable接口
注意事项和细节说明
    1、读写顺序要一致
    2、要求序列化或反序列化对象，需要实现 Serializable
    3、序列化的类中建议添加SerializableUID，为了提高版本的兼容性
    4、序列化对象时，默认将里面所有属性都进行序列化，但除了static或transient修饰的成员
    5、序列化对象时，要求里面属性的类型也需要实现序列化接口
    6、序列化具备可继承性，也就是如果某类已经实现了序列化，则它的所有子类也已经默认实现了序列化
    //序列化操作
        //序列化后，保存的文件格式，不是存文本格式，而是按照他的格式来保存
        String filePath = "e:\\data.dat";
        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(filePath));
        //序列化数据 e:\data.dat
        oos.writeInt(100);//int -> Integer (实现了 Serializable)
        oos.writeBoolean(true); //boolean -> Boolean (实现了 Serializable)
        oos.writeChar('a');//char -> Character (实现了 Serializable)
        oos.writeDouble(9.7);
        oos.writeUTF("你好你好你好");
        //保存一个Dog对象
        oos.writeObject(new Dog("维维",12));
        oos.close();
        System.out.println("数据保存完毕(序列化形式)");
	
	//反序列化
        //序列化后，保存的文件格式，不是存文本格式，而是按照他的格式来保存
        String filePath = "e:\\data.dat";
        ObjectOutputStream oos = new ObjectOutputStream(new FileOutputStream(filePath));
        //序列化数据 e:\data.dat
        oos.writeInt(100);//int -> Integer (实现了 Serializable)
        oos.writeBoolean(true); //boolean -> Boolean (实现了 Serializable)
        oos.writeChar('a');//char -> Character (实现了 Serializable)
        oos.writeDouble(9.7);
        oos.writeUTF("你好你好你好");
        //保存一个Dog对象
        oos.writeObject(new Dog("维维",12));
        oos.close();
        System.out.println("数据保存完毕(序列化形式)");
```

```java
//转换流-InputStreamReader和OutputStreamWriter
1、InputStreamReader:Reader的子类，可以将InputStream(字节流)包装成(转换)Reader(字符流)
2、OutputStreamWriter:Writer的子类，实现将OutputStream(字节流)包装成Writer(字符流)
3、当处理纯文本数据时，如果使用字符流效率更高，并且可以有效解决中文问题，所以建议将字节流转换成字符流
4、可以在使用时，指定编码格式(比如 utf-8,gbk,gb2312,ISO8859-1 等)
        String filePath = "e:\\a.txt";
        //1.new FileInputStream(filePath) 转成 InputStreamReader
//        //2.指定编码 gbk
//        InputStreamReader isr = new InputStreamReader(new FileInputStream(filePath));
//        //3. 将 InputStreamReader 传入 BufferedReader
//        BufferedReader br = new BufferedReader(isr);
        //将 2和3 合在一起
        BufferedReader br = new BufferedReader(new InputStreamReader(
                new FileInputStream(filePath),"gbk"));
        //4.读取
        String s = br.readLine();
        System.out.println("读取内容："+ s);
        //5.关闭外层流
        br.close();
```

```java
//Properties类
1、专门用于读写配置文件的集合类
    配置文件的格式：
    键=值
    键=值
2、注意：键值对不需要有空格，值不需要用引导一起来。默认类型是String
3、Properties的常见方法
    load:加载配置文件的键值对到Properties对象
    list:将数据显示到指定设备
    getProperty(key):根据键获取值
    setProperty(key,value):设置键值对到Properties对象
    store:将Properties中的键值对存储到配置文件，在idea中，保存信息到配置文件，如果含有中文，会存储为Unicode码
        //使用Properties  类来创建，修改配置文件内容
        Properties properties = new Properties();
        //创建
        //1、如果该文件没有Key 就是创建
        //2、如果该文件有Key 就是修改
        properties.setProperty("charset","utf-8");
        properties.setProperty("root","lmj");
        properties.setProperty("pwd","888");
        //将k-v 存储文件即可
        properties.store(new FileOutputStream("src\\mysql02.properties"),null);
        System.out.println("保存配置文件成功~");
        //2.加载指定配置文件
        properties.load(new FileReader("src\\mysql02.properties"));
        //3.把k-v显示在控制台
        properties.list(System.out);
```



##### ★网络编程★

```java
//网络通信
	1、概念：两台设备之间通过网络实现数据传输
    2、网络通信：将数据通过网络从一台设备传输到另一台设备
    3、java.net包下提供了一系列的类或接口，供程序员使用，完成网络通信
        
//TCP和UDP
    TCP协议：
        1、使用TCP协议前，须先建立TCP连接，形成传输数据通道
        2、传输前，采用"三次握手"方式，是可靠的
        3、TCP协议进行通信的两个应用进程:客户端、服务端
        4、在连接中可进行大数据量的传输
        5、传输完毕，须释放已建立的连接，效率低
	UDP协议:
		1、将数据、源、目的封装成数据包，不需要建立连接
        2、每个数据报的大小限制在64K内
        3、因无需连接，故是不可靠的
        4、发送数据结束时无需释放资源(因为不是面向连接的),速度快
        5、例：厕所通知：发短信
           
//InetAddress类
	相关方法：
		1、获取本机InetAddress对象getLocalHost
        2、根据指定主机名/域名获取ip地址对象getByName
        3、获取InetAddress对象的主机名getHostName
        4、获取InetAddress对象的地址getHostAddress
```

###### Socket

```java
//基本介绍：
    1、套接字(Socket)开发网络应用程序被广泛采用，以至于成为事实上的标准。
    2、通信的两端都要有Socket，是两台机器间通信的端点
    3、网络通信其实就是Socket间的通信。
    4、Socket允许程序把网络连接当成一个流，数据在两个Socket间通过IO传输。
    5、一般主动发起通信的应用程序属客户端，等待通信请求的为服务端
```

###### TCP网络通信编程

```java
//TCP网络通信编程
1、基于客户端——服务端的网络通信
2、底层使用得是TCP/IP协议
3、基于Socket的TCP编程

code例子
服务端-SocketTCP03Server.java
public class SocketTCP03Server {
    public static void main(String[] args) throws IOException {
        //1、在本机的9999端口监听，等待连接
        //细节：要求在本机没有其他服务在监听9999
        //细节：这个 ServerSocket 可以通过 accept() 返回多个Socket[多个客户端连接服务器的并发]
        ServerSocket serverSocket = new ServerSocket(9999);
        System.out.println("服务器，在9999端口监听，等待连接...");
        //当没有客户端连接9999端口时，程序会阻塞，等待连接
        //2、如果有客户端连接，则会返回Socket对象，程序继续
        Socket socket = serverSocket.accept();
        System.out.println("服务器端socket="+socket.getClass());
        //3、通过socket.getInputStream()读取
        //      客户端写入到数据通道的数据，显示
        InputStream inputStream = socket.getInputStream();
        //4、IO读取
//        byte[] buf = new byte[1024];
//        int readline = 0;
//        while ((readline = inputStream.read(buf)) != -1){
//            System.out.println(new String(buf,0,readline));//根据读取到的实际长度 显示内容
//        }
        //4、IO读取 使用字符流 使用InputStreamReader 将 InputStream 转成字符流
        BufferedReader br = new BufferedReader(new InputStreamReader(inputStream));
        String s = br.readLine();
        System.out.println(s);//输出

        //5、获取socket相关联的输出流
        OutputStream outputStream = socket.getOutputStream();
//        outputStream.write("服务器：hello Client".getBytes());
//        //  设置结束标记
//        socket.shutdownOutput();
        //使用 字符输出流的方式回复信息
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(outputStream));
        bw.write("服务器：hello client 字符流");
        bw.newLine();//插入一个换行符，表示回复内容结束
        bw.flush();//注意 需要手动flush
        //6、关闭流和socket
//        inputStream.close();
//        outputStream.close();
        bw.close();//关闭外层流
        br.close();
        socket.close();
        serverSocket.close();//关闭
    }
}    

客户端-SocketTCP03Client.java
public class SocketTCP03Client {
    public static void main(String[] args) throws IOException {
        //1、连接服务器(ip,端口)
        //解读：连接第一个参数(主机、服务器)的9999端口
        Socket socket = new Socket(InetAddress.getLocalHost(), 9999);
        System.out.println("客户端 socket返回="+socket.getClass());
        //2、连接上后，生成socket，通过socket.getOutputStream()
        // 得到 和 socket对象关联的输出流对象
        OutputStream outputStream = socket.getOutputStream();
        //3、通过输出流，写入数据到 数据通道 要求使用字符流
        BufferedWriter bw = new BufferedWriter(new OutputStreamWriter(outputStream));
        bw.write("客户端：hello server 字符流");
        bw.newLine();//插入一个换行符，表示写入的内容结束，注意，要求对方使用readline()!!
        bw.flush();//如果使用得字符流，需要手动刷新，否则数据不会写入数据通道

        //  设置结束标记 插入一个换行符就可以表示标记结束
        //socket.shutdownOutput();

        //4、获取和socket关联的输入流，读取数据(字节)，并显示
        InputStream inputStream = socket.getInputStream();
//        byte[] buf = new byte[1024];
//        int readline = 0;
//        while ((readline = inputStream.read(buf))!=-1){
//            System.out.println(new String(buf,0,readline));
//        }
        //4、读取 字符流
        BufferedReader br = new BufferedReader(new InputStreamReader(inputStream));
        String s = br.readLine();
        System.out.println(s);
        //5、关闭流对象和socket，必须关闭
//        outputStream.close();
//        inputStream.close();
        br.close();//关闭外层流
        bw.close();
        socket.close();
        System.out.println("客户端退出~~");
    }
}

输出结果：
//服务端：
服务器，在9999端口监听，等待连接...
服务器端socket=class java.net.Socket
客户端：hello server 字符流
//客户端：
客户端 socket返回=class java.net.Socket
服务器：hello client 字符流
客户端退出~~
```

###### UDP网络通信编程

```java
//UDP网络通信编程
1、核心的两个类/对象 DatagramSocket与DatagramPacket
2、建立发送端，接收端
3、建立数据包
4、调用DatagramSocket的发送、接收方法
5、关闭DatagramSocket

code例子
//UDPReceiverA.java文件
/**
 * 接收端A  ===> 发送端A
 */
public class UDPReceiverA {
    public static void main(String[] args) throws IOException {
        //1.创建一个DatagramSocket对象，准备在9999端口接受数据
        DatagramSocket socket = new DatagramSocket(9999);
        //2.构建一个 DatagramPacket 对象，准备接受数据
        //  UPD协议 一个数据包最大64k
        byte[] buf = new byte[1024];
        DatagramPacket packet = new DatagramPacket(buf, buf.length);
        //调用接受方法  将通过网络传输的 DatagramPacket对象
        // 填充 到 packet对象
        // 当有数据包发送到 本机的9999端口时，就好接收到数据
        // 如果没有数据包发送到 本机 的9999端口，就好阻塞等待。
        System.out.println("接收端A 等待接收数据...");
        socket.receive(packet);
        System.out.println("接收端A 接受到了数据...");
        //4.可以把packet 进行拆包，取出数据  并显示
        int length = packet.getLength();//实际接收到的数据字节长度
        byte[] data = packet.getData();//接收到数据
        String s = new String(data, 0, length);
        System.out.println(s);

        System.out.println("==============");
        System.out.println("A端 发送数据。。");
        //发送数据
        data = "A: hello B   sadasdas".getBytes();
        packet = new DatagramPacket(data, data.length,
                InetAddress.getByName("192.168.0.105"), 8888);
        socket.send(packet);//发送

        //5.关闭资源
        socket.close();
        System.out.println("A端退出");

    }
}    

//UDPSenateB.java文件    
/**
 * 发送端B  ===> 接收端B
 */
public class UDPSenateB {
    public static void main(String[] args) throws IOException {
        //1.创建DatagramSocket 对象，准备在8888端口发送数据
        DatagramSocket socket = new DatagramSocket(8888);
        //2.将需要发送的数据， 封装到 DatagramPacket对象
        byte[] data = "hello 你好你好你好".getBytes();
        //说明：封装的 DatagramPacket对象 data内容字节数组，data.length,主机(IP),端口
        DatagramPacket packet =
                new DatagramPacket(data, data.length, InetAddress.getByName("192.168.0.105"), 9999);
        socket.send(packet);

        System.out.println("================");

        System.out.println("B端 接收数据。；。。");
        //接受数据
        byte[] buf = new byte[1024];
        packet = new DatagramPacket(buf, buf.length);
        System.out.println("接收端B 等待接收数据..");
        socket.receive(packet);
        System.out.println("接收端B 接收到了数据..");
        int length = packet.getLength();
        data = packet.getData();
        String s = new String(data,0,length);
        System.out.println(s);

        //关闭资源
        socket.close();
        System.out.println("B端退出");
    }
}

//输出结果
UDPReceiverA：
    接收端A 等待接收数据...
	接收端A 接受到了数据...
	hello 你好你好你好
	==============
	A端 发送数据。。
	A端退出
UDPSenateB：
    ================
	B端 接收数据。；。。
	接收端B 等待接收数据..
	接收端B 接收到了数据..
	A: hello B   sadasdas
	B端退出
```



##### 反射

![Java反射机制](E:\Java\笔记\image\Java反射机制.png)

反射原理示意图

![Java反射原理示意图](E:\Java\笔记\image\Java反射原理示意图.png)

```java
//反射机制能做什么：
	1、在运行时判断任意一个对象所属的类
    2、在运行时构造任意一个类的对象
    3、在运行时得到任意一个类所具有的成员变量和方法
    4、在运行时调用任意一个对象的成员变量和方法
    5、生成动态代理

//反射相关的主要类        
	1. java.lang.Class:代表一个类，Class对象表示某个类加载后在堆中的对象
	2. java.lang.reflect.Method:代表类的方法,Method对象表示某个类的方法
	3.java.lang.reflect.Field:代表类的成员变量, Field对象表示某个类的成员变量
	4. java.lang.reflect.Constructor:代表类的构造方法, Constructor对象表示构造器
        
//反射优点和缺点
	优点：可以动态的创建和使用对象(也是框架底层核心),使用灵活，没有反射机制。框架技术就失去底层支撑。
	缺点：使用反射基本是解释执行，对执行速度有影响
        
//反射调用优化-关闭访问检查
	1.Method和Field、Constructor对象都有setAccessible()方法
	2.setAccessible作用是启动和禁用访问安全检查的开关    
	3．参数值为true表示反射的对象在使用时取消访问检查，提高反射的效率。参数值为false则表示反射的对象执行访问检查 
```

###### Class类常用方法

|                       方法名                       |                           功能说明                           |
| :------------------------------------------------: | :----------------------------------------------------------: |
|         static Class forName(String name)          |                 返回指定类名name的Class对象                  |
|                object newlnstance()                |         调用缺省构造函数，返回该Class对象的一个实例          |
|                     getName()                      | 返回此Class对象所表示的实体(类、接口、数组类、基本类型等)名称 |
|               Class getSuperClass()                |              返回当前Class对象的父类的Class对象              |
|              Class [] getlnterfaces()              |                   获取当前Class对象的接口                    |
|            ClassLoader getClassLoader()            |                      返回该类的类加载器                      |
|               Class getSuperclass()                |           返回表示此Class所表示的实体的超类的Class           |
|          Constructor[] getConstructors()           |            返回一个包含某些Constructor对象的数组             |
|             Fieldl getDeclaredFields()             |                   返回Field对象的一个数组                    |
| Method getMethod(String name,Class ... paramTypes) |       返回一个Method对象，此对象的形参类型为paramType        |

###### 获取Class类对象方式

```java
//共六种
//第一种：Class.forName(); 多用于配置文件，读取类全路径，加载类
        String classAllPath = "com.company.Car";//通过读取配置文件获取
        Class cls1 = Class.forName(classAllPath);
        System.out.println(cls1);

//第二种：当已知具体的类，直接 类名.class,该方式 最为安全可靠，程序性能最高, 应用场景：用于参数传递
        Class cls2 = Car.class;
        System.out.println(cls2);

//第三种：对象.getClass(). 应用场景：有对象实例
        Car car = new Car();
        Class cls3 = car.getClass();
        System.out.println(cls3);

//第四种：通过类加载器【4种】来获取到类的Class对象
        //(1)先得到类加载器 car
        ClassLoader classLoader = car.getClass().getClassLoader();
        //(2)通过类加载器得到Class对象
        Class cls4 = classLoader.loadClass(classAllPath);
        System.out.println(cls4);

        //cls1 cls2 cls3 cls4 其实是同一个对象
        System.out.println(cls1.hashCode());
        System.out.println(cls2.hashCode());
        System.out.println(cls3.hashCode());
        System.out.println(cls4.hashCode());

//第五种：基本数据(int,char,boolean,float,double,byte,long,short) 按如下方式得到Class类对象
        Class<Integer> integerClass = int.class;
        Class<Character> characterClass = char.class;
        Class<Boolean> booleanClass = boolean.class;
        System.out.println(integerClass);//int
        System.out.println(integerClass.hashCode());

//第六种：基本数据类型对应的包装类，可以通过.TYPE 得到Class类对象
        Class<Integer> type = Integer.TYPE;
        Class<Character> type1 = Character.TYPE;//其他包装类BOOLEAN...本质一样
        System.out.println(type);//int
        System.out.println(type.hashCode());
        System.out.println(type1);
```

###### 哪些类型有Class对象

```java
1．外部类,成员内部类，静态内部类,局部内部类，匿名内部类
2. interface:接口
3.数组
4. enum:枚举    
5. annotation:注解
6.基本数据类型   
7.void
```

###### 类加载

```java
//类加载说明
反射机制是Java实现动态语言的关键，也就是通过反射实现类动态加载。
1、静态加载：编译时加载相关的类，如果没有则报错，依赖性太强
2、动态加载：运行时加载需要的类，如果运行时不用该类，即使不存在该类，也不会报错，降低了依赖性
//类加载时机
1、当创建对象时(new) //静态加载
2、当子类被加载时，父类也加载 //静态加载
3、调用类中的静态成员时 //静态加载
4、通过反射 //动态加载    
```

![Java类加载过程图1](E:\Java\笔记\image\Java类加载过程图1.png)

![Java类加载各阶段完成任务](E:\Java\笔记\image\Java类加载各阶段完成任务.png)

![Java类加载-加载阶段](E:\Java\笔记\image\Java类加载-加载阶段.png)

![Java类加载-连接阶段-验证](E:\Java\笔记\image\Java类加载-连接阶段-验证.png)

![Java类加载-连接阶段-准备](E:\Java\笔记\image\Java类加载-连接阶段-准备.png)

![Java类加载-连接阶段-解析](E:\Java\笔记\image\Java类加载-连接阶段-解析.png)

![Java类加载-Initialization(初始化)](E:\Java\笔记\image\Java类加载-Initialization(初始化).png)

###### 通过反射获取类结构

```java
//获取类的结构信息
//第一组：Java.lang.Class类
	1.getName:获取全类名
    2. getSimpleName:获取简单类名
    3. getFields:获取所有public修饰的属性，包含本类以及父类的
    4. getDeclaredFields:获取本类中所有属性    
    5. getMethods:获取所有public修饰的方法，包含本类以及父类的
    6.getDeclaredMethods:获取本类中所有方法    
    7. getConstructors:获取所有public修饰的构造器，包含本类
    8. getDeclaredConstructors:获取本类中所有构造器   
    9.getPackage:以Package形式返回包信息    
    10.getSuperClass:以Class形式返回父类信息
    11.getlnterfaces:以Class门形式返回接口信息    
    12.getAnnotations:以Annotation[形式返回注解信息    
//第二组：java.lang.reflect.Field类
    1.getModifiers:以int形式返回修饰符
      [说明:默认修饰符是0，public是1，private是2，protected是4,static是8,final是16], public(1) + static (8)=9                              
    2. getType:以Class形式返回类型                             
    3.getName:返回属性名
//第三组：java.lang.reflect.Method类
    1. getModifiers:以int形式返回修饰符                              
    	[说明:默认修饰符是0，public是1，private是2，protected是4static是8,final是16]     
    2.getReturnType:以Class形式获取返回类型
    3.getName:返回方法名     
    4.getParameterTypes:以Class返回参数类型数组                           //第四组: java.lang.reflect.Constructor类
	1.getModifiers: 以int形式返回修饰符
    2.getName:返回构造器名(全类名)
    3.getParameterTypes:以Class[返回参数类型数组                         
```

###### 通过反射创建对象、访问类成员

```java
//创建对象
1.方式一:调用类中的public修饰的无参构造器
2.方式二:调用类中的指定构造器
3.Class类相关方法 
    newlnstance:调用类中的无参构造器,获取对应类的对象
	getConstructor(Class...clazz):根据参数列表，获取对应的public构造器对象     getDecalaredConstructor(Class...clazz):根据参数列表，获取对应的所有构造器对象
4.Constructor类相关方法
	setAccessible:暴破      
    newlnstance(Object...obj):调用构造器  
        
//访问属性
1.根据属性名获取Field对象
Field f = clazz对象.getDeclaredField(属性名);
2.暴破:f.setAccessible(true);/f 是Field
3．访问    
f.set(o,值);/o表示对象syso(f.get(o));//o表示对象
4、注意:如果是静态属性，则set和get中的参数o，可以写成null
    
//访问方法
1．根据方法名和参数列表获取Method方法对象: Method m = clazz.getDeclaredMethod(方法名，XX.class);//得到本类的所有方法
2.获取对象:Object o=clazz.newlnstance0);   
3．暴破:m.setAccessible(true);
4、访问:Object returnValue = m.invoke(o,实参列表);//o 就是对象
5.注意:如果是静态方法，则invoke的参数o，可以写成null!    
```

```java
//反射机制创建实例code
package com.company.reflection;

import java.lang.reflect.Constructor;

/**
 * 通过反射机制创建实例
 */
public class ReflecCreateInstance {
    public static void main(String[] args) throws Exception {
        //1、先获取到User类的Class对象
        Class<?> userClass = Class.forName("com.company.reflection.User");
        //2、通过public的无参构造器创建实例
        Object o = userClass.newInstance();
        System.out.println(o);
        //3、通过public的有参构造器创建实例
        /*
            constructor对象 就是
            public User(String name){
                this.name=name;
            }
         */
        //先得到对应的构造器
        Constructor<?> constructor = userClass.getConstructor(String.class);
        //再创建实例，并传入实参
        Object zs = constructor.newInstance("zs");
        System.out.println("zs="+zs);
        //4、通过非public的无参构造器创建实例
        //先得到私有的构造器对象
        Constructor<?> constructor1 = userClass.getDeclaredConstructor(int.class, String.class);
        //创建实例
        //爆破【暴力破解】，使用反射可以访问private的构造器/方法/属性 ， 反射面前 都是纸老虎
        constructor1.setAccessible(true);
        Object zhangsan = constructor1.newInstance(12, "张三");
        System.out.println("zhangsan="+zhangsan);
    }
}

class User {
    private int age = 10;
    private String name = "lll";

    public User() {
    }

    public User(String name) {
        this.name = name;
    }

    public User(int age, String name) {
        this.age = age;
        this.name = name;
    }

    @Override
    public String toString() {
        return "User{" +
                "age=" + age +
                ", name='" + name + '\'' +
                '}';
    }
}

```

```java
//反射操作属性code
package com.company.reflection;

import java.lang.reflect.Field;

/**
 * 演示反射操作属性
 */
public class ReflecAccessProperty {
    public static void main(String[] args) throws Exception{

        //1.得到Student对应的 Class对象
        Class<?> stuClass = Class.forName("com.company.reflection.Student");
        //2.创建对象
        Object o = stuClass.newInstance();//o的运行类型Student
        System.out.println(o.getClass());//Student
        //3.使用反射得到age 属性对象
        Field age = stuClass.getField("age");
        age.set(o,18);//通过反射来操作属性
        System.out.println(o);//18
        System.out.println(age.get(o));//返回age属性的值

        //4. 使用反射操作name 属性
        Field name = stuClass.getDeclaredField("name");
        //对 name 进行爆破，可以操作 private属性
        name.setAccessible(true);
//        name.set(o,"张三");
        name.set(null,"张三");//因为 name 是 static属性，因此 o 也可以写成null
        System.out.println(o);
        System.out.println(name.get(o));//获取属性值
        System.out.println(name.get(null));//获取属性值，要求name是static

    }
}

class Student{
    public int age;
    private static String name;

    public Student(){
    }

    @Override
    public String toString() {
        return "Student{" +
                "age=" + age + ",name="+name+
                '}';
    }
}

```

```java
//通过反射调用方法code
package com.company.reflection;

import java.lang.reflect.Method;

/**
 * 演示通过反射调用方法
 */
public class ReflecAccessMethod {
    public static void main(String[] args) throws Exception{
        //1.得到Boss类对应的Class对象
        Class<?> bossCls = Class.forName("com.company.reflection.Boss");
        //2.创建对象
        Object o = bossCls.newInstance();
        //3.调用public的hi方法
//        Method hi = bossCls.getMethod("hi",String.class);//OK
        // 1、得到hi方法对象
        Method hi = bossCls.getDeclaredMethod("hi",String.class);//OK
        // 2、调用
        hi.invoke(o,"你好");

        //4.调用 private static  方法
        // 1.得到 say方法对象
        Method say = bossCls.getDeclaredMethod("say", int.class, String.class, char.class);
        // 2.因为say方法时 private的 需要爆破
        say.setAccessible(true);
        System.out.println(say.invoke(o,19,"张三",'男'));
        // 3.因为 say方法 是static 还可以这样调用
        System.out.println(say.invoke(null,65,"李四",'男'));

        //5. 在反射中，如果方法有返回值，统一返回Object  但是它的运行类型和方法定义的返回类型一致
        Object reVal = say.invoke(null, 20, "维维", '女');
        System.out.println("reVal的运行类型="+reVal.getClass());

    }
}
class Boss{
    public int age;
    private static String name;

    public Boss(){
    }

    private static String say(int n,String s,char c){
        return n + " " + s + " " + c;
    }

    public void hi(String s){
        System.out.println("hi"+s);
    }

}
```



##### ★JDBC连接池★

![JavaJDBC概述](E:\Java\笔记\image\JavaJDBC概述.png)

![JavaJDBC原理示意图](E:\Java\笔记\image\JavaJDBC原理示意图.png)

![JavaJDBCAPI](E:\Java\笔记\image\JavaJDBCAPI.png)

![JavaResultSet结果集](E:\Java\笔记\image\JavaResultSet结果集.png)

![JavaStatement](E:\Java\笔记\image\JavaStatement.png)

![JavaPreparedStatement](E:\Java\笔记\image\JavaPreparedStatement.png)

![Java预处理好处](E:\Java\笔记\image\Java预处理好处.png)

![JavaJdbcAPI2](E:\Java\笔记\image\JavaJdbcAPI2.png)

![Java事务](E:\Java\笔记\image\Java事务.png)

![Java批处理](E:\Java\笔记\image\Java批处理.png)

![Java数据库连接池-传统连接的问题](E:\Java\笔记\image\Java数据库连接池-传统连接的问题.png)

![Java数据库连接池](E:\Java\笔记\image\Java数据库连接池.png)

![Java数据库连接池种类](E:\Java\笔记\image\Java数据库连接池种类.png)

![JavaApache-DBUtils](E:\Java\笔记\image\JavaApache-DBUtils.png)

![JavaDAO和增删改查调用方法-BasicDao](E:\Java\笔记\image\JavaDAO和增删改查调用方法-BasicDao.png)

​	
