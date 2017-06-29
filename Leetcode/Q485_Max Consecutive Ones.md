寻找一个只包含0和1的数组中连续1最长的长度

#### Example

```
Input: [1,1,0,1,1,1]
Output: 3
Explanation: The first two digits or the last three digits are consecutive 1s.
    The maximum number of consecutive 1s is 3.

```

#### Solution Java

> **思路**:暴力循环(速度太慢，打败0.6%);使用临时数组进行一次遍历（打败55%）；

```

    public class Solution {
        public int findMaxConsecutiveOnes(int[] nums) {
            int max = 0;
            for(int i = 0;i < nums.length;i++){
                if(nums[i] == 1){
                    int temp = 1;
                    for(int j = i+1;j < nums.length;j++){
                        if(nums[j] == 1){
                            temp++;
                        }else{
                            break;
                        }
                    }
                    if(temp > max){
                        max = temp;
                    }
                }
            }
            return max;
        }
    }

```

---

```

    public class Solution {
        public int findMaxConsecutiveOnes(int[] nums) {
            int[] result = new int[nums.length];
            int max = 0;
            for(int i = nums.length - 1;i >= 0;i--){
                if(i != nums.length - 1){
                    if(nums[i] == 1){
                        result[i] = result[i+1] + 1;
                    }
                }else{
                    if(nums[i] == 1){
                       result[i] = 1; 
                    }
                }
                if(result[i] > max){
                    max = result[i];
                }
            }
            return max;
        }
    }

```