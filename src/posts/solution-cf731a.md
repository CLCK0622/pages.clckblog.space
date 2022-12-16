---
title: "题解 CF731A 【Night at the Museum】"
date: 2020-10-05 21:49:59
---

~~又来一道大水题~~

因为字符串必须从前往后打，所以顺序确定了，没什么好思考的，直接模拟就好。

这里有个小技巧：可以用字符类型代替int类型进行运算，免去了计算环形位数的步骤。

具体思路用 `pos` 变量记录当前字母，初始设为 'a'，然后计算比较顺时针和逆时针方向转动距离的大小，累加到 `ans` 变量中即可。

代码如下：
```cpp
#include <iostream>
using namespace std;
string s;
char pos;
int ans;
int main() {
    pos = 'a';
    cin >> s;
    for (int i = 0; i < s.size(); i++) {
        ans += min(abs(pos - s[i]), 26 - abs(pos - s[i]));
        pos = s[i];
    }
    cout << ans << endl;
    return 0;
}
```

#### 就这些了，完结撒花～