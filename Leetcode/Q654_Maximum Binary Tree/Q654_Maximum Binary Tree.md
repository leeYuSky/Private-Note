给一个没有重复数字的数组，按以下定义构造一棵树。
1. 根节点是数组最大的值
2. 左子树由处于最大的值左边的数构成。
3. 右子树由处于最大的值右边的数构成。

#### Example 1

```
Input: [3,2,1,6,0,5]
Output: return the tree root node representing the following tree:

      6
    /   \
   3     5
    \    / 
     2  0   
       \
        1

```

#### Java Solution

> **思路**: 递归

```
class Solution {
    public TreeNode constructMaximumBinaryTree(int[] nums) {
        return getNode(nums,0,nums.length-1);
    }
    
    public static TreeNode getNode(int[] nums,int start,int end){
        if(start > end) return null;   
        int temp = Integer.MIN_VALUE;
        int index = -1;
        for(int i = start;i <= end;i++){
            if(nums[i] > temp){
                temp = nums[i];
                index = i;
            }
        }
        TreeNode result = new TreeNode(nums[index]);
        result.left = getNode(nums,start,index-1);
        result.right = getNode(nums,index+1,end);
        return result;
    }
}

```