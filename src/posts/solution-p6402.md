---
title: "题解 P6402 【[COCI2014-2015#2] UTRKA】"
date: 2020-08-24 15:21:23
---
本题比较简单，不过题意稍微转化一下：

第一个数组存储参加人，第二个数组存储完成人，因为两个数组**只有一人不同**，故只需要把两数组都按照一定顺序排好，**一一比较**即可，而唯一不同项即为答案。

（注：$C++$ 语言可以直接使用 $string$ 数组存储，数组中存储人名字，而在 $C++$ 语法中，**允许直接进行 $string$ 比较**，即**按字典序**，所以可以直接使用 $string$ 排序）
```cpp
#include <iostream>
#include <algorithm>
using namespace std;
string a[100005];
string b[100005];
int main() { //简明易懂
    int n;
    cin >> n;
    for (int i = 0; i < n; i++) { //读入
        cin >> a[i];
    }
    for (int i = 0; i < n - 1; i++) {
        cin >> b[i];
    }
    sort(a, a + n); //排序
    sort(b, b + n - 1);
    for (int i = 0; i < n; i++) {
        if (a[i] != b[i]) { //如果不对应，那么就是所求结果
            cout << a[i] << endl;
            return 0;
        }
    }
}
```

### 完结撒花～