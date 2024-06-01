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
