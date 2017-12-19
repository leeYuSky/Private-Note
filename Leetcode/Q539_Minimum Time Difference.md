给定一个"时间:分钟"格式的字符串线性表，判断两个时间的时间差最小是多少？

#### Example 1

```
Input: ["23:59","00:00"]
Output: 1
```

#### Java Solution

> 直接计算每个字符串的分钟数，在进行排序，依次计算每个的差值。注意最后一个元素和第一个元素的差值的计算方式.

```
class Solution {
    public int findMinDifference(List<String> timePoints) {
        int length = timePoints.size();
        int[] realValue = new int[length];
        for(int i = 0; i < length;i++){
            String[] temp = timePoints.get(i).split(":");
            realValue[i] = Integer.parseInt(temp[0]) * 60 + Integer.parseInt(temp[1]);
        }
        Arrays.sort(realValue);
        int result = Integer.MAX_VALUE;
        for(int i = 1;i < length;i++){
            if(realValue[i] - realValue[i-1] < result){
                result = realValue[i] - realValue[i-1];
            }
        }
        int other = 24 * 60 - realValue[length-1] + realValue[0];
        return result < other ? result : other;
    }
}
```