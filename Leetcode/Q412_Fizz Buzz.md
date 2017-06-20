逢3的倍数输出“Fizz”，逢5的倍数输出“Buzz”，3和5的倍数输出“FizzBuzz”。

#### Example

```
n = 15,

Return:
[
    "1",
    "2",
    "Fizz",
    "4",
    "Buzz",
    "Fizz",
    "7",
    "8",
    "Fizz",
    "Buzz",
    "11",
    "Fizz",
    "13",
    "14",
    "FizzBuzz"
]

```


#### Solution Java

> **思想**:基本逻辑判断，但是判断的顺序对执行时间有影响


```

	public class Solution {
	    public List<String> fizzBuzz(int n) {
	        List<String> result = new ArrayList<String>();      
	        for(int i = 1;i <= n;i++){
	            if(i % 3 != 0 && i % 5 != 0){
	                result.add(String.valueOf(i));
	            }else if(i % 3 == 0 && i % 5 != 0){
	                result.add("Fizz");
	            }else if(i % 3 != 0 && i % 5 == 0){
	                result.add("Buzz");
	            }else{
	                result.add("FizzBuzz");
	            }
	        }   
	        return result;
	    }
	}

```