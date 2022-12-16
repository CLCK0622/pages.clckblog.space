---
title: "题解 P6369 【[COCI2006-2007#6] MARATON】"
date: 2020-10-02 10:02:10
---

### 一道~~大~~模拟。

数据范围很小，读入之后，每找到一个字母，向周围扩展即可。

扩展方法：if语句（见check函数）

详解：先想想如何构成获胜的局面呢？

1.横向：

1）横向最左点 2）横向最右点 3）横向中点

2.纵向：

1）纵向最上点 2）纵向最下点 3）纵向中点

3.斜向：

类上略

注：部分可以忽略 因为main函数中全盘扫过一遍

```cpp
bool check(int x, int y, char c) {
    if (map[x - 1][y] == c && map[x - 2][y] == c && in(x - 1, y) && in(x - 2, y)) return true; //1.2）
	if (map[x + 1][y] == c && map[x + 2][y] == c && in(x + 1, y) && in(x + 2, y)) return true; //1.1）
	if (map[x][y - 1] == c && map[x][y - 2] == c && in(x, y - 1) && in(x, y - 2)) return true; //2.1）
	if (map[x][y + 1] == c && map[x][y + 2] == c && in(x, y + 1) && in(x, y + 2)) return true;//2.2）
	if (map[x - 1][y - 1] == c && map[x - 2][y - 2] == c && in(x - 1, y - 1) && in(x - 2, y - 2)) return true; //3.
	if (map[x + 1][y + 1] == c && map[x + 2][y + 2] == c && in(x + 1, y + 1) && in(x + 2, y + 2)) return true; //3.
	if (map[x + 1][y - 1] == c && map[x + 2][y - 2] == c && in(x + 1, y - 1) && in(x + 2, y - 2)) return true; //3.
	if (map[x - 1][y + 1] == c && map[x - 2][y + 2] == c && in(x - 1, y + 1) && in(x - 2, y + 2)) return true; //3.
	return false;
}
```

难度不高，其余代码如下，简洁易懂。

```cpp
bool in(int x, int y) {
    return 0 <= x && x < n && 0 <= y && y < n;
}
int main() {
    cin >> n;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            cin >> map[i][j];
        }
    }
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n; j++) {
            if (map[i][j] != '.') {
                if (check(i, j, map[i][j])) {
                    cout << map[i][j] << endl;
                    return 0;
                } else {
                    continue;
                }
            }
        }
    }
    cout << "ongoing" << endl;
    return 0;
}
```

#### 还有，记得判界内（in函数）。

##### 完结撒花。