---
title: "题解 CF667A 【Pouring Rain】"
date: 2020-10-17 09:54:57
---

~~哇哇哇这题目单位。。。还好加粗了~~

注意，$v$ 是**毫升每秒**！！！

一开始先把 $v$ 转换单位（为计算方便转成**厘米每秒**）：

$$v1=v/s$$

若 $v1 < e$ 就输出 `NO`。

否则输出 `YES` 和秒数

$$h/(v1 - e)$$

即可（此处 $v1 - e$ 是一秒减少的**高度**，$h$ 为原始高度）。

代码如下，简单明了：

```cpp
#include <iostream>
#include <cmath> //acos函数的库
const double pi = acos(-1.0); //pi的标准求法
using namespace std;
double d, h, v, e;
int main() {
    cin >> d >> h >> v >> e;
    v = v / ((d / 2) * (d / 2) * pi); //单位转换，自己更新
    if (v <= e) {
        cout << "NO" << endl;
    } else {
        double ans = h / (v - e); //答案
        cout << "YES" << endl << ans << endl;
    }
    return 0;
}
```