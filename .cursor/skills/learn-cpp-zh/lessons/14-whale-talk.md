# 鲸鱼语

所属单元：5. Vectors，项目「鲸鱼语」  
上一课：`13-vectors.md`  
下一课：`15-functions.md`

大纲里的这个项目是：从一句话里把元音挑出来，放进新的 `vector`。下面用一句新的英文做简化版，不追加额外规则。一次只讲一个步骤。

## 步骤 1：符合条件就排到队尾

`push_back` 把一个新元素加到 `vector` 的最后。外层循环看句子里的每个字符，内层循环看元音表。对上了就收进 `picked`。

`char` 装一个字符，用单引号，例如 `'a'`。字符串用双引号。

类比：值日生看每一名进门的同学，名单上有的才领到一张贴纸，贴纸按到达顺序贴成一排。

这一课用英文字母，因为一个字母正好占一格。汉字一个字会占好几格，现在先不处理。

```cpp
#include <iostream>
#include <string>
#include <vector>

int main() {
  std::string sentence = "I like music";
  std::vector<char> vowels = {'a', 'e', 'i', 'o', 'u'};
  std::vector<char> picked;
  int n = static_cast<int>(sentence.size());
  int m = static_cast<int>(vowels.size());
  for (int i = 0; i < n; i++) {
    for (int j = 0; j < m; j++) {
      if (sentence[i] == vowels[j]) {
        picked.push_back(sentence[i]);
      }
    }
  }
  int kmax = static_cast<int>(picked.size());
  for (int k = 0; k < kmax; k++) {
    std::cout << picked[k];
  }
  std::cout << "\n";
  return 0;
}
```

```bash
g++ vowels.cpp -o vowels
./vowels
```

会看到 `ieui`。大写的 `I` 不在小写元音表里，所以没被收进去。空格也不是元音。

练习：不要收元音了。改成只把字符 `'i'` 放进 `picked`，并打印结果。这句话里有两个小写 `i`，结果应是 `ii`。

## 讲完就停

学生打印出 `mm` 就可以。不要再加「某个元音要收集两次」之类的新规则。
