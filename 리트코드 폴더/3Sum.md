## 3Sum

```java
class Solution {
    public List<List<Integer>> threeSum(int[] nums) {

    if (nums.length <= 2) {
      return Collections.emptyList();
    }

    Arrays.sort(nums);

    int zeroIndex = -1;
    for (int i = 0; i < nums.length; i++) {
      if (nums[i] >= 0) {
        zeroIndex = i;
        break;
      }
    }

    if (zeroIndex < 0) {
      return Collections.emptyList();
    }


    Set<List<Integer>> result = new HashSet<>();
    for (int i = 0; i <= zeroIndex ; i++) {

        if (i != 0 && nums[i] == nums[i - 1])
        continue;

      int left = i + 1;
      int right = nums.length - 1;

      while(left < right) {

        if (nums[left] + nums[right] + nums[i] < 0) {
          left++;
        } else if (nums[left] + nums[right] + nums[i] == 0) {
          List<Integer> subResult = new ArrayList<>();
          subResult.add(nums[i]);
          subResult.add(nums[left]);
          subResult.add(nums[right]);
          result.add(subResult);
          left++;
          right--;
        } else {
          right--;
        }
      }

      if (nums[i] == 0) {
        if (nums.length - i > 2 && nums[i + 1] == 0 && nums[i + 2] == 0) {
          result.add(Arrays.asList(0, 0, 0));
        }

        return new ArrayList<>(result);
      }
    }

    return new ArrayList<>(result);
  }
}
```
