只有全为大写（如USA），或全为小写（如leetcode），或只有第一个字母大写（如Google）为合法的，返回true，否则返回false

#### Example 1

```
Input: "USA"
Output: True

```

#### Example 2

```
Input: "FlaG"
Output: False

```

#### Solution Java

> **思路**:全是大写的字符串toUpperLower后不变，全是小写同理。只有首字母大写可以通过字串分别判断。也可以使用CHARACTER.isUpperLower是否是大写。

```
public class Solution {
    public boolean detectCapitalUse(String word) {
        String header = word.substring(0,1);
        String body = word.substring(1);
        if(word.toUpperCase().equals(word) || word.toLowerCase().equals(word)){
            return true;
        }else if(header.toUpperCase().equals(header) && body.toLowerCase().equals(body) ){
            return true;
        }else{
            return false;
        }
    }
}

```