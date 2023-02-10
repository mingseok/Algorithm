## K번째 큰 수

```java
import java.util.*;

class Main {
    public int solution(int num, int k, int[] arr) {
        int answer = -1;
        TreeSet<Integer> treeSet = new TreeSet<>(Collections.reverseOrder());
        for (int i = 0; i < num; i++) {
            for (int j = i + 1; j < num; j++) {
                for (int l = j + 1; l < num; l++) {
                    treeSet.add(arr[i] + arr[j] + arr[l]);
                }
            }
        }

        int count = 0;
        for (int x : treeSet) {
            count++;

            if (count == k) {
                return x;
            }
        }
        return answer; // 없다면 -1 출력
    }

    public static void main(String[] args) {
        Main main = new Main();
        Scanner sc = new Scanner(System.in);

        int num = sc.nextInt();
        int k = sc.nextInt();

        int[] arr = new int[num];
        for (int i = 0; i < num; i++) {
            arr[i] = sc.nextInt();
        }

        System.out.println(main.solution(num, k, arr));
    }
}
```