# C++ Advanced Knowledge

## 1. [CPU Branch Predictor](http://matt33.com/2020/04/16/cpu-branch-predictor/) (To Be Studied)

> ***if-else*** 涉及到分支预测的概念。首先看一段经典的代码，并统计它的执行时间: 
```
    #include <algorithm>
    #include <ctime>
    #include <iostream>

    int main() {
        const unsigned ARRAY_SIZE = 50000;
        int data[ARRAY_SIZE];
        const unsigned DATA_STRIDE = 256;

        for (unsigned c = 0; c < ARRAY_SIZE; ++c) data[c] = std::rand() % DATA_STRIDE;

        std::sort(data, data + ARRAY_SIZE);

        {  // 测试部分
            clock_t start = clock();
            long long sum = 0;

            for (unsigned i = 0; i < 100000; ++i) {
                for (unsigned c = 0; c < ARRAY_SIZE; ++c) {
                    if (data[c] >= 128) sum += data[c];
                }
            }

            double elapsedTime = static_cast<double>(clock() - start) / CLOCKS_PER_SEC;

            std::cout << elapsedTime << "\n";
            std::cout << "sum = " << sum << "\n";
        }
        return 0;
    }
```

```
    ~/test$ g++ test_predict.cc ;./a.out
    7.95312
    sum = 480124300000
```
> 此程序的执行时间是7.9秒，如果把排序那一行代码注释掉，即
```
// std::sort(data, data + ARRAY_SIZE);
```
> 结果为
```
~/test$ g++ test_predict.cc ;./a.out
24.2188
sum = 480124300000
```
> 改动后的程序执行时间变为了24秒。其实只改动了一行代码，程序执行时间却有3倍的差距，而且看上去数组是否排序与程序执行速度貌似没什么关系，这里面其实涉及到CPU分支预测的知识点。

> 了解了分支预测的概念，我们回到最开始的问题，为什么同一个程序，排序和不排序的执行速度相差那么多。因为程序中有个if条件判断，对于不排序的程序，数据散乱分布，CPU进行分支预测比较困难，预测失败的频率较高，每次失败都会浪费10-20个时钟周期，影响程序运行的效率。而对于排序后的数据，CPU根据历史记录比较好判断即将走哪个分支，大概前一半的数据都不会进入if分支，后一半的数据都会进入if分支，预测的成功率非常高，所以程序运行速度很快。如何解决此问题？总体思路肯定是在程序中尽量减少分支的判断，方法肯定是具体问题具体分析了，对于该示例程序

> 使用位操作: 
```
    int t = (data[c] - 128) >> 31;
    sum += ~t & data[c];
```

> 其实Linux中有一些工具可以检测出分支预测成功的次数，有***valgrind***和***perf***，使用方式如图：
<img src="https://pic2.zhimg.com/50/v2-22f81e01c5c1c479ed3a9bb4514139e5_720w.jpg?source=1940ef5c" data-size="normal" data-rawwidth="647" data-rawheight="621" data-default-watermark-src="https://pica.zhimg.com/50/v2-8cbe7244eed88038ffaa6a5e63314228_720w.jpg?source=1940ef5c" class="origin_image zh-lightbox-thumb" width="647" data-original="https://pic1.zhimg.com/v2-22f81e01c5c1c479ed3a9bb4514139e5_r.jpg?source=1940ef5c"/>

> 条件分支的使用会影响程序执行的效率，我们平时开发过程中应该尽可能减少在程序中随意使用过多的分支，能避免则避免。

From: https://www.zhihu.com/question/441518636/answer/1701252133

## 2. Usage of Macro (To Be Studied)

> inline 无法代替宏的地方：
1. 循环展开：
```
    // loop unroll double
    #define LOOP_UNROLL_DOUBLE(action, actionx2, width) do { \
            unsigned long __width = (unsigned long)(width); \
            unsigned long __increment = __width >> 2; \
            for (; __increment > 0; __increment--) { \
                actionx2;	\
                actionx2;	\
            }	\
            switch (__width & 3) { \
            case 2: actionx2; break; \
            case 3: actionx2; \
            case 1: action; break; \
            }	\
        }	while (0)

    // loop unroll quatro
    #define LOOP_UNROLL_QUATRO(action, actionx2, actionx4, width) do { \
            unsigned long __width = (unsigned long)(width);	\
            unsigned long __increment = __width >> 2; \
            for (; __increment > 0; __increment--) { \
                actionx4;	\
            }	\
            switch (__width & 3) { \
            case 2: actionx2; break; \
            case 3: actionx2; \
            case 1: action; break; \
            }	\
        }	while (0)
```
> 假设你需要高速循环做一个事情，那么展开循环可以极大的减少***CPU分支***，并且充分利用CPU流水线的并行效果，比如你开发一个 FIR滤波器来处理信号，那么你的代码如果从 for (...) { .... } 变成循环展开的话，可以这么写
```
    LOOP_UNROLL_DOUBLE(
        {
            x = *src++;
            // do something with x and h and output to y
            *dst++ = y;
        },
        {
            x1 = *src++;
            x2 = *src++;
            // do something with x1 and h and output to y1
            // do something with x2 and h and output to y2
            *dst++ = y1;
            *dst++ = y2;
        },
        nsamples,
    );
```
> 如此写法将每个循环只计算一个 sample，变为每个循环同时计算两个sample，分开写代码，也能更好的利用 SIMD去加速同时多个 sample的计算过程，这就是利用循环展开来优化性能的用法，直接传 "{...}" 里面的运行代码给宏，宏不变，但是每处使用LOOP_UNROLL的地方 "{.. } " 中的代码都是不同的，inline是代替不了的，你总不至于传个函数指针过去吧，这是性能优化方面情况。
2. 函数组装
> 想象一下，你写图形图像的代码，现在你需要给像素合成实现 SRC_ATOP， SRC_OVER, SRC_IN, SRC_OUT, DST_ATOP, DST_OVER, DST_IN, DST_OUT, XOR, PLUS, ALLANON, TINT, DIFF, DARKEN, LIGHTEN, SCREEN, OVERLAY 等等 二十种像素合成的方法，你如果不用宏，那么你需要写多少个函数？20多个看起来类似的函数，你不得写疯了么？此时用函数指针其实是很浪费性能的事情，那么该如何写呢？你可以规定一系列用来计算composite的方法，接受两组 RGBA，生成新的，比如
```
    /* compositing */
    #define IBLEND_COMPOSITE(sr, sg, sb, sa, dr, dg, db, da, FS, FD) do { \
            (dr) = _ipixel_mullut[(FS)][(sr)] + _ipixel_mullut[(FD)][(dr)]; \
            (dg) = _ipixel_mullut[(FS)][(sg)] + _ipixel_mullut[(FD)][(dg)]; \
            (db) = _ipixel_mullut[(FS)][(sb)] + _ipixel_mullut[(FD)][(db)]; \
            (da) = _ipixel_mullut[(FS)][(sa)] + _ipixel_mullut[(FD)][(da)]; \
        }	while (0)

    /* premultiply: src over */
    #define IBLEND_OP_SRC_OVER(sr, sg, sb, sa, dr, dg, db, da) do { \
            IUINT32 FD = 255 - (sa); \
            IBLEND_COMPOSITE(sr, sg, sb, sa, dr, dg, db, da, 255, FD); \
        }	while (0)

    /* premultiply: dst atop */
    #define IBLEND_OP_DST_ATOP(sr, sg, sb, sa, dr, dg, db, da) do { \
            IUINT32 FS = 255 - (da); \
            IUINT32 FD = (sa); \
            IBLEND_COMPOSITE(sr, sg, sb, sa, dr, dg, db, da, FS, FD); \
        }	while (0)

    /* premultiply: dst in */
    #define IBLEND_OP_DST_IN(sr, sg, sb, sa, dr, dg, db, da) do { \
            IUINT32 FD = (sa); \
            IBLEND_COMPOSITE(sr, sg, sb, sa, dr, dg, db, da, 0, FD); \
        }	while (0)
```
> 然后用 #连接各种方法和格式，生成不同的函数，比如：
```
    #define IPIXEL_COMPOSITE_FN(name, opname) \
    static void ipixel_comp_##name(IUINT32 *dst, const IUINT32 *src, int w)\
    { \
        IUINT32 sr, sg, sb, sa, dr, dg, db, da; \
        for (; w > 0; dst++, src++, w--) { \
            _ipixel_load_card(src, sr, sg, sb, sa); \
            _ipixel_load_card(dst, dr, dg, db, da); \
            IBLEND_OP_##opname(sr, sg, sb, sa, dr, dg, db, da); \
            dst[0] = IRGBA_TO_A8R8G8B8(dr, dg, db, da); \
        } \
    }
```
> 然后开始生成我们的各种合成函数
```
    IPIXEL_COMPOSITE_PREMUL(pre_xor, XOR);
    IPIXEL_COMPOSITE_PREMUL(pre_plus, PLUS);
    IPIXEL_COMPOSITE_PREMUL(pre_src_atop, SRC_ATOP);
    IPIXEL_COMPOSITE_PREMUL(pre_src_in, SRC_IN);
    IPIXEL_COMPOSITE_PREMUL(pre_src_out, SRC_OUT);
    IPIXEL_COMPOSITE_PREMUL(pre_src_over, SRC_OVER);
    IPIXEL_COMPOSITE_PREMUL(pre_dst_atop, DST_ATOP);
    IPIXEL_COMPOSITE_PREMUL(pre_dst_in, DST_IN);
    IPIXEL_COMPOSITE_PREMUL(pre_dst_out, DST_OUT);
    IPIXEL_COMPOSITE_PREMUL(pre_dst_over, DST_OVER);
```
> 这样你相当于定义了：```ipixel_comp_pre_xor (...). ipixel_comp_pre_plus (...)``` 等好几个函数了，并且这些函数都是被你 “组装” 出来的，你并没有使用函数指针，也没有笨重的去写20多个函数。进一步如果你写图形图像你会发现你需要面对多种设备的像素格式，从 A8R8G8B8, A8B8G8R8 到 A1R5G5B5 , 主流需要处理的像素格式都有10多种。那么你可以把 “从不同格式读取 r,g,b,a”， 以及 “将 r,g,b,a组装成任意格式”，展开成很多个宏，然后不管你在这些像素格式里面做转换还是要做一些其他处理，你都可以用任意的 “像素读写” 宏 + “像素计算” 宏 组装成一个个具体需要的函数。所以用宏来解决性能问题，并且简化自己的程序设计往往能起到 inline不能起的作用，甚至能完成很多 template 所不能完成的任务
3. 数据结构和算法
> 具体可以参考 Linux Kernel的 ***include/linux/list.h*** 同样的应用，在 Kernel中，还有红黑树 ***rbtree.h，rbtree.c***中的实现，和 list很类似，大量的宏应用。Linux 用基础的宏实现的 list, rbtree等基础数据结构，用起来是相当方便的，有些地方比 std::list, std::map 都方便多了，比 STL性能高的同时，避免象模版一样为每种类型生成不同的代码，让你的二进制程序变得很臃肿。比如你在做题的时候，用上了这样的数据结构，你程序会比用 stl容器的代码更高效和精简，同时你不知道目标平台 STL是怎么实现的，你无法控制，明明我在这个平台写着很快的代码，为何换个平台又慢了，为了追求究极性能，这样重新定义数据结构，其实是可以理解的
4. 其他 inline 无法代替宏的地方
> 针对不同平台特性（比如整数是32还是64，lsb还是msb）写出的优化代码。泛型的模拟小型高频重复的代码片硬件操作的定义等等，很多情况，inline或者 template还是无法把宏给代替了，所以很多开源项目的代码里面，大量的出现各种宏，主要是出于这些方面的考虑。

From: https://www.zhihu.com/question/30659549/answer/49956788

## 3. [构建C/C++良好的工程结构](https://zhuanlan.zhihu.com/p/59450618) (To Be Studied)

## 4. 内存对齐 (To Be Studied)

> 字节对齐主要是为了提高内存的访问效率，比如intel 32位cpu，每个总线周期都是从偶地址开始读取32位的内存数据，如果数据存放地址不是从偶数开始，则可能出现需要两个总线周期才能读取到想要的数据，因此需要在内存中存放数据时进行对齐。

> 通常我们说字节对齐很多时候都是说struct结构体的内存对齐，比如下面的结构体:

```
    struct A{
        char a;
        int b;
        short c;
    }
```
> 在32位机器上char 占1个字节，int 占4个字节，short占2个字节，一共占用7个字节.但是实际真的是这样吗？

> 我们先看下面程序的输出:

```
#include <stdio.h>

    struct A{
        char a;
        int b;
        short c;
    };
    int main(){
        struct A a;
        printf("A: %ld\n", sizeof(a));
        return 0;
    }
```
> 测试输出的结果是**A: 12**, 比计算的7多了5个字节。这个就是因为编译器在编译的时候进行了内存对齐导致的。

> 内存对齐主要遵循下面三个原则:

1. 结构体变量的起始地址能够被其最宽的成员大小整除
2. 结构体每个成员相对于起始地址的偏移能够被其自身大小整除，如果不能则在前一个成员后面补充字节
3. 结构体总体大小能够被最宽的成员的大小整除，如不能则在后面补充字节
> 其实这里有点不严谨，编译器在编译的时候是可以指定对齐大小的，实际使用的有效对齐其实是取指定大小和自身大小的最小值，一般默认的对齐大小是4。
> 再回到上面的例子，如果默认的对齐大小是4，结构体a的起始地址为0x0000，能够被最宽的数据成员大小(这里是int， 大小为4，有效对齐大小也是4)整除，姑char a的从0x0000开始存放占用一个字节即0x0000~0x0001，然后是int b，其大小为4，故要满足2，需要从0x0004开始，所以在char a后填充三个字节，因此a对齐后占用的空间是0x0000~0x0003，b占用的空间是0x0004~0x0007, 然后是short c其大小是2，故从0x0008开始占用两个字节，即0x0008~0x0009。 此时整个结构体占用的空间是0x0000~0x0009， 占用10个字节，10%4 ！= 0, 不满足第三个原则，所以需要在后面补充两个字节，即最后内存对齐后占用的空间是0x0000~0x000B，一共12个字节。

From: https://www.zhihu.com/question/27862634/answer/208895189

### ***New*** Operator Overloading and std::allocator (To Be Studied)

1. 对齐版本的 operator new 重载 
```
    void* operator new(std::size_t count, std::align_val_t al);
```
2. new 申请不到内存时，在默认情况下，是会一个循环，不断调用 std::get_new_handler 返回的函数指针，直到分配成功为止的。我觉得这也太坑了，顶多试三次就行了

> vector 最核心的需求是什么？是要求内存分配和对象的构造之间能解耦、解分配和对象的析构之间能解耦。说人话，就是需要先用 allocator.allocate() 方法从分配器中提前分配出内存块，等推迟到合适的时候，才在这个内存块上构造出对象。那些叫嚣 100 行写出的 vector，其实现都是根本不能用的，里面全是用的 new T[]。正规的写法必须要用到 placement new —— 这是重载 new 的最机智的利用。vector 的基本原理如下

```
    #include <new>
    #include <iostream>

    struct Foo
    {
        int i;

        Foo(int i) : i(i)
        {
            std::cout << "构造 " << i << std::endl;
        }
        ~Foo()
        {
            std::cout << "析构 " << i << std::endl;
        }
    };

    int main()
    {
        std::allocator<Foo> alloc;
        Foo * p = alloc.allocate(3);
        
        std::cout << "分配好缓冲区了" << std::endl;
        
        for (int i = 0; i < 3; ++i) {
            std::cout << "push_back 第 " << i << " 个元素" << std::endl;
            new (p + i) Foo(i);
        }
        for (int i = 0; i < 3; ++i) {
            std::cout << "pop_back 第 " << i << " 个元素" << std::endl;
            (p + 2 - i)->~Foo();
        }
        
        alloc.deallocate(p, 3);
        std::cout << "释放完缓冲区了" << std::endl;
    }
```

```
    输出：分配好缓冲区了
    push_back 第 0 个元素
    构造 0
    push_back 第 1 个元素
    构造 1
    push_back 第 2 个元素
    构造 2
    pop_back 第 0 个元素
    析构 2
    pop_back 第 1 个元素
    析构 1
    pop_back 第 2 个元素
    析构 0
```

> 释放完缓冲区了你以为 placement new 是 C++ 为其特殊设计的语法？不是的，placement new 只是一个函数调用而已。它只不过是
```
    void* operator new(std::size_t, void* p)
    {
        return p;
    }
```

- [Placement new](https://en.cppreference.com/w/cpp/language/new)

- [alignas](https://stackoverflow.com/questions/17091382/memory-alignment-how-to-use-alignof-alignas)

From: https://www.zhihu.com/question/470670449/answer/1984399361