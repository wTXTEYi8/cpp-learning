# C++の学習まとめ
C++の学習まとめ

<a id="toc"></a>
## 目次
- [文法](#文法)
  - [関数](#関数)
  - [演算子](#演算子)
    - [算術演算子](#算術演算子)
    - [ビット演算子](#ビット演算子)
    - [シフト演算子](#シフト演算子)
  - [ポインター](#ポインター)
  - [コンソールからの入力](#コンソールからの入力)
  - [構造体](#構造体)
  - [クラス](#クラス)
- [応用](#応用)
- [参考文献](#参考文献)

## 文法
[↑ 目次へ戻る](#toc)

### ・関数
- 戻り値を返さない関数<br><br>
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
- 戻り値を返す関数<br><br>
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

### 演算子
[↑ 目次へ戻る](#toc)
#### 算術演算子
| 演算子 | 説明 | 例 | 結果 |
|--------|------|------|--------|
| `+` | 加算 | `3 + 2` | `5` |
| `-` | 減算 | `3 - 2` | `1` |
| `*` | 乗算 | `3 * 2` | `6` |
| `/` | 除算 | `3 / 2` | `1` |
| `%` | 剰余 | `7 % 3` | `1` |

<br>

### ビット演算子
| 演算子 | 説明 | 例 | 結果 |
|--------|------|------|--------|
| `&` | AND（ビットごと） | `6 & 3` | `2` |
| `\|` | OR（ビットごと） | `6 \| 3` | `7` |
| `^` | XOR（排他的 OR） | `6 ^ 3` | `5` |
| `~` | NOT（ビット反転） | `~6` | `-7` |
<br>

```cpp
#include <iostream>
#include <bitset>

int main() {
    int bit1 = 0b1111;
    int bit2 = 0b1010;

    std::bitset<4> a(bit1);
    std::bitset<4> b(bit2);

    std::cout << "a & b = " << (a & b) << std::endl; // 1010
    std::cout << "a | b = " << (a | b) << std::endl; // 1111
    std::cout << "a ^ b = " << (a ^ b) << std::endl; // 0101
    std::cout << "~a    = " << (~a) << std::endl;    // 0000
}
```

### シフト演算子
| 演算子 | 説明 | 例 | 結果 |
|--------|------|------|--------|
| `<<` | 左シフト | `3 << 1` | `6` |
| `>>` | 右シフト | `6 >> 1` | `3` |

```cpp
#include <iostream>
#include <bitset>

int main(){
std::bitset<4> b("1110");
std::cout << b << std::endl;
std::cout << (b << 2) << std::endl;
std::cout << (b >> 2) << std::endl;
}
```

<br>

[↑ 目次へ戻る](#toc)


### コンソールからの入力
```cpp
#include <iostream>

int main() {
    int i;    
    std::cin >> i; 
    std::cout << i; 
    return 0;
}
```
[↑ 目次へ戻る](#toc)
### 構造体
```cpp
#include <iostream>
#include <string>

struct Person {
    std::string name;
    int age;
};

int main() {
    Person p;
    p.name = "Taro";
    p.age = 20;
    Person* ptr = &p;

    std::cout << ptr->name << std::endl;
    std::cout << ptr->age << std::endl;

    return 0;
}
```
[↑ 目次へ戻る](#toc)

### ポインター
```cpp
#include <iostream>

int main(){
int num = 10;
int *ptr;
ptr = &num;
std::cout << "num  : " << num << std::endl;
std::cout << "ptr  : " << ptr << std::endl;
std::cout << "*ptr : " << *ptr << std::endl;
std::cout << "&num : " << &num << std::endl;
}
```
[↑ 目次へ戻る](#toc)

### クラス
```cpp
#include <iostream>
#include <string>

class Person {
private:
    std::string name;
    int age;

public:
    void setData(std::string n, int a) {
        name = n;
        age = a;
    }

    void show() {
        std::cout << name << " (" << age << ")" << std::endl;
    }
};

int main() {
    Person p;
    p.setData("Taro", 20);
    p.show();
}
```
[↑ 目次へ戻る](#toc)

### 応用
```cpp
#include <iostream>
#include <termios.h>
#include <unistd.h>

char getch() {
    termios oldt, newt;

    tcgetattr(STDIN_FILENO, &oldt);
    newt = oldt;

    newt.c_lflag &= ~(ICANON | ECHO);
    tcsetattr(STDIN_FILENO, TCSANOW, &newt);

    char c = getchar();

    tcsetattr(STDIN_FILENO, TCSANOW, &oldt);

    return c;
}

int main() {
    std::cout << "キーを押してください: ";
    char c = getch();
    std::cout << "\n入力されたキー: " << c << std::endl;
    return 0;
}
```
[↑ 目次へ戻る](#toc)

## 参考文献
- 『独習C++ 新版』翔泳社<br><br>
[↑ 目次へ戻る](#toc)
