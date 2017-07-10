给一个非负数，将这个数的各个位的数相加直到这个数只有一位数字。

#### Example

```
Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.

```

#### Solution Java

> **思路**:循环

```
public class Solution {
    public int addDigits(int num) {
        while(num >= 10){
            int temp = num;
            int currentResult = 0;
            while(temp != 0){
                int i = 1;
                int last = temp % ( (int)Math.pow(10,i));
                temp = temp / ( (int)Math.pow(10,i));
                i+=1;
                currentResult+=last;
            }
            num = currentResult;
        }
        return num;
    }
}

```

#### 其他网友答案

```
public class Solution {
    public int addDigits(int num) {
        if (num == 0){
            return 0;
        }
        if (num % 9 == 0){
            return 9;
        }
        else {
            return num % 9;
        }
    }
}

```

```
public int addDigits(int num) {
        return (num!=0 && num%9==0) ? 9 : num%9;
}

```

> 解释 

```
10^k % 9 = 1
a*10^k % 9 = a % 9 

```

```
if you list all results from 0 to 30, you may see some rule. the results periodically occur.

0~9 (10 nums) :      0,1,2,3,4,5,6,7,8,9
10~18(9 nums):         1,2,3,4,5,6,7,8,9
19~27(9 nums):         1,2,3,4,5,6,7,8,9
and so on

```