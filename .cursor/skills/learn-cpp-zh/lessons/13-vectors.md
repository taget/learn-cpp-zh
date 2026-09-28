# vector

所属单元：5. Vectors  
上一课：`12-fizz-buzz.md`  
下一课：`14-whale-talk.md`

一次只讲一个步骤。这一课只讲 `vector` 的编号、个数，以及边看边分类。

## 步骤 1：一排有编号的抽屉

`std::vector` 能按顺序放很多个同类型的值。需要 `#include <vector>`。编号从 0 开始，不是从 1。`.size()` 是抽屉个数。用上一课的 `for` 把每一格看一遍。

类比：成绩条钉成一排。第一格的编号是 0。问「有几格」用 `size()`。

```cpp
#include <iostream>
#include <vector>

int main() {
  std::vector<int> scores = {92, 75, 88};
  int n = static_cast<int>(scores.size());
  for (int i = 0; i < n; i++) {
    std::cout << "第 " << i << " 格：" << scores[i] << "\n";
  }
  return 0;
}
```

```bash
g++ scores.cpp -o scores
./scores
```

会看到第 0 格 92，第 1 格 75，第 2 格 88。`static_cast<int>` 只是把个数转成整数，方便和 `i` 比较。学生可以把它读成「个数」。

访问不存在的编号，例如 `scores[3]`，是错误的。最后一格是 `n - 1`。

练习：数一数有几个分数不低于 60，最后只打印这个人数。上面这三个数都及格，所以答案是 3。

## 步骤 2：边看边分成两类

循环里面可以再放 `if`。偶数和奇数用 `% 2` 区分。

```cpp
#include <iostream>
#include <vector>

int main() {
  std::vector<int> scores = {92, 75, 88, 59};
  int pass_count = 0;
  int n = static_cast<int>(scores.size());
  for (int i = 0; i < n; i++) {
    if (scores[i] >= 60) {
      pass_count++;
    }
  }
  std::cout << "及格有 " << pass_count << " 人\n";
  return 0;
}
```

会看到及格有 3 人。

练习：在同一个循环里再数出不及格的人数，并一起打印。

## 讲完就停

不要在这一课讲 `push_back`。那是下一课的第一步。
