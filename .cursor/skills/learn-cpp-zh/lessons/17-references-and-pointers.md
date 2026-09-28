# 引用与指针

所属单元：8. References & Pointers，包含项目「消音」  
上一课：`16-classes-and-objects.md`  
下一课：`18-tic-tac-toe.md`（选学）

一次只讲一个步骤。这一课最容易混的是符号 `&`：它贴在不同地方，意思不同。

## 步骤 1：每个变量都有地址

变量住在内存里的一格。`&score` 是问「这格的编号是多少」。编号通常印成一串十六进制，每次运行可能不同。看懂「这是地址」就行，不用背那一串数字。

类比：储物柜上的柜号。分数是柜子里的卷子，`&score` 是柜门上的号码。

```cpp
#include <iostream>

int main() {
  int score = 92;
  std::cout << "分数 " << score << "\n";
  std::cout << "柜号 " << &score << "\n";
  return 0;
}
```

```bash
g++ addr.cpp -o addr
./addr
```

第一行是 92。第二行是一串地址。

练习：再做一个 `int seat = 12;`，把座位号和它的地址都打印出来。

## 步骤 2：指针是写着柜号的纸条

`int*` 是「装得下 int 柜号」的纸条。`int* note = &score;` 把柜号抄到纸条上。`*note` 是顺着柜号去看里面的数。

类比：你不把卷子带回家，只抄下柜号。回家想看分数时，按柜号再去开柜。

```cpp
#include <iostream>

int main() {
  int score = 92;
  int* note = &score;
  std::cout << "纸条上的柜号 " << note << "\n";
  std::cout << "打开后看到 " << *note << "\n";
  return 0;
}
```

打开后会看到 92。这里的 `*` 出现两次：写类型 `int*` 时，表示「这是指针」；写 `*note` 时，表示「去那一格看」。

练习：不改 `score = 92` 那一行，试着写 `*note = 80;`，再打印 `score`。柜子里的数会跟着变成 80。

## 步骤 3：引用是同一个盒子的另一个名字

参数写成 `int &bonus` 时，`bonus` 不是新盒子，而是调用处那个盒子的别名。函数里改 `bonus`，外面的变量一起变。

这和步骤 1 的 `&` 不一样。贴在类型旁边，是引用。放在已有变量前面，是取地址。

类比：同桌给「语文分」起了个小名「卷面分」。改卷面分，就是在改语文分，不是另抄一份。

```cpp
#include <iostream>

void add_five(int &score) { score = score + 5; }

int main() {
  int chinese = 80;
  add_five(chinese);
  std::cout << chinese << "\n";
  return 0;
}
```

会打印 85。如果把参数改成 `int score` 而没有 `&`，函数里改的是复印件，`main` 里的 `chinese` 仍是 80。

练习：写 `void cut_one(int &pencils)`，让枝数减少 1。在 `main` 里从 4 调用一次，打印结果应为 3。

## 步骤 4：消音，改的是原来那句话

大纲里的消音项目要在函数里改掉句子中的一个词，所以参数必须是引用。否则 `main` 里的句子不会变。

这一课仍用英文字母，一个字母占一格。`cover` 从某一格开始，把后面几格换成 `*`。

```cpp
#include <iostream>
#include <string>

void cover(std::string &text, int start, int length) {
  for (int i = 0; i < length; i++) {
    text[start + i] = '*';
  }
}

int main() {
  std::string sentence = "please bring a pen";
  cover(sentence, 7, 5);
  std::cout << sentence << "\n";
  return 0;
}
```

`bring` 从第 7 格开始，长度 5。运行后会看到 `please ***** a pen`。

如果 `cover` 的第一个参数去掉 `&`，打印出来的仍是原来的 `please bring a pen`。

练习：把句子改成 `do not forget the pen`，自己数一数 `forget` 从第几格开始、有多长，调用 `cover` 把它换成星号。空格也算一格，编号从 0 开始。

## 讲完就停

不要讲 `new`、`delete`，也不要讲指针的加减。
