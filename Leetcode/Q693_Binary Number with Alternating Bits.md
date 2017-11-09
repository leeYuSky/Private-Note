判断一个专为二进制的整数是否0、1交替

#### Example 1

```
Input: 5
Output: True
Explanation:
The binary representation of 5 is: 101
``
#### Example 2

```
Input: 7
Output: False
Explanation:
The binary representation of 7 is: 111.
```
#### Example 3

```
Input: 11
Output: False
Explanation:
The binary representation of 11 is: 1011.
```
#### Example 4

```
Input: 10
Output: True
Explanation:
The binary representation of 10 is: 1010.

```

#### Solution Java

> 二进制字符串必为1开头，判断1和0的差值是否为0或1

```
class Solution {
    public boolean hasAlternatingBits(int n) {
        String s = Integer.toBinaryString(n);
        int[] temp = new int[2];
        for(int i = 0;i < s.length();i++){
            char a = s.charAt(i);
            if(a == '0'){
                temp[0]++;
            }else{
                temp[1]++;
            }
            if( !(temp[1] - temp[0] == 1 || temp[1] - temp[0] == 0) ){
                return false;
            }
        }
        return true;
    }
}

```

> 其他网友答案：位运算

```
public boolean hasAlternatingBits(int n) {
    int prev = n & (1);
    n >>= 1;
    while(n > 0) {
        if(((n & 1) ^ prev) == 0) return false;
        prev = n & 1;
        n >>= 1;
    }
    return true;
}

```