# C++数据类型

# 一、整型

| 数据类型  |                        占用空间                         |         取值范围          |
| :-------: | :-----------------------------------------------------: | :-----------------------: |
|    int    |                         4个字节                         | ${-2^{31}}$~ $2^{31}-  1$ |
|   short   |                         2个字节                         |   $-2^{15}$~$2^{15}-1$    |
|   long    | windows占4个字节；Linux中占4个字节(32位)，8个字节(64位) | ${-2^{31}}$~ $2^{31}-  1$ |
| long long |                         8个字节                         |   $-2^{63}$~$2^{63}-1$    |

> 一个字节八位，默认首位为符号位，所以取值范围是能通过占用空间计算出来的
>
> 比如`int`，占用空间为4个字节，也就是32位