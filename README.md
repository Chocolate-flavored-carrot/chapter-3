# chapter-3

#include <stdio.h>
int main(void)
{
	float weight;//你的体重
	float value;//相等重量的白金价值

	printf("Are you worth your weight in platinum?\n");
	printf("Let's check it out.\n");
	printf("Please enter your weight in pounds:");
	
	//获取用户的输入
	scanf_s("%f",&weight);
	//假设白金的价格是每盎司$1700 
	//14.5833是把英镑常衡盎司转换为金衡盎司
	value = 1700.0 * weight * 14.5833;
	printf("Your weight in platinum is worth $%.2f.\n", value);
	printf("You are easily worth that! If platinum prices drop,\n");
	printf("eat more to maintain your value.\n");
	
	getchar();/*此处用了两个getchar函数，它读取下一个输入字符，因此程序会等待用户输入。第一个getchar读取换行符，第二个
			  让程序暂停，等待输入。*/       
	getchar();

	return 0;
}
分析；
1.新引入了声明变量浮点数类型（float），可以储存带小数的数字。
2.为了打印新类型的变量，在printf()中使用%f来处理浮点值，%.2f中的.2是指定输出的浮点数只显示小数点后两位。（%d是整数的占位符）
3.scanf_s()函数用于读取键盘的输入。%f说明scanf_s（）是要读取用户从键盘上输入的浮点数，&weight告诉scanf_s把输入的值赋给weight的变量
4.本程序突出了它的交互性。
