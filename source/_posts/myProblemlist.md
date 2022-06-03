---
title: myProblemlist
date: 2022-05-25 19:46:43
tags:
---

### acwing.1671-三角形

题目描述：

Farmer John 想要给他的奶牛们建造一个三角形牧场。

有 NN 个栅栏柱子分别位于农场的二维平面上不同的点 (X1,Y1)…(XN,YN)(X1,Y1)…(XN,YN)。

他可以选择其中三个点组成三角形牧场，只要三角形有一条边与 xx 轴平行，且有另一条边与 yy 轴平行。

Farmer John 可以围成的牧场的最大面积是多少？

保证存在至少一个合法的三角形牧场。

#### 输入格式

输入的第一行包含整数 NN。

以下 NN 行每行包含两个整数 XiXi 和 YiYi，均在范围 −104…104−104…104 之内，描述一个栅栏柱子的位置。

#### 输出格式

由于面积不一定为整数，输出栅栏柱子可以围成的合法三角形的最大面积的**两倍**。

#### 数据范围

3≤N≤1003≤N≤100

#### 输入样例：

```
4
0 0
0 1
1 0
1 2
```

#### 输出样例：

```
2
```

#### 样例解释

位于点 (0,0)、(1,0)(0,0)、(1,0) 和 (1,2)(1,2) 的木桩组成了一个面积为 11 的三角形。所以，答案为 2⋅1=22⋅1=2。

只有一个其他的三角形，面积为 0.50.5。



``` C++
//暴力枚举
#include<bits/stdc++.h>
#define x first
#define y second
using namespace std;
const int N = 110;
typedef pair<int, int> PII;
PII p[N];
int n;

int res;
int main()
{
    cin >> n;
    for(int i = 0; i < n; i ++) cin >> p[i].x >> p[i].y;
    
    for(int i = 0; i < n; i ++)
        for(int j = 0;j < n; j ++)
            for(int k = 0; k < n; k ++)
                if(i != j && j != k && i != k)
                    if(p[i].x == p[j].x && p[j].y == p[k].y) 
                    res = max(res,abs(p[i].y - p[j].y) * abs(p[j].x - p[k].x));
    
    cout << res << endl;
    return 0;
}
```

