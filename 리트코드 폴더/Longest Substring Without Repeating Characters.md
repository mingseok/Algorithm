## Longest Substring Without Repeating Characters

```java
import java.util.HashMap;

public class Solution {
    public int lengthOfLongestSubstring(String s) {
        // 해시맵을 사용하여 문자의 위치를 저장
        HashMap<Character, Integer> map = new HashMap<>();
        int maxLength = 0; // 가장 긴 부분 문자열의 길이
        int start = 0; // 슬라이딩 윈도우의 시작점

        // 문자열을 순회하며 처리
        for (int end = 0; end < s.length(); end++) {
            char currentChar = s.charAt(end);

            // 현재 문자가 이미 맵에 있다면, 중복된 부분을 처리
            if (map.containsKey(currentChar)) {
                // 중복된 문자의 다음 위치로 슬라이딩 윈도우의 시작점을 이동
                start = Math.max(map.get(currentChar) + 1, start);
            }

            // 현재 문자의 위치를 해시맵에 업데이트
            map.put(currentChar, end);

            // 최대 부분 문자열의 길이 갱신
            maxLength = Math.max(maxLength, end - start + 1);
        }

        return maxLength;
    }

    public static void main(String[] args) {
        Solution solution = new Solution();
        String s = "abcabcbb";
        System.out.println("Longest substring without repeating characters: " + solution.lengthOfLongestSubstring(s));
    }
}
```
