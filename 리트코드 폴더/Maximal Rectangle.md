## Maximal Rectangle

```java
import java.util.*;
import java.lang.*;

class Solution {
    public int largestRectangleArea(int[] heights) {
        int answer = 0;
        
        for(int i=0; i<heights.length; i++){
            int right = i+1;
            int left = i-1;
            int height = heights[i];
            while(left>=0&&height<=heights[left]) {
                left--;
            }
            
            while(right<heights.length && height<=heights[right]) {
                right++;
            }

            int row = right - left-1;
            int result = row * height;
            answer = Math.max(answer,result);
        }
        return answer;
    }
}
```
