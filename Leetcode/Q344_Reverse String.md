字符串反转

#### Example

```
Given s = "hello", return "olleh".

```

#### Solution

> **思路**:stringbuilder（StringBuffer）的reverse()方法;转换为字符数组；

```

    public class Solution {
        public String reverseString(String s) {
            StringBuilder sb = new StringBuilder(s);
            sb.reverse();
            return sb.toString();
        }
    }
    

```

---


```

    public class Solution {
        public String reverseString(String s) {
            char[] temp = s.toCharArray();
            for(int i = 0;i < temp.length/2;i++){
                char tempchar = temp[i];
                temp[i] = temp[temp.length - 1 - i];
                temp[temp.length - 1 - i] = tempchar;
            }
            return new String(temp);
        }
    }

```