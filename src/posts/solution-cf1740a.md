---
title: "题解 CF1740A 【Factorise N+M】"
date: 2022-11-03 19:58:43
---

~~大水题~~

题解区做的都太烦了吧

简单：若 $m+n$ 为合数，$m$为质数，则直接输出其本身即可，$2 \times m$ 必为合数，此题有SPJ，满足题意。

```cpp
#include <iostream>
using namespace std;
int t;
int main() {
	cin >> t;
    while (t--) {
    	int m;
        cin >> m;
        cout << m << endl;
    }
    return 0;
}
```

完结撒花~