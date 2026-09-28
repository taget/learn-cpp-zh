# 分院帽

所属单元：3. Conditionals & Logic，项目「分院帽」  
上一课：`08-magic-8-ball.md`  
下一课：`10-rock-paper-scissors.md`

大纲里的这个项目是：根据回答把人分到不同组。这里改成兴趣社团，不依赖某本小说里的情节。一次只讲这个步骤。

## 步骤 1：读进一个词，再比较

`std::string` 也可以用 `==` 比较。先问一个问题，再按回答进入不同社团。对不上的回答走 `else`。

类比：报名表上勾一个爱好，老师按勾选把你分到对应教室。

```cpp
#include <iostream>
#include <string>

int main() {
  std::string hobby;
  std::cout << "输入 basketball、calligraphy 或 science：";
  std::cin >> hobby;
  if (hobby == "basketball") {
    std::cout << "分到篮球社团\n";
  } else if (hobby == "calligraphy") {
    std::cout << "分到书法社团\n";
  } else if (hobby == "science") {
    std::cout << "分到科学社团\n";
  } else {
    std::cout << "先去音乐社团看看\n";
  }
  return 0;
}
```

```bash
g++ clubs.cpp -o clubs
./clubs
```

输入 `science` 会看到科学社团。大小写必须一致，`Science` 对不上 `science`。

这一课用拼音或英文单词做输入，是为了让 `>>` 一次读完一个词。

练习：再加一个社团 `music`。输入 `music` 时不要掉进最后的 `else`。

## 讲完就停

不要要求学生一次回答三个问题。
