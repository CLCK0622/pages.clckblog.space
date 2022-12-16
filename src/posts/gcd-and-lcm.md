---
title: "最大公约数和最小公倍数问题"
date: 2020-07-28 13:22:13
---

**在编程中，常常会遇到使用最大公约数与最小公倍数的情况，而这个模块对于初学小白来说逻辑有点复杂，接下来我将介绍两种常用的实现方式。**

------------

## 方法一 直接使用函数
那么如何实现呢？在C++的 **algorithm** 库中有一个函数：
__gcd

对于其使用（非常方便）给出如下示例代码：
```cpp
#include <iostream>
#include <algorithm> 
using namespace std;
int a, b;
int main() {
    cin >> a >> b;
    int ans = __gcd(a, b); //注意！这里有双下划线（拼写_ _ g c d），千万别漏!
    cout << ans << endl;
    return 0;
}
```
好了，使用就是这样。优点是使用方便，但很大一个问题就是（非OIer忽略）——NOIP明确声明**不支持一切以双下划线开头的函数、命名空间等（自己定义的不算）**

那么就需要我们方法二出场啦！



------------
## 方法二 欧几里得算法
哈哈，听起来很深奥对不对？实际上，它有个更为简单的名字———辗转相除法。相信这个有点数学基础的都该听过吧？实际也很简单。

话不多说，上代码！
```cpp
int gcd(int a, int b) { //这里就不附完整代码了，方法类同
    if (b == 0) {
        return a;
    }
    return gcd(b, a % b);
}
```
至于证明这里就不给出了，感兴趣的小伙伴可以自己百度哦！


------------

## 最后，最小公倍数咋求呢？
直接给出公式，推导很简单，可以自己试试。

$$\text{lcm}(a, b) = \frac{a \times b}{\gcd(a, b)}$$

------------
## 例题
题目链接：[https://www.luogu.com.cn/problem/P1029](https://www.luogu.com.cn/problem/P1029)

先分析一下题目：

给出两数的gcd和lcm，求两者方案数。

那么如何求解呢？

首先，想到双重循环枚举，当然可以，所以……TLE 了。

那么换一种算法，优化方法：

既然两数的乘积可以由输入得到（见上面知识分析），那么就可以通过
n / i * m
（n，m分别为输入，i为枚举数）
来得到另外一个数。
如上即为基本思路。
但为了避免程序超时（对的，这样还是超时的），我们只能枚举一半，即
i * i <= n * m
。这样就能避免超时。

而每一组数值都被计算两遍（见样例），那么再找到一组符合情况的答案时，ans需要加2。

~~好啦，这就对了。~~

并不是，想想还有什么没考虑到？
就是完全平方数！即
i * i == n * m
时，需要特判：
if (n == m) ans--;
这样，答案就完全正确了。

AC代码如下：
```cpp
#include <iostream>
#include <algorithm>
using namespace std;
int n, m, ans;
int gcd(int a, int b) {
	if (b == 0) return a;
	return gcd(b, a % b);
}
int main() {
	cin >> n >> m;
	if (n == m) {
		ans--;
	}
	for(int i = 1; i * i <= n * m; i++) {
		if (n * m % i == 0 && gcd(i, m * n / i)== n) { //想用__gcd函数的把这里改下就可，前面定义可以去掉
			ans += 2;
		}
	}
	cout << ans << endl;
	return 0;
}
```
