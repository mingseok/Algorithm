## Concatenation of Consecutive Binary Numbers

```java
class Solution {
    private static final int MOD = 1000000007;

    public int concatenatedBinary(int n) {
        //long은 19자리수 가능
        long result = 0;

        for (int i = 1; i <= n; i++) {
            int num = i;
            StringBuilder binaryStr = new StringBuilder();
            while (num > 0) {
                binaryStr.append(num % 2); //나머지 넣기
                num /= 2; //2나누기

            }

            binaryStr.reverse();
            String binary = binaryStr.toString();

            //비트 연산을 통해 이진 문자열을 추가
            for (char c : binary.toCharArray()) {
                //2로 곱하고 나머지를 더하는 식임 
                // '0'을 빼면 수로 변환됨
                //MOD를 사용하는 이유는 매우큰 숫자 다룰 때 오버플로우 방지하고 결과를 적절한 범위내에서 유지하기 위함임
                result = (result * 2 + (c - '0')) % MOD;

            }


        }
        return (int) result;

    }
}
```
