给定两个数组nums1、nums2，寻找nums1中每个数x在nums2中对应的数的位置之后的比它大的数。没有返回-1

#### Example 1

```
Input: nums1 = [4,1,2], nums2 = [1,3,4,2].
Output: [-1,3,-1]
Explanation:
    For number 4 in the first array, you cannot find the next greater number for it in the second array, so output -1.
    For number 1 in the first array, the next greater number for it in the second array is 3.
    For number 2 in the first array, there is no next greater number for it in the second array, so output -1.

```

#### Example 2

```
Input: nums1 = [2,4], nums2 = [1,2,3,4].
Output: [3,-1]
Explanation:
    For number 2 in the first array, the next greater number for it in the second array is 3.
    For number 4 in the first array, there is no next greater number for it in the second array, so output -1.

```

#### Solution Java

> **思路**:暴力检索；

```

    public class Solution {
            public int[] nextGreaterElement(int[] findNums, int[] nums) {                        
            int[] result = new int[findNums.length];
            for(int i = 0;i < findNums.length;i++){
                int temp = findNums.length;
                for(int j = 0;j < nums.length;j++){
                    if(findNums[i] == nums[j]){
                        temp = j;
                    }
                    if(j > temp && findNums[i] < nums[j]){
                        result[i] = nums[j];
                        break;
                    }
                }
                if(result[i] == 0){
                    result[i] = -1;
                }
            }
            return result;
        }
    }
    

```

其他网友答案

```

    public int[] nextGreaterElement(int[] findNums, int[] nums) {
        Map<Integer, Integer> map = new HashMap<>(); // map from x to next greater element of x
        Stack<Integer> stack = new Stack<>();
        for (int num : nums) {
            while (!stack.isEmpty() && stack.peek() < num)
                map.put(stack.pop(), num);
            stack.push(num);
        }   
        for (int i = 0; i < findNums.length; i++)
            findNums[i] = map.getOrDefault(findNums[i], -1);
        return findNums;
    }

```