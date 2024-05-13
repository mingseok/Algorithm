## Missing Number

```java
class Solution {
    fun missingNumber(nums: IntArray): Int {
        // 배열의 길이를 n으로 저장
        val n = nums.size
        // 완전한 범위에서의 총합을 계산 (0부터 n까지 모든 수의 . 하)
        val totalSum = n * (n + 1) / 2

        // 주어진 배열 nums의 모든 원소의 총합을 계산
        var actualSum = 0
        for (num in nums) {
            // 각 원소를 주어진 배열의 총합에 더함
            actualSum += num
        }

        // 완전한 범위의 총합과 주어진 배열의 총합을 차이를 통해 누락된 숫자를 계산
        return totalSum - actualSum
    }
}
```

<br/>

```java
class Solution {
    public int missingNumber(int[] nums) {
        int total = IntStream.range(0,nums.length+1).sum();
        int sum = 0;
        for (int i = 0; i < nums.length; i++) {
            sum += nums[i];
        }
        return total - sum;
    }
}
```
