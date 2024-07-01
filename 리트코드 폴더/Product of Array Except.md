## Product of Array Except

```java
class Solution {
    public int[]  productExceptSelf(int[] nums) {
        int left = 1;
        int right = 1;
        int[] result = new int[nums.length];

        for (int idx = 0; idx < nums.length; idx++) {
            result[idx] = left;
            left *= nums[idx];
        }


        for (int idx = nums.length - 1; idx >= 0; idx--) {
            result[idx] *= right;
            right *= nums[idx];
        }

        return result;
    }
}
```
