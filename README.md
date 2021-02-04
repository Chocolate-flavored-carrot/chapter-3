   # 3.4.4_Bool类型

_Bool类型用于表示布尔值，即逻辑值false和true。因为C语言用值1表示true,值0表示false，所以_Bool类型实际上也是一种整数类型。原则上它只占一位存储空间。

3.4.5可移植类型：stdint.h和inttypes.h
C99新增了两个头文件stdint.h和inttypes.h，以确保C语言的类型在各系统中的功能相同。
例如在32位的系统中，头文件会把int32_t作为int的别名。不同的系统也可以定义相同的类型名。
例如：在int为16位、long为32位的系统中系统会把int32_t作为long的别名。然后使用int32_t类型编写程序，并包含stdint.h头文件时，编译器会把int或者long替换成系统匹配的类型。
因为printf()打印要求与相应的转换说明匹配。如果要打印int32_t类型的值，有些定义使用%d,而有些使用%ld，针对这一情况提供了一些字符串宏来显示可移植类型。例如，inttypes.h头文件中定义了
PRId32字符串宏，代表打印32位有符号值的合适转换说明(如d或l)。


//altnames.c 可移植整数类型名
#include <stdio.h>
#include <inttypes.h>   //支持可移植类型
int main(void)
{
	int32_t me32;    //me32是一个32位有符号整型变量

	me32 = 45933945;
	printf("First, assume int32_t is int:");
	printf("me32 = %d\n",me32);
	printf("Next, let's not make any assumption.\n");
	printf("Instead,use a \"macro\"form inttypes.h: ");//程序中用了转义序列来显示显示双引号。
	printf("me32 = %" PRId32 "\n", me32);/*参数PRId32被定义在inttypes.h中的“d”替换，因而这条语句等价于：
										 printf("me32 = %" d"\n", me32);在C语言中可以把多个连续的字符组合成一个字符串，
										 所以这条语句有等价于：printf("me32 = %d\n", me32);*/
	getchar();
	return 0;

}
运行结果：
First, assume int32_t is int:me32 = 45933945 //假设int32_t是整数类型
Next, let's not make any assumption. //接下来，我们不要做任何假设。
Instead,use a "macro"form inttypes.h: me32 = 45933945    //而是从inttypes 中使用“宏”的形式。

3.4.6 floa、double和long double
前面提到过，浮点数累死你个能表示包括小数在内更大范围的数。浮点数的表述类似于科学技术法。
指数计数法中的e代表10的指数。
1.声明浮点型变量
float noah， jonah；
double trouble;
float planck = 6.63e-34;
long double gnp;
2.浮点型常量
在代码中，可以用多种形式书写浮点型常量。浮点型常量的基本形式是：有符号的数字（包括小数点），后面紧跟e或E，最后是一个有符号数表示10的指数。
-1.56E+12
正号可以省略。可以没有小数点或指数部分，但是不能同时省略。可以省略小数部分，也可省略整数部分，但是不能同时省略。
不要在浮点型常量中间加空格：1.56 E+12 错误！！

在浮点数后面加上f或者F编译器会将浮点型常量看做float类型例如2.3f，使用L或l后缀成为龙double类型，没有后缀的浮点型常量是double类型。
double类型精度较高，但是运行速度会变慢。
3.打印浮点值
printf()函数使用%f转换说明打印十进制记数法的float和double类型的浮点数，用%e打印指数记数法的浮点数。
如果系统支持十六进制格式的浮点数，可用a和A分别代替e和E。
打印long double类型要使用%Lf %Le %La
注：十六进制a等于十进制

//showf_pt.c --以两种方式显示float类型的值
#include <stdio.h>
int main(void)
{
	float aboat = 32000.0;
	double abet = 2.14e9;
	long double dip = 5.32e-5;

	printf("%f can be written %e\n", aboat, aboat);
	//下一行要求编译器支持c99或其中的相关特性
	printf("And it's %a in hexadecimal, powers of 2 notation\n",aboat);
	printf("%f can be written %e\n", abet, abet);
	printf("%Lf can be written %Le\n",dip,dip);

	getchar();
	return 0;

}
输出结果：
32000.000000 can be written 3.200000e+04
And it's 0x1.f400000000000p+14 in hexadecimal, powers of 2 notation
2140000000.000000 can be written 2.140000e+09
0.000053 can be written 5.320000e-05
注：%a是以指数形式输出一个浮点数(十六进制)。

该程序只演示了默认的输出效果。下一章将介绍如何通过设置字段宽度和小数位数来控制输出格式。

4.浮点值得上溢和下溢
假设系统的最大float类型值是3.4E38,编写如下代码：
float toobig=3.4E38 * 100.0f;
printf("%e\n", toobig);
会发生上溢。输出的值应该是inf 或者infinity。
下溢：
