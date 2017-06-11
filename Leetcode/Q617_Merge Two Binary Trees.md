将两个树合并，合并规则为若为重合节点值相加，否则取有值节点的值。

#### Example

```
Input: 
	Tree 1                     Tree 2                  
          1                         2                             
         / \                       / \                            
        3   2                     1   3                        
       /                           \   \                      
      5                             4   7                  
Output: 
Merged tree:
	     3
	    / \
	   4   5
	  / \   \ 
	 5   4   7
```

#### Solution Java

> **思路**：递归思想。将当前输入节点按规则依次处理，生成的新的节点的左右节点递归调用merge方法。

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
    public TreeNode mergeTrees(TreeNode t1, TreeNode t2) {
        if(t1 == null && t2 == null){
            return null;
        }
        TreeNode newnode = new TreeNode(0);
        if(t1 == null && t2 != null){
            newnode.val = t2.val;
            newnode.left = mergeTrees(null,t2.left);
            newnode.right = mergeTrees(null,t2.right);
        }else if(t1 != null && t2 == null){
            newnode.val = t1.val;
            newnode.left = mergeTrees(t1.left,null);
            newnode.right = mergeTrees(t1.right,null);
        }else{
            newnode.val = t1.val + t2.val;
            newnode.left = mergeTrees(t1.left,t2.left);
            newnode.right = mergeTrees(t1.right,t2.right);
        }
        
        return newnode;
        
    }
}
```