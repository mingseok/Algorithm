## Maximum Gap

```java
import java.util.Arrays;

public class Solution {
    public int maximumGap(int[] nums) {
        // 예외 처리: 배열의 크기가 2보다 작으면 최대 차이가 없으므로 0 반환
        if (nums == null || nums.length < 2) {
            return 0;
        }

        // 배열의 최대값과 최소값을 찾음
        int minVal = Arrays.stream(nums).min().getAsInt();
        int maxVal = Arrays.stream(nums).max().getAsInt();

        // 모든 값이 동일한 경우, 최대 차이는 0
        if (minVal == maxVal) {
            return 0;
        }

        int n = nums.length;

        // 각 버킷의 크기 계산
        int bucketSize = Math.max(1, (maxVal - minVal) / (n - 1));
        int bucketCount = (maxVal - minVal) / bucketSize + 1;

        // 각 버킷에 저장할 최소값과 최대값을 저장할 배열
        int[] bucketMin = new int[bucketCount];
        int[] bucketMax = new int[bucketCount];
        Arrays.fill(bucketMin, Integer.MAX_VALUE);
        Arrays.fill(bucketMax, Integer.MIN_VALUE);

        // 각 숫자를 해당하는 버킷에 할당
        for (int num : nums) {
            int bucketIndex = (num - minVal) / bucketSize;
            bucketMin[bucketIndex] = Math.min(bucketMin[bucketIndex], num);
            bucketMax[bucketIndex] = Math.max(bucketMax[bucketIndex], num);
        }

        // 버킷 사이의 최대 차이를 계산
        int maxGap = 0;
        int prevMax = minVal;

        for (int i = 0; i < bucketCount; i++) {
            // 비어있는 버킷은 건너뜀
            if (bucketMin[i] == Integer.MAX_VALUE && bucketMax[i] == Integer.MIN_VALUE) {
                continue;
            }

            // 이전 버킷의 최대값과 현재 버킷의 최소값의 차이를 계산하여 최대 차이를 업데이트
            maxGap = Math.max(maxGap, bucketMin[i] - prevMax);
            prevMax = bucketMax[i];
        }

        return maxGap;
    }
}

```
