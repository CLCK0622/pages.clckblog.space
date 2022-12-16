---
title: "题解 SP4300 【AE00 - Rectangles】"
date: 2020-11-22 21:51:38
---

~~偶见一道水题~~

不难的一道题，求出因数个数即可。

~~（啥？这还要问为什么？）~~

热心的我来解释一番。

假设长方形面积为 $S$（即所需小正方体个数），那么易得
$$S = a \times b \text{（其中a, b均为正整数）}$$
因此求得所有 $a$ 与 $b$ 的值即可。

模拟（时间复杂度 $O(n \sqrt{n})$）：

```cpp
#include <iostream>
using namespace std;
int main() {
    int n, ans = 0;
    cin >> n;
    for (int i = 1; i <= n; i++) { //注意不大于N的个数都可以！！！
        for (int j = 1; j * j <= i; j++) {
            if (i % j == 0) ans++;
        }
    }
    cout << ans << endl;
    return 0;
}
```

#### 完结撒花～留下个赞再走吧～