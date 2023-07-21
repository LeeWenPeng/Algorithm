# 时间复杂度计算

**前情提要**：

+   $O(f(n)$ ：上界
+   $\Theta(f(n)$ ：上界和下届
+   $\Omega(f(n)$ ：下界

## 1 常规情况

1. 统计算法中常数级操作 $f(n)$

    >   按照最差情况估计

2. 将公式展开成泰勒展开式 

3. 保留最高级数项，并去除系数 $f(n) = O(g(n))$

### 1 选择排序

```c++
//选择排序
void SelectionSort(int* arr, int length) {
	if (length <= 1) return;

	int maxI;

	for (int i = 0; i < length; ++i) {
		maxI = i;
		for (int j = i+1; j < length; ++j) {
			if (arr[j] > arr[maxI]) maxI = j;
		}
		sway(arr[i], arr[maxI]);
	}
}
```

索引次数：
$$
f_1(n) = n + (n-1) + (n-2) + (n-3) + .. + 1
$$

$$
f_1(n) =  \frac{n(1+n)}{2}
$$

比较次数：
$$
f_2(n) = (n-1) + (n-2) + (n-3) + .. + 1
$$

$$
f_2(n) =  \frac {n(n-1)} {2}
$$

交换次数：
$$
f_3(n) = n
$$
总：
$$
f(n) &=\sum_{i=1}^{3}f_i(n) \\
&=n^2 + n  \\ 
&=O(n^2)
$$


### 2 冒泡排序

```c++
//冒泡排序
void BubbleSort(int* arr, int length) {
	if (length <= 1) return;

	for (int i = 0; i < length; ++i) {
		for (int j = length - 1; j > i; --j) {
			if(arr[j - 1] < arr[j]) sway(arr[j - 1], arr[j]);
		}
	}
}
```

索引次数：
$$
f_1(n) = n + (n-1) + (n-2) + (n-3) + .. + 1
$$

$$
f_1(n) =  \frac{n(1+n)}{2}
$$

比较次数：
$$
f_2(n) = (n-1) + (n-2) + (n-3) + .. + 1
$$

$$
f_2(n) =  \frac {n(n-1)} {2}
$$

交换次数：(最坏)
$$
f_3(n) = (n-1) + (n-2) + (n-3) + .. + 1
$$

$$
f_2(n) =  \frac {n(n-1)} {2}
$$

总：
$$
f(n) &=\sum_{i=1}^{3}f_i(n) \\
&=\frac{3}{2}n^2 - \frac{1}{2}n  \\ 
&=O(n^2)
$$

### 3 插入排序

```C++
//插入排序
void InsertSort(int* arr, int length) {
	if (arr == nullptr || length < 2) return;

	for (int i = 0; i < length; ++i) {
		for (int j = i ; j > 0 && arr[j] > arr[j-1]; --j) 
            sway(arr[j -1], arr[j]);
	}
}
```

查看次数：
$$
f_1(n) &= 1 + 2 + 3 + ... + n \\
&= \frac{n(n+1)}{2}
$$
比较次数：
$$
f_2(n) &= 0 + 1 + 2 + 3 + ... + (n-1) \\
&= \frac{n(n-1)}{2}
$$
交换次数(最差)：
$$
f_3(n) &= 0 + 1 + 2 + 3 + ... + (n-1) \\
&= \frac{n(n-1)}{2}
$$
总计：
$$
f(n) &= f_1(n) + f_2(n) + f_3(n) \\
&=\frac{3}{2} n^2 - \frac{1}{2} n \\
&=O(n^2)
$$


### 4 二分查找法

题目：二分查找到某一个数字k



## 2 递归代码

### 1、主定理法——Master定理

适用范围：
$$
T(n) = aT(\frac{n}{b})+f(n)
$$

+   $n$：问题规模
+   $a$：子问题个数
+   $\frac {n}{b}$：子问题规模
+   $f(n)$：将原问题分解为子问题的时间和将子问题的解合并成原问题的解的时间

结果：

1.   如果 $f(n) = O(n^{log_b{a} - \epsilon})$ $(\epsilon > 0)$ ，则$T(n) = \Theta (n^{log_b{a}})$ 
     +   **如果$f(n) \leq n^{log_b{a} - \epsilon}$ ，则$T(n) = \Theta (n^{log_b{a}})$** 
2.   如果$f(n) = \Theta(n^{log_b{a}}log^k{n})$ $(k \geq 0)$，则$T(n) = \Theta(n^{log_b{a} \space log^{k+1}{n}})$
     +   **如果$f(n) == n^{log_b{a}}log^k{n}$ ， 则$**T(n) = \Theta(n^{log_b{a} \space log^{k+1}{n}})$
3.   如果$f(n) = \Omega(n^{log_b{a}+\epsilon})$ $(\epsilon > 0)$ ,且$a(f(n/b) \leq cf(n))$ ，则$T(n) = \Theta(f(n))$
     +   如果$f(n) \geq n^{log_b{a}+\epsilon}$ ，且 $a(f(n/b) \leq cf(n))$ ，则 $T(n) = \Theta(f(n))$

## 3 时间复杂度比较

1、通过指标进行比较（n为很大的数）
$$
O(1) < O(log{n}) < O(n) < O(nlogn) \\
<O(n^2) <O(n^3) < O(2^n)
$$
2、无法通过指标进行比较（同量级内）

1.   通过常数项进行比较

2.   直接run，统计时间
