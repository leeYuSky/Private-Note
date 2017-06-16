当单词所有的字符都来源于键盘的同一行时，那么返回该字符串
#### Example

```
Input: ["Hello", "Alaska", "Dad", "Peace"]
Output: ["Alaska", "Dad"]

```

#### Solution Java

> **思路**:正则表达式;暴力检索

```
import java.util.regex.*;
public class Solution {
    public String[] findWords(String[] words) {
        Pattern p = Pattern.compile("[qwertyuiop]*|[asdfghjkl]*|[zxcvbnm]*");
        ArrayList<String> list = new ArrayList<String>(); 
        for(String s : words){
            Matcher m = p.matcher(s.toLowerCase());
            if(m.matches()){
               list.add(s); 
            }
        }
        // String[] result = new String[list.size()];
        // for(int i = 0;i < list.size();i++){
        //     result[i] = list.get(i);
        // }
        // return result;
        return list.toArray(new String[0]);
    }
}

```