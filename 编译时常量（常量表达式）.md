
需要预先学习：
 - [[编译基础]]
 - [[常量]]

注意：`constexpr` 关键字在 C++11 中才引入。

# 1. 编译时常量（constant expression）

**编译时常量**：也叫常量表达式，是指在编译时就能确定其值的表达式。

编译时常量和常量一样，也必须在定义时初始化，并且在程序运行过程中不能被修改。

但是，编译时常量初始化的值必须在编译时就能确定，即必须是一个由其它编译时能确定的常量或字面值组成的表达式。
```cpp
// after C++11
#include <iostream>

int main()
{
    const int a = 10;           // a 是一个普通常量，但是它的值在编译时也能确定
    constexpr int b = 20;       // b 是一个编译时常量
    constexpr int c = a + b;    // c 是一个编译时常量，值为 30

    return 0;
}
```

注：
1. 普通的常量**既可以在编译时就确定值，也可以在运行的时候才确定值**，前者可以被用来初始化编译时常量，后者则不能。
```cpp
#include <iostream>

int main()
{
    int variable = 10;              // variable 是一个变量
    const int a = variable;         // a 是一个常量，值在运行时才确定
    constexpr int b = variable;     // 错误，编译时常量不能被变量初始化
    constexpr int c = a;            // 错误，编译时常量不能被运行时才确定的常量初始化

    return 0;
}
```

编译该代码，得到以下报错：
```
code7.cpp: In function 'int main()':
code7.cpp:7:23: error: the value of 'variable' is not usable in a constant expression
    7 |     constexpr int b = variable;     // 错误，编译时常量不能被变量初始化
      |                       ^~~~~~~~
code7.cpp:5:9: note: 'int variable' is not const
    5 |     int variable = 10;              // variable 是一个变量
      |         ^~~~~~~~
code7.cpp:8:23: error: the value of 'a' is not usable in a constant expression
    8 |     constexpr int c = a;            // 错误，编译时常量不能被运行时才确定的常量初始化
      |                       ^
code7.cpp:6:15: note: 'a' was not initialized with a constant expression
    6 |     const int a = variable;         // a 是一个常量，值在运行时才确定
      |               ^
```

2. 编译时常量的值在编译阶段就能确定，随后就会被直接替换到代码中，这样在程序运行时就不需要再查找地址、访问内存来获取值了，因此编译时常量的访问效率更高。

编译时常量的替换在这一步被完成：
```
a.cpp(源代码) -> a.i(预处理后文件) -> a.s(汇编代码) -> a.o(目标文件) -> a.exe(可执行文件)
                                 ^ 在这一步
```

# 2. 编译时常量与普通常量的区别

