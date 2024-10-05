## Valid Palindrome II

```java
class Solution {
    public boolean validPalindrome(String s) {
        int left = 0, right = s.length() - 1;

        // 두 포인터로 회문 확인
        while (left < right) {
            if (s.charAt(left) != s.charAt(right)) {
                // 하나의 문자를 삭제하고 다시 검사
                return isPalindrome(s, left + 1, right) || isPalindrome(s, left, right - 1);
            }
            left++;
            right--;
        }
        return true;
    }

    // 주어진 범위에서 문자열이 회문인지 확인하는 메서드
    private boolean isPalindrome(String s, int left, int right) {
        while (left < right) {
            if (s.charAt(left) != s.charAt(right)) {
                return false;
            }
            left++;
            right--;
        }
        return true;
    }
}

```
