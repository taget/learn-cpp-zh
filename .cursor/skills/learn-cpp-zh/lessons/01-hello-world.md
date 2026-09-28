# 你好，世界

所属单元：1. Hello World  
下一课：`02-block-letters.md`

一次只讲一个步骤。讲完练习就停。

## 步骤 1：第一张便条

电脑先看 `main` 里面的内容。`std::cout` 把文字送到屏幕。`<<` 像把字推出去。`\n` 是换行。`return 0;` 表示这张便条做完了。

类比：`main` 是作业纸的正文。`std::cout` 是把答案写到黑板上。

```cpp
#include <iostream>

int main() {
  // 这行是给人看的，编译时会跳过
  std::cout << "早读开始了\n";
  return 0;
}
```

保存为 `hello.cpp` 后：

```bash
g++ hello.cpp -o hello
./hello
```

屏幕上会出现：`早读开始了`

`#include <iostream>` 是去工具箱里拿出「输入输出」。`std::` 是姓，表示这个工具来自 C++ 标准库。这课先不要写 `using namespace std;`，免得看不清名字从哪来。`//` 后面到行尾是备注，不参加运行。

练习：把字符串改成你的名字，编译并运行。不要改 `main` 和 `return`。

## 步骤 2：多行和空格

可以写好几次 `std::cout`。空格会原样出现，电脑不会自动帮你对齐。

类比：每一行 `std::cout` 像在黑板上写一行通知，你空了几格，黑板就空几格。

```cpp
#include <iostream>

int main() {
  std::cout << "早餐  豆浆\n";
  std::cout << "午餐  米饭\n";
  std::cout << "晚餐  面条\n";
  return 0;
}
```

运行后能看到三行。两字之间那两个空格也会留着。

练习：打印明天的三节课，每节课一行，课名前面留两个空格。

## 讲完就停

不要在这一课讲变量。
