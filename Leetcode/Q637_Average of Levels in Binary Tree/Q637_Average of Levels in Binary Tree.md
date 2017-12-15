给一个二叉树，返回该二叉树每一层的平均值

#### Example 1
```
Input:
    3
   / \
  9  20
    /  \
   15   7
Output: [3, 14.5, 11]
Explanation:
The average value of nodes on level 0 is 3,  on level 1 is 14.5, and on level 2 is 11. Hence return [3, 14.5, 11].
```
#### Java Solution

> **思路:** 自己使用的是DFS，效果不好。网上答案使用BFS。

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
class Solution {
    
    Map<Integer,Long> map = new HashMap<Integer,Long>();
    Map<Integer,Integer> count = new HashMap<Integer,Integer>();
    int h = 0;
    public List<Double> averageOfLevels(TreeNode root) {
        List<Double> result = new ArrayList<Double>();
        countOfLevels(root,0);
        Object[] keys = map.keySet().toArray();
        Arrays.sort(keys);
        for(Object key : keys){
            Integer value = (Integer)key;
            result.add(map.get(value)*1.0/count.get(value));
        }
        return result;
    }
    
    public void countOfLevels(TreeNode root,int depth){
        if(map.containsKey(depth)){
            map.put(depth,map.get(depth)+(long)root.val);
            count.put(depth,count.get(depth)+1);
        }else{
            map.put(depth,(long)root.val);
            count.put(depth,1);
        }
        if(root.left != null) countOfLevels(root.left,depth+1);
        if(root.right != null) countOfLevels(root.right,depth+1);
    }
}
```

> 网上BFS答案

```
public List<Double> averageOfLevels(TreeNode root) {
    List<Double> result = new ArrayList<>();
    Queue<TreeNode> q = new LinkedList<>();
    
    if(root == null) return result;
    q.add(root);
    while(!q.isEmpty()) {
        int n = q.size();
        double sum = 0.0;
        for(int i = 0; i < n; i++) {
            TreeNode node = q.poll();
            sum += node.val;
            if(node.left != null) q.offer(node.left);
            if(node.right != null) q.offer(node.right);
        }
        result.add(sum / n);
    }
    return result;
}
```