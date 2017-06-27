计算一个由二维数组组成的岛的周长

#### Example 1:

```
[[0,1,0,0],
 [1,1,1,0],
 [0,1,0,0],
 [1,1,0,0]]

Answer: 16

```

#### Solution

> **思路**:暴力判断四周(速度感人，只打败了6%的人....)

```

    public class Solution {
        public int islandPerimeter(int[][] grid) {
            int count = 0;
            for(int i = 0;i < grid.length;i++){
                for(int j = 0;j < grid[i].length;j++){
                    if(grid[i][j] == 1){
                        if( (((i - 1) >= 0) && grid[i-1][j] == 0) || (i - 1) < 0 ){
                            count++;
                        }
                        if( (((i + 1) < grid.length) && grid[i+1][j] == 0) || (i + 1) >= grid.length ){
                            count++;
                        }
                        if( (((j - 1) >= 0) && grid[i][j-1] == 0) || (j - 1) < 0 ){
                            count++;
                        }
                        if( (((j + 1) < grid[i].length) && grid[i][j+1] == 0) || (j + 1) >= grid[i].length ){
                            count++;
                        }
                    }
                }
            }
            return count;
        }
    }

```

其他网友答案

> 计算右边与下边的覆盖的岛，避免重复计算

```

    public class Solution {
        public int islandPerimeter(int[][] grid) {
            int islands = 0, neighbours = 0;

            for (int i = 0; i < grid.length; i++) {
                for (int j = 0; j < grid[i].length; j++) {
                    if (grid[i][j] == 1) {
                        islands++; // count islands
                        if (i < grid.length - 1 && grid[i + 1][j] == 1) neighbours++; // count down neighbours
                        if (j < grid[i].length - 1 && grid[i][j + 1] == 1) neighbours++; // count right neighbours
                    }
                }
            }

            return islands * 4 - neighbours * 2;
        }
    }

```
