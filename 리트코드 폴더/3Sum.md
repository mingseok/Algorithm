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
