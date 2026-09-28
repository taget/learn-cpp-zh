# 变量

所属单元：2. Variables  
上一课：`02-block-letters.md`  
下一课：`04-dog-years.md`

一次只讲一个步骤。

## 步骤 1：贴了标签的盒子

变量先起名字，再放进一个值。`int` 装整数。改盒子里的数，名字不用换。

类比：文具盒上贴着「铅笔」。盒子还是那个盒子，里面可以是 2 支，也可以改成 5 支。

```cpp
#include <iostream>

int main() {
  int pencils = 2;
  std::cout << "铅笔有 " << pencils << " 支\n";
  pencils = 5;
  std::cout << "现在有 " << pencils << " 支\n";
  return 0;
}
```

```bash
g++ vars.cpp -o vars
./vars
```

会看到 2 支，然后是 5 支。

名字用英文或拼音，不要用空格。先写类型，再写名字。

练习：做一个 `int`，表示今天有几节课。先打印 6，再改成 4，再打印一次。

## 步骤 2：小数，以及除法

`double` 装带小数点的数。两个整数相除，小数部分会被丢掉。除数写成 `100.0` 这样的小数，结果才能保留小数。

类比：150 厘米换成米。如果只用整数去除，像只用「整米」来量，零头被扔掉了。

```cpp
#include <iostream>

int main() {
  int cm = 150;
  double meters = cm / 100.0;
  std::cout << cm << " 厘米是 " << meters << " 米\n";
  return 0;
}
```

会看到 `1.5`。如果写成 `cm / 100`，结果会变成 `1`。

练习：设 `int` 克数是 250，换成千克（1000 克为 1 千克），用 `double` 打印结果。

## 步骤 3：从键盘读进盒子

`std::cin >>` 停下来等别人打字，回车后把字放进变量。变量要先准备好。

类比：老师提问，你把答案写进已经贴好标签的盒子。

```cpp
#include <iostream>

int main() {
  int count;
  double price;
  std::cout << "几支笔：";
  std::cin >> count;
  std::cout << "每支多少元：";
  std::cin >> price;
  double total = count * price;
  std::cout << "一共 " << total << " 元\n";
  return 0;
}
```

输入 `3` 和 `2.5`，会看到 `一共 7.5 元`。

这一单元后面会让学生把两个输入代进一个公式。练习先用文具总价，不要提前讲求根公式。

练习：问「身高是多少厘米」，读进一个 `double`，再打印「你输入的是 … 厘米」。

## 讲完就停

不要在这一课讲 `if`。
