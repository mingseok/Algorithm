## Maximum Subarray

```java
public class Solution {
    public int maxSubArray(int[] nums) {
        // 초기 최대 합을 첫 번째 요소로 설정
        int maxSum = nums[0];
        // 현재 합을 첫 번째 요소로 초기화
        int currentSum = nums[0];

        // 배열의 두 번째 요소부터 순회 시작
        for (int i = 1; i < nums.length; i++) {
            // 현재 요소와 현재 합 + 현재 요소 중 큰 값을 선택해 현재 합으로 설정
            currentSum = Math.max(nums[i], currentSum + nums[i]);
            // 현재 합과 기존 최대 합 중 큰 값을 선택해 최대 합으로 설정
            maxSum = Math.max(maxSum, currentSum);
        }

        return maxSum;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        int[] nums = {-2, 1, -3, 4, -1, 2, 1, -5, 4};
        int result = solution.maxSubArray(nums);
        System.out.println("Maximum Subarray Sum: " + result);
    }
}
```
