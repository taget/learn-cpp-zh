# 石头剪刀布蜥蜴史波克

所属单元：3. Conditionals & Logic，项目「石头剪刀布蜥蜴史波克」  
上一课：`09-sorting-hat.md`  
下一课：`11-loops.md`

一次只讲一个步骤。先学会比较两个选择。五种手势是同一想法的加长，不要在第一步就写完整胜负表。

## 步骤 1：两个选择比一次

用数字代表手势：1 石头，2 剪刀，3 布。先只判断一种赢法：石头砸剪刀。两边数字一样就是平局。

类比：两个人同时伸手，先看是不是同一种，再看谁赢过谁。

```cpp
#include <iostream>

int main() {
  int mine;
  int yours;
  std::cout << "你出 1 石头 2 剪刀 3 布：";
  std::cin >> mine;
  std::cout << "同桌出 1 石头 2 剪刀 3 布：";
  std::cin >> yours;
  if (mine == yours) {
    std::cout << "平局\n";
  } else if (mine == 1 && yours == 2) {
    std::cout << "石头砸剪刀，你赢了\n";
  } else if (mine == 2 && yours == 1) {
    std::cout << "剪刀被石头砸了，你输了\n";
  } else {
    std::cout << "这一种胜负还没写\n";
  }
  return 0;
}
```

```bash
g++ rps.cpp -o rps
./rps
```

你出 1、同桌出 2，会看到你赢了。

练习：补上「布包石头」。你出 3 且同桌出 1 时，打印你赢了。其他没写的组合可以仍走最后一句。

## 步骤 2：手势变多时，先用 switch 说出名字

蜥蜴和史波克让选择变多。先不要背整张胜负表。用 `switch` 把编号说成名字，确认每一路都有 `break`。

编号：1 石头，2 剪刀，3 布，4 蜥蜴，5 史波克。

```cpp
#include <iostream>

int main() {
  int choice = 4;
  switch (choice) {
    case 1:
      std::cout << "石头\n";
      break;
    case 2:
      std::cout << "剪刀\n";
      break;
    case 3:
      std::cout << "布\n";
      break;
    case 4:
      std::cout << "蜥蜴\n";
      break;
    case 5:
      std::cout << "史波克\n";
      break;
    default:
      std::cout << "没有这种手势\n";
      break;
  }
  return 0;
}
```

练习：把 `choice` 改成从键盘读入。输入 5 时应打印「史波克」。

## 讲完就停

学生没把步骤 1 的练习做完之前，不要展开五种手势的全部胜负。
