## Sort Colors

```java
public class Solution {
    public void sortColors(int[] nums) {
        int zeroIndex = 0, current = 0, twoIndex = nums.length - 1; // (1)
        while (current <= twoIndex) {
            if (nums[current] == 0) { // (2)
                swap(nums, current++, zeroIndex++);
            } else if (nums[current] == 2) { // (3)
                swap(nums, current, twoIndex--);
            } else { // (4)
                current++;
            }
        }
    }

    private void swap(int[] nums, int left, int right) {
        int temp = nums[left];
        nums[left] = nums[right];
        nums[right] = temp;
    }
}
```
