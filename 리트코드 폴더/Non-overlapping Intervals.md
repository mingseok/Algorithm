## Non-overlapping Intervals

```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {

        Arrays.sort(intervals,(a,b)->a[1]-b[1]);

        int end=intervals[0][1];
        int count=1; // count the valid intervals
        for(int i=1;i<intervals.length;i++){
            if(intervals[i][0]>=end){
                count++;
            }
        }
        return intervals.length-count;
    }
}
```

<br/>
<br/>

```java
class Solution {
    public int eraseOverlapIntervals(int[][] intervals) {
        // intervals가 비어있는 경우 0 반환
        if (intervals.length == 0)
            return 0;

        // Intervals을 종료 시간을 기준으로 정렬
        Arrays.sort(intervals, (a, b) -> Integer.compare(a[1], b[1]));

        // 초기화: 첫 번째 interval의 종료 시간으로 초기화
        int end = intervals[0][1];
        int count = 0;

        // Interval 순회
        for (int i = 1; i < intervals.length; i++) {
            // 현재 interval의 시작 시간이 이전 interval의 종료 시간보다 작은 경우
            if (intervals[i][0] < end) {
                // 겹치는 interval이므로 제거해야 함
                count++;
            } else {
                // 겹치지 않으면 end를 업데이트
                end = intervals[i][1];
            }
        }

        // 제거해야 하는 interval의 수 반환
        return count;
    }
}
```
