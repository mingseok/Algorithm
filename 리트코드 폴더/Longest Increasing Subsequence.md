## Longest Increasing Subsequence

```java
class Solution {
    public int lengthOfLIS(int[] nums) {
        // 1. 예외
        if (nums.length == 0) return 0;

        // 2. dp 배열
        int[] dp = new int[nums.length];
        // 2-1. dp[0] 초기화
        dp[0] = 1;
        // 2-2. LIS 초기화
        int maxResult = 1;

        // 3. 현재 원소를 기준으로
        for (int i = 1; i < nums.length; i ++) {
            // 3-1. 현재 원소를 기준으로, LIS
            int maxVal = 0;
            // 3-2. 이전의 원소들을 비교
            for (int j = 0; j < i; j ++) {
                if (nums[i] > nums[j]) {
                    maxVal = Math.max(maxVal, dp[j]);
                }
            }

            // 4. 현재 원소를 기준으로, LIS + 1
            dp[i] = maxVal + 1;
            // 5. 현재까지 가장 큰 LIS
            maxResult = Math.max(maxResult, dp[i]);
        }

        return maxResult;
    }
}
```

<br/><br/>

```java
class Solution {
    // LIS ??? LCS ???
    // LIS : Longest Increasing Sequence
    // LCS : Longest Common subsequence
    public int lengthOfLIS(int[] nums) {
        if (nums.length == 0) return 0;
        int[] dp = new int [nums.length];
        dp[0] = 1;
        int maxResult = 1;

        for (int i = 1; i < nums.length; i++) {
            int maxVal = 0;
            for (int j = 0; j < i; j++) {
                // 현재의 값 (nums[i]) > 과거의 값(nums[i])
                // 5 > 2
                System.out.println("인덱스 입니다 -> i : " + i + " j : " + j);
                if(nums[i] > nums[j]) {
                System.out.println(" >> nums[i] : " + nums[i] + " >> nums[j] : " + nums[j]);         
                  maxVal = Math.max(maxVal, dp[4]);//-> 핵심 포인트
                  System.out.println("maxVal : " + maxVal);
                }
            }
            dp[i] = maxVal + 1;
            System.out.println("dp : " + Arrays.toString(dp));
            maxResult = Math.max(maxResult, dp[i]);
            System.out.println("maxResult : " + maxResult);
        }
        return maxResult;
    }
}
```
