将字符串的每一个单词反转

#### Example

```
Input: "Let's take LeetCode contest"
Output: "s'teL ekat edoCteeL tsetnoc"

```

#### Solution Java

> **思路**:将字符转splie，然后将string转为stringbuilder或stringbuffer调用reverse，最后合并

```
public class Solution {
    public String reverseWords(String s) {
       String[] temp = s.split(" ");
       for(int i = 0;i < temp.length;i++){
           StringBuilder sb = new StringBuilder(temp[i]);
           sb.reverse();
           temp[i] = sb.toString();
       }
       StringBuilder result = new StringBuilder();
       for(String n : temp){
           result.append(n+" ");
       }
       
       return result.substring(0,s.length());
    }
}

```

#### 其他网友答案

```
public String reverseWords(String s) 
{
    char[] s1 = s.toCharArray();
    int i = 0;
    for(int j = 0; j < s1.length; j++)
    {
        if(s1[j] == ' ')
        {
            reverse(s1, i, j - 1);
            i = j + 1;
        }
    }
    reverse(s1, i, s1.length - 1);
    return new String(s1);
}

public void reverse(char[] s, int l, int r)
{
	while(l < r)
	{
		char temp = s[l];
		s[l] = s[r];
		s[r] = temp;
		l++; r--;
	}
}

```