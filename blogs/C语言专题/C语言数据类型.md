### 基础数据类型

**char**

**unsigned char**

**short**

**unsigned short**

**int**

**unsigned  int**

**long**

**long int**

**long long**

**unsigned long  long**

**float**

**double**



##### boolean类型

C99以前没有boolean类型。**一切不等0的值都表示为真(包括负值)，0表示假。**

一般的在C99以前这样定义boolean类型。

```c
#define TRUE 1
#define FALSE 0
```

C99以后提供了boolean类型，C99定义了```_Bool```为关键字。 ```_Bool```的具体实现由gcc提供。一般的gcc定义1为true，0为false。 C99为了操作方便，提供了stdbool.h 以更好的使用boolean类型。

```c
#include <stdio.h>
#include <stdbool.h>

int main(void) {
	bool x0 = true;
	bool x1 = false;
	printf("x0 = %d\n", x0);
	printf("x1 = %d\n", x1);
}
```

#### 

数组



字符串



结构体



复合类型



枚举类型



指针

```c
void * ptr // 指向任意类型。
```



#### 基础类型转换

数据类型之间相互转换



指针类型的转换



字符串与数字类型转换

```c
itoa()：将整型值转换为字符串。
ltoa()：将长整型值转换为字符串。
ultoa()：将无符号长整型值转换为字符串。
gcvt()：将浮点型数转换为字符串，取四舍五入。
ecvt()：将双精度浮点型值转换为字符串，转换结果中不包含十进制小数点。
fcvt()：指定位数为转换精度，其余同ecvt()。
```

```c
atof()：将字符串转换为双精度浮点型值。
atoi()：将字符串转换为整型值。
atol()：将字符串转换为长整型值。
strtod()：将字符串转换为双精度浮点型值，并报告不能被转换的所有剩余数字。
strtol()：将字符串转换为长整值，并报告不能被转换的所有剩余数字。
strtoul()：将字符串转换为无符号长整型值，并报告不能被转换的所有剩余数字。
```



