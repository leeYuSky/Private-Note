将一个个数为2n的数组两两配对，取每一对的最小值，然后让最小值之和最大
#### Example

```
Input: [1,4,3,2]

Output: 4
Explanation: n is 2, and the maximum sum of pairs is 4 = min(1, 2) + min(3, 4).

```

#### Solution Java

> **思路**:对数组排序，从第一个开始，每隔两个加起来。

```
public class Solution {
    public int arrayPairSum(int[] nums) {
        Arrays.sort(nums);
        int count = 0;
        for(int i = 0;i < nums.length;i+=2){
            count+=nums[i];
        }
        
        return count;
    }
}

```


> 网友思路：以空间换时间

```

public class Solution {
    public int arrayPairSum(int[] nums) {
         int[] hash=new int[20001];
         for(int ele:nums){
             hash[ele+10000]++;
         }
         int sum=0;
         int p=0;
         for(int i=0;i<20001;i++){
             if(hash[i]==0) continue;
             while(hash[i]!=0){
                 if(p%2==0){
                     sum+=(i-10000);
                 }
                 p++;
                 hash[i]--;
             }
         }
         return sum;
    }
}

```