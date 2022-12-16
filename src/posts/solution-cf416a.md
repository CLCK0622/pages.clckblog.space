---
title: "题解 CF416A 【Guess a number!】"
date: 2020-10-06 11:33:55
---

~~有点水，不过不告诉你我WA了5次~~

思路很简单，但逻辑一定要理清，尤其注意：当结果为 `N` 的时候对上下界的更新（要取反）。

其实就是根据输入在线更新取值的上界和下界了啦。

具体情况：

(1) 当 `Y` 时：

1. `>=` 更新下界

2. `>` 更新下界

3. `<=` 更新上界

4. `<` 更新上界

(2) 当 `N` 时：

1. `>=` 更新上界(等价于 `<`)

2. `>` 更新上界(等价于 `<=`)

3. `<=` 更新下界(等价于 `>`)

4. `<` 更新下界(等价于 `>=`)

好了，给一下代码：

```cpp
#include <iostream>
using namespace std;
int lb = -0x3f3f3f3f, ub = 0x3f3f3f3f; //注意这里为了考虑负数，初始值设为正（负）无穷
int n;
int main() {
    cin >> n;
    for (int i = 0; i < n; i++) {
        string s; cin >> s; int x; cin >> x; char c; cin >> c;
        //上面这句都是输入，压一下行
        if (s == ">=") {
            if (c == 'Y') {
                lb = max(lb, x); //(1)1
            } else {
                ub = min(ub, x - 1); //(2)1
            }
        }
        if (s == ">") {
            if (c == 'Y') {
                lb = max(lb, x + 1); //(1)2
            } else {
                ub = min(ub, x); //(2)2
            }
        }
        if (s == "<=") {
            if (c == 'Y') {
                ub = min(ub, x); //(1)3
            } else {
                lb = max(lb, x + 1); //(2)3
            }
        }
        if (s == "<") {
            if (c == 'Y') {
                ub = min(ub, x - 1); //(1)4
            } else {
                lb = max(lb, x); //(2)4
            }
        }
        //上面一段分别更新
    }
    if (lb <= ub) cout << lb << endl;
    else cout << "Impossible" << endl; //输出结果（记得还有Impossible的情况）
    return 0;
}
```

#### 完结撒花～