编写程序时，应注意合理选择所需的变量及其类型。
把一个类型的数值初始化给不同类型的变量时，编译器会把值转换成与变量匹配的类型，这会导致部分数据的丢失。
int cost=12.99 用double类型的值初始化int类型的变量
float pi=3.1415926536; 用double类型的值初始化float类型的变量
第一个声明cost值是12.c编译器把浮点数转换为整数时，直接丢弃小数点后的部分，不会四舍五入。
第二个声明会损失精度，因为c只保证了float类型前6位的精度。

3.6参数和陷阱
//bad count.c 参数错误的情况
#include <stdio.h>
int main(void)
{
	int n = 4;
	int m = 5;
	float f = 7.0f;
	float g = 8.0f;

	printf("%d\n", n, m);//参数太多
	printf("%d %d %d\n",n);//参数太少
	printf("%d %d\n", f, g);//类型不匹配

	getchar();
	return 0;

}
运行结果：
4
4 987171 987171
0 1075576832
注意：用%d显示float类型的值，其值不会被转换成int类型。
# 转义序列示例
// escape.c 使用转义序列
#include <stdio.h>
int main(void)
{
	float salary;

	printf("\aEnter your desired monthly salary:");
	printf(" $_______\b\b\b\b\b\b\b");
	scanf_s("%f", &salary);
	printf("\n\t$%.2f a month is $%.2f a year.", salary, salary * 12.0);
	printf("\rGee!\n");

	getchar();
	getchar();
	return 0;

}
结果：
Enter your desired monthly salary: $1500___

Gee!    $1500.00 a month is $18000.00 a year.
首先第一个print函数\a发出警报再打印
第二个有七个下划线有七个\b退格。
\r是使得光标回到当前行的起始处。

刷新输出
printf()何时吧输出发送到屏幕上？
最初printf语句会把输出发送到缓冲区，然后再发送到屏幕上。
何时将缓冲区内容发送到屏幕？
当缓冲区满、遇到换行字符或需要输入的时候（从缓冲区把数据发送到屏幕或文件被称为刷新缓冲区）
