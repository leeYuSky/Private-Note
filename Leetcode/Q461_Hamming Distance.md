汉明距离，寻找两个串或数字不同的位数有多少

#### Example
```
Note:0 ≤ x, y < 2^31.

Input: x = 1, y = 4

Output: 2

Explanation:
1   (0 0 0 1)
4   (0 1 0 0)
       ↑   ↑

The above arrows point to positions where the corresponding bits are different.


```

#### Solution

> **思路**:将两个int数值做异或运算得到的数的1的个数就是结果;或直接使用`Integer.bitCount(x ^ y)`

```
public class Solution {
    public int hammingDistance(int x, int y) {
        int temp = x ^ y;
        int count = 0;
        while(temp != 0){
            count += temp & 1;
            temp = temp >> 1;
        }
        
        return count;
        
    }
}

```