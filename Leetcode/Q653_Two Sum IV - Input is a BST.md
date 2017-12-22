给一颗二叉排序树和一个给定值k，判断树中是否有两个元素的和等于k。

#### Example 1
```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 9

Output: True
```

#### Example 2
```
Input: 
    5
   / \
  3   6
 / \   \
2   4   7

Target = 28

Output: False
```

#### Java Solution

> **思路:** 两次遍历树，一次存值，一次搜索。注意判断是否是同一个值。

```
class Solution {
    public boolean findTarget(TreeNode root, int k) {
        Set<Integer> set = new HashSet<Integer>();
        bstFirst(root,set,k);
        return bstSecond(root,set,k);
    }
    
    public void bstFirst(TreeNode node,Set<Integer> set,int k){
        if(node == null) return;
        set.add(k - node.val);
        if(node.left != null) bstFirst(node.left,set,k);
        if(node.right != null) bstFirst(node.right,set,k);
    }
    
    public boolean bstSecond(TreeNode node,Set<Integer> set,int k){
        if(node == null) return false;
        if(node.val*2 != k){
            if(set.contains(node.val)) return true;
        }
        return bstSecond(node.left,set,k) || bstSecond(node.right,set,k);
    }
}

```

> 网上答案将两次遍历二合一。

```
public boolean findTarget(TreeNode root, int k) {
        HashSet<Integer> set = new HashSet<>();
        return dfs(root, set, k);
    }
    
    public boolean dfs(TreeNode root, HashSet<Integer> set, int k){
        if(root == null)return false;
        if(set.contains(k - root.val))return true;
        set.add(root.val);
        return dfs(root.left, set, k) || dfs(root.right, set, k);
    }
```