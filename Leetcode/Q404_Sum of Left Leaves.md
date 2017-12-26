给定一个二叉树，计算该二叉树所有左叶结点的值的和。

#### Example 1
```
    3
   / \
  9  20
    /  \
   15   7

There are two left leaves in the binary tree, with values 9 and 15 respectively. Return 24.
```

#### Java Solution

> **思路:** 直接判断

```
class Solution {
    int sum = 0;
    public int sumOfLeftLeaves(TreeNode root) {
        DFS(root);
        return sum;
    }
    
    public void DFS(TreeNode node){
        if(node == null){
            return;
        }
        if(node.left != null && node.left.left == null && node.left.right == null){
            sum+=node.left.val;
        }
        if(node.left != null){
            DFS(node.left);
        }
        if(node.right != null){
            DFS(node.right);
        }
    }
}
```

> 网上简洁递归

```
public int sumOfLeftLeaves(TreeNode root) {
    if(root == null) return 0;
    int ans = 0;
    if(root.left != null) {
        if(root.left.left == null && root.left.right == null) ans += root.left.val;
        else ans += sumOfLeftLeaves(root.left);
    }
    ans += sumOfLeftLeaves(root.right);
    
    return ans;
}
```