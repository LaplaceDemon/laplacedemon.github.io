#### 定义枚举类型

```c
enum Week {
    MON,TUE,WED,THU,FRI,SAT,SUN
};
```



#### 定义枚举类型变量

枚举变量本质是一个整型数据。

例：

```c
#include <stdio.h>

enum Week {
	MON, TUE, WED, THU, FRI, SAT, SUN
};

int main(int argc, char ** argv) {
    // 枚举变量。
	enum Week day = MON;
    
    // 枚举变量本质是一个整型数据。
	printf("MON value = %d",day);  // 打印：MON value = 0
    
	return 0;
}
```



例：

```c
#include <stdio.h>

enum Week {
	MON, TUE, WED, THU, FRI, SAT, SUN
};

int main(int argc, char **argv) {
	printf("%d\n",MON);
	printf("%d\n",TUE);
	printf("%d\n",WED);
	printf("%d\n",THU);
	printf("%d\n",FRI);
	printf("%d\n",SAT);
	printf("%d\n",SUN);

	return 0;
}
```

打印：

```
0
1
2
3
4
5
6
```





#### 定义枚举整数值

枚举的整数值是可以自定义的。

```c
enum Week0{MON,TUE=3,WED,THU,FRI,SAT,SUN};
// MON=0,TUE=3,WED=4,THU=5,FRI=6,SAT=7,SUN=8

enum Week1{MON=10,TUE=3,WED=1,THU,FRI,SAT,SUN};
// MON=0,TUE=3,WED=1,THU=2,FRI=3,SAT=4,SUN=5

enum Week2{MON=10,TUE=10,WED=10,THU=10,FRI=10,SAT=10,SUN=10};
// MON=10,TUE=10,WED=10,THU=10,FRI=10,SAT=10,SUN=10
```

以上代码均可以通过编译，可以看到枚举的整数值默认情况下是从0递增的。当中间枚举值被定义数值后，其后的值也依次递增。而且枚举值是可以相等的，即便这并无太大意义。



#### 枚举与switch语句

枚举与switch语句可以有很好的结合。但要注意，枚举值不能有相等的值出现，否则switch无法通过编译。

例：

```c
#include <stdio.h>

enum Week {
	MON, TUE, WED, THU, FRI, SAT, SUN
};

int main(int argc, char **argv) {
    enum Week day = MON;
    
	switch (day) {
	case MON:
		printf("monday");
		break;
	case TUE:
		printf("tuesday");
		break;
	case WED:
		printf("wednesday");
		break;
	case THU:
		printf("thursday");
		break;
	case FRI:
		printf("friday");
		break;
	case SAT:
		printf("saturday");
		break;
	case SUN:
		printf("sunday");
		break;
	default:
		break;
	}
	return 0;
}
```











