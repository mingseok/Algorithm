## 회문 문자열

```java
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Main main = new Main();
        Scanner sc = new Scanner(System.in);
        String str = sc.next();

        String solution = main.solution(str);
        System.out.println(solution);
    }

    public String solution(String str) {
        String answer = "NO";
        String result = new StringBuffer(str).reverse().toString();

        if (str.equalsIgnoreCase(result)) {
            answer = "YES";
        }
        return answer;
    }
}
```