---
title: "题解 CF616B 【Dinner with Emma】"
date: 2020-10-04 12:07:29
---

### ~~翻译者来水一发题解~~~

##### 右上角博客食用……其实口味并不更佳

啊这，我翻译已经够清楚了吧，Emma要让餐费尽可能高，而Jack为了让餐费变低，会选择街上餐馆费用最小值，所以Emma会选择餐费最小值最高的街道，所以就是每一行最小值的最大值。

代码如下：
```cpp
#include <iostream>
using namespace std;
int n, m;
int main() {
    cin >> n >> m;
    int ans = 0;
    for (int i = 0; i < n; i++) {
        int powmin = 0x3f3f3f3f;
        for (int j = 0; j < m; j++) {
            int x;
            cin >> x;
            powmin = min(powmin, x);
        }
        ans = max(ans, powmin);
    }
    cout << ans << endl;
    return 0;
}
```