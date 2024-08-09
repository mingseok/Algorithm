## House Robber

```java
class Solution {
    public int rob(int[] nums) {
        // nums의 원소가 한 개일 경우 해당 원소를 바로 return
        if(nums.length == 1) return nums[0];

        // 첫 번째 집을 들르는 경우
        int[] dp1 = new int[nums.length];
        // 두 번째 집을 들르는 경우
        int[] dp2 = new int[nums.length];
        
        dp1[0] = dp1[1] = nums[0];
        dp2[1] = nums[1];
        
        for(int i = 2; i < nums.length; i++) {
            if(i < nums.length - 1) {
                // dp1은 마지막 집 전까지만 탐색
                dp1[i] = Math.max(dp1[i-2] + nums[i], dp1[i-1]);                
            }
            // dp2는 마지막 집까지 탐색
            dp2[i] = Math.max(dp2[i-2] + nums[i], dp2[i-1]);
        }
        
        // 두 개의 최종 탐색값중 큰 값을 return
        return Math.max(dp1[nums.length - 2], dp2[nums.length - 1]);
    }
}
```
