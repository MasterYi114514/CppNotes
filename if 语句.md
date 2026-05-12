
需要预先学习：
 - [[基础语句与复合语句]]

# 1. if 语句

if 语句是 C++ 中的一种条件控制结构，用于根据条件的真假来决定是否执行某段代码。它的基本语法如下：

```cpp
if(可以判断是真假的条件)
    相邻的语句;

if(可以判断是真假的条件)
{
    // 相邻的代码块
}
```

当条件为真时，if 语句会执行相邻的语句或代码块；当条件为假时，if 语句会跳过这些代码。

```cpp
#include <iostream>

int main()
{
    unsigned int age = 20;

    if(age >= 18)
        std::cout << "你已经成年了，请买全票。" << std::endl;
    
    if(age < 18)
    {
        std::cout << "你还妹有成年，可以买儿童票。" << std::endl;
        std::cout << "儿童票价格是成人票的一半。" << std::endl;
    }
}
```

# 2. else 语句

else 语句是 if 语句的一个可选部分，用于在条件为假时执行另一段代码。它的基本语法如下：

```cpp
if(可以判断是真假的条件)
    相邻的语句;
else
    另一个相邻的语句;
```

同样地，这里相邻的都可以是单条语句，也可以是代码块：

```cpp
#include <iostream>

int main()
{
    unsigned int age = 20;

    if(age >= 18)
        std::cout << "你已经成年了，请买全票。" << std::endl;
    else
    {
        std::cout << "你还妹有成年，可以买儿童票。" << std::endl;
        std::cout << "儿童票价格是成人票的一半。" << std::endl;
    }
}
```

#  3. if-else-if 结构

```cpp
#include <iostream>

int main()
{
    unsigned int age = 5;          // 买票人的年龄

    if(age >= 18)
    {
        std::cout << "你已经成年了，请买全票。" << std::endl;
    }
    else if(age <= 5)       // 第一个 if 条件不满足时，才会判断这个 else if 条件
    {
        // 此处逻辑上为 age <= 5 且 age < 18
        std::cout << "年龄过小的婴幼儿可以免费游玩。" << std::endl;
    }
    else
    {
        // 此处逻辑上为 5 < age < 18
        std::cout << "你是未成年人，请买半价票。" << std::endl;
    }

    return 0;
}
```

该写法其实等价于：
```cpp
#include <iostream>

int main()
{
    unsigned int age = 5;          // 买票人的年龄

    if(age >= 18)
    {
        std::cout << "你已经成年了，请买全票。" << std::endl;
    }
    else 
    {
        if(age <= 5)
        {
            std::cout << "年龄过小的婴幼儿可以免费游玩。" << std::endl;
        }
        else
        {
            std::cout << "你是未成年人，请买半价票。" << std::endl;
        }
    }

    return 0;
}
```

多个 if-else-if 连起来的一个示例：
```cpp
#include <iostream>

int main()
{
    int score = 85;

    if(score > 100)
    {
        std::cout << "成绩有问题，不是你作弊了吗兄弟" << std::endl;
        std::cout << "我要举报你了！" << std::endl;
    }
    else if(score >= 90)
    {
        std::cout << "哥们太有实力了，你的评分是 A！" << std::endl;
        std::cout << "大佬大佬教教我吧！" << std::endl;
    }
    else if(score >= 80) 
        std::cout << "不错不错，你的评分是 B。" << std::endl;
    else if(score >= 70) 
        std::cout << "还行，你的评分是 C。" << std::endl;
    else if(score >= 60) 
        std::cout << "勉强及格，你的评分是 D。" << std::endl;
    else
    {
        std::cout << "你不及格了bro，重修去吧！" << std::endl;
        std::cout << "好好学习，天天向上！" << std::endl;
    }

    return 0;
}
```