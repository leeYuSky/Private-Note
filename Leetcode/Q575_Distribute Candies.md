给定even个数的数组，分成两组，寻找一个组中最多的不同数的个数

#### Example 1
```
Input: candies = [1,1,2,2,3,3]
Output: 3
Explanation:
There are three different kinds of candies (1, 2 and 3), and two candies for each kind.
Optimal distribution: The sister has candies [1,2,3] and the brother has candies [1,2,3], too. 
The sister has three different kinds of candies. 

```

#### Example 2

```
Input: candies = [1,1,2,3]
Output: 2
Explanation: For example, the sister has candies [2,3] and the brother has candies [1,1]. 
The sister has two different kinds of candies, the brother has only one kind of candies. 

```

#### Solution Java

> **思路**:将所有的数放到hashmap中（考虑性能可以放到hashset）

```
public class Solution {
    public int distributeCandies(int[] candies) {
        HashMap<Integer,Integer> map = new HashMap<Integer,Integer>();
        for(int num : candies){
            if(map.containsKey(num)){
                map.put(num,map.get(num)+1);
            }else{
                map.put(num,1);
            }
        }
        int count = map.size();
        if(count < candies.length/2){
            return count;
        }else{
            return candies.length/2;
        }
    }
}

```

#### HashSet

```

public class Solution {
    public int distributeCandies(int[] candies) {
        HashSet<Integer> set = new HashSet<Integer>();
        for(int num : candies){
            set.add(num);
        }
        return set.size() < candies.length/2 ? set.size() : candies.length/2;
    }
}

```