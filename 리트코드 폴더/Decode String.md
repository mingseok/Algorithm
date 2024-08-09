## Decode String

```java
class Solution {
    int i = 0;

    public String decodeString(String s) {
        int cnt = 0;    
        StringBuilder sb = new StringBuilder();

        while (i < s.length()) {
            char c = s.charAt(i++);

            if (Character.isDigit(c)) {
                cnt = (cnt * 10) + Character.getNumericValue(c);
            } else if (c == '[') {
                String inner = decodeString(s);

                for (int i = 0; i < cnt; i++) {
                    sb.append(inner);
                }
                cnt = 0;
            } else if (c == ']') {
                break;
            } else {
                sb.append(c);
            }
        }

        return sb.toString();
    }
}
```

<br/><br/>

```java
class Solution {
    public String decodeString(String s) {
        // 스택을 두 개 사용: 하나는 반복 횟수, 하나는 문자열을 저장
        Stack<Integer> countStack = new Stack<>();
        Stack<StringBuilder> stringStack = new Stack<>();
        
        // 현재 문자열을 저장할 StringBuilder
        StringBuilder currentString = new StringBuilder();
        int k = 0; // 반복 횟수를 저장할 변수
        
        // 입력 문자열을 하나씩 순회
        for (char ch : s.toCharArray()) {
            if (Character.isDigit(ch)) {
                // 숫자인 경우 반복 횟수를 계산 (여러 자리 숫자를 고려)
                // 현재 k 값에 10을 곱한 후 현재 숫자 값을 더함으로써 여러 자리 숫자를 처리
                // 예를 들어, "123"이 주어졌을 때:
                // 첫 번째 문자 '1' 처리 후 k = 1
                // 두 번째 문자 '2' 처리 후 k = 12
                // 세 번째 문자 '3' 처리 후 k = 123
                k = k * 10 + (ch - '0');
            } else if (ch == '[') {
                // '['가 나타나면 현재까지의 반복 횟수와 문자열을 스택에 저장
                countStack.push(k); // 현재 반복 횟수를 스택에 저장
                stringStack.push(currentString); // 현재 문자열을 스택에 저장
                // 새로운 문자열과 반복 횟수를 시작
                currentString = new StringBuilder(); // 새로운 문자열을 시작
                k = 0; // 반복 횟수를 초기화
            } else if (ch == ']') {
                // ']'가 나타나면 스택에서 이전 문자열을 꺼내서 반복된 문자열을 붙임
                StringBuilder decodedString = stringStack.pop(); // 스택에서 이전 문자열을 꺼냄
                int repeatTimes = countStack.pop(); // 스택에서 반복 횟수를 꺼냄
                for (int i = 0; i < repeatTimes; i++) {
                    decodedString.append(currentString); // 반복된 문자열을 이전 문자열에 붙임
                }
                // 이전 문자열과 결합
                currentString = decodedString; // 현재 문자열을 업데이트
            } else {
                // 일반 문자일 경우 현재 문자열에 추가
                currentString.append(ch); // 현재 문자열에 문자를 추가
            }
        }
        
        return currentString.toString(); // 최종 문자열을 반환
    }
}
```
