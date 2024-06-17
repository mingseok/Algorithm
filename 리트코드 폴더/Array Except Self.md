## Product of Array Except Self

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        int[] results = new int[nums.length];

        int allMultipleValue = 1;
        for (int num : nums) {
            allMultipleValue *= num;
        }

        for (int i = 0; i < nums.length; i++) {
            results[i] = nums[i] == 0 ? 0 : (allMultipleValue / nums[i]);
        }

        return results;
    }
}
```
