## Number of Recent Calls

```java
class RecentCounter {
    Queue<Integer> que;

    public RecentCounter() {
        que = new LinkedList<>();
    }
    
    public int ping(int t) {
        que.add(t);
        while (que.peek() < t - 3000) {
            que.poll();
        }

        return que.size();
    }
}
```
