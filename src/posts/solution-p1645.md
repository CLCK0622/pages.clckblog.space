---
title: "题解 P1645 【序列】"
date: 2020-09-05 11:49:31
---

基础贪心问题，思路不太好想：
从右往左排序后依次覆盖，若按照右边界从小到大排序就从右往左覆盖，以达到最佳解法，左侧关键字同。

```cpp
#include <cstdio>
#include <iostream>
#include <algorithm>
using namespace std;
bool sz[1005];
int n;
struct lrc {
    int l, r;
    int c;
} a[1005];
bool cmp(lrc a, lrc b) { //自定义比较函数
    return a.r < b.r;
}
int main() {
    cin >> n;
    for (int i = 0; i < n; i++) {
        cin >> a[i].l >> a[i].r >> a[i].c;
    }
    sort(a, a + n, cmp); //排序
    for (int i = 0; i < n; i++) {
        int cc = a[i].c;
        for (int j = a[i].r; j >= a[i].l; j--) { //区间处理
            if (sz[j]) cc--;
        }
        if (cc <= 0) continue;
        for (int j = a[i].r; j >= a[i].l; j--) { //覆盖部分
            if (cc == 0) break;
            if (!sz[j]) {
                sz[j] = true;
                cc--;
            }
        }
    }
    int ans = 0;
    for (int i = 0; i < 1005; i++) { //统计答案
        if (sz[i]){
            ans++;
        }
    }
    cout << ans << endl;
    return 0;
}
```
