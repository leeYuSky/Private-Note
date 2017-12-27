判断两棵树是否一样。

#### Example 1
```
Input:     1         1
          / \       / \
         2   3     2   3

        [1,2,3],   [1,2,3]

Output: true

```

#### Example 2
```
Input:     1         1
          /           \
         2             2

        [1,2],     [1,null,2]

Output: false

```

#### Example 3
```
Input:     1         1
          / \       / \
         2   1     1   2

        [1,2,1],   [1,1,2]

Output: false

```

#### Java Solution

> **思路: ** 递归

```
public boolean isSameTree(TreeNode p, TreeNode q) {
    if(p == null && q == null) return true;
    if(p == null || q == null) return false;
    if(p.val == q.val)
        return isSameTree(p.left, q.left) && isSameTree(p.right, q.right);
    return false;
}

```