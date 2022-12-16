---
title: "题解 CF424A 【Squats】"
date: 2022-04-20 16:15:28
---

难度：橙

### 一道简单的字符串模拟问题。

给定一个长度为 $n$ 的字符串 $s$ 作为输入，只含有字符 `x` 或 `X` ，要求：最少需要多少次操作，使字符串中的 `x` 与 `X` 的数量相同，输出最少操作数以及操作完的字符串。

思路：统计原始字串中的 `x` 与 `X` 的数量，因为长度 $n \mod 2 = 0$ ，所以 $|n_x - n_X| \mod 2 = 0$ ，且操作一次会使二者同时变化 $1$ ，所以显而易见，答案要求的操作数就是 $\frac{|n_x - n_X|}{2}$ ，然后进行遍历操作，题目应该有SPJ，输出正确即可。

```cpp
#include <cmath>
#include <iostream>
#include <algorithm>
using namespace std;
int n;
string s;
int nx, nX;
int main() {
    cin >> n >> s;
    for (int i = 0; i < s.size(); i++) {
        if (s[i] == 'x') {
            nx++;
        } else if (s[i] == 'X') {
            nX++;
        }
    }
    if (nx < nX) {
        cout << (nX - nx) / 2 << endl; //独树一帜的操作计数法，else部分同。
        int cnt = 0;
        for (int i = 0; i < s.size(); i++) {
            if (cnt == (nX - nx) / 2) break; //符合条件即可结束操作，else部分同。
            if (s[i] == 'X') {
                s[i] = 'x'; cnt++; //WA了几次居然是操作写反了呜呜呜
            }
        }
        cout << s << endl;
    } else {
        cout << (nx - nX) / 2 << endl;
        int cnt = 0;
        for (int i = 0; i < s.size(); i++) {
            if (cnt == (nx - nX) / 2) break;
            if (s[i] == 'x') {
                s[i] = 'X'; cnt++;
            }
        }
        cout << s << endl;
    }
    return 0;
}
```

完结撒花～

管理大大求过 `：D`