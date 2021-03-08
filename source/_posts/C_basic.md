---
title: C语言复习笔记
author:
	name: 覃浩
	avatar: https://cdn.jsdelivr.net/gh/queen999/ImageHosting//imagesavatar.jpg
	url: https://imqinhao.cn
categories: C语言
date: 2020-12-15 20:13:14
comments: true
---

第一章：

- C语言的发展历史
- C语言的特点及程序结构

第二章：

- 标记
- 类型
- 运算符与表达式

第三章：

- 编程小练习

<!-- more -->

# 第一章 

## C语言程序的基本结构

- C语言程序是<kbd>由函数构成</kbd>的。一个C语言程序<kbd>至少包含一个main函数</kbd>。

- C语言程序总是<kbd>从main函数开始执行</kbd>。

- 为了增强程序的可读性，通常书写C语言程序时应遵循以下规则：

  > 一行内仅写一条语句
  >
  > 正反大括号分别各占一行
  >
  > 每对大括号上下对齐
  >
  > 语句采用缩进格式，错落有致

- 每条语句的最后必须有一个分号，分号是C语句的组成部分。

- C语言本身没有输入/输出语句，输入/输出的操作由<kbd>scanf</kbd>和<kbd>printf</kbd>等函数来完成。

- 可以用/* ····· */  或者  // ·······  在C语言程序中加注释，以增强程序的可读性。

## C语言程序的上机执行过程

编写好的C语言程序要经过<kbd>编辑（输入）</kbd> ，<kbd>编译</kbd> 和 <kbd>连接</kbd> 后才能形成可执行的程序。

C语言程序的上机执行过程一般要经过四个步骤：<kbd>编辑（Edit）</kbd>、<kbd>编译（compile）</kbd>、<kbd>连接（link）</kbd> 和 <kbd>运行</kbd> 。

![C程序上机执行过程](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/C%E7%A8%8B%E5%BA%8F%E4%B8%8A%E6%9C%BA%E6%89%A7%E8%A1%8C%E6%96%87%E4%BB%B6.png)

### 编辑（Edit）

编辑指<kbd>源程序的输入</kbd>，对应的文件称为源文件，其拓展名为"<kbd>.c</kbd>"。

### 编译（compile）

编译是使用编译器（compiler）<kbd>将源文件转换为目标文件的过程</kbd>。编译器对源程序进行语法检查，当发现错误时，将错误的类型和所在位置显示出来，以帮助程序员修改源程序中的错误。目标文件的扩展名为"<kbd>.obj</kbd>"。

### 连接（link）

连接是<kbd>将目标文件和其他分别进行编译生成的目标文件</kbd>（如果有的话）以及<kbd>库函数连接生成可执行文件的过程</kbd>。可执行文件的扩展名为"<kbd>.exe</kbd>"。

### 运行

运行时将可执行文件投入运行，以获取程序处理的结果。如果程序运行结果不正确，则回到第一步，重新对程序进行编辑、编译、连接和运行。直到取得预期结果为止。

# 第二章

## 标记



> 标记（token）是具有唯一含义的语言的最小单位，分为五种：<kbd>关键字（keyword）</kbd>、<kbd>标识符（identifier）</kbd>、<kbd>常量（constant）</kbd>、<kbd>串字面量（string  literal）</kbd>以及<kbd>标点符号（punctuator）</kbd>。

### 关键字

关键字也称为保留字，C语言共有44个关键字：

| auto           | break         | case               | char              | const        |
| :------------- | :------------ | :----------------- | :---------------- | :----------- |
| **continue**   | **default**   | **do**             | **double**        | **else**     |
| **enum**       | **extern**    | **float**          | **for**           | **goto**     |
| **if**         | **inline**    | **int**            | **long**          | **register** |
| **restrict**   | **return**    | **short**          | **signed**        | **sizeof**   |
| **static**     | **struct**    | **switch**         | **typedef**       | **union**    |
| **unsigned**   | **void**      | **volatile**       | **while**         | **_Alignas** |
| **_Alignof**   | **_Atomic**   | **_Bool**          | **_Complex**      | **_Generic** |
| **_Imaginary** | **_Noreturn** | **_Static_assert** | **_Thread_local** |              |

### 标识符

标识符由<kbd>小写字母</kbd>、<kbd>大写字母</kbd>、<kbd>数字</kbd>、<kbd>下划线</kbd>、<kbd>通用字符名</kbd>或<kbd>实现定义的字符</kbd>构成，且<kbd>数字不能作为标识符的第一个字符</kbd>，<kbd>关键字不能作为标识符</kbd>。

C语言<kbd>大小写敏感</kbd>。

C语言对标识符的最大长度没有具体的限制，VC允许标识符的最大长度为<kbd>247</kbd>个字符。

通常，应该选择相应的英文单词或其缩写作为标识符，做到<kbd>见名知义</kbd>。

### 常量

> <font color="red">在程序运行过程中，其值不变的量称为常量。常量分为四种类型。</font>

---

#### 整数常量

整数常量<font color="red">只包括正整数和零，不包括负整数</font>。

整数常量分为<kbd>十进制整数常量</kbd>、<kbd>八进制整数常量</kbd>和<kbd>十六进制整数常量</kbd>。

十进制整数常量由 0~9 组成，且以非零数字开头，如 123 、 1000 。

八进制整数常量由 0~7 组成，且以 0 开头，或者只有一个0，如 017 、 0 。

十六进制整数常量由 0~9 、A~F（或 a~f ）组成，且以 0x 或 0X 开头，如0x1a 、 0XD5 。

```c
#include <stdio.h>
int main(void)
{
        printf("sum = %d \n",123 + 012 + 0x12);
        return 0;
}
```

---

#### 浮点常量

计算机中的浮点数只能<font color="red">近似地表示值在某个范围之内的有理数和一些特殊值</font>，如NAN（非数值）、+INF（正无穷大）、-INF（负无穷大）等。

浮点常量是<font color="red">非负</font>的浮点数，其十进制书写形式有以下两种：

1. 小数点表示法

> 由数字 0 ~9 和小数点组成，必须有小数点。如果小数点左边为0，则 0 可省略；如果小数点右边为 0 ，则 0 可省略。
>
> 例如： <kbd>5.20</kbd>	<kbd>520.0</kbd>	<kbd>520.</kbd>	<kbd>0.520</kbd>	<kbd>.520</kbd>	<kbd>0.0</kbd>	<kbd>0.</kbd>	<kbd>.0</kbd>

2. 指数表示法

> 第一种形式：
>
> ```
> 					十进制整数常量E符号位		十进制整数常量
> ```
>
> 第二种形式：
>
> ```
> 				浮点常量的小数表示法E符号位		十进制整数常量
> ```

<font color="red">其中，E 也可以写成 e ， “符号位” 即正负号是可选的。</font>

---

#### 枚举常量

> 枚举常量是类型为 int 的标识符。

---

#### 字符常量

字符常量分为整数字符常量和宽字符常量。

```c
#include <stdio.h>
int main(void)
{
        printf("%d %d %d %d\n", 'A' , 'b' + 2 , '0' , '1' + 3);
        return 0;
}
```

> 分析 ASCII 码表，可以得出四条规则：
>
> （1）数字字符 0~9 的 ASCII 码值是连续递增的。
>
> （2）大写字母 A~Z 的ASCII 码值是连续递增的。
>
> （3）小写字母 a~z 的 ASCII 码值是连续递增的。
>
> （4）大写字母的 ASCII 码比相应小写字母的 ASCII 码值小 32 。

| 转义序列 |                          含义                           | 十进制ASCII码值 |
| :------: | :-----------------------------------------------------: | :-------------: |
|    \a    |                       响铃(alert)                       |        7        |
|    \b    |                     退格(backspace)                     |        8        |
|    \f    |                  走纸换页(form  feed)                   |       12        |
|    \n    |          换行(new  line)，光标移到下一行的行首          |       10        |
|    \r    |      回车(carriage  rerurn)，光标移到当前行的行首       |       13        |
|    \t    | 水平制表(horizontal  tab)，光标移到当前行的下一个制表位 |        9        |
|    \v    |                 垂直制表(verical  tab)                  |       11        |

### 串字面量

串字面量分为三种：<kbd>字符串字面量</kbd>、<kbd>UTF-8串字面量</kbd> 和 <kbd>宽串字面量</kbd>。

字符串字面量是用一对双引号括起来的零个或多个字符。在翻译的第七个阶段，空字符即'\0'被加到字符串字面量的末尾，然后字符串字面量以数组元素类型为 char 的数组的形式存储在内存中。

如果字符串字面中不含'\0'，则该字符串字面量也称为字符串。

字符串的长度是指空字符前的字符在内存中所占的字节数。因此，长度为 n 的字符串，在内存中占 n+1 个字节。

<font color="red">不要将字符常量与字符串相混淆。例如，'z' 是字符常量，占 4 个字节；而 "z" 是字符串，占 2 个字节。</font>

## 类型

类型分为两种：

> 对象类型（object  type）：用于描述对象
>
> 函数类型（function  type）：用于描述函数

### 基本类型

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/%E5%9F%BA%E6%9C%AC%E7%B1%BB%E5%9E%8B.png)

### 枚举类型

一组命名的整数常量值构成枚举（enumeration），不同的枚举构成不同的枚举类型。

### 空类型

空类型的值的集合是空集，空类型是不完整对象类型，而且不可能是完整的。

### 派生类型

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/%E6%B4%BE%E7%94%9F%E7%B1%BB%E5%9E%8B.png)

## 变量与常用类型说明符

### 变量

常用类型说明符有四种，分别是 <kbd>int </kbd>、<kbd>char</kbd>、<kbd>float</kbd> 和 <kbd>double</kbd> 。

变量必须<font color="red">先声明后使用</font>。

### 常用类型

![](https://cdn.jsdelivr.net/gh/queen999/ImageHosting/images/%E5%B8%B8%E7%94%A8%E7%B1%BB%E5%9E%8B.png)

在 0 ~ 2147483647 范围内的整数常量，其类型是 int 。

char 类型在输入时，两个数字字符之间不能加空格符，如果加了空格符，char 类型的变量获取的是空格符，而不是数字字符。

双精度浮点类型 double 比单精度浮点类型 float 精度更高，表示数据的范围更大。

浮点常量默认是 double 类型，在浮点常量后加后缀 f 或 F 则是 float 类型。

在没有特殊要求的情况下，程序设计中声明浮点常量，建议使用 double 类型。

## 运算符与表达式

### 表达式

表达式是由运算符和运算对象构成的序列。

表达式具有以下一个或多个功能：

1. 描述一个值的计算
2. 指定一个对象或一个函数
3. 产生副作用

根据运算符的运算对象的数量，可将运算符分为以下三种：

1. 单目运算符：只有一个运算对象
2. 双目运算符：有两个运算对象
3. 三目运算符：有三个运算对象

### 乘法类运算符

| 乘法运算符 | 除法运算符 | 模运算符 |
| :--------: | :--------: | :------: |
|     *      |     /      |    %     |

<font color="red">乘法类运算符有三个，都是双目运算符。</font>

### 加法类运算符

| 加法运算符 | 减法运算符 |
| :--------: | :--------: |
|     +      |     -      |

<font color="red">加法类运算符有两个，都是双目运算符。</font>

### sizeof运算符

>sizeof 运算符是单目运算符，表达式的值是运算对象所占用内存大小（按字节计算），其运算对象是表达式或用小括号括起来的类型名。

<font color="red"> char 类型在内存中占 1 个字节。</font>

<font color="red">int 类型在内存中占 4 个字节。</font>

<font color="red">float 类型在内存中占 4 个字节。</font>

<font color="red">double 类型在内存中占 8 个字节。</font>

### 一元加运算符与一元减运算符

一元加运算符 + 是单目运算符，表达式的值是运算对象的值。

一元减运算符 - 是单目运算符，表达式的值是运算对象的相反数。

---

整数提权实例：

```c
#include <stdio.h>
int main(void)
{
        char ch;
        printf("sizeof +ch = %d\n",sizeof +ch);
        printf("sizeof ch = %d\n",sizeof ch);
        printf("sizeof -ch = %d\n",sizeof -ch);
        printf("sizeof ch = %d\n",sizeof ch);
        return 0;
}
```

运行结果：

```
sizeof +ch = 4
sizeof ch = 1
sizeof -ch = 4
sizeof ch = 1
```

<font color="red">变量 ch 是 char 类型，在内存中占 1 个字节，整数提升将 ch 的值转换为 int 类型的值，因此，表达式 +ch 和 -ch 的类型都是 int ，在内存中占 4 个字节。</font>

> <font color="LimeGreen">注意：变量 ch 的类型并没有改变，仍然是 char 类型。</font>

### 常用算术转换

其中一个运算对象是 double 类型，另一个运算对象的值被转换为 double 类型的值。

如果以上条件不满足，并且其中一个运算对象是 float 类型，另一个运算对象的值被转换为 float 类型的值。

如果以上两个条件都不满足，对两个运算对象进行整数提升，即 char 类型运算对象的值被转换为 int 类型的值。

> <font color="red">运算对象的类型并没有改变。</font>

# 第三章

## 编程练习1

输入三个整数，求其平均值。

```c
#include <stdio.h>
int main(void)
{
        // 输入三个整数，求其平均值
        int num1;
        scanf("%d",&num1);
        int num2;
        scanf("%d",&num2);
        int num3;
        scanf("%d",&num3);
        int average = (num1 + num2 + num3)/3;
        printf("( %d + %d + %d) ÷ 3 = %d\n",num1,num2,num3,average);
        return 0;
}
```

## 编程练习2

输入圆的半径，求圆的周长和面积。

```c
#include <stdio.h>
int main(void)
{
        int r;
        double PI = 3.14;
        double c;
        double s;
        //用户输入半径
        scanf("%d",&r);
        //圆的周长
        c = PI * (2 * r);
        //圆的面积
        s = PI * (r * r);
        //输出
        printf("圆的周长为：%.2lf，圆的面积为：%.2lf。\n",c,s);
        return 0;
}
```

## 编程练习3

输入学生的相关信息：学号（int类型）、年龄（int类型）、性别（char 类型，'M'代表男生，'F'代表女生）和五门课程的成绩（double 类型）；输出该学生的相关信息：学号、年龄、性别、各科成绩和平均成绩。

```c
#include <stdio.h>
int main(void)
{
        // 输入学生的相关信息
        // 学号：int类型
        // 年龄：int类型
        // 性别：char类型（M：男生，N：女生）
        // 五门课程的成绩：double类型

        // 学号
        int id;
        // 年龄
        int age;
        // 性别
        char sex;
        // 成绩1
        double score1;
        // 成绩2
        double score2;
        // 成绩3
        double score3;
        // 成绩4
        double score4;
        // 成绩5
        double score5;
        // 获取输入信息
        printf("请输入学号：");
        scanf("%d",&id);
        printf("请输入年龄：");
        scanf("%d",&age);
        printf("请输入性别(男生：M  女生：F）：");
        getchar();
        scanf("%c",&sex);
        printf("请输入语文成绩：");
        scanf("%lf",&score1);
        printf("请输入数学成绩：");
        scanf("%lf",&score2);
        printf("请输入英语成绩：");
        scanf("%lf",&score3);
        printf("请输入物理成绩：");
        scanf("%lf",&score4);
        printf("请输入化学成绩：");
        scanf("%lf",&score5);
        // 计算平均分
        double average = (score1 + score2 + score3 + score4 + score5) / 5;
        // 输出成绩信息
        printf("学号\t\t年龄\t\t性别\t\t语文\t\t数学\t\t英语\t\t物理\t\t化学\t\t平均分\t\t\n");
    printf("%d\t\t%d\t\t%c\t\t%.1lf\t\t%.1lf\t\t%.1lf\t\t%.1lf\t\t%.1lf\t\t%.1lf\t\t\n",id,age,sex,score1,score2,score3,score4,score5,average);
        return 0;
}
```

## 编程练习4

输入一个四位正整数，求其各位数字之和。例如：1357的各位数字之和为1 + 3 + 5 + 7 = 16 。

```c
#include <stdio.h>
int main(void)
{
        // 输入一个四位正整数，求其各位数字之和。

        int number;
        // 获取用户输入
        scanf("%d",&number);
        // 计算第一位数
        int num1 = number / 1000;
        printf("第一位数是：%d\n",num1);
        // 计算第二位数
        int num2 = number % 1000 / 100;
        printf("第二位数是：%d\n",num2);
        // 计算第三位数
        int num3 = number % (num1 * 1000 + num2 * 100) /10;
        printf("第三位数是：%d\n",num3);
        // 计算第四位数
        int num4 = number % (num1 * 1000 + num2 * 100 + num3 * 10);
        printf("第四位数是：%d\n",num4);

        // 计算各个数字之和
        int result = num1 + num2 + num3 + num4;
        printf("%d + %d + %d + %d = %d\n",num1,num2,num3,num4,result);

        return 0;
}
```

