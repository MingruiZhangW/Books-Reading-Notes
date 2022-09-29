# C++ Basics

<p align="center">
  <img src="imgs/155.png" />
</p>

<p align="center">
  <img src="imgs/156.png" />
</p>

- Memory Hierarchy

<p align="center">
  <img src="imgs/158.png" />
</p>

<p align="center">
  <img src="imgs/161.png" />
</p>

- Least Recently Used (LRU Cache)

<p align="center">
  <img src="imgs/159.png" />
</p>

<p align="center">
  <img src="imgs/160.png" />
</p>

- [Source](https://www.learncpp.com/)

## [Compiler vs Interpreter](https://stackoverflow.com/questions/38491212/difference-between-compiled-and-interpreted-languages/38491646#38491646)

<p align="center">
  <img src="imgs/1.png" />
</p>

<p align="center">
  <img src="imgs/2.png" />
</p>

- For Java(interpreting), it runs the executable on JVM (virtual machine)
- Java use Just-in-time compilation (Jit)

<p align="center">
  <img src="imgs/157.png" />
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

- Stack - function calls 

<p align="center">
  <img src="imgs/193.png" />
</p>

<p align="center">
  <img src="imgs/194.png" />
</p>

<p align="center">
  <img src="imgs/195.png" />
</p>

<p align="center">
  <img src="imgs/196.png" />
</p>

## [lvalues and rvalues](https://www.learncpp.com/cpp-tutorial/value-categories-lvalues-and-rvalues/)

<p align="center">
  <img src="imgs/115.png" />
</p>

<p align="center">
  <img src="imgs/116.png" />
</p>

<p align="center">
  <img src="imgs/117.png" />
</p>

<p align="center">
  <img src="imgs/118.png" />
</p>

<p align="center">
  <img src="imgs/119.png" />
</p>

- [Lvalue references](https://www.learncpp.com/cpp-tutorial/lvalue-references/)

<p align="center">
  <img src="imgs/120.png" />
</p>

<p align="center">
  <img src="imgs/121.png" />
</p>

<p align="center">
  <img src="imgs/122.png" />
</p>

<p align="center">
  <img src="imgs/123.png" />
</p>

<p align="center">
  <img src="imgs/124.png" />
</p>

<p align="center">
  <img src="imgs/125.png" />
</p>

<p align="center">
  <img src="imgs/126.png" />
</p>

<p align="center">
  <img src="imgs/127.png" />
</p>

<p align="center">
  <img src="imgs/128.png" />
</p>

<p align="center">
  <img src="imgs/129.png" />
</p>

- [Pass by lvalue Reference](https://www.learncpp.com/cpp-tutorial/pass-by-lvalue-reference/)

<p align="center">
  <img src="imgs/130.png" />
</p>

<p align="center">
  <img src="imgs/131.png" />
</p>

<p align="center">
  <img src="imgs/132.png" />
</p>

<p align="center">
  <img src="imgs/133.png" />
</p>

<p align="center">
  <img src="imgs/134.png" />
</p>

<p align="center">
  <img src="imgs/135.png" />
</p>

<p align="center">
  <img src="imgs/136.png" />
</p>

- [R Value Reference](https://www.learncpp.com/cpp-tutorial/rvalue-references/)

<p align="center">
  <img src="imgs/146.png" />
</p>

<p align="center">
  <img src="imgs/147.png" />
</p>

## [Pointers](https://www.learncpp.com/cpp-tutorial/introduction-to-pointers/)

<p align="center">
  <img src="imgs/137.png" />
</p>

<p align="center">
  <img src="imgs/138.png" />
</p>

<p align="center">
  <img src="imgs/139.png" />
</p>

<p align="center">
  <img src="imgs/140.png" />
</p>

<p align="center">
  <img src="imgs/141.png" />
</p>

<p align="center">
  <img src="imgs/142.png" />
</p>

<p align="center">
  <img src="imgs/143.png" />
</p>

<p align="center">
  <img src="imgs/144.png" />
</p>

<p align="center">
  <img src="imgs/145.png" />
</p>

<p align="center">
  <img src="imgs/148.png" />
</p>

<p align="center">
  <img src="imgs/149.png" />
</p>

<p align="center">
  <img src="imgs/150.png" />
</p>

<p align="center">
  <img src="imgs/151.png" />
</p>

<p align="center">
  <img src="imgs/152.png" />
</p>

- Const Pointer & Pointer to Const

<p align="center">
  <img src="imgs/153.png" />
</p>

<p align="center">
  <img src="imgs/154.png" />
</p>

- [Pass by Address](https://www.learncpp.com/cpp-tutorial/pass-by-address/)

<p align="center">
  <img src="imgs/162.png" />
</p>

<p align="center">
  <img src="imgs/163.png" />
</p>

<p align="center">
  <img src="imgs/164.png" />
</p>

> Prefer pass by (const) reference

<p align="center">
  <img src="imgs/165.png" />
</p>

<p align="center">
  <img src="imgs/166.png" />
</p>

- [Return by reference and return by address](https://www.learncpp.com/cpp-tutorial/return-by-reference-and-return-by-address/)

<p align="center">
  <img src="imgs/167.png" />
</p>

<p align="center">
  <img src="imgs/168.png" />
</p>

<p align="center">
  <img src="imgs/169.png" />
</p>

## Scoped enumerations (enum classes)

<p align="center">
  <img src="imgs/170.png" />
</p>

<p align="center">
  <img src="imgs/171.png" />
</p>

<p align="center">
  <img src="imgs/172.png" />
</p>

<p align="center">
  <img src="imgs/173.png" />
</p>

## Struct

<p align="center">
  <img src="imgs/174.png" />
</p>

<p align="center">
  <img src="imgs/175.png" />
</p>

<p align="center">
  <img src="imgs/176.png" />
</p>

<p align="center">
  <img src="imgs/177.png" />
</p>

<p align="center">
  <img src="imgs/178.png" />
</p>

<p align="center">
  <img src="imgs/179.png" />
</p>

<p align="center">
  <img src="imgs/180.png" />
</p>

- Struct size and data structure alignment

<p align="center">
  <img src="imgs/181.png" />
</p>

<p align="center">
  <img src="imgs/182.png" />
</p>

<p align="center">
  <img src="imgs/183.png" />
</p>

<p align="center">
  <img src="imgs/184.png" />
</p>

> [Class template argument deduction (CTAD) and deduction guides](https://www.learncpp.com/cpp-tutorial/class-template-argument-deduction-ctad-and-deduction-guides/)

## Function Pointers

<p align="center">
  <img src="imgs/185.png" />
</p>

<p align="center">
  <img src="imgs/186.png" />
</p>

<p align="center">
  <img src="imgs/187.png" />
</p>

- Callback functions

<p align="center">
  <img src="imgs/188.png" />
</p>

<p align="center">
  <img src="imgs/189.png" />
</p>

```c++
#include <utility> // for std::swap
#include <iostream>

// Note our user-defined comparison is the third parameter
void selectionSort(int* array, int size, bool (*comparisonFcn)(int, int))
{
    // Step through each element of the array
    for (int startIndex{ 0 }; startIndex < (size - 1); ++startIndex)
    {
        // bestIndex is the index of the smallest/largest element we've encountered so far.
        int bestIndex{ startIndex };

        // Look for smallest/largest element remaining in the array (starting at startIndex+1)
        for (int currentIndex{ startIndex + 1 }; currentIndex < size; ++currentIndex)
        {
            // If the current element is smaller/larger than our previously found smallest
            if (comparisonFcn(array[bestIndex], array[currentIndex])) // COMPARISON DONE HERE
            {
                // This is the new smallest/largest number for this iteration
                bestIndex = currentIndex;
            }
        }

        // Swap our start element with our smallest/largest element
        std::swap(array[startIndex], array[bestIndex]);
    }
}

// Here is a comparison function that sorts in ascending order
// (Note: it's exactly the same as the previous ascending() function)
bool ascending(int x, int y)
{
    return x > y; // swap if the first element is greater than the second
}

// Here is a comparison function that sorts in descending order
bool descending(int x, int y)
{
    return x < y; // swap if the second element is greater than the first
}

// This function prints out the values in the array
void printArray(int* array, int size)
{
    for (int index{ 0 }; index < size; ++index)
    {
        std::cout << array[index] << ' ';
    }

    std::cout << '\n';
}

int main()
{
    int array[9]{ 3, 7, 9, 5, 6, 1, 8, 2, 4 };

    // Sort the array in descending order using the descending() function
    selectionSort(array, 9, descending);
    printArray(array, 9);

    // Sort the array in ascending order using the ascending() function
    selectionSort(array, 9, ascending);
    printArray(array, 9);

    return 0;
}
```

<p align="center">
  <img src="imgs/190.png" />
</p>

- Making function pointers prettier with type aliases

<p align="center">
  <img src="imgs/191.png" />
</p>

- ```std::function```

<p align="center">
  <img src="imgs/192.png" />
</p>

## [Ellipsis](https://www.learncpp.com/cpp-tutorial/ellipsis-and-why-to-avoid-them/)

```c++
#include <iostream>
#include <cstdarg> // needed to use ellipsis

// The ellipsis must be the last parameter
// count is how many additional arguments we're passing
double findAverage(int count, ...)
{
    int sum{ 0 };

    // We access the ellipsis through a va_list, so let's declare one
    std::va_list list;

    // We initialize the va_list using va_start.  The first argument is
    // the list to initialize.  The second argument is the last non-ellipsis
    // parameter.
    va_start(list, count);

    // Loop through all the ellipsis values
    for (int arg{ 0 }; arg < count; ++arg)
    {
         // We use va_arg to get values out of our ellipsis
         // The first argument is the va_list we're using
         // The second argument is the type of the value
         sum += va_arg(list, int);
    }

    // Cleanup the va_list when we're done.
    va_end(list);

    return static_cast<double>(sum) / count;
}

int main()
{
    std::cout << findAverage(5, 1, 2, 3, 4, 5) << '\n';
    std::cout << findAverage(6, 1, 2, 3, 4, 5, 6) << '\n';

    return 0;
}
```

# [Lambdas](https://www.learncpp.com/cpp-tutorial/introduction-to-lambdas-anonymous-functions/)

<p align="center">
  <img src="imgs/197.png" />
</p>

- [Lambda captures](https://www.learncpp.com/cpp-tutorial/lambda-captures/)

<p align="center">
  <img src="imgs/198.png" />
</p>

<p align="center">
  <img src="imgs/199.png" />
</p>

<p align="center">
  <img src="imgs/200.png" />
</p>

<p align="center">
  <img src="imgs/201.png" />
</p>

<p align="center">
  <img src="imgs/202.png" />
</p>

<p align="center">
  <img src="imgs/203.png" />
</p>

<p align="center">
  <img src="imgs/204.png" />
</p>

<p align="center">
  <img src="imgs/205.png" />
</p>

<p align="center">
  <img src="imgs/206.png" />
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