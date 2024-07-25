## Find Pivot Index

```java
public int pivotIndex(int[] nums) {
    int totalSum = Arrays.stream(nums).sum();
    int leftSum = 0;
    int pivot = 0;

    for (int i = 0; i < nums.length; i++) {

        pivot = i;
        totalSum -= nums[i];

        if (totalSum == leftSum) {
            return pivot;
        }
        leftSum += nums[i];
    }

    return -1;
}
```

<br/><br/>

```java
public int pivotIndex(int[] nums) {

    int answer = -1;

    for (int pivotIdx = 0; pivotIdx < nums.length; pivotIdx++) {
        int leftSum = 0;
        int rightSum = 0;

        for(int left = pivotIdx; left < pivotIdx; left++)
            leftSum += nums[left];
        
        for (int right = nums.length - pivotIdx; right < nums.length; right++)
            rightSum += nums[right];

        if (leftSum == rightSum) answer = i;
    }

    return answer;
}
```
