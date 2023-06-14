## 题目：

![](30%E2%80%94%E5%8C%85%E5%90%ABmin%E5%87%BD%E6%95%B0%E7%9A%84%E6%A0%88.png)

## 解题思路：

设置标志位min，初始化为最大值

每次元素x入栈时，判断x是不是最小值：

+ x是最小值：min = x

每次元素x出栈时，判断x是不是最小值

+ x是最小值：在0到top中重新寻找新的最小值

## 代码展示：

```
class MinStack {

    /** initialize your data structure here. */
    int[] value = new int[20000];
    int top = -1;
    int min = Integer.MAX_VALUE;
    public MinStack() {

    }
    
    public void push(int x) {
        top++;
        value[top] = x;
        if (x < min){
            min = x;
        }
    }
    
    public void pop() {

        top--;

        if (value[top+1] == min){
            min = Integer.MAX_VALUE;
            for (int i = 0;i <= top;i++){
                if (value[i]<min)
                min = value[i];
            }
        }
        
    }
    
    public int top() {
        return value[top];
    }
    
    public int min() {
        return min;
    }
}
```

