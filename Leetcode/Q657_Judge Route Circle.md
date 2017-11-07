给定一串代表方向的字符串，初始坐标为(0,0)，判断是否回到原点

#### Example 1

```
Input: "UD"
Output: true
```

#### Example 2

```
Input: "LL"
Output: false
```

#### Solution Java

> **思路**:暴力检测

```
class Solution {
    public boolean judgeCircle(String moves) {
        int x = 0;
        int y = 0;
        for(int i = 0;i < moves.length();i++){
            char temp = moves.charAt(i);
            if(temp == 'U'){
                y++;
            }else if(temp == 'D'){
                y--;
            }else if(temp == 'R'){
                x--;
            }else{
                x++;
            }
        }
        if(x == 0 && y == 0){
            return true;
        }
        return false;
    }
}

```

> 网友答案

```
public boolean judgeCircle(String moves) {
        moves=" " + moves + " ";
        return moves.split("L").length==moves.split("R").length && moves.split("U").length == moves.split("D").length;
}

```