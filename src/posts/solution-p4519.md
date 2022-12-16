---
title: "题解 P4519 【[COCI2017-2018 Contest4]Rasvjeta 】"
date: 2020-10-31 11:27:56
---

### ~~这是道难题。~~

### ~~因为没有翻译。~~

大致题意见题解区。

我就直接来讲做法吧：先按照题目给出的灯的位置进行标记，然后**从前到后**依次遍历路的位置，找到第一个没有灯照亮的区间，**贪心**，给它装上灯，并且**使这个灯的位置尽量靠后**（确保**不浪费照亮范围**），累加答案，最后输出即可。

代码如下：

```cpp
#include <iostream>
#include <cstdio>
using namespace std;
const int MAX = 1005;
int ans;
int n, m, k;
bool flag[MAX];
void work(int x) { //标记照亮部分
	for (int i = max(x - k, 1); i <= min(n, x + k); i++) { 
	    //防止越界（小心RE）
		flag[i] = true;
	}
}
int main() {
	cin >> n >> m >> k;
	for (int i = 1; i <= m; i++) { //读入并标记
	    int x;
	    cin >> x;
	    work(x);
	}
	for (int i = 1; i <= n; i++) { //贪心
	    if (!flag[i]) {
	        work(i + k); //标记（这里i+k是让灯尽量靠后，见上面解法）
	        ans++; //累加答案
	    }
	}
	cout << ans << endl; //输出
	return 0;
}
```

### 完结撒花～

#### ~~这么认真不留下个赞再走嘛～~~