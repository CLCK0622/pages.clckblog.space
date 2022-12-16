---
title: "题解 P6322 【[COCI2006-2007#4] PRSTENI】"
date: 2020-08-07 17:58:26
---

~~我太蒻了~~
看见这么一道题，一开始想到传动比（已经忘了），然后~~随便一瞄~~认真分析一下样例，发现：

每一个答案其实就是其半径除以第一个半径，以分数形式表示即可。

证明一下：

众所周知，圆周长为 $ C = 2 \pi r $，设 $a$ 圆半径为 $R_A$，$b$ 圆半径为$R_B$，那么当 $a$ 转 $1$ 圈时，$b$ 转了 $2 \pi R_B / 2 \pi R_A$，即 $R_B/R_A$ 圈。

如何将分数化为最简呢？？？不难想到~~（这是这题考点……）~~，直接除以最大公倍数即可。

（啥？这个不会求？看：[gcd & lcm](https://www.luogu.com.cn/blog/zhongyi070622/gcd-and-lcm))

知道这点这题就 淼 了，话不多说，代码如下：
```
#include <iostream>
#include <algorithm>
using namespace std;
int n;
int s[1005];
int main() {
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> s[i];
    }
    for (int i = 1; i < n; i++) {
        int a, b;
        a = s[0];
        b = s[i];
        int g = __gcd(a, b); //正规函数写法参考上面链接）
        a /= g;
        b /= g;
        cout << a << "/" << b << endl;
    }
    return 0;
}
```
#### 完结撒花~