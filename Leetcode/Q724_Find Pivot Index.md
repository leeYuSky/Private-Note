给定一个整形数组，返回pivot，该pivot的左边的和等于右边的和。没有返回-1

#### Example 1
```

Input: 
nums = [1, 7, 3, 6, 5, 6]
Output: 3
Explanation: 
The sum of the numbers to the left of index 3 (nums[3] = 6) is equal to the sum of numbers to the right of index 3.
Also, 3 is the first index where this occurs.

```

#### Example 2
```
Input: 
nums = [1, 2, 3]
Output: -1
Explanation: 
There is no index that satisfies the conditions in the problem statement.

```

#### Solution Java

```
class Solution {
    public int pivotIndex(int[] nums) {
        for(int i = 0;i < nums.length;i++){
            int sumLeft = 0;
            int sumRight = 0;
            for(int m = 0;m < i;m++){
                sumLeft += nums[m];   
            }
            for(int n = i+1;n < nums.length;n++){
                sumRight += nums[n];   
            }
            if(sumLeft == sumRight){
                return i;   
            }
        }
        return -1;
    }
}

```

> 先计算总和total，可以减少计算量

```
class Solution {
    public int pivotIndex(int[] nums) {
        int total = 0;
        for (int num : nums) total += num;
        int sum = 0;
        for (int i = 0; i < nums.length; sum += nums[i++])
            if (sum * 2 == total - nums[i])
                return i;
        
        return -1;  
    }
}

```