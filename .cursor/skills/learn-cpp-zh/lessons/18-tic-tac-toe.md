# 井字棋

所属单元：挑战项目，在前八个单元之后  
上一课：`17-references-and-pointers.md`  
没有下一课。

学生没学完前面的单元时，不要主动打开这一课。一次只讲一个步骤。棋盘用已经学过的 `vector`、函数和引用来做。

## 步骤 1：先把空棋盘印出来

九个格子装在 `vector` 里，用 `.` 表示空位。打印函数只负责显示，不负责判断输赢。

类比：先在纸上画好九宫格，再轮流落子。今天先把格子画出来。

```cpp
#include <iostream>
#include <string>
#include <vector>

void show(std::vector<std::string> &cell) {
  std::cout << cell[0] << "|" << cell[1] << "|" << cell[2] << "\n";
  std::cout << cell[3] << "|" << cell[4] << "|" << cell[5] << "\n";
  std::cout << cell[6] << "|" << cell[7] << "|" << cell[8] << "\n";
}

int main() {
  std::vector<std::string> cell(9, ".");
  show(cell);
  return 0;
}
```

```bash
g++ ttt.cpp -o ttt
./ttt
```

会看到三行，每行三个点，中间用 `|` 分开。`cell(9, ".")` 表示准备 9 格，每格都是点。

练习：把第 0 格改成 `X`，再调用 `show`。左上角应变成 X。

## 步骤 2：按 1 到 9 落一颗子

人习惯从 1 数到 9，`vector` 从 0 数起，所以落子时用「输入的数减 1」。函数要改到原来的棋盘，参数用引用。

```cpp
#include <iostream>
#include <string>
#include <vector>

void show(std::vector<std::string> &cell) {
  std::cout << cell[0] << "|" << cell[1] << "|" << cell[2] << "\n";
  std::cout << cell[3] << "|" << cell[4] << "|" << cell[5] << "\n";
  std::cout << cell[6] << "|" << cell[7] << "|" << cell[8] << "\n";
}

void place(std::vector<std::string> &cell, int pos, std::string mark) {
  cell[pos - 1] = mark;
}

int main() {
  std::vector<std::string> cell(9, ".");
  int pos;
  std::cout << "把 X 放在 1 到 9：";
  std::cin >> pos;
  place(cell, pos, "X");
  show(cell);
  return 0;
}
```

输入 `5`，正中间是 X，其余仍是点。

练习：再问一次位置，把 `O` 放下去，然后再次 `show`。先不要判断谁赢了。

## 讲完就停

学生想继续时，再提示一句：某一行三个格子相同，并且不是点，就可以先只检查第一行。不要把整盘胜负和全部轮次一次写完。
