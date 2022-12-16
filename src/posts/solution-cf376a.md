---
title: "题解 CF376A 【Lever】"
date: 2021-08-05 11:01:21
---

~~水题，建议评红或橙。~~

### 前铺芝士

典型的杠杆问题，原理：
$$ F_1 \times L_1 + F_2 \times L_2 + ... + F_n \times L_n = F_1' \times L_1' + F_2' \times L_2' + ... + F_n' \times L_n' $$

因为悬挂重物，所以受到的拉力 $F$ 就等于 $G_\text{物}$ ，且方向竖直向下，那么力臂就是悬挂点到支点的距离（施力方向垂直杠杆）。

知道了这些，这题就没有技术含量了，一道简单的字符串模拟。

### 具体做法

先依次读入输入，因为换行符也会被识别成 `char` 类型，所以可以读入字符串依次遍历。对于每一个物体，可以建立一个**结构体**存储位置（绝对位置）和重量，并同时标记支点位置。一次遍历后，一次对于结构体数组中的数据求出两边力矩相比较即可。

### AC代码

```cpp
#include <iostream>
using namespace std;
string s; 
struct item { //建立结构体
	int weight;
	int pos;
}a[1000005];
int acnt;
int main() {
	int point = 0;
	char s; string ss;
	int npos = 0;
	cin >> ss;
	for (int i = 0; i < ss.length(); i++) { //遍历字符串
		s = ss[i];
		npos++;
		if (s == '=') continue;
		if (s == '^') {
			point = npos;
		}
		if (s >= '0' && s <= '9') { //对于物体存储数据
			a[acnt].weight = s - '0';
			a[acnt++].pos = npos;
		}
	}
	long long leftm = 0, rightm = 0; //注意这里要用long long，题面有提示
	for (int i = 0; i < acnt; i++) {
		if (a[i].pos < point) { //累加力矩
			leftm += (point - a[i].pos) * a[i].weight;
		} else if (a[i].pos > point) {
			rightm += (a[i].pos - point) * a[i].weight;
		}
	}
	if (leftm == rightm) { //比较并输出
		cout << "balance" << endl;
		return 0;
	}
	cout << (leftm > rightm ? "left" : "right" ) << endl;
	return 0;
}
```

这么认真不留个赞再走嘛~

管理大大求过

完结撒花