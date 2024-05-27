## Word Break II

```java
class Solution {
    public List<String> wordBreak(String s, List<String> wordDict) {
        // 단어 사전을 HashSet으로 변환하여 단어 존재 여부를 빠르게 확인할 수 있도록 함
        Set<String> wordSet = new HashSet<>(wordDict);
        // 메모이제이션을 위해 시작 인덱스와 해당 인덱스에서 시작하는 가능한 문장들을 저장하는 맵
        Map<Integer, List<String>> memo = new HashMap<>();
        // 동적 계획법 배열 초기화: dp[i]는 s[0:i] 부분 문자열이 단어 사전으로 구성될 수 있는지 여부를 나타냄
        boolean[] dp = new boolean[s.length() + 1];
        dp[0] = true;

        // dp 배열을 채우는 과정
        for (int i = 1; i <= s.length(); i++) {
            for (int j = 0; j < i; j++) {
                // s[j:i] 부분 문자열이 단어 사전에 있고, dp[j]가 참이면 dp[i]를 참으로 설정
                if (dp[j] && wordSet.contains(s.substring(j, i))) {
                    dp[i] = true;
                    break; // 조기 종료: dp[i]가 참이면 더 이상 확인할 필요 없음
                }
            }
        }

        // s 전체 문자열이 단어 사전으로 구성될 수 없다면 빈 리스트 반환
        if (!dp[s.length()]) {
            return new ArrayList<>();
        }

        // 가능한 모든 단어 조합을 찾기 위해 백트래킹 함수 호출
        return backtrack(s, wordSet, memo, 0);
    }

    // 백트래킹: 주어진 시작 인덱스부터 가능한 모든 문장을 찾음
    private List<String> backtrack(String s, Set<String> wordSet, Map<Integer, List<String>> memo, int start) {
        // 이미 계산된 결과가 있으면 해당 결과를 반환
        if (memo.containsKey(start)) {
            return memo.get(start);
        }

        List<String> sentences = new ArrayList<>();
        // 시작 인덱스가 문자열 끝에 도달하면 빈 문자열을 결과에 추가
        if (start == s.length()) {
            sentences.add("");
            return sentences;
        }

        StringBuilder sb = new StringBuilder();
        // 현재 시작 인덱스부터 문자열 끝까지 확인
        for (int end = start + 1; end <= s.length(); end++) {
            String word = s.substring(start, end);
            // 현재 부분 문자열이 단어 사전에 있는지 확인
            if (wordSet.contains(word)) {
                // 부분 문자열이 있으면, 나머지 문자열에 대해 재귀 호출
                List<String> subSentences = backtrack(s, wordSet, memo, end);
                for (String subSentence : subSentences) {
                    // StringBuilder를 사용하여 새로운 문장을 만듦
                    sb.setLength(0);
                    sb.append(word);
                    if (!subSentence.isEmpty()) {
                        sb.append(" ").append(subSentence);
                    }
                    sentences.add(sb.toString());
                }
            }
        }

        // 현재 시작 인덱스에서 시작하는 가능한 문장들을 메모이제이션 맵에 저장
        memo.put(start, sentences);
        return sentences;
    }
}
```
