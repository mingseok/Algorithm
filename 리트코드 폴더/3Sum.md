## 3Sum

```java
import java.util.*;

public class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        HashSet<List<Integer>> uniqueList = new HashSet<>();
        Arrays.sort(nums);

        for (int current = 0; current <= nums.length - 2; current++) {
            int left = current + 1;
            int right = nums.length - 1;

            while (left < right) {
                int sum = nums[left] + nums[right] + nums[current];

                if (sum == 0) {
                    List<Integer> triplet = Arrays.asList(nums[current], nums[left], nums[right]);
                    // Collections.sort(triplet);
                    uniqueList.add(triplet);

                    left++;
                    right--;
                } else if (sum > 0) {
                    right--;
                } else {
                    left++;
                }
            }
        }
        return new ArrayList<>(uniqueList);
    }
}
```

<br/><br/>

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {
        List<List<Integer>> res = new LinkedList<List<Integer>>();
        
        Arrays.sort(nums);
        
        for (int i = 0; i < nums.length - 2; i++) {
            if (i > 0 && nums[i] == nums[i-1]) continue;
            
            int left = i + 1;
            int right = nums.length - 1;
            
            while (left < right) {
                int sum = nums[left] + nums[right] + nums[i];
                
                if (sum == 0) {
                    res.add(Arrays.asList(nums[i], nums[left], nums[right]));
                    left++;
                    right--;
                    while (nums[left] == nums[left - 1] && left < right) left++;
                    while (nums[right] == nums[right + 1] && left < right) right--;
                } else if (sum > 0) {
                    right--;
                } else {
                    left++;
                }
            }
        }
        
        return res;
    }
}
```
