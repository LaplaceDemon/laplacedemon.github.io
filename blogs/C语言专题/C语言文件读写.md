文件FILE结构

```c
struct _iobuf {  
    char *_ptr;  
    int   _cnt;  
    char *_base;  
    int   _flag;  
    int   _file;  
    int   _charbuf;  
    int   _bufsiz;  
    char *_tmpfname;  
};  
typedef struct _iobuf FILE;
```





#### 打开文件

```c
FILE *fopen(const char *filename, const char *mode)
```

该函数返回一个 FILE 指针。否则返回 NULL，且设置全局变量 errno 来标识错误。

- **filename**：文件名称。
- **mode** ：文件访问模式。

| 模式 | 描述                                                         |
| ---- | :----------------------------------------------------------- |
| "r"  | 打开一个用于读取的文件。该文件必须存在。                     |
| "w"  | 创建一个用于写入的空文件。如果文件名称与已存在的文件相同，则会删除已有文件的内容，文件被视为一个新的空文件。 |
| "a"  | 追加到一个文件。写操作向文件末尾追加数据。如果文件不存在，则创建文件。 |
| "r+" | 打开一个用于更新的文件，可读取也可写入。该文件必须存在。     |
| "w+" | 创建一个用于读写的空文件。                                   |
| "a+" | 打开一个用于读取和追加的文件。                               |





#### 关闭文件

```c
int fclose(FILE *stream)
```

关闭文件。刷新所有的缓冲区。返回值: 

成功：0，失败：-1 





#### 文件结尾

C中定义了EOF值（End of File）。

```c
#define EOF (-1)
```



feof检测是否已经读到文件尾部了。

```c
int feof(FILE *stream)
```

返回值非0：已经到文件结尾。 

返回值为0：没有到文件结尾。



一个字符的读写

```c++
int fputc(int char, FILE *stream)
```

```c
int fgetc(FILE *stream) 
```





一行字符串的读写

```c
char *fgets(char *str, int n, FILE *stream)
```

从 stream 指定的文件内读入字符，保存到 str 所指定的内存空间，直到出现换行字 

符或是文件结尾或是已读了 size-1 个字符为止，最后会自动加上字符'\0' 作为字符串结。



```c
int fputs(const char *str, FILE *stream)
```



按格式写写文件

```c
int fprintf(FILE *stream, const char *format, ...)
```



```c
int fscanf(FILE *stream, const char *format, ...)
```

功能:从 stream 指定的文件读取字符串，并根据参数 format 字符串来转换并格式化数据。 



按块读写文件

```c
size_t fwrite(const void *ptr, size_t size, size_t nmemb, FILE *stream)
```

功能：以数据块的方式给文件写入内容 

参数

ptr：准备写入文件数据的地址 。

size：指定写入文件内容的块数据大小。 

nmemb：写入文件的块数，写入文件数据总大小为:size * nmemb 

stream：已经打开的文件指针。

返回值：成功:实际成功写入文件数据的块数目，此值和nmemb相等。 





```c
size_t fread(void *ptr, size_t size, size_t nmemb, FILE *stream)
```

- **ptr**：指向带有最小尺寸 *size\*nmemb* 字节的内存块的指针。
- **size**：要读取的每个元素的大小，以字节为单位。
- **nmemb** ：元素的个数，每个元素的大小为 size 字节。
- **stream** ：指向 FILE 对象的指针，该 FILE 对象指定了一个输入流。

 



文件读写位置定位

```c
int fseek(FILE *stream, long int offset, int whence)
```

设置流 **stream** 的文件位置为给定的偏移 **offset**，参数 offset 意味着从给定的 **whence** 位置查找的字节数。

**stream** ：指向 FILE 对象的指针，该 FILE 对象标识了流。

**offset** ：相对 whence 的偏移量，以字节为单位。

**whence** ：表示开始添加偏移 offset 的位置。

whence预定义了一些特殊常量：

| 常量     | 描述               |
| -------- | ------------------ |
| SEEK_SET | 文件的开头         |
| SEEK_CUR | 文件指针的当前位置 |
| SEEK_END | 文件的末尾         |

 例：

```c
#include <stdio.h>

int main (void) {
   FILE *fp;

   fp = fopen("file.txt","w+");
   fputs("This is runoob.com", fp);
  
   fseek(fp, 7, SEEK_SET);
   fputs("C Programming Langauge", fp);
   fclose(fp);
   
   return(0);
}
```





#### 刷新文件缓冲

```c
int fflush(FILE *stream);
```





#### 获取文件状态

```c
#include <sys/types.h>
#include <sys/stat.h>
int stat(const char *restrict pathname,struct stat *restrict buf);
```

```c
struct stat { 
     dev_t st_dev; // 文件所在设备ID。
     ino_t st_ino; // 结点(inode)编号。
     mode_t st_mode; // 文件的类型和存取的权限。
     nlink_t st_nlink; // 连接到文件的硬连接数，对于刚建立的文件该值为1
     uid_t st_uid; // 所有者用户ID。  
     gid_t st_gid; // 所有者组ID。
     dev_t st_rdev; // 设备类型，若此文件为设备文件，则为设备编号。
     off_t st_size; // 文件字节数（文件大小）。
     blksize_t st_blksize; // 块大小，文件系统 I/O 缓冲区块大小。
     blkcnt_t st_blocks; // 块数
     time_t st_atime; // 最后一次访问时间。
     time_t st_mtime; // 最后一次修改时间。
     time_t st_ctime; // 最后一次属性的修改时间。
};
```



例：

```c
#include <sys/types.h>
#include <sys/stat.h>
#include <stdio.h>

int main(int argc, char **argv) {
	struct stat st = {0};
	stat("files/test.dat",&st);
	int size = st.st_size;
	printf("%d\n",size);
	return 0;
}
```





#### rm文件

```c
int remove(const char *filename);
```



#### mv文件

```c
int rename(const char *old_filename, const char *new_filename);
```







