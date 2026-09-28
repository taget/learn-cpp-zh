# 存钱罐

所属单元：2. Variables，项目「存钱罐」  
上一课：`05-quadratic-formula.md`  
下一课：`07-conditionals-and-logic.md`

一次只讲这个步骤。这一课练习：准备好几个变量，读入多次，再做一次算术。

## 步骤 1：把不同硬币加在一起

一元硬币按 1 元一只算，五角硬币按 0.5 元一只算。个数用 `int`，总金额用 `double`。

类比：存钱罐倒在桌上，先数清每种硬币有几只，再换成一共多少元。

```cpp
#include <iostream>

int main() {
  int yuan_coins;
  int jiao_coins;
  std::cout << "一元硬币有几只：";
  std::cin >> yuan_coins;
  std::cout << "五角硬币有几只：";
  std::cin >> jiao_coins;
  double total = yuan_coins + jiao_coins * 0.5;
  std::cout << "一共 " << total << " 元\n";
  return 0;
}
```

```bash
g++ bank.cpp -o bank
./bank
```

输入 `2` 和 `3`，会看到 `一共 3.5 元`。先乘 0.5，再加一元硬币的个数。

练习：再问「一角硬币有几只」。一角按 0.1 元算，加进总额后再打印。

## 讲完就停

不要在这一课讲汇率表或 `if`。
