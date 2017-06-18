矩阵reshape，将原有矩阵reshape成相应大小的新矩阵。

#### Example 1

```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 1, c = 4
Output: 
[[1,2,3,4]]
Explanation:
The row-traversing of nums is [1,2,3,4]. The new reshaped matrix is a 1 * 4 matrix, fill it row by row by using the previous list.

```


#### Example 2

```
Input: 
nums = 
[[1,2],
 [3,4]]
r = 2, c = 4
Output: 
[[1,2],
 [3,4]]
Explanation:
There is no way to reshape a 2 * 2 matrix to a 2 * 4 matrix. So output the original matrix.

```

#### Solution Java

> **思路**:获取矩阵大小，按要求生成新矩阵（遍历矩阵）

```
public class Solution {
    public int[][] matrixReshape(int[][] nums, int r, int c) {
        int height = nums.length;
        int width = nums[0].length;
        if((height * width) != (r * c)){
            return nums;
        }else{
            int[][] result = new int[r][c];
            int currentR = 0;
            int currentC = 0;
            for(int i = 0;i < nums.length;i++){
                for(int j = 0;j < nums[i].length;j++){
                    result[currentR][currentC] = nums[i][j];
                    if(currentC < c-1){
                        currentC++;
                    }else{
                        currentR++;
                        currentC = 0;
                    }
                }
            }
            return result;
        }
    }
}

```