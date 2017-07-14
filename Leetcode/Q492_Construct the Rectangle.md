给定一个数字，此数字代表一个矩形的面积，返回 `[length,width]` 使得`L >= W`，并且使得 L 和 W 相差最小。

#### Example

```
Input: 4
Output: [2, 2]
Explanation: The target area is 4, and all the possible ways to construct it are [1,4], [2,2], [4,1]. 
But according to requirement 2, [1,4] is illegal; according to requirement 3,  [4,1] is not optimal compared to [2,2]. So the length L is 2, and the width W is 2.

```

#### Solution Java

> **思路**:寻找相差最小的因数(即离sqrt(area)最近的因数);

```
public class Solution {
    public int[] constructRectangle(int area) {
        int width = 1;
        for(int i = 2;i <= Math.sqrt(area);i++){
            if(area % i == 0){
                width = i;
            }     
        }
        int[] result = new int[]{area/width,width};
        return result;       
    }
}

```

#### 其他网友答案

```
public int[] constructRectangle(int area) {
    int[] result = new int[2];
    if(area == 0){
        return result;
    }
    int a = (int)Math.sqrt(area);
    while(area%a != 0){
        a--;
    }
    int b = area/a;
    result[0] = b;
    result[1] = a;
    return result;
}

```