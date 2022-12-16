---
title: "题解 P5671 【【SWTR-02】Triangles】"
date: 2020-08-12 12:45:59
---

## 前言
题目不难，专业水平不高，主要涉及初中几何问题。

## 分析
**方法千万条，审题第一条，多解不考虑，爆零两行泪。**

⬆️这个非常重要，考点之一为分类讨论。

### 问题1
直接用图说话，几种可能画出来了，稍加计算可得：
![](https://cdn.luogu.com.cn/upload/image_hosting/x194dq91.png)
(有四个答案)

$x/2$

$x$

$180 − x * 2$

$(180 − x) / 2$

代入数据：$ x < 90 $ 后，发现答案均合法，排序去重输出即可。

### 问题2
还是一样，这题主要用到勾股定理，图附上，两种情况。

![](https://cdn.luogu.com.cn/upload/image_hosting/v3a5fs4a.png)
那么显而易见，答案就出来了。

（顺便普及一下，大犇跳过）
勾股定理指的是对于一个直角三角形，两条直角边的平方和（注意是平方后加和），等于斜边平方。

勾股函数因为输出格式有要求，这里给出来，两种方式输出都可。

```cpp
void gg(int m, int n) {
	if (n != m) {
	    cout << fixed << setprecision(5) << sqrt(n * n - m * m) << " "; //记得iomanip和cmath头文件
	    //printf("%.5lf ", sqrt(n * n - m * m));
	}
	cout << fixed << setprecision(5) << sqrt(n * n + m * m);
	//printf("%.5lf ", sqrt(n * n + m * m));
	return ;
}
```

**完结撒花～**