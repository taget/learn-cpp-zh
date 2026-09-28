# 函数

所属单元：6. Functions  
上一课：`14-whale-talk.md`  
下一课：`16-classes-and-objects.md`

大纲里的项目把一个小游戏拆成几个函数，再分到头文件和源文件。这里改成「课间点名」，只学同样的拆法。一次只讲一个步骤。

## 步骤 1：给一组步骤起名字

函数是一段起了名字的步骤。`void` 表示它只做事，不交回一个数。写好以后，在 `main` 里用名字调用它。调用之前，程序要已经看见这个函数。

类比：广播操有一节叫「点名」。老师喊这个名字，大家就做那一串动作，不用把动作再描述一遍。

```cpp
#include <iostream>
#include <string>

void greet() {
  std::cout << "课间点名开始\n";
}

void call_student(std::string name) {
  std::cout << name << "，到了吗\n";
}

int main() {
  greet();
  call_student("小周");
  return 0;
}
```

```bash
g++ call.cpp -o call
./call
```

会看到两行：点名开始，然后问小周。

括号里的 `name` 是参数，像点名时临时填上的那个名字。

练习：再写一个 `void dismiss()`，打印「点名结束」。在 `main` 里，问完小周之后调用它。

## 步骤 2：把结果交回来

函数可以交出一个值。交出什么类型，就写在名字左边，用 `return` 交回。`bool` 只有真和假，适合「是不是」。

```cpp
#include <iostream>

int longer(int a, int b) {
  if (a >= b) {
    return a;
  }
  return b;
}

bool needs_ruler(int cm) {
  return cm > 15;
}

int main() {
  std::cout << "较长的是 " << longer(12, 20) << "\n";
  if (needs_ruler(18)) {
    std::cout << "这节课要带尺子\n";
  }
  return 0;
}
```

会看到较长的是 20，并且要带尺子。`return` 一执行，函数就结束了。

练习：写 `int pages_left(int total, int done)`，交回还没写的页数。在 `main` 里用总数 10、已写 4 调用它并打印。

## 步骤 3：声明、头文件、两个源文件

函数可以分开放。`.hpp` 里只写声明，像目录：有这个函数，但不写步骤。`.cpp` 里写定义，也就是步骤本身。`main` 所在的文件包含头文件。

类比：课程表贴在门上（头文件），真正上课在教室里（另一个 cpp）。

`roster.hpp`：

```cpp
#include <string>

void greet();
void call_student(std::string name);
```

`roster.cpp`：

```cpp
#include <iostream>
#include <string>

void greet() {
  std::cout << "课间点名开始\n";
}

void call_student(std::string name) {
  std::cout << name << "，到了吗\n";
}
```

`main.cpp`：

```cpp
#include "roster.hpp"

int main() {
  greet();
  call_student("小周");
  return 0;
}
```

两个源文件要一起编译：

```bash
g++ main.cpp roster.cpp -o call
./call
```

引号写成 `"roster.hpp"`，表示这个头文件就在旁边，不是系统工具箱。

练习：把步骤 1 里的 `dismiss` 也加进头文件和 `roster.cpp`，并在 `main` 里调用。

## 讲完就停

不要在这一课讲类。
