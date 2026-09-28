# 循环

所属单元：4. Loops  
上一课：`10-rock-paper-scissors.md`  
下一课：`12-fizz-buzz.md`

一次只讲一个步骤。

## 步骤 1：while，条件还在就再来一次

`while` 先看条件。条件为真，就做循环体，然后回来再看。条件为假，就跳过去。

类比：储物柜密码不对，就再问一次。对了才停。下面的 `2468` 只是练习用的假密码。

```cpp
#include <iostream>

int main() {
  int pin = 0;
  std::cout << "储物柜密码：";
  std::cin >> pin;
  while (pin != 2468) {
    std::cout << "不对，再试一次：";
    std::cin >> pin;
  }
  std::cout << "柜子开了\n";
  return 0;
}
```

```bash
g++ pin.cpp -o pin
./pin
```

先输入一个错的数，程序会再问。输入 `2468` 才结束。

如果一直输错，它会一直问。这是 `while` 的特点。

练习：加一个 `int tries = 0;`。每问错一次就 `tries++`。循环改成「密码不对，并且尝试次数小于 3」。超过 3 次就不要再问。

## 步骤 2：while 也可以用来数数

循环里要有一句让数字靠近终点，否则会停不下来。`i++` 表示 i 增加 1。

类比：从 0 数到 9，每数一个就在本子上写下它的平方，数完 10 个就合上本子。

```cpp
#include <iostream>

int main() {
  int i = 0;
  while (i < 5) {
    std::cout << i << " 的平方是 " << i * i << "\n";
    i++;
  }
  return 0;
}
```

会打印 0 到 4 的平方。忘了 `i++`，i 永远小于 5，程序就停不下来。停不下来时，可以在终端按 Ctrl+C。

练习：把上限改成 10，让它打印 0 到 9 的平方。

## 步骤 3：for，把起点、条件和步进写在一起

`for (起点; 条件; 步进)` 是数数循环的紧凑写法。和步骤 2 是同一件事。

类比：眼保健操做 5 次。第几次，写在括号里就行。

```cpp
#include <iostream>

int main() {
  for (int i = 1; i <= 5; i++) {
    std::cout << "第 " << i << " 次：把椅子推进去\n";
  }
  return 0;
}
```

会看到第 1 次到第 5 次。

倒数就是步进改成 `i--`，条件改成还没数到头：

```cpp
#include <iostream>

int main() {
  for (int i = 3; i >= 1; i--) {
    std::cout << i << "\n";
  }
  std::cout << "放学\n";
  return 0;
}
```

会依次看到 3、2、1，然后是「放学」。

练习：用 `for` 从 5 倒数到 1，每行一个数，最后一行打印「集合」。

## 讲完就停

不要在这一课同时讲 `vector`。
