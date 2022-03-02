# C++ Idioms - 设计习语 (To Be Studied)

## RAII-Resource Acquisition Is Initialization
> ```资源获取即初始化 (简称 RAII)``` 是C++防止内存泄露一个很好解决方案，它结合构造函数和析构函数，把资源生命周期和对象生命周期绑定起来，在构造函数中获取资源（这些错误会引发异常），然后将其释放到析构函数中（永不抛出），并且不需要显式清理，从而防止忘记释放资源；

<img src=" https://pic1.zhimg.com/80/v2-ef568ed7934fe99d83d81b917fcc79a8_720w.jpg" data-size="normal" data-rawwidth="647" data-rawheight="621"/>

> C ++STL库很多类遵循RAII设计原则，比如std :: string，std :: vector，std :: thread等。

## Policy-based class Design
> 基于策略设计又名 ```policy-based class design``` 是一种基于C++计算机程序设计模式，以策略（Policy）为基础，并结合C++的模板元编程。就是将原本复杂的系统，拆解成多个独立运作的“策略类别”，每一组```policy class```都只负责单纯如行为或结构的某一方面。多重继承由于继承自多组 ```Base Class```，故缺乏型别消息，而```Templetes```基于型别，拥有丰富的型别消息。多重继承容易扩张，而```Templetes```的特化不容易扩张。```Policy-Based Class Design``` 同时使用了 ```Template``` 以及 ```Multiple Inheritance``` 两项技术，结合两者的优点，看下面例子：

<img src=https://pic2.zhimg.com/80/v2-e3f96684f86a3743ed3f7b8a6b44075d_720w.jpg data-size="normal" data-rawwidth="647" data-rawheight="621"/>

> ```ResourceManager```则称为宿主类别```(host class)```，只需要切换不同 ```Policy Class (ReadPolicy or WritePolicy)```，就可以得到不同的功能实体。```Policy```不一定要被宿主继承，只需要用委托完成这一工作。但```policies```必须遵守一个隐含的```constraint```，接口必须一样，故参数不能有巨大改变，```policy``` 的一个重要的特征是，宿主类别经常(并不一定要)使用多重继承的机制去使用多个```policy classes```. 因此在进行```policy```拆解时，必须要尽可能达成正交分解，```policy```之间最好彼此独立运作，不相互影响。

## Pimpl - Pointer to implementation
> ```Pimpl```是一种广泛使用的削减编译依赖项的技术, 看下面例子可能就明白了：

<img src=https://pic4.zhimg.com/80/v2-9e255cc576d0cc45256f962e2df56267_720w.jpg data-size="normal" data-rawwidth="647" data-rawheight="621"/>

> 因为```Widget```的成员变量有```std::string，std::vector和Gadget```，那么这些类型的头文件在```Widget```编译时必须出现，这意味```Widget```的用户必须包含```“gadget.h”```。这些增加的头文件会增加```Widget```用户的编译时间，而且这使得用户依赖于这些头文件，即如果某个头文件的内容被改变了，```Widget```的用户就要重新编译。标准库头文件不会经常改变，但是```“gadget.h”```可能会经常修改。所以需要```Pimp```技术来消除这种变化影响--隔离变化；

<img src=https://pic1.zhimg.com/80/v2-fe955f6cbf09f2027924df96e61ca340_720w.jpg data-size="normal" data-rawwidth="647" data-rawheight="621"/>

>这样```Widget```头文件里面就不需要包含```“gadget.h”```文件了，再```CPP```文件中再声明具体的类型：

<img src=https://pic4.zhimg.com/80/v2-a3f2dbd023a4edf83e6e5873554bc06b_720w.jpg data-size="normal" data-rawwidth="647" data-rawheight="621"/>

> 在这里，我展示了```“#include”```指令，只为了说明所有对头文件的依赖（即```std::string，std::vector和Gadget```）依然存在。不过呢，依赖已经从```“widget.h”```（```Widget```用户可见的和使用的）转移到```“widget.cpp”```(只有```Widget```的实现者才能看见和使用)，这样就把widget头文件变化影响隔离在内部实现中，对外接口不变。

## CRTP -The curiously recurring template pattern
> ```CRTP``` (奇异递归模板模式）是一种在编译期实现多态方法，是对运行时多态一种优化，多态是个很好的特性，但是动态绑定比较慢，因为要查虚函数表。而使用 ```CRTP```，完全消除了动态绑定，降低了继承带来的虚函数表查询开销。

- ```CRTP```包含：
1. 从模板类继承，
2. 使用派生类本身作为基类的模板参数。

<img src=https://pic1.zhimg.com/80/v2-a26539a315f149c513fdfe5b95f15d54_720w.jpg data-size="normal" data-rawwidth="647" data-rawheight="621"/>

> 这样做的目的是在基类中使用派生类。从基础对象的角度来看，派生对象本身就是对象，但是是向下转换的对象。因此，基类可以通过将```static_cast```自身放入派生类来访问派生类.

From: https://zhuanlan.zhihu.com/p/459417765