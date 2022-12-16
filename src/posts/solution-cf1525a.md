---
title: "题解 CF1525A 【Potion-making溶液配制】"
date: 2021-05-23 17:06:05
---

## 水题

题目要求：

配制一份浓度为 $x$% 的溶液，并且添加最少的溶剂与溶质。

#### 显而易见，将 $\frac{x}{100}$ 化为最简后的分母就是答案。

code:

```cpp
#include <iostream>
#include <algorithm>
#include <cmath>
using namespace std;
/*
int gcd(int a, int b) {
    if(b == 0) return a;
    return gcd(b, a % b);
}
*/
int main() {
    int n; cin >> n;
    while(n--) {
        int k; cin >> k;
        cout << 100 / __gcd(100, k) << endl; //C++自带最大公约数，也可以去掉__用上面的自定义函数。
    }
    return 0;
}
```