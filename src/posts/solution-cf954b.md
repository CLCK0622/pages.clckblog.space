---
title: "题解 CF954B 【String Typing】"
date: 2022-10-03 16:46:05
---

## ~~水题~~

u1s1 这个翻译感觉并不是很好（像机翻）建议撤下

如题，有两种方法读入长度为 $n$ 的字符串：

- 直接输入
- 把前面的 `Ctrl(Command)+C` 然后 `Ctrl(Command)+V`

显而易见，如果能找到 **从头开始** 的一个字串连续重复两次，就可以用一次操作代替。

注意：$2$ **只能使用一次**，故从 $\frac{n}{2}$ 向下倒序遍历，避免了不合法内存空间也 **确保为最优解**。

如果找不到则直接输出长度即可。

```cpp
#include <iostream>
#include <cstring> //substr函数的头文件
using namespace std;
int n;
string s;
int main(){
	cin >> n >> s;
	for (int i = n / 2; i > 0; i--) {
		if (s.substr(0, i) == s.substr(i, i)) { //可以用substr函数截取，省去循环判断
			cout << n - i + 1 << endl;
			return 0;
		}
	}
	cout << n << endl;
	return 0;
}
```

完结撒花～