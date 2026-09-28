# 神奇八号球

所属单元：3. Conditionals & Logic，项目「神奇八号球」  
上一课：`07-conditionals-and-logic.md`  
下一课：`09-sorting-hat.md`

一次只讲一个步骤。这一课把随机数和多档分支接在一起。回答用我们自己的短句。

## 步骤 1：抽一个数，再分档

`std::rand()` 给出一个不确定的整数。`% 4` 把它收成 0、1、2、3。程序每次运行可以不同。`std::srand(std::time(nullptr));` 让这一次启动和上一次不一样。

类比：课间抽纸条。盒子里只有四张，抽到哪张就读哪句。

```cpp
#include <cstdlib>
#include <ctime>
#include <iostream>

int main() {
  std::srand(std::time(nullptr));
  int slip = std::rand() % 4;
  if (slip == 0) {
    std::cout << "今天适合先做数学\n";
  } else if (slip == 1) {
    std::cout << "先喝水，再写作业\n";
  } else if (slip == 2) {
    std::cout << "问问同桌再决定\n";
  } else {
    std::cout << "先复习昨天的错题\n";
  }
  return 0;
}
```

```bash
g++ slips.cpp -o slips
./slips
```

多运行几次，四句话会轮着出现。

练习：再加一条你自己的建议，并把 `% 4` 改成 `% 5`，让第五条也有机会出现。

## 步骤 2：同一件事改用 switch

编号已经是 0 到 3 的整数，用 `switch` 会更整齐。判断内容不变。

```cpp
#include <cstdlib>
#include <ctime>
#include <iostream>

int main() {
  std::srand(std::time(nullptr));
  int slip = std::rand() % 4;
  switch (slip) {
    case 0:
      std::cout << "今天适合先做数学\n";
      break;
    case 1:
      std::cout << "先喝水，再写作业\n";
      break;
    case 2:
      std::cout << "问问同桌再决定\n";
      break;
    default:
      std::cout << "先复习昨天的错题\n";
      break;
  }
  return 0;
}
```

练习：把步骤 1 里你新加的那一条，也放进这个 `switch`。记得每路都写 `break`。

## 讲完就停

不要一次写满二十句。四句已经够学会分支。
