给两个字符串a和b，判断a字符串是否能够通过b字符串里的字符构建，其中b字符串中的字符只能使用一次。

#### Example 1

```
canConstruct("a", "b") -> false
canConstruct("aa", "ab") -> false
canConstruct("aa", "aab") -> true

```

#### Solution Java

> 实质就是判断两个字符串里各个字符的个数

```
class Solution {
    public boolean canConstruct(String ransomNote, String magazine) {
        int[] temp = new int[26];
        for(char current : magazine.toCharArray()){
            temp[current - 97]++;   
        }
        for(char current : ransomNote.toCharArray()){
            if(temp[current - 97] - 1 >= 0){
                temp[current - 97] -= 1;
            }else{
                return false;   
            }
        }
        return true;
    }
}

```