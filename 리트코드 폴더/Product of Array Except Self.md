## Product of Array Except Self

```java
class Solution {
    public int[] productExceptSelf(int[] nums) {
        // 결과를 저장할 배열을 초기화 한다.
        int[] ans = new int[nums.length];
        // 왼쪽부터 시작하는 누적 곱을 저장할 변수
        int left = 1;

        // 왼쪽 곱셈
        for (int i = 0; i < nums.length; i++) {
            // 현재 인덱스 이전의 모든 요소의 곱을 ans[i]에 저장한다.
            ans[i] = left;
            // 다음 요소에 대해 왼쪽 요소의 곱을 갱신한다.
            left *= nums[i];
        }

        // 오른쪽부터 시작하는 누적 곱을 저장할 변수
        int right = 1;
        // 오른쪽 곱셈
        for (int i = nums.length - 1; i >= 0; i--) {
            // 현재 인덱스 이후의 모든 요소의 곱을 ans[i]에 누적 곱한다.
            ans[i] *= right;
            // 이전 요소에 대해 오른쪽 요소의 곱을 갱신한다.
            right *= nums[i];
        }
        // 결과 배열을 반환한다.
        return ans;
    }
}
```
