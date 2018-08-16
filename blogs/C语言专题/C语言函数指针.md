## 函数指针

函数指针就是指向函数的指针。

函数指针的作用非常类似于 **Java的函数式接口** ，但函数指针比函数式接口更为灵活。



### 声明函数指针变量

```c
void print();  // 函数声明
//     ⬇️
void (*fuc)();  // 声明可以指向print函数的指针变量。
```

注意：声明函数指针一定要使用括号。

 

### 使用函数指针变量

```c
#include <stdio.h>
#include <stdlib.h>

void print();

int main(void) {
	void (*func)();
	func = print;  // 赋值函数指针变量。
	func();    // 调用函数。

	return EXIT_SUCCESS;
}


void print() {
	printf("hello world\n");
}
```





### 函数指针变量作为函数参数

```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

#define PI 3.1415926535897932


// 积分函数，接收一个数学函数指针，x0与x1是积分上下限。step是积分步长。
double integral(double (*func)(double), double x0,double x1,int step);
/*
// 这样也行。
// 函数的参数部分在声明阶段是不要指定变量名的。
double integral(double (*math_func)(double x), double x0,double x1,int step);
*/

int main(void) {
	double result = integral(sin,0,PI,1000);
	printf("sin integral,%f",result);
	return EXIT_SUCCESS;
}

// 积分函数的实现
double integral(double (*math_func)(double), double x0,double x1,int step) {
	double sum = 0.0;
	double x = x0;
	double dx = (x1-x0)/step;
	for(int i = 0;i<step;i++) {
		sum += func(x)*dx;
		x += dx;
	}
	return sum;
}
```



### 函数返回函数指针

```c
#include <stdio.h>

typedef int (*FP)(int,int);//定义一个函数指针类型

int add(int a, int b) {
	return a + b;
}

int sub(int a, int b) {
	return a - b;
}

int mul(int a, int b) {
	return a * b;
}

int div(int a, int b) {
	return b ? a/b : -1;
}

FP calc_func(char op) {
	switch( op ) {
		case '+': return add;
		case '-': return sub;
		case '*': return mul;
		case '/': return div;
		default: return NULL;
	}
}

void main() {
	int a = 100, b = 20;
	FP calc = calc_func('+');
	int res = calc(a, b);
	printf("calc(%d, %d, %c) = %d\n", a, b, '+', res);
}
```





### 辨析

```c
char * (*fun1)(char * p1,char * p2); // 函数指针
char * *fun2(char * p1,char * p2);   // 返回二级指针，char**
char * fun3(char * p1,char * p2);    // 返回指针，char*
```

特别是```char * *fun2(char * p1,char * p2);```  fun2并不是一个指针变量，而仅仅是函数名称。



## typedef 定义函数指针类型

之前使用的方式实在太麻烦了，每次声明一个函数指针变量都要重写一遍函数形式。

```c
double (*func1)(double) = sin;
double (*func2)(double) = cos;
```

可以使用typedef定义这种函数形式的函数指针变量。

```c
typedef double (*MathFunc)(double x);
```

```MathFunc``` 就可以当作一种类型来使用了。

```c
#include <stdio.h>
#include <stdlib.h>
#include <math.h>

typedef double (*MathFunc)(double);

int main(void) {
	MathFunc func1 = sin;
	MathFunc func2 = cos;
	double res1 = func1(1.0);
	double res2 = func2(1.0);
	printf("sin(1.0) = %f\n",res1);
	printf("cos(1.0) = %f",res2);
	return EXIT_SUCCESS;
}
```

