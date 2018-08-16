## 数组初始化

#### 在栈上分配数组

```c
int a0[] = {1,2,3}; 
// [1,2,3]

int a1[10] = {1,2,3,4,5,6};
// [1,2,3,4,5,6,0,0,0,0]
```



#### 在堆上分配数组

```c
#include <stdio.h>
#include <stdlib.h>

int main(void) {
    // 分配内存
	int * pints = (int *) malloc(100 * sizeof(int));
    
    // 初始化内存
	memset(pints, 0, 100 * sizeof(int));
	pints[0] = 1; pints[1] = 1; pints[2] = 2; pints[3] = 3;
    pints[4] = 5; pints[5] = 8; pints[6] = 13; pints[7] = 21;
    pints[8] = 34; pints[9] = 55; pints[10] = 89; pints[11] = 144;
    
    // 打印数组
	for (int i = 0; i < 100; i++) {
		printf("%d -> %d\n", i, pints[i]);
	}
    
    // 释放
	free(pints);
	return 0;
}
```





## 数组长度

```c
int x[] = {1,2,3};
int len = sizeof(x)/sizeof(x[0]);
```





## 数组作为函数参数

```int x[]``` 这种类型的的变量无法作为函数的参数。

数组作为函数的参数，必须向函数内传入数组的长度。

数组作为函数参数有两种形式。

形式一：函数参数形式为```int arr[10]``` 

```c
void printArray(int arr[10]) {
    int len = sizeof(arr)/sizeof(arr[0]);
	printf("[");
	if(len > 1) {
		printf("%d",arr[0]);
	}
	for(int i = 1;i<len;i++) {
		printf(", %d",arr[i]);
	}
	printf("]");
}
```

这种形式的参数传递，会导致数组的内存拷贝。



形式二：传递数组指针与数组长度。 

```c
void printArray(int * arr,int len) {
	printf("[");
	if(len > 1) {
		printf("%d",arr[0]);
	}
	for(int i = 1;i<len;i++) {
		printf(", %d",arr[i]);
	}
	printf("]");
}
```



## 指针与数组

数组变量名等价于指针变量。



## 二维数组

多维数组

