关键字：
基本数据类型由11个关键字组成：int long short unsigned char float double signed _Bool _Complex和 Imaginary。

# 有符号整型：
有符号整型可用于表示正整数和负整数。
int——系统给定的基本整数类型。C语言规定int类型不小于16位。
short或short int——最大的short类型整数小于或等于最大的int类型整数。C语言规定short类型至少占16位
long 或long int——该类型可表示的整数大于或等于最大的int类型整数。C语言规定long类型至少占32位。
long long或者long long int——该类型可表示的整数大于或等于最大的long类型整数。long long 类型至少占64位。
一般而言，long类型占用的内存比short类型大，int类型的宽度要么和long类型相同，要么和short类型相同。
# 无符号整型
无符号整型只能用于表示零和正整数，因此无符号整型可表示的正整数比有符号整型的大。在整数类型前加上关键字unsigned表明该类型是无符号整型。

# 字符类型
可打印出来的符号（如A、&和+）都是字符。char类型表示一个字符要占用1字节内存。
char———字符类型的关键字。在需要时可在前面加上关键字signed或者unsigned来指明具体使用哪一种类型。

# 布尔类型
布尔值表示true和false。C语言用1表示true，0表示false。
_Bool——布尔类型的关键字。布尔类型是无符号int类型，所占用的空间只要能存储0或1即可。

# 实浮点类型
实浮点类型可表示正浮点数和负浮点数。
float——系统的基本浮点类型，可精确表示至少6位有效数字。
double——存储浮点数的范围（可能）更大，能比float类型更多的有效数字（至少10位，通常会更多）和更大的指数。
long double——存储浮点数的范围比double更大，能表示比double更多的有效数字和更大的指数。

# 复数和虚数浮点数
虚数类型是可选的类型。复数的实部和虚部类型都基于实浮点类型来构成。
float_Complex
double_Complex
long double_Complex
float _Imaginary
double _Imaginary
long double _Imaginary

小结：如何声明简单变量
1.选择需要的类型
2.使用有效的字符给变量起一个变量名
类型说明符由一个或者多个关键字组成
3.可以同时声明形同类型的多个变量，用逗号分隔各变量名
4.在生命的同时还可以初始化变量

3.4.9类型大小
如何知道当前系统指定类型的大小是多少呢？
//typesize.c 打印类型大小
#include <stdio.h>
int main(void)
{
	//c99为类型大小提供%zd转换说明
	printf("Type int has a size of %zd bytes.\n", sizeof(int));
	printf("Type char has a size of %zd bytes.\n", sizeof(char));
	printf("Type long has a size of %zd bytes.\n", sizeof(long));
	printf("Type long long has a size of %zd bytes.\n",sizeof(long long));
	printf("Tyoe double has a size of %zd bytes.\n",sizeof(double));
	printf("Type long double has a size of %zd bytes.\n", sizeof(long double));
	
	getchar();

	return 0;
	
}
运行结果：
Type int has a size of 4 bytes.
Type char has a size of 1 bytes.
Type long has a size of 4 bytes.
Type long long has a size of 8 bytes.
Tyoe double has a size of 8 bytes.
Type long double has a size of 8 bytes.

sizeof是C语言的内置运算符，以字节为单位给出指定类型的大小。c99和c11的编译器可用%u或%lu代替%zd
