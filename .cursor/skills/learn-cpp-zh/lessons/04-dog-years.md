# 狗狗年龄

所属单元：2. Variables，项目「狗狗年龄」  
上一课：`03-variables.md`  
下一课：`05-quadratic-formula.md`

这一课把名字和年龄拼进一句话。一次只讲一个步骤。

## 步骤 1：文字盒子和整数盒子

`std::string` 装一串字，需要 `#include <string>`。整数和文字可以用 `<<` 接在同一句输出里。

类比：自我介绍有两张卡片，一张写名字，一张写年龄。读出来时把它们连成一句。

下面用一个很粗的算法：狗的 1 岁大约当成 7 个人年。这不是精确科学，只用来练习乘法。

```cpp
#include <iostream>
#include <string>

int main() {
  std::string name = "豆豆";
  int dog_age = 3;
  int human_age = dog_age * 7;
  std::cout << name << " 大约相当于 " << human_age << " 个人年\n";
  return 0;
}
```

```bash
g++ dog.cpp -o dog
./dog
```

会看到：`豆豆 大约相当于 21 个人年`

练习：把狗的名字改成你家附近一只狗的名字，年龄改成 4，先心算再运行核对。

## 步骤 2：让使用者自己填

名字和年龄都可以从键盘读入。先打印提示，再 `std::cin`。

```cpp
#include <iostream>
#include <string>

int main() {
  std::string name;
  int dog_age;
  std::cout << "狗的名字：";
  std::cin >> name;
  std::cout << "狗的年龄：";
  std::cin >> dog_age;
  int human_age = dog_age * 7;
  std::cout << name << " 大约相当于 " << human_age << " 个人年\n";
  return 0;
}
```

`std::cin >> name` 读到空格为止。名字先用一个词，例如 `doudou`。

练习：运行程序，输入一只狗的名字和年龄，看打印出的人年对不对。

## 讲完就停

不要把换算公式换成别的动物，除非学生已经做完练习。
