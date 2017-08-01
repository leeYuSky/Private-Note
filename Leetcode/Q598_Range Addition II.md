给定 m,n 两个数字，以及一个二维数组 [[a,b],[c,d] ... ]，使得在二维数组 [m][n] 中 0 < i < a, 0 < j < b 中的每一位加1，最后求得最大值的个数。

#### Example

````
Input: 
m = 3, n = 3
operations = [[2,2],[3,3]]
Output: 4
Explanation: 
Initially, M = 
[[0, 0, 0],
 [0, 0, 0],
 [0, 0, 0]]

After performing [2,2], M = 
[[1, 1, 0],
 [1, 1, 0],
 [0, 0, 0]]

After performing [3,3], M = 
[[2, 2, 1],
 [2, 2, 1],
 [1, 1, 1]]

So the maximum integer in M is 2, and there are four of it in M. So return 4.

````

#### Solution Java

> **思路**:暴力求解（最后导致内存溢出，不可取）;问题转换后就是求列的最小值和行的最小值，返回两个最小值的乘积;

##### 暴力

````
public class Solution {
    public int maxCount(int m, int n, int[][] ops) {
        if(ops.length == 0)
            return m*n;
        
        int[][] resultM = new int[m][n];
        for(int i = 0;i < ops.length;i++){
            for(int j = 0;j < ops[i][0];j++){
                for(int k = 0;k < ops[i][1];k++){
                    resultM[j][k]++;
                }
            }
        }
        int maxNum = 0;
        int count = 0;
        for(int i = 0;i < m;i++){
            for(int j = 0;j < n;j++){
                if(resultM[i][j] == maxNum){
                    count++;
                }else if(resultM[i][j] > maxNum){
                    count = 1;
                    maxNum = resultM[i][j];
                }
            }
        }
        return count;
    }
}

````

##### 最小值乘积

````
public class Solution {
    public int maxCount(int m, int n, int[][] ops) {
        int minRow = m;
        int minCol = n;
        for(int i = 0;i < ops.length;i++){
            if(ops[i][0] < minRow){
                minRow = ops[i][0];
            }
            if(ops[i][1] < minCol){
                minCol = ops[i][1];
            }
        }
        return minRow*minCol;
    }
}

````