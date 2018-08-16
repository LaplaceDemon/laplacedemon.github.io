### C语言内存分区

* 代码区（text segment）
* 未初始化数据区（BSS）
* 全局初始化数据区/静态数据区（data segment）
* 栈区（stack）
* 堆区（heap）



### 内存分配

栈上分配：在函数上初始化数据。

堆上分配：malloc与free



### 内存操作

**memchr 字节搜索**

```c
void *memchr(const void *str, int c, size_t n)
```

在参数 str 所指向的字符串的前 n 个字节中搜索第一次出现字符 c（一个无符号字符）的位置。



**memset 内存设置**

```c
void *memset(void *str, int c, size_t n)
```

复制字符 c（一个无符号字符）到参数 *str* 所指向的字符串的前 n 个字符。   



**memcpy 内存拷贝**

```c
void *memcpy(void *dest, const void *src, size_t n)
```

从 src 复制 n 个字符到 dest。



**memmove 内存数据移动**

```c
void *memmove(void *dest, const void *src, size_t n)
```

另一个用于从 str2 复制 n 个字符到 str1 的函数。 



**memcmp 内存比较**

```c
int memcmp(const void *str1, const void *str2, size_t n)
```

把 str1 和 str2 的前 n 个字节进行比较。



