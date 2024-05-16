## Find Minimum in Rotated Sorted Array

```java
public class Solution {
    public int findMin(int[] nums) {
        int left = 0, right = nums.length - 1;
        
        // 반복 조건: left와 right가 만나지 않는 동안 계속 탐색
        while (left < right) {
            // 중간 인덱스 계산
            int mid = left + (right - left) / 2;
            
            // 중간 값과 오른쪽 끝 값 비교
            if (nums[mid] > nums[right]) {
                // 중간 값이 오른쪽 값보다 크다면, 최소값은 중간 인덱스의 오른쪽에 있다는 뜻
                // 따라서 왼쪽 범위를 조정하여 중간 인덱스의 오른쪽 부분을 탐색
                left = mid + 1;
            } else {
                // 중간 값이 오른쪽 값보다 작거나 같다면, 최소값은 중간 인덱스 이하에 있다는 뜻
                // 따라서 오른쪽 범위를 조정하여 중간 인덱스의 왼쪽 부분을 포함하여 탐색
                right = mid;
            }
        }
        // 최소값 반환: 반복문 종료 후 left는 최소값을 가리키는 인덱스가 됨
        return nums[left];
    }
}
```
