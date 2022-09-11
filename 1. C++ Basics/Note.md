# C++ Basics

- [Source](https://www.learncpp.com/)

## [Compiler vs Interpreter](https://stackoverflow.com/questions/38491212/difference-between-compiled-and-interpreted-languages/38491646#38491646)

<p align="center">
  <img src="imgs/1.png" />
</p>

<p align="center">
  <img src="imgs/2.png" />
</p>

## [Uninitialized variables and undefined behavior](https://www.learncpp.com/cpp-tutorial/uninitialized-variables-and-undefined-behavior/)

<p align="center">
  <img src="imgs/3.png" />
</p>

## Return by value && Pass by value

<p align="center">
  <img src="imgs/4.png" />
</p>

<p align="center">
  <img src="imgs/5.png" />
</p>

## [Forward declarations and definitions](https://www.learncpp.com/cpp-tutorial/forward-declarations/)

<p align="center">
  <img src="imgs/6.png" />
</p>

## [The scope of defines](https://www.learncpp.com/cpp-tutorial/introduction-to-the-preprocessor/)

<p align="center">
  <img src="imgs/7.png" />
</p>

<p align="center">
  <img src="imgs/8.png" />
</p>

## [Angled brackets vs double quotes](https://www.learncpp.com/cpp-tutorial/header-files/#includemethod)

<p align="center">
  <img src="imgs/9.png" />
</p>

## [Header guards](https://www.learncpp.com/cpp-tutorial/header-guards/)

<p align="center">
  <img src="imgs/10.png" />
</p>

<p align="center">
  <img src="imgs/11.png" />
</p>

<p align="center">
  <img src="imgs/12.png" />
</p>

## [Object sizes and the sizeof operator](https://www.learncpp.com/cpp-tutorial/object-sizes-and-the-sizeof-operator/)

<p align="center">
  <img src="imgs/13.png" />
</p>

<p align="center">
  <img src="imgs/14.png" />
</p>

<p align="center">
  <img src="imgs/15.png" />
</p>

<p align="center">
  <img src="imgs/16.png" />
</p>

## [The controversy over unsigned numbers](https://www.learncpp.com/cpp-tutorial/unsigned-integers-and-why-to-avoid-them/)

<p align="center">
  <img src="imgs/17.png" />
</p>

<p align="center">
  <img src="imgs/18.png" />
</p>

<p align="center">
  <img src="imgs/19.png" />
</p>

## [Fixed-width integers && Fast and least integers](https://www.learncpp.com/cpp-tutorial/fixed-width-integers-and-size-t/)

<p align="center">
  <img src="imgs/20.png" />
</p>

## [type conversion and static_cast](https://www.learncpp.com/cpp-tutorial/introduction-to-type-conversion-and-static_cast/)

<p align="center">
  <img src="imgs/21.png" />
</p>

## [Compile-time constants, constant expressions, and constexpr](https://www.learncpp.com/cpp-tutorial/compile-time-constants-constant-expressions-and-constexpr/)

<p align="center">
  <img src="imgs/22.png" />
</p>

<p align="center">
  <img src="imgs/23.png" />
</p>

<p align="center">
  <img src="imgs/24.png" />
</p>

<p align="center">
  <img src="imgs/25.png" />
</p>

<p align="center">
  <img src="imgs/26.png" />
</p>

## [Constexpr and consteval functions](https://www.learncpp.com/cpp-tutorial/constexpr-and-consteval-functions/)

<p align="center">
  <img src="imgs/27.png" />
</p>

<p align="center">
  <img src="imgs/28.png" />
</p>

<p align="center">
  <img src="imgs/29.png" />
</p>

<p align="center">
  <img src="imgs/30.png" />
</p>

<p align="center">
  <img src="imgs/31.png" />
</p>

<p align="center">
  <img src="imgs/32.png" />
</p>

<p align="center">
  <img src="imgs/33.png" />
</p>

## [Literals](https://www.learncpp.com/cpp-tutorial/literals/)

<p align="center">
  <img src="imgs/34.png" />
</p>

<p align="center">
  <img src="imgs/35.png" />
</p>

## [std::ws](https://www.learncpp.com/cpp-tutorial/introduction-to-stdstring/)

<p align="center">
  <img src="imgs/36.png" />
</p>

<p align="center">
  <img src="imgs/37.png" />
</p>

## [Introduction to std::string_view](https://www.learncpp.com/cpp-tutorial/introduction-to-stdstring_view/)

<p align="center">
  <img src="imgs/38.png" />
</p>

<p align="center">
  <img src="imgs/39.png" />
</p>

<p align="center">
  <img src="imgs/40.png" />
</p>

<p align="center">
  <img src="imgs/41.png" />
</p>

- Passing strings by ```const std::string&``` or ```std::string_view```?

> ```std::string_view```

<p align="center">
  <img src="imgs/41.png" />
</p>

<p align="center">
  <img src="imgs/42.png" />
</p>

<p align="center">
  <img src="imgs/43.png" />
</p>

## Bit Manipulation

- Binary literals and digit separators

<p align="center">
  <img src="imgs/44.png" />
</p>

- Bit flags and bit manipulation via ```std::bitset```

> Since all objects need to have unique memory addresses, this means ```objects must be at least one byte in size```.

For most variable types, this is fine. However, **for Boolean values, this is a bit wasteful (pun intended)**. Boolean types only have two states: true (1), or false (0). This set of states only requires one bit to store. **However, if a variable must be at least a byte, and a byte is 8 bits, that means a Boolean is using 1 bit and leaving the other 7 unused.**

<p align="center">
  <img src="imgs/45.png" />
</p>

<p align="center">
  <img src="imgs/46.png" />
</p>

- The bitwise operators

<p align="center">
  <img src="imgs/47.png" />
</p>

<p align="center">
  <img src="imgs/48.png" />
</p>

<p align="center">
  <img src="imgs/49.png" />
</p>

<p align="center">
  <img src="imgs/50.png" />
</p>

<p align="center">
  <img src="imgs/51.png" />
</p>

- [Other](https://m-peko.github.io/craft-cpp/posts/different-ways-to-define-binary-flags/)

<p align="center">
  <img src="imgs/52.png" />
</p>

## Scope, Duration, and Linkage

- Multiple namespace blocks are allowed

<p align="center">
  <img src="imgs/53.png" />
</p>

<p align="center">
  <img src="imgs/54.png" />
</p>

- Local variables

<p align="center">
  <img src="imgs/55.png" />
</p>

<p align="center">
  <img src="imgs/56.png" />
</p>

<p align="center">
  <img src="imgs/57.png" />
</p>

<p align="center">
  <img src="imgs/58.png" />
</p>

- [Variable shadowing](https://www.learncpp.com/cpp-tutorial/variable-shadowing-name-hiding/)

> Need to avoid

<p align="center">
  <img src="imgs/59.png" />
</p>

<p align="center">
  <img src="imgs/60.png" />
</p>

- Global variables

<p align="center">
  <img src="imgs/61.png" />
</p>

- Internal linkage

<p align="center">
  <img src="imgs/62.png" />
</p>

<p align="center">
  <img src="imgs/63.png" />
</p>

- External linkage

<p align="center">
  <img src="imgs/64.png" />
</p>

<p align="center">
  <img src="imgs/65.png" />
</p>

<p align="center">
  <img src="imgs/66.png" />
</p>

<p align="center">
  <img src="imgs/67.png" />
</p>

<p align="center">
  <img src="imgs/68.png" />
</p>

## [Sharing global constants across multiple files (using inline variables)](https://www.learncpp.com/cpp-tutorial/sharing-global-constants-across-multiple-files-using-inline-variables/)

<p align="center">
  <img src="imgs/69.png" />
</p>

<p align="center">
  <img src="imgs/70.png" />
</p>

## [Static local variables](https://www.learncpp.com/cpp-tutorial/static-local-variables/)

<p align="center">
  <img src="imgs/71.png" />
</p>

<p align="center">
  <img src="imgs/72.png" />
</p>

## [Scope, duration, and linkage summary](https://www.learncpp.com/cpp-tutorial/scope-duration-and-linkage-summary/)

## [The performance of inline code](learncpp.com/cpp-tutorial/inline-functions/)

<p align="center">
  <img src="imgs/73.png" />
</p>

<p align="center">
  <img src="imgs/74.png" />
</p>

<p align="center">
  <img src="imgs/75.png" />
</p>

## [Unnamed and inline namespaces](https://www.learncpp.com/cpp-tutorial/unnamed-and-inline-namespaces/)

<p align="center">
  <img src="imgs/76.png" />
</p>

<p align="center">
  <img src="imgs/77.png" />
</p>

## [The [[fallthrough]] attribute](https://www.learncpp.com/cpp-tutorial/switch-fallthrough-and-scoping/)

<p align="center">
  <img src="imgs/78.png" />
</p>

<p align="center">
  <img src="imgs/79.png" />
</p>

<p align="center">
  <img src="imgs/80.png" />
</p>

## [For loops with multiple counters](https://www.learncpp.com/cpp-tutorial/for-statements/)

<p align="center">
  <img src="imgs/81.png" />
</p>

## [Random number generation](https://www.learncpp.com/cpp-tutorial/generating-random-numbers-using-mersenne-twister/)

- https://www.learncpp.com/cpp-tutorial/introduction-to-random-number-generation/

## [Type casting](https://www.learncpp.com/cpp-tutorial/explicit-type-conversion-casting-and-static-cast/)

- Avoid C-style casts

<p align="center">
  <img src="imgs/82.png" />
</p>

<p align="center">
  <img src="imgs/83.png" />
</p>

- [Dynamic casting](https://www.learncpp.com/cpp-tutorial/dynamic-casting/)

<p align="center">
  <img src="imgs/84.png" />
</p>

<p align="center">
  <img src="imgs/85.png" />
</p>

<p align="center">
  <img src="imgs/86.png" />
</p>

<p align="center">
  <img src="imgs/87.png" />
</p>

<p align="center">
  <img src="imgs/88.png" />
</p>

<p align="center">
  <img src="imgs/89.png" />
</p>

<p align="center">
  <img src="imgs/90.png" />
</p>

<p align="center">
  <img src="imgs/91.png" />
</p>

<p align="center">
  <img src="imgs/92.png" />
</p>

- Const cast

<p align="center">
  <img src="imgs/93.png" />
</p>

## [Type aliases](https://www.learncpp.com/cpp-tutorial/typedefs-and-type-aliases/)

<p align="center">
  <img src="imgs/94.png" />
</p>

<p align="center">
  <img src="imgs/95.png" />
</p>

<p align="center">
  <img src="imgs/96.png" />
</p>

<p align="center">
  <img src="imgs/97.png" />
</p>

<p align="center">
  <img src="imgs/98.png" />
</p>

<p align="center">
  <img src="imgs/99.png" />
</p>

<p align="center">
  <img src="imgs/100.png" />
</p>

## [Type deduction](https://www.learncpp.com/cpp-tutorial/type-deduction-with-pointers-references-and-const/)

<p align="center">
  <img src="imgs/101.png" />
</p>

<p align="center">
  <img src="imgs/102.png" />
</p>

- Top-level const and low-level const

<p align="center">
  <img src="imgs/103.png" />
</p>

<p align="center">
  <img src="imgs/104.png" />
</p>

> Once initialized, a reference in C++ cannot be reseated, meaning it cannot be changed to reference another object.

> So no const reference, but has reference to a const object.

> ```const std::string&``` is low-level const (reference to a const object)

> ```const int* const ptr``` left is hight-level const(cannot re-point to another obj), right is low-level const(point to a const obj) 

<p align="center">
  <img src="imgs/105.png" />
</p>

<p align="center">
  <img src="imgs/106.png" />
</p>

<p align="center">
  <img src="imgs/107.png" />
</p>

## [Function overload differentiation](https://www.learncpp.com/cpp-tutorial/function-overload-differentiation/)

<p align="center">
  <img src="imgs/108.png" />
</p>

<p align="center">
  <img src="imgs/109.png" />
</p>

<p align="center">
  <img src="imgs/110.png" />
</p>

<p align="center">
  <img src="imgs/111.png" />
</p>

- [Function overload resolution and ambiguous matches](https://www.learncpp.com/cpp-tutorial/function-overload-resolution-and-ambiguous-matches/)

## [Abbreviated function templates (c++ 20)](https://www.learncpp.com/cpp-tutorial/function-templates-with-multiple-template-types/)

<p align="center">
  <img src="imgs/112.png" />
</p>

<p align="center">
  <img src="imgs/113.png" />
</p>

## Stack && Heap

<p align="center">
  <img src="imgs/114.png" />
</p>

## **图解 Git 工作原理**

From: https://mp.weixin.qq.com/s/YM2dNmmR_oKPO9hctTOhjg

- ++i will increment the value of i, and then return the incremented value.

```C++ 
i = 1;
j = ++i;
(i is 2, j is 2)
 ```
- i++ will increment the value of i, but return the original value that i held before being incremented.

```C++
i = 1;
j = i++;
(i is 2, j is 1)
 ```