---
title: "题解 CF466B 【Wonder Room】"
date: 2022-10-24 17:05:55
---

~~水题~~

如题，每个同学需要 $6$ 平方米的面积，现在有 $n$ 个同学，因此可以直接读入时将 $n\times6$ 计算。

因为 $S=a\times b$ ，因此只需要令 $a\gt b$ 后直接枚举 $a$ 的值即可。

注意：枚举时为了保证 $a \gt b$ ，只需要将 $a$ 枚举到 $\sqrt{6n}$ （此时为 $\sqrt{n}$ ）即可。

最后直接输出，注意取整时避免因向下取整导致面积小于原始面积。

以上，完结撒花～


```cpp
#include <iostream>
#include <cmath>
#include <algorithm>
using namespace std;
long long a, b, n;
bool fl = 0;
long long minn=0x3f3f3f3f3f3f3f3f;
long long tmp, aa, ab;
int main() {
    cin >> n >> a >> b;
    n *= 6;
    if (a * b >= n) {
        cout << a * b << endl;
        cout << a << " " << b << endl;;
        return 0;
    }
    if (a >= b) {
    	swap(a, b);
    	fl = 1;
    }
    for (int i = a; i <= sqrt(n); i++) {
        tmp = n / i;
        if (tmp * i < n) tmp++;
        if (tmp >= b && minn >= tmp * i) {
            minn = tmp * i;
            aa = i;
            ab = tmp;
        }
    }
    if (fl) swap(aa, ab);
    cout << aa * ab << endl << aa << " " << ab << endl;
    return 0;
} // do not just copy the answer, do it by yourself~
```
