给定一个二叉树，找出该二叉树最底层的最左侧的元素。

#### Example 1
```
Input:

    2
   / \
  1   3

Output:
1
```
#### Example 2
```
Input:

        1
       / \
      2   3
     /   / \
    4   5   6
       /
      7

Output:
7
```

#### Java Solution

> **思路:** 直接遍历

```
class Solution {
    
    int result = 0;
    int h = 0;
    public int findBottomLeftValue(TreeNode root) {
        findBottomLeftValue(root,1);
        return result;
    }
    
    public void findBottomLeftValue(TreeNode root,int depth) {
        if(h < depth) {
            result = root.val;
            h = depth;
        }
        if(root.left != null){
            findBottomLeftValue(root.left,depth+1);
        }
        if(root.right != null){
            findBottomLeftValue(root.right,depth+1);
        }
    }
}
```