# 类与对象

所属单元：7. Classes & Objects  
上一课：`15-functions.md`  
下一课：`17-references-and-pointers.md`

大纲里的项目是做一张能展示的个人资料。这里做成「同学名片」：数据放在一起，动作用成员函数来做。一次只讲一个步骤。

## 步骤 1：图纸和学生本人

类是图纸。对象是按图纸做出的一个具体同学。写在 `private` 里的数据，外面不要直接改。写在 `public` 里的函数，外面可以调用。

构造函数和类同名，没有返回类型。创建对象时自动执行，用来把名字放好。

类比：学生证的空白模板是类。写上「小周」之后，那一张证是对象。别人看证，不直接往证的夹层里塞纸，而是请你自己添加爱好。

```cpp
#include <iostream>
#include <string>
#include <vector>

class Classmate {
 private:
  std::string name;
  std::vector<std::string> hobbies;

 public:
  Classmate(std::string new_name) { name = new_name; }

  void add_hobby(std::string hobby) { hobbies.push_back(hobby); }

  void show() {
    std::cout << "姓名：" << name << "\n";
    std::cout << "爱好：\n";
    int n = static_cast<int>(hobbies.size());
    for (int i = 0; i < n; i++) {
      std::cout << "- " << hobbies[i] << "\n";
    }
  }
};

int main() {
  Classmate mate("小周");
  mate.add_hobby("跳绳");
  mate.show();
  return 0;
}
```

```bash
g++ card.cpp -o card
./card
```

会看到姓名小周，爱好下面一行「跳绳」。

`mate.add_hobby` 里的点，表示「请这个对象做这件事」。

练习：再添加一个爱好「画画」，然后调用一次 `show`。不要在 `main` 里直接写 `mate.name`。

## 步骤 2：名片的函数也可以分到头文件

和上一课一样：声明放进 `classmate.hpp`，定义放进 `classmate.cpp`，`main.cpp` 只负责创建对象。类的成员函数在类外面定义时，名字要写成 `Classmate::show`。`::` 表示「这个函数属于 Classmate」。

这一步学生如果还容易把括号写错，可以先停留在步骤 1。

练习：把 `show` 的函数体从类里挪到一个 `classmate.cpp`。头文件里只留下 `void show();`。三个文件一起编译：

```bash
g++ main.cpp classmate.cpp -o card
```

## 讲完就停

不要讲继承。这门课的类到「数据和成员函数」为止。
