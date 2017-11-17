给定两个复数字符串，进行复数乘法

#### Example 1

```
Input: "1+1i", "1+1i"
Output: "0+2i"
Explanation: (1 + i) * (1 + i) = 1 + i2 + 2 * i = 2i, and you need convert it to the form of 0+2i.

```

#### Example 2

```
Input: "1+-1i", "1+-1i"
Output: "0+-2i"
Explanation: (1 - i) * (1 - i) = 1 + i2 - 2 * i = -2i, and you need convert it to the form of 0+-2i.

```

#### Solution Java

> 取出4个整数分别进行乘法

```
class Solution {
    public String complexNumberMultiply(String a, String b) {
        String[] temp1 = a.split("\\+");
        String[] temp2 = b.split("\\+");
        int a1 = Integer.parseInt(temp1[0]);
        int b1 = Integer.parseInt(temp2[0]);
        int a2 = Integer.parseInt(temp1[1].substring(0,temp1[1].length()-1));
        int b2 = Integer.parseInt(temp2[1].substring(0,temp2[1].length()-1));
        int val1 = a1 * b1;
        int val2 = a1 * b2;
        int val3 = a2 * b1;
        int val4 = a2 * b2;
        int result1 = val1 - val4;
        int result2 = val2 + val3;
        StringBuilder sb = new StringBuilder();
        sb.append(result1).append("+").append(result2).append("i");
        return sb.toString();
        
    }
}

```




