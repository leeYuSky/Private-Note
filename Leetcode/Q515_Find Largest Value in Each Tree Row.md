给定一个二叉树，找出每一层最大的数。

#### Example 1
```
Input: 

          1
         / \
        3   2
       / \   \  
      5   3   9 

Output: [1, 3, 9]
```
#### Java Solution

> **思路:** 类似于 637 题--寻找每一层的平均值，采用BFS或者DFS。自己使用的是BFS

```
class Solution {
    public List<Integer> largestValues(TreeNode root) {
        List<Integer> result = new ArrayList<Integer>();
        LinkedList<TreeNode> queue = new LinkedList<TreeNode>();
        if(root == null) return result;
        queue.add(root);
        while(!queue.isEmpty()){
            int n = queue.size();
            int temp = Integer.MIN_VALUE;
            for(int i = 0;i < n;i++){
                TreeNode node = queue.poll();
                if(node.val > temp){
                    temp = node.val;
                }
                if(node.left != null){
                    queue.offer(node.left);
                }
                if(node.right != null){
                    queue.offer(node.right);
                }
            }
            result.add(temp);
        }
        return result;
    }
}
```

> 网上使用DFS，这次比BFS时间快
```
class Solution {
    public List<Integer> largestValues(TreeNode root) {
        List<Integer> res=new ArrayList<>();
        if(root==null)
            return res;
        return largestValues(root,0,res);
    }
    private List<Integer> largestValues(TreeNode node, int d,List<Integer> list){
        if(d>=list.size()){
            list.add(node.val);
        }
        else if(node.val>list.get(d)){
            list.set(d,node.val);
        }
        if(node.left!=null)
            list=largestValues(node.left, d+1, list);
        if(node.right!=null)
            list=largestValues(node.right, d+1, list);
        return list;
    }
}
```