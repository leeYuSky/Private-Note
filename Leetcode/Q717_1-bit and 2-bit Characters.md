有两种特殊的字符，一种是只有一位的0，一种是有两位的10或11，给定一个int型数组，这个数组的最后一个是0，判断最后一位是否只能代表第一种字符。

#### Example 1

```
Input: 
bits = [1, 0, 0]
Output: True
Explanation: 
The only way to decode it is two-bit character and one-bit character. So the last character is one-bit character.

```

#### Example 2

```
Input: 
bits = [1, 1, 1, 0]
Output: False
Explanation: 
The only way to decode it is two-bit character and two-bit character. So the last character is NOT one-bit character.

```

#### Solution Java

> 一开始考虑本题类似于“上台阶”，故使用了递归。最后发现由于各个可能是不相关的，所以可以直接跳跃判断。

```
class Solution {
    public boolean isOneBitCharacter(int[] bits) {
        return isCharacter(bits,0);
    }
    
    public static boolean isCharacter(int[] bits,int index){
        if(index == bits.length-1){
            if(bits[index] == 0){
                return true;
            }else{
                return false;
            }
        }else{
            if(bits[index] == 1 && index + 2 <= bits.length-1){
                return isCharacter(bits,index+2);
            }else if(bits[index] == 0 && index + 1 <= bits.length-1){
                return isCharacter(bits,index+1);
            }else{
                return false;
            }
        }
    }
}

```

> 是上面答案的简化

```
class Solution {
    public boolean isOneBitCharacter(int[] bits) {
        int n = bits.length, i = 0;
        while (i < n - 1) {
            if (bits[i] == 0) i++;
            else i += 2;
        }
        return i == n - 1;
    }
}

```