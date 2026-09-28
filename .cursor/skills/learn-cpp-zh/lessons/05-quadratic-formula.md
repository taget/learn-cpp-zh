# 求根公式

所属单元：2. Variables，项目「求根公式」  
上一课：`04-dog-years.md`  
下一课：`06-piggy-bank.md`

一次只讲这个步骤。方程课上的求根公式可以直接用，这不是新的数学发明。

## 步骤 1：把 a、b、c 代进公式

一元二次方程写成 `a x² + b x + c = 0`。先算判别式 `b*b - 4*a*c`。它大于 0 时有两个实数根。开平方用 `std::sqrt`，需要 `#include <cmath>`。

类比：a、b、c 是三个已知数，像菜谱里的三样调料。求根公式是固定步骤，电脑按步骤算出 x。

```cpp
#include <cmath>
#include <iostream>

int main() {
  double a = 1;
  double b = -3;
  double c = 2;
  double delta = b * b - 4 * a * c;
  double x1 = (-b + std::sqrt(delta)) / (2 * a);
  double x2 = (-b - std::sqrt(delta)) / (2 * a);
  std::cout << "两个根是 " << x1 << " 和 " << x2 << "\n";
  return 0;
}
```

```bash
g++ quad.cpp -o quad
./quad
```

会看到两个根：`2` 和 `1`。这一课先只做判别式大于 0 的情况。小于 0 时先不要开方。

练习：把 a、b、c 改成 `1`、`-5`、`6`。运行前先说出你预计的两个根，再运行核对。

## 讲完就停

学生没要求时，不要加 `std::cin`，也不要处理判别式小于 0。
