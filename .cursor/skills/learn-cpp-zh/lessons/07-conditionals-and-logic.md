# 条件与逻辑

所属单元：3. Conditionals & Logic  
上一课：`06-piggy-bank.md`  
下一课：`08-magic-8-ball.md`

一次只讲一个步骤。

## 步骤 1：如果……否则……

`if` 后面的括号里是一个真假问题。为真才执行紧挨着的那一块。`else` 是另一条路。比较两个数是否相等，用 `==`，不是 `=`。`=` 是把值放进盒子。

真假值的类型叫 `bool`。真写成 `true`，假写成 `false`。

类比：下雨就带伞，否则把伞留在教室。

```cpp
#include <iostream>

int main() {
  int coin = 0;
  if (coin == 0) {
    std::cout << "正面：课间去操场\n";
  } else {
    std::cout << "反面：课间去图书馆\n";
  }
  return 0;
}
```

```bash
g++ coin.cpp -o coin
./coin
```

`coin` 现在是 0，所以走正面。改成 1 会走反面。

练习：设 `int score = 72;`。不低于 60 就打印「及格」，否则打印「再练一次」。

## 步骤 2：好几档，用 else if

分档时，从高到低问。一旦有一档成立，后面的档就不再看。

类比：成绩条贴在墙上，先看「90 以上」，再看「60 以上」，最后才是其余。

```cpp
#include <iostream>

int main() {
  int score = 76;
  if (score >= 90) {
    std::cout << "优秀\n";
  } else if (score >= 60) {
    std::cout << "及格\n";
  } else {
    std::cout << "再练一次\n";
  }
  return 0;
}
```

会打印「及格」。如果先写 `score >= 60`，76 分也会被第一档接住，后面的「优秀」就没机会了。所以更严的条件要写在前面。

练习：用 `double ph = 6.5;`。小于 7 打印「偏酸」，大于 7 打印「偏碱」，等于 7 打印「中性」。

## 步骤 3：两个条件都要成立

`&&` 是「并且」，两边都为真，整个才为真。`||` 是「或者」，有一边为真即可。`!` 是「不是」。

闰年可以用这三条合在一起：能被 4 整除，并且不能被 100 整除，或者能被 400 整除。`%` 是求余数，余数是 0 就表示整除。

类比：出门要「带了学生证并且今天有课」。两条里缺一条就不算。

```cpp
#include <iostream>

int main() {
  int year;
  std::cout << "年份：";
  std::cin >> year;
  bool leap = (year % 4 == 0 && year % 100 != 0) || (year % 400 == 0);
  if (leap) {
    std::cout << year << " 是闰年\n";
  } else {
    std::cout << year << " 不是闰年\n";
  }
  return 0;
}
```

输入 `2024` 会看到是闰年。输入 `1900` 不是。输入 `2000` 是。

练习：问一个整数。它同时大于 0 并且小于 100 就打印「在 1 到 99 之间」，否则打印「不在这个范围」。

## 步骤 4：switch，按编号分岔

同一个整数要分成很多路时，可以用 `switch`。`case` 是某一个编号。`break` 表示这一路走完，不要掉进下一路。`default` 是没有任何编号对上。

类比：储物柜编号。对上 1 号开 1 号柜，对上 2 号开 2 号柜。忘了 `break`，柜门会一连串弹开。

```cpp
#include <iostream>

int main() {
  int day = 3;
  switch (day) {
    case 1:
      std::cout << "星期一：数学\n";
      break;
    case 2:
      std::cout << "星期二：语文\n";
      break;
    case 3:
      std::cout << "星期三：体育\n";
      break;
    default:
      std::cout << "这一天先看课表\n";
      break;
  }
  return 0;
}
```

会看到星期三的体育。

练习：用 `switch` 判断 `int seat = 2;`。1 打印「靠窗」，2 打印「中间」，3 打印「靠门」，其他编号打印「没有这个座位」。

## 讲完就停

随机数留到下一课。
