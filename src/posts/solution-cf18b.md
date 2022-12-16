---
title: "题解 CF18B 【Platforms】"
date: 2020-10-03 18:31:41
---

## ~~先吐槽一下翻译，连k是啥都没说。~~

### 题目大意

给定一根坐标轴，现有 $n$ 条线段，每根线段从 $1$ 开始编号，设线段编号为 $k$，则该线段覆盖范围为：

$$[(k - 1) \times m, (k - 1) \times m + l]$$

有一个动点从原点开始移动，每次移动 $d$ 距离，问第一个**不被**线段覆盖的点的位置在哪里？

### 解法

看懂了题目，代码就很简单了，模拟一下，如果**上一线段**右端点和**该线段**左端点（之间就不是覆盖部分）不在一次移动范围内，那么这次移动的落点就是答案。

记得开 long long（~~不告诉你我这个卡了2次~~）

代码如下：

```cpp
#include <iostream>
using namespace std;
long long n, m, d, l;
int main() {
    cin >> n >> d >> m >> l;
    long long a = 0, b = 0;
    for (long long i = 1; i <= n; i++) {
        a = (i - 1) * m + l, b = i * m - 1;
        if (a / d != b / d) break;
    }
    cout << (a / d + 1) * d << endl;
    return 0;
}
```

#### 完结撒花～