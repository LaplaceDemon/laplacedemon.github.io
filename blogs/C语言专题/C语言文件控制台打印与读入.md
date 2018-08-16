## 打印数据

### putchar 打印字符

```c
int putchar(int char)
```

把参数 char 指定的字符（一个无符号字符）写入到标准输出 stdout 中。

例：

```c
#include <stdio.h>

int main(int argc, char **argv) {
	putchar('h'); putchar('e'); putchar('l'); putchar('l'); putchar('o');
	putchar(' ');
	putchar('w'); putchar('o'); putchar('r'); putchar('l'); putchar('d');
	return 0;
}
```



### puts 打印字符串

```c
int puts(char*string);
```

打印字符串。要注意。puts最后自动为字符串换行。

例：打印字符串。

```c
#include <stdio.h>

int main(int argc, char **argv) {
	puts("hello");
	puts("world");
	return 0;
}
```

打印：

```
hello
world
```





### printf 打印带格式的字符串

打印数据。

| *specifier*  | Output                                                       | Example        |
| ------------ | ------------------------------------------------------------ | -------------- |
| `d` *or* `i` | 带符号十进制整数（Signed decimal integer）                   | `392`          |
| `u`          | 无符号十进制整数（Unsigned decimal integer）                 | `7235`         |
| `o`          | 无符号八进制整数（Unsigned octal）                           | `610`          |
| `x`          | 无符号十六进制整数（Unsigned hexadecimal integer）           | `7fa`          |
| `X`          | 无符号十六进制整数（大写）（Unsigned hexadecimal integer (uppercase)） | `7FA`          |
| `f`          | 十进制浮点数（Decimal floating point, lowercase）            | `392.65`       |
| `F`          | 十进制浮点数（Decimal floating point, uppercase）            | `392.65`       |
| `e`          | 科学技术法，e小写。（Scientific notation (mantissa/exponent), lowercase） | `3.9265e+2`    |
| `E`          | 科学技术法，E大写。（Scientific notation (mantissa/exponent), uppercase） | `3.9265E+2`    |
| `g`          | Use the shortest representation: `%e` or `%f`                | `392.65`       |
| `G`          | Use the shortest representation: `%E` or `%F`                | `392.65`       |
| `a`          | 16进制浮点数，小写（Hexadecimal floating point, lowercase）  | `-0xc.90fep-2` |
| `A`          | 16进制浮点数，大写 （Hexadecimal floating point, uppercase） | `-0XC.90FEP-2` |
| `c`          | 字符（Character）                                            | `a`            |
| `s`          | 字符串（String of characters）                               | `sample`       |
| `p`          | 指针地址（Pointer address）                                  | `b8000000`     |
| `n`          | 空，什么也不打印。（Nothing printed.）                       |                |
| `%`          | 打印出`%`                                                    | `%`            |

 例：打印各种类型

```c
#include <stdio.h>

int main(void) {
	// 打印整数
	int x = 15;
	printf("x = %d,十进制\n",x);
	printf("x = %i，十进制\n",x);
	printf("x = %o，八进制\n",x);
	printf("x = %x，十六进制\n",x);
	printf("x = %X，十六进制\n",x);

	// 打印浮点数
	double y = 3.1415926535897932;
	printf("y = %f，单精度浮点数\n",y);
	printf("y = %F，单精度浮点数\n",y);
	printf("y = %10.20f，十六进制浮点数\n",y);
	printf("y = %e，单精度浮点数，科学技术法\n",y);
	printf("y = %E，单精度浮点数，科学技术法\n",y);
	printf("y = %a，十六进制浮点数\n",y);
	printf("y = %A，十六进制浮点数\n",y);

	// 打印字符串
	char * str = "abcdefghijklmn";
	printf("str = %s，字符串\n",str);

	// 打印字符
	printf("str[0] = %c，字符\n",str[0]);
    
    // 打印%
	printf("%%d\n");

	// 打印指针
	int * px = &x;
	printf("the address of the x is %p\n",px);
}

```

打印内容：

```
x = 15,十进制
x = 15，十进制
x = 17，八进制
x = f，十六进制
x = F，十六进制
y = 3.141593，单精度浮点数
y = 3.141593，单精度浮点数
y = 3.14159265358979311600，十六进制浮点数
y = 3.141593e+00，单精度浮点数，科学技术法
y = 3.141593E+00，单精度浮点数，科学技术法
y = 0x1.921fb54442d18p+1，十六进制浮点数
y = 0X1.921FB54442D18P+1，十六进制浮点数
str = abcdefghijklmn，字符串
str[0] = a，字符
%d
the address of the x is 0x7ffee2e2d30c
```



## 获取数据

### getchar 获取字符

```c
int getchar(void)
```

例：

```c 
#include <stdio.h>

int main(int argc, char **argv) {
	puts("please input a char:");
	int c = getchar();
	printf("you input %c",c);
	return 0;
}
```



### gets  获取一行字符串

```c
char * gets(char *str) 
```

例：

```c
#include <stdio.h>

int main(int argc, char **argv) {
	char str[64];
	puts("please input a word:");
	gets(str);
	printf("you input:%s",str);
	return 0;
}
```



### scanf 读取带格式的字符串中的数据

```c
int scanf(const char *format, ...)
```

例：

```c
#include <stdio.h>

int main(int argc, char **argv) {
	char ch,s1[20],s2[20];
	scanf("%s",s1);
	scanf("%s",s2);
	scanf("%c",&ch);
	printf("s1=%s,s2=%s,ch=%d",s1,s2,ch);

	return 0;
}
```

输入：`hello world ` 回车

打印：`s1=hello,s2=world,ch=10 ` 

说明：可以看到scanf只会接受一次回车符号。多个scanf并不会有多次输入的机会。scanf默认使用空格为风格符。10是回车符`\n`的ASCII码。



想要使用scanf多次读入不同输入，可以这样使用：

```c
#include <stdio.h>

#define  PRINT_CLEAR  while('\n' != getchar());

int main(int argc, char **argv) {
	char name[64];
	int age = 0;

	printf("please input the username:");
	scanf("%s", name);
	PRINT_CLEAR;
	printf("the username is:%s\n", name);

	scanf("my age is %d", &age);
	PRINT_CLEAR;
	printf("your age is is:%d", age);

	return 0;
}
```

`PRINT_CLEAR`的具体说明参考：https://blog.csdn.net/panfengsoftware/article/details/22062537







