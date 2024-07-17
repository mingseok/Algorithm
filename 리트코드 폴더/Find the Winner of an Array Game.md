## Find the Winner of an Array Game

```java
class Solution {
    public int getWinner(int[] arr, int k) {
        Queue<Integer> q = new LinkedList<>();
        int winner = arr[0];
        int count = 0;
        for(int i=1; i<arr.length; i++) {
            q.offer(arr[i]);
        }
        while(count < k && !q.isEmpty()) {
            int num = q.poll();
            if (winner > num) {
                count += 1;
                q.offer(num);
            } else {
                count = 1;
                q.offer(winner);
                winner = num;
            }
            if (count > q.size()) {
                break;
            }
        }
        return winner;
    }
}
```

<br/><br/>

```java
class Solution {
    public int getWinner(int[] arr, int k) {
        int win = 0, cur = arr[0];
        for(int i=1; i < arr.length; i++) {
            if (arr[i] > cur) {
                cur = arr[i];
                win = 0;
            }
            if (++win == k) {
                break;
            }
        }
        return cur;
    }
}
```
