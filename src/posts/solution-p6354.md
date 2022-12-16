---
title: "题解 P6354 【[COCI2007-2008#3] TAJNA】"
date: 2020-09-05 15:15:29
---

没什么好说的，按照题意模拟即可。此处采用二维数组模拟表格的形式记录密码，来得出密码。

```cpp
#include <iostream>
using namespace std;
string s;
int l, h;
char ans[105][105];
int main() {
    cin >> s;
    int n = s.size(); //字符数量
    for (int i = 1; i * i <= n; i++) {
        if (n % i == 0) { //计算长宽，尽可能接近平方根为最大
            h = i;
            l = n / i;
        }
    }
    int cnt = 0;
    for (int i = 0; i < l; i++) {
        for (int j = 0; j < h; j++) { //存字符串
            ans[i][j] = s[cnt++];
        }
    }
    for (int i = 0; i < h; i++) {
        for (int j = 0; j < l; j++) { //换序输出（和上面换下也可）
            cout << ans[j][i];
        }
    }
    return 0;
}
```