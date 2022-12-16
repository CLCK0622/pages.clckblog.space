---
title: "题解 CF1747A 【Two Groups】"
date: 2022-11-06 09:57:50
---

一道简单题。

将数列分为两组，其实只需要任意分配，最后大减小必为答案。

接着证明结论正确性。

对于数列 $a_1, a_2, a_3, 0, b_1, b_2, b_3(a1 \gt a_2 \gt a_3 \gt 0 \gt b_1 \gt b_2 \gt b_3)$，将其分组后，不妨设其结果为 $\lvert sum_1 \rvert - \lvert sum_2 \rvert (\lvert sum_1 \rvert > \lvert sum_2 \rvert)$ 时取到最大值，且 $sum_1 \gt 0, sum_2 \lt 0$，在 $sum_2$ 中取出一项 $b_1$，放入 $sum_1$ 中，$ans = \lvert sum_1 + b_1 \rvert - \lvert sum_2 - b_1 \rvert = \lvert sum_1 \rvert - \lvert b_1 \rvert - (\lvert sum_2 \rvert - \lvert b_1 \rvert) = \lvert sum1 \rvert - \lvert sum_2 \rvert$，与原答案相同，故得证。


```cpp
#include <iostream>
#include <cmath>
#define int long long //一定要开long long！
using namespace std;
int t;
signed main() {
	ios::sync_with_stdio(false); //输入输出优化
	cin.tie(0); cout.tie(0);
	cin >> t;
	while (t--) {
		int n;
		int sum1 = 0, sum2 = 0;
		cin >> n;
		for (int i = 0; i < n; i++) {
			int x = 0;
			cin >> x;
			if (x >= 0) sum1 += x; //为方便按照正负分组
			else sum2 += x;
		}
		cout << max(abs(sum1), abs(sum2)) - min(abs(sum1), abs(sum2)) << endl; //大减小必为正解
	}
	return 0;
}
```

完结撒花～