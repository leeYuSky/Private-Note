给定一个一个正数，将它的二进制码各个位取反

#### Example1

```
Input: 5
Output: 2
Explanation: The binary representation of 5 is 101 (no leading zero bits), and its complement is 010. So you need to output 2.

```

#### Example2

```
Input: 1
Output: 0
Explanation: The binary representation of 1 is 1 (no leading zero bits), and its complement is 0. So you need to output 0.

```

> **思路**:获得当前数值二进制位数，即11...11 - 当前数

#### Solution

```
public class Solution {
    public int findComplement(int num) {
        int source = num;
        int count = 0;
        while(num!=0){
            count++;
            num = num >> 1;
        }
        int temp = 0;
        for(int i = 0;i < count;i++){
            temp += (int)Math.pow(2,i);
        }
        return temp - source;
    }
}

```

#### 网友其他答案

```
public int findComplement(int num) {
        return ~num + (Integer.highestOneBit(num) << 1);
}

```