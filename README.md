# C++の学習まとめ
C++の学習まとめ

<a id="toc"></a>
## 目次
- [文法](#文法)
  - [関数](#関数)
- [演算子](#)
   - [算術演算子](#算術演算子)
   - [ビット演算子とシフト演算子](#ビット演算子と算術演算子)
- [参考文献](#参考文献)

## 文法
[↑ 目次へ戻る](#toc)

### ・関数
戻り値を返さない関数<br><br>
```cpp
#include <iostream>

void hello() {
    std::cout << "こんにちは！" << std::endl;
}

int main() {
    hello();
    return 0;
}
```
戻り値を返す関数<br><br>
```cpp
#include <iostream>

int add(int a, int b) {
    return a + b;
}

int main() {
    int result = add(3, 5);
    std::cout << "結果: " << result << std::endl;
    return 0;
}
```
[↑ 目次へ戻る](#toc)

### ・演算子

[↑ 目次へ戻る](#toc)

## 参考文献
[↑ 目次へ戻る](#toc)
- 『独習C++ 新版』翔泳社
