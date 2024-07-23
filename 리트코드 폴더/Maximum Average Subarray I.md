## Maximum Average Subarray I

```java
private static double findMaxAverage(int[] nums, int k) {
        int n = nums.length;
        double oriSum = 0.0;
        double max = -1 * Double.MAX_VALUE;

        if (n == 1) return (double) nums[0];

        for (int i = 0; i <= n - k; i++) {
            if (i == 0) {
                for (int j = 0; j < k; j++) {
                    oriSum += nums[j];
                }
                max = Math.max(max, oriSum);
            } else {
                double newSum = oriSum - nums[i - 1] + nums[i + k - 1];
                oriSum = newSum;
                max = Math.max(max, newSum);

            }
        }
        return max / k;

    }
```

<br/><br/>

```java
private static double findMaxAverage(int[] nums, int k) {
        int n = nums.length;
        double sum = 0.0;
        double max = -1 * Double.MAX_VALUE;

        if (n == 1) return (double) nums[0];

        for (int j = 0; j < k; j++) {
            sum += nums[j];
        }
        max = Math.max(max, sum);

        for (int i = k; i < n; i++) {
            sum += nums[i] - nums[i - k];
            max = Math.max(max, sum);

        }
        return max / k;

    }
```
