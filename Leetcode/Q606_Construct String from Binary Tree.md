将一个数组表示的树转换成字符串形式，并且使转换无歧义。

#### Example 1

```
Input: Binary tree: [1,2,3,4]
       1
     /   \
    2     3
   /    
  4     

Output: "1(2(4))(3)"

Explanation: Originallay it needs to be "1(2(4)())(3()())", 
but you need to omit all the unnecessary empty parenthesis pairs. 
And it will be "1(2(4))(3)".

```

#### Example 2

```
Input: Binary tree: [1,2,3,null,4]
       1
     /   \
    2     3
     \  
      4 

Output: "1(2()(4))(3)"

Explanation: Almost the same as the first example, 
except we can't omit the first parenthesis pair to break the one-to-one mapping relationship between the input and the output.

```

#### Solution Java

> **思路**:递归，注意要保证树的结构不变且无歧义；

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
    public String tree2str(TreeNode t) {
        StringBuilder sb = new StringBuilder();
        if(t == null)
            return "";
        sb.append(String.valueOf(t.val));
        if(t.left != null){
            sb.append("("+tree2str(t.left)+")");
        }else if(t.left == null && t.right != null){
            sb.append("()");
        }
        if(t.right != null){
            sb.append("("+tree2str(t.right)+")");
        }
        return sb.toString();
    }
}

```