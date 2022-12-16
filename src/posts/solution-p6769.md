---
title: "题解 P6769 【[USACO05MAR]Yogurt factory 奶酪工厂】"
date: 2020-08-18 10:29:28
---

看着各路神犇发的题解 ~~（好吧也就几篇）~~，我深感找到了一种简单解法——废话少说，上代码。

```cpp
#include<iostream>
using namespace std;
int c, y, s, last;
long long n, ans = 0; //话说题目都提示了,要是还不开long long……见祖宗吧
int main() {
    cin >> n >> s;
    for (int i = 1; i <= n; i++) {
        cin >> c >> y;
        if (i == 1) last = c;
        else last = min(last + s, c);
        ans += last * y;
    }
    cout << ans << endl;
    return 0;
}
```
直接贪心，代码简单易懂，__时间复杂度 $O(n)$，空间复杂度 $O(1)$。__

（稍作讲解，神犇跳过）
为什么可以这样直接处理呢？因为题目已经说了，每次的奶酪不管之前放的还是新生产的，__价值都一样，而且没有保质期，不需要废除奶酪__，故不用考虑太多，记录库存总数和代价即可。

这题就这么解决啦。

__完结撒花～__