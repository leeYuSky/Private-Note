给一个字符串s和一个字符串t，t由s随机排列组成并且在一个位置多插入了一个字符，找到这个字符。

#### Example 

```

Input:
s = "abcd"
t = "abcde"

Output:
e

Explanation:
'e' is the letter that was added.

```

#### Solution Java

> **思路**:将字符串s和字符串t各遍历一边并将字符出现的字符分别记录在各自的计数int[]中，在比较数组的数字。

```

public class Solution {
    public char findTheDifference(String s, String t) {
        int[] result1 = new int[26];
        int[] result2 = new int[26];
        for(int i = 0;i < s.length();i++){
            char temp = s.charAt(i);
            result1[temp - 97] = result1[temp - 97] + 1;
        }
        for(int j = 0;j < t.length();j++){
            char temp = t.charAt(j);
            result2[temp - 97] = result2[temp - 97] + 1;    
        }
        char result = 'a';
        for(int i = 0;i < result1.length;i++){
            if(result1[i] != result2[i]){
                result = (char)(result + i);
                break;
            }
        }
        return result;
    }
}

```