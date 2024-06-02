## Contains Duplicate

```java
import java.util.*;  
  
class Solution {  
  
    Map<Integer, Integer> map = new HashMap<>();  
    
    public boolean containsNearbyDuplicate(int[] nums, int k) {  
        for(int i = 0; i < nums.length; i++) {  
            if(map.containsKey(nums[i])) {  
                if (Math.abs(i - map.get(nums[i])) <= k) {  
                    return true;  
                }  
            }  
            map.put(nums[i], i);  
        }  
        return false;  
    }  
}
```

<br/>
<br/>

```java
class Solution {
    public boolean containsDuplicate(int[] nums) {
        Set<Integer> set = new HashSet<>();

        for (int num : nums) {
            if (!set.add(num)) {
                return true;
            }
        }

        return false;
    }
}
```
