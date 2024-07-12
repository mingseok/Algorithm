## Greatest Common Divisor of Strings

```java
class Solution {
    public String gcdOfStrings(String str1, String str2) {
        // 최대 공약수 구하기
        int gcd = getGCD(Math.max(str1.length(), str2.length()), Math.min(str1.length(), str2.length()));
        // 최대 공약 문자열 구함
        String answer = str1.substring(0, gcd);

        // str1이 answer을 반복하는지 확인
        for (int i = 0; i <= str1.length()-gcd; i+=gcd) {
            // 반복하지 않으면, 공약 문자열은 없음
            if (!str1.substring(i, i+gcd).equals(answer)) {
                return "";
            }
        }
        // str2가 answer을 반복하는지 확인
        for (int i = 0; i <= str2.length()-gcd; i+=gcd) {
            // 반복하지 않으면, 공약 문자열은 없음
            if (!str2.substring(i, i+gcd).equals(answer)) {
                return "";
            }
        }

        // 전부 answer을 반복하고 있으므로 answer을 리턴
        return answer;
    }

    public int getGCD(int a, int b) {
        while(b > 0) {
            int tmp = a;
            a = b;
            b = tmp%b;
        }
        return a;
    }
}
```
