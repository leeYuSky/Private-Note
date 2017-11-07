包含4种类型字符串的数组：

* Integer : 本局得分
* "+" : 本局得分为前两个有效局的得分之和
* "D" : 本局得分为前一个有效局的两倍
* "C" : 前一局为无效局，去除

#### Example 1

```
Input: ["5","2","C","D","+"]
Output: 30
Explanation: 
Round 1: You could get 5 points. The sum is: 5.
Round 2: You could get 2 points. The sum is: 7.
Operation 1: The round 2's data was invalid. The sum is: 5.  
Round 3: You could get 10 points (the round 2's data has been removed). The sum is: 15.
Round 4: You could get 5 + 10 = 15 points. The sum is: 30.

```

#### Example 2

```
Input: ["5","-2","4","C","D","9","+","+"]
Output: 27
Explanation: 
Round 1: You could get 5 points. The sum is: 5.
Round 2: You could get -2 points. The sum is: 3.
Round 3: You could get 4 points. The sum is: 7.
Operation 1: The round 3's data is invalid. The sum is: 3.  
Round 4: You could get -4 points (the round 3's data has been removed). The sum is: -1.
Round 5: You could get 9 points. The sum is: 8.
Round 6: You could get -4 + 9 = 5 points. The sum is 13.
Round 7: You could get 9 + 5 = 14 points. The sum is 27.

```

#### Solution Java

> 按规则直接写

```
class Solution {
    public int calPoints(String[] ops) {
        int sum = 0;
        int[] temp = new int[ops.length];
        for(int i = 0;i < ops.length;i++){
            if(ops[i].equals("+")){
                int tempCount = 0;
                for(int j = i-1;j >=0;j--){
                    if(temp[j] != Integer.MIN_VALUE && tempCount < 2){
                        temp[i] = temp[j] + temp[i];
                        tempCount++;
                    }
                }
            }else if(ops[i].equals("C")){
                temp[i] = Integer.MIN_VALUE;
                for(int j = i-1;j >=0;j--){
                    if(temp[j] != Integer.MIN_VALUE){
                        temp[j] = Integer.MIN_VALUE;
                        break;
                    }
                }
            }else if(ops[i].equals("D")){
                for(int j = i-1;j >=0;j--){
                    if(temp[j] != Integer.MIN_VALUE){
                        temp[i] = temp[j] * 2;
                        break;
                    }
                }
            }else{
                temp[i] = Integer.parseInt(ops[i]);
            }
        }
        int result = 0;
        for(int i = 0;i < temp.length;i++){
            if(temp[i] != Integer.MIN_VALUE){
                result += temp[i];
            }
        }
        return result;
    }
}

```

> 其他网友答案 ，使用栈

```

public int calPoints(String[] ops) {
    int sum = 0;
    Stack<Integer> stack = new Stack<Integer>();
    for(int i = 0; i < ops.length; i++)
    {
        if(ops[i].equals("+"))
        {
            int temp1 = stack.pop();
            int temp2 = stack.pop();
            int temp_sum = temp1 + temp2;
            sum += temp_sum;
            stack.push(temp2);
            stack.push(temp1);
            stack.push(temp_sum);
        }
        else if(ops[i].equals("D"))
        {
            int temp = stack.pop();
            int temp_d = 2 * temp;
            sum += temp_d;
            stack.push(temp);
            stack.push(temp_d);
        }
        else if(ops[i].equals("C"))
        {
            int cancel = stack.pop();
            sum -= cancel;
        }
        else
        {
            int temp = Integer.parseInt(ops[i]);
            sum += temp;
            stack.push(temp);   
        }
    }
    return sum;
}

```