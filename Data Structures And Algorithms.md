#数据结构与算法

## 1.排序

### 1.1 快速排序

#### 思想1 分治思想

> divide and conquer, D&C
> 一种著名的递归式问题解决方法

步骤：  
1. 找出简单的基线条件
2. 确定如何缩小问题的规模，使其符合基线条件

---

快速排序：  
1. 若该数列不超过一个元素，则排序完成 （基线条件）
2. 选取基准值 `P` (pivot)
3. 将数列分为两个子数列：小于`P`的元素与大于`P`的元素 （缩小问题的规模）
	1. 将操作数列中最左边与最右边的数字分别标记为`i`与`j`
	2. 若`j`到达`i`的位置，则将`P`与该位置的数对换，划分完成，否则重复进行下列操作直到满足条件：
		1. 将`j`向左移动，直到其到达小于 `P` 的数`b`的位置
		2. 将`i`向右移动，直到其到达大于 `P` 的数`a`的位置
		3. 将`a`与`b`对换
4. 对两个子数列进行快速排序


代码实现：
```cpp

int n[101]; //Numbers

void quickSort(int left, int right)
{
	if(left>right) return;
	int p=n[left]; //choose the leftest one as the pivot
	int i=left,j=right;
	while(i<j)
	{
		while(i<j && n[j]>=p)
			j--;
		while(i<j && n[i]<=p)
			i++;
		swap(n[i],n[j]);
	}
	swap(n[left],n[i]);
	
	quickSort(left,i-1);
	quickSort(i+1,right);
}

```

C++的STL库提供了排序模版：
 
```cpp
#include<algorithm>
bool cmp(int a,int b){ return a>b;)
// a>b: descending order
// a<b: ascending order (default)

sort(<head address>,<end address>,[compare function]);
// example: sort(n,n+100,cmp);
```













