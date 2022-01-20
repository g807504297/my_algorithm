# 基础算法
## 快速排序
**算法思想：**
快排属于分治算法，分治算法都有三步：
1. 分成子问题
2. 递归处理子问题
3. 子问题合并

```c++
void quick_sort(int q[], int l, int r)
{
    //递归的终止情况
    if(l >= r) return;
    //第一步：分成子问题
    int i = l - 1, j = r + 1, x = q[l + r >> 1];
    while(i < j)
    {
        do i++; while(q[i] < x);
        do j--; while(q[j] > x);
        if(i < j) swap(q[i], q[j]);
    }
    //第二步：递归处理子问题
    quick_sort(q, l, j), quick_sort(q, j + 1, r);
    //第三步：子问题合并.快排这一步不需要操作，但归并排序的核心在这一步骤
}

```

## 归并排序
算法思想：


```c++
void merge_sort(int q[], int l, int r)
{
    //递归的终止情况
    if(l >= r) return;

    //第一步：分成子问题
    int mid = l + r >> 1;

    //第二步：递归处理子问题
    merge_sort(q, l, mid ), merge_sort(q, mid + 1, r);

    //第三步：合并子问题
    int k = 0, i = l, j = mid + 1, tmp[r - l + 1];
    while(i <= mid && j <= r)
        if(q[i] <= q[j]) tmp[k++] = q[i++];
        else tmp[k++] = q[j++];
    while(i <= mid) tmp[k++] = q[i++];
    while(j <= r) tmp[k++] = q[j++];

    for(k = 0, i = l; i <= r; k++, i++) q[i] = tmp[k];
}
```

## 二分排序

### 整数二分

**算法思想：**

**二分的本质是二段性不是单调性。**

![img](https://gitee.com/adameta/img/raw/master/1580979705_20200206160241434_9286.png)

1.先写一个check函数。

2.判定在check的情况下（true和false的情况下），如何更新区间。
3.在check(m)==true的分支下是:
	l=mid的情况，中间点的更新方式是m=(l+r+1)/2
	r=mid的情况，中间点的更新方式是m=(l+r)/2


```c++
bool check(int x) {/* ... */} // 检查x是否满足某种性质

// 区间[l, r]被划分成[l, mid]和[mid + 1, r]时使用：
int bsearch_1(int l, int r)
{
    while (l < r)
    {
        int mid = l + r >> 1;
        if (check(mid)) r = mid;    // check()判断mid是否满足性质
        else l = mid + 1;
    }
    return l;
}
// 区间[l, r]被划分成[l, mid - 1]和[mid, r]时使用：
int bsearch_2(int l, int r)
{
    while (l < r)
    {
        int mid = l + r + 1 >> 1;
        if (check(mid)) l = mid;
        else r = mid - 1;
    }
    return l;
}
```

### 浮点数二分

算法思想：

```c++
bool check(double x) {/* ... */} // 检查x是否满足某种性质

double bsearch_3(double l, double r)
{
    const double eps = 1e-6;   // eps 表示精度，取决于题目对精度的要求
    while (r - l > eps)
    {
        double mid = (l + r) / 2;
        if (check(mid)) r = mid;
        else l = mid;
    }
    return l;
}
```



## 高精度

算法思想：


```c++



```



## 前缀和 与 差分
算法思想：


```c++



```


## 双指针算法
算法思想：

```c++



```


##  位运算
算法思想：

```c++



```


## 离散化
算法思想：

```c++



```


## 区间合并

算法思想：

```c++



```





