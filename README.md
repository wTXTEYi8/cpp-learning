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
  - [getterとsetter](#getterとsetter)
  - [コンストラクター](#コンストラクター)
  - [デストラクター](#デストラクター)
- [応用](#応用)
  - [フラグ管理](#フラグ管理)
  - [ビット演算](#ビット演算)
  - [bit全探索](#bit全探索)
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
| 演算子 | 説明 |
|--------|------|
| `+` | 加算 |
| `-` | 減算 |
| `*` | 乗算 |
| `/` | 除算 |
| `%` | 剰余 |
| `++` | インクリメント |
| `--` | デクリメント |

<br>

### ビット演算子
| 演算子 | 説明 |
|--------|------|
| `&` | AND |
| `\|` | OR |
| `^` | XOR |
| `~` | NOT |
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
    std::cout << "~b    = " << (~b) << std::endl;    // 0101
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
    int bit = 0b1010;

    std::bitset<4> b(bit);
    std::cout << "b << 2 = " << (b << 2) << std::endl; // 1000
    std::cout << "n >> 2 = " << (b >> 2) << std::endl; // 0010
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

    std::cout << "名前: " <<  ptr->name << std::endl;
    std::cout << "年齢: " << ptr->age << std::endl;

    return 0;
}
```

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

    std::cout << "名前: " << p.name << std::endl;
    std::cout << "年齢: " << p.age << std::endl;

    return 0;
}
```

[↑ 目次へ戻る](#toc)

### ポインター
```cpp
#include <iostream>

int main(){
int num = 10;
int* ptr;
ptr = &num;
std::cout << "num  : " << num << std::endl;
std::cout << "ptr  : " << ptr << std::endl;
std::cout << "*ptr : " << *ptr << std::endl;
std::cout << "&num : " << &num << std::endl; // 変数numのアドレス
}
```
[↑ 目次へ戻る](#toc)

### クラス
```cpp
#include <iostream>
#include <string>

class Person {
        std::string name;
        int age;

public:
        void setData(std::string n, int a) {
                name = n;
                age = a;
        }

        void show() {
                std::cout << "name : " << name << std::endl;
                std::cout << "age : " << age << std::endl;
        }
};

int main() {
        Person p;
        p.setData("Taro", 20);
        p.show();
}
```
[↑ 目次へ戻る](#toc)

### getterとsetter
```cpp
#include <iostream>

class person
{
        std::string address;
        int age;

        public:
        std::string get_address();
        void set_address(std::string new_address);

        int get_age();
        void set_age(int new_age);
};

std::string person::get_address()
{
        return address;
}

void person::set_address(std::string new_address)
{
        address = new_address;
}

int person::get_age()
{
        return age;
}

void person::set_age(int new_age)
{
        age = new_age;
}

int main()
{
        person takashi;

        takashi.set_address("TOKYO");
        takashi.set_age(20);

        person* ptr = &takashi;

        std::cout << "住所: " << ptr->get_address() << std::endl;
        std::cout << "年齢: " << ptr->get_age() << std::endl;
}
```
[↑ 目次へ戻る](#toc)

### コンストラクター
[↑ 目次へ戻る](#toc)

### デストラクター
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

### フラグ管理
|やりたいこと|実装|
|---------|-----|
| `ビット bit に i 番目のフラグが立っているかどうか` | if (bit & (1<<i)) |
| `ビット bit に i 番目のフラグが消えているかどうか` | if (!(bit & (1<<i))) |
| `ビット bit に i 番目のフラグを立てる` | bit｜= (1<<i) |
| `ビット bit に i 番目のフラグを消す` | bit &= ~(1<<i) |

[↑ 目次へ戻る](#toc)

### ビット演算
| ビット列 | 値 |
|---------|-----|
| `0000` | 0 |
| `0001` | 1 |
| `0010` | 2 |
| `0011` | 3 |
| `0100` | 4 |
| `0101` | 5 |
| `0110` | 6 |
| `0111` | 7 |
| `1000` | -8 |
| `1001` | -7 |
| `1010` | -6 |
| `1011` | -5 |
| `1100` | -4 |
| `1101` | -3 |
| `1110` | -2 |
| `1111` | -1 |

LSB(Least Significant Bit)の求め方
```cpp
#include <iostream>
#include <bitset>

int LSB(int n) {
        return n & -n;
}

int main() {
        int n = 10;

        std::cout << "LSB : " << LSB(n) << std::endl;
}
```
[↑ 目次へ戻る](#toc)

### bit全探索
全部で
```math
2^5=32通り
```
| 4 | 3 | 2 | 1 | 0 |
|--------|------|--------|------|--------|
| 0 | 0 | 0 | 0 | 0 |
| 0 | 0 | 0 | 0 | 1 |
| 0 | 0 | 0 | 1 | 0 |
| 1 | 1 | 1 | 1 | 1 |
```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
        int n = 5;

        for (int bit = 0; bit < (1<<n); ++bit) {

                vector<int> S;
                for (int i = 0; i < n; ++i) {
                        if (bit & (1<<i)) {
                                S.push_back(i);
                        }
                }
                cout << bit << ": {";
                for (int i = 0; i < (int)S.size(); ++i) {
                        cout << S[i] << " ";
                }
        cout << "}" << endl;
        }

}
```
[↑ 目次へ戻る](#toc)

## 参考文献
- 『独習C++ 新版』翔泳社<br><br>
- https://qiita.com/drken/items/7c6ff2aa4d8fce1c9361#3-%E3%83%93%E3%83%83%E3%83%88%E6%BC%94%E7%AE%97%E3%82%92%E7%94%A8%E3%81%84%E3%81%9F%E3%83%95%E3%83%A9%E3%82%B0%E7%AE%A1%E7%90%86<br><br>
[↑ 目次へ戻る](#toc)
