求树的最大深度

#### Solution Java

> **思路**:递归

```
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     int val;
 *     TreeNode left;
 *     TreeNode right;
 *     TreeNode(int x) { val = x; }
 * }
 */
public class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null)
            return 0;
        if(root.left != null && root.right == null){
            return maxDepth(root.left)+1;
        }
        else if(root.left == null && root.right != null){
            return maxDepth(root.right)+1;
        }
        else if(root.left != null && root.right != null){
            return Math.max(maxDepth(root.left)+1,maxDepth(root.right)+1);
        }
        else{
            return 1;
        }
    }
}

```

---

> 上面的代码等同于

```
public class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null)
            return 0;
        else
            return Math.max(maxDepth(root.left)+1,maxDepth(root.right)+1);
        
    }
}

```