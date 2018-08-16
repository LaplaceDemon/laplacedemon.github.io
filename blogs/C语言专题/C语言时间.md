### 获取当前时间

```c
#include <time.h>

time_t time(time_t *t)
```

该函数返回当前时间戳，以秒为单位。`time_t` 本质是一个4字节整数。



例：

```c
#include <stdio.h>
#include <time.h>

int main(int argc, char **argv) {
	time_t seconds = time(NULL);
	printf("timestamp = %lds", seconds);
	return 0;
}
```



获取指定时间戳的当地时间

```c
#include <time.h>
 
struct tm *localtime(const time_t *timer)
```







打印时间



