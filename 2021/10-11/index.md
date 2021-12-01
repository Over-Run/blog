# 2021.10.11: C++ 问题总结

> Updated: 2021.10.11
>
> Author: squid233

鱿鱼个人在用 C++ 编写[游戏](https://github.com/Over-Run/Real2D)，所以在这里写一些对 C++ 一部分知识的理解以及遇到的一些问题，新手可以参考一下。

## 1. `using namespace`?

不推荐使用。特别容易发生冲突。建议使用以下代码：

```cpp
// 只使用需要的符号
using std::cout;
```

## 2. 测试是否为空指针

```cpp
int* p = func();
// 推荐
if (p == nullptr) {
    cout << "p is null" << endl;
}
// 不推荐，使用思考时间换取更多可用空间
if (!p) {
    cout << "p is null" << endl;
}
```

## 3. `#define`和`constexpr`

```cpp
//#define WIDTH (1024)
// 能用 constexpr 就用
// constexpr 与 #define 的区别：
// #define 无类型，且无法调试
constexpr int WIDTH = 1024;

// #define 的优点：减少源码占用空间
// #define 的缺点：增加预处理时间
```

## 4. `malloc`与`new`

`malloc`为C语言中动态分配内存的函数。其函数原型如下：

```c
#include <malloc.h>
/**
 * 动态分配内存至堆中。
 *
 * @param _Size 要分配的大小（以字节为单位）。
 * @return 如果分配成功，返回任意类型；否则返回NULL。
 * @example int* p = (int*)malloc(4 * sizeof(int))
 * @exampleinfo 分配一个长度为4的数组。
 * @note 必须将其初始化。必须使用sizeof计算字节大小。
 */
void* malloc(size_t _Size);
```

`malloc`还需要搭配`free`使用。

```c
#include <malloc.h>
/**
 * 释放从 malloc 中返回的指针。
 *
 * @param _Block 一块内存。
 * @example free(p)
 * @note malloc和free函数是配对的，如果申请后不释放就是内存泄露;
 *       如果无故释放那就是什么都没有做，释放只能释放一次，如果释放两次及两次以上会出现错误
 *       （但是释放空指针例外，释放空指针其实也等于什么都没有做，所以，释放多少次都是可以的）
 */
void free(void* _Block);
```

### `new`

`new`与`delete`是 C++ 中特有的**运算符**。`new`返回指定类型的指针，并且可以自动计算所需要的大小。

```c++
int* p;
// 分配大小为sizeof(int)
p = new int;
// 分配大小为4 * sizeof(int)
p = new int[4];
// 释放 p
delete p;
// 释放 p 并逐个析构
delete[] p;
```



