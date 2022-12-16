---
title: "题解 CF1740B 【Jumbo Extra Cheese 2】"
date: 2022-11-03 20:34:33
---

一道贪心题。

如图所示，小学学习的周长计算相关问题可知，可以**将内部的线段补全到图形最外层**，以计算整个图形的周长。这种方法最适用于此类各个长方形拼接以及一个长方形中挖去的题目。

![](https://cdn.luogu.com.cn/upload/image_hosting/pnh0nn1b.png)

那么既然如此，我们再来看题目的题面：

将若干长方形以任意顺序排列，计算整个图形的**最小周长**。

在这个图形中，有哪些边是一定要被选择的呢？

——**所有** $x$ 轴上的边以及**最大的**与 $y$ 轴平行的边。

根据这个原理，答案的表达式就不难推出了。

```cpp
#include <iostream>
#include <cstring>
using namespace std;
#define int long long
int t, n;
struct sq {
    int a, b;
} s[200005];
signed main() {
    ios::sync_with_stdio(false); //优化输入输出速度
    cin.tie(0); cout.tie(0);
    cin >> t;
    while (t--) {
        cin >> n;
        int ans = 0;
        int m = -1;
        for (int i = 0; i < n; i++) {
            cin >> s[i].a >> s[i].b;
            m = max(m, max(s[i].a, s[i].b)); //计算最大的竖直边
            ans += min(s[i].a, s[i].b); //统计x轴上边能够实现的最小值
        }
        ans += m; //合并答案
        ans *= 2; //输出总周长
        cout << ans << endl;
    }
    return 0;
}
```