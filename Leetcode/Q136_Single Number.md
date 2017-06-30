一个数组中，只有一个数只出现一次，剩余的出现两次，找出这个数

#### Solution Java

> **思路**:将整个数组进行xor运算，相同的数进行xor运算为0，故最后剩下只出现一次的数

```

    public class Solution {
        public int singleNumber(int[] nums) {
            int current = nums[0];
            for(int i = 1;i < nums.length;i++){
                current = current ^ nums[i];
            }
            return current;
        }
    }


```