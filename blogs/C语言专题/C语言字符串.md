### 字符串初始化

#### 栈上分配字符串

```c
char s0[] = {'j','a','v','a'};   // 字符串：|j|a|v|a|

char s1[10] = {'a','b','c','d','e'}; // 字符串：|a|b|c|d|e|\0|\0|\0|\0|\0|

char s2[] = "python";  // 字符串：|p|y|t|h|o|n|\0|

char s3[] = "\0str";  // 字符串：|\0|s|t|r|\0|

char * s4 = "c++";
```



#### 堆上分配字符串

```c
#include <string.h>
#include <stdio.h>
#include <stdlib.h>

int main() {
	const char * pstr = (char *)malloc(100 * sizeof(char));  // 分配
	strcpy(pstr,"helloworld");  // 赋值
	puts(pstr);    // 打印
	free(pstr);    // 释放
	return 0;
}
```





#### 辨析：`char s[]` 与 `char * s`有什么区别

`char s[]`要发生一次内存拷贝。`char s[]`的字符串可以被更改。

`char * s`没有内存拷贝，`char * s`直接指向字符串。`char * s`指向的字符串不可以被修改。

**一般的`char s[]`更加通用。**一些函数只能使用`char s[]`，比如`strtok`函数。





#### 格式化的字符串

```c
#include <stdio.h>

int sprintf(char *str, const char *format, ...)
```

str获取格式化的字符串。该函数生产的字符串，结尾处会自动添加`'\0'`。

例：

```c
#include <stdio.h>
#include <math.h>

int main(void) {
   char str[80] = "asdfasdfasdfkashdfkjhasdkfhlkasdhfkjhasdkjf";
   sprintf(str, "Pi 的值 = %2.10f", M_PI);
   puts(str);
   return 0;
}
```





#### 字符串长度

```c
#include <string.h>

size_t strlen(const char * s);
```

该函数以`\0` 作为字符串的结尾。

例：

```c
#include <stdio.h>
#include <string.h>


int main(int argc, char **argv) {
	char * s0 = "python";
	size_t len0 = strlen(s0);
	printf("len(s0) = %zu\n",len0); 

	char s1[] = "py\0thon";
	size_t len1 = strlen(s1);
	printf("len(s1) = %zu\n",len1);

	return 0;
}


```

输出：

```
len(s0) = 6
len(s1) = 2
```



#### 字符串拷贝

```c
#include <string.h>
char * strcpy(char * dest, char * src);
```

返回值 : 

成功：返回 dest 字符串的首地址。

失败：NULL

注意：如果参数 dest 所指的内存空间不够大，可能会造成缓冲溢出的错误情况。 

 

```c
#include <string.h>
char *  strncpy(char * dest, const char * src,size_t n);
```

功能:把 src 指向字符串的前 n 个字符复制到dest所指向的空间中，是否拷贝结束符看指定的长度是否包含`\0`。

返回值：

成功：返回dest字符串的首地址。

失败：返回NULL。



#### 字符串连接

```c
#include <string.h>
char * strcat(char * dest, const char * src);
```

功能：将src字符串连接到dest的尾部，`\0`也会追加过去。

返回值：

成功：返回dest字符串的首地址。

失败：返回NULL。



```c
#include <string.h>
char * strncat(char * dest, const char * src, size_t n);
```

功能：将src字符串的前n个字符连接到dest的尾部，`\0`也会追加过去。

返回值：

成功：返回dest字符串的首地址。

失败：返回NULL。



#### 字符串比较

```c
#include <string.h>
int strcmp(const char *str1, const char *str2)
```

把 str1 所指向的字符串和 str2 所指向的字符串进行比较。 



返回值 

相等：=0

大于：>0

小于：<0 



```c
#include <string.h>
int strncmp(const char *str1, const char *str2, size_t n);
```

把 *str1* 和 *str2* 进行比较，最多比较前 n 个字节。



#### 查找

```c
#include <string.h>
char * strchr(const char *str, int c);
```

在字符串str中查找字母c第一次出现的地址。

成功:返回第一次出现的c的地址。

失败:NULL 



```c
#include <string.h>
char * strstr(const char *haystack, const char *needle);
```

返回值：该函数返回在 haystack 中第一次出现 needle 字符串的位置。

如果未找到则返回 null。



#### 切割

```c
char *strtok(char *str, const char *delim)
```

分解字符串 str 为一组字符串，delim 为分隔符字符串。

返回值：该函数返回被分解的第一个子字符串，如果没有可检索的字符串，则返回一个空指针。

例：

```c
#include <string.h>
#include <stdio.h>

int main () {
    char str[] = "This is--www.taobao.com--website";
    char * s = "--";
    char * token = strtok(str, s);
    while(token != NULL) {
       printf("%s\n", token);
       token = strtok(NULL, s);
    }
    puts(str);
    return 0;
}
```

注意：strtok函数不能使用`char *` 形式的字符串。因为strtok要修改字符串。而`char *`指向的字符串无法被修改。

`puts(str)` 打印结果为`This is`。







#### Unicode字符串













