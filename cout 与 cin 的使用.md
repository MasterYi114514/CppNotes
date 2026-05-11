
在使用 `cout` 与 `cin` 之前，需要先包含头文件 `iostream`

```cpp
#include <iostream>
```

# 1. `cout` 的使用

`cout` 是 C++ 中用于输出的对象，属于 `std` 命名空间。它可以用来输出文本、变量的值等信息到控制台。

```cpp
#include <iostream>

int main()
{
    std::cout << "Hello, World!" << std::endl; // 输出文本并换行
    int a = 10;
    std::cout << "The value of a is: " << a << std::endl; // 输出变量的值
    return 0;
}
```

注：
1. 这里的 `std::endl` 是一个特殊的操作符，用于在输出后换行并刷新输出缓冲区。
2. 也可以使用 `\n` 来换行，但 `std::endl` 会同时刷新缓冲区，确保输出立即显示。

# 2. `cin` 的使用