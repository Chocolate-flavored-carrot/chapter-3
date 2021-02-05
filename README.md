关键字：
基本数据类型由11个关键字组成：int long short unsigned char float double signed _Bool _Complex和 Imaginary。

# 有符号整型：
有符号整型可用于表示正整数和负整数。
int——系统给定的基本整数类型。C语言规定int类型不小于16位。
short或short int——最大的short类型整数小于或等于最大的int类型整数。C语言规定short类型至少占16位
long 或long int——该类型可表示的整数大于或等于最大的int类型整数。C语言规定long类型至少占32位。
long long或者long long int——该类型可表示的整数大于或等于最大的long类型整数。long long 类型至少占64位。
一般而言，long类型占用的内存比short类型大，int类型的宽度要么和long类型相同，要么和short类型相同。
# 无符号类型
无符号类型只能用于表示零和正整数，因此无符号整型可表示的正整数比有符号整型的大。
