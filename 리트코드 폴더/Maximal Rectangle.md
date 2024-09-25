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

<br/>

```java
class Solution {
    public int maximalRectangle(char[][] matrix) {
        if (matrix == null || matrix.length == 0 || matrix[0].length == 0) {
            return 0;
        }
        
        int maxArea = 0;
        int[] heights = new int[matrix[0].length];
        
        System.out.println("최대 직사각형 계산 시작");
        for (int i = 0; i < matrix.length; i++) {
            System.out.println("\n" + i + "번쨰 행 처리 중");
            for (int j = 0; j < matrix[0].length; j++) {
                if (matrix[i][j] == '1') {
                    heights[j]++;
                } else {
                    heights[j] = 0;
                }
            }
            System.out.println("현재 높이 배열: " + Arrays.toString(heights));
            int area = largestRectangleArea(heights);
            System.out.println("이 행에서의 가장 큰 직사각형 높이 : " + area);
            maxArea = Math.max(maxArea, largestRectangleArea(heights));
            System.out.println("현재까지의 최대 넓이 : " + maxArea);
        }
        System.out.println("\n최종 최대 넓이: " + maxArea);
        return maxArea;
    }
    
    private int largestRectangleArea(int[] heights) {
        System.out.println(" 가장 큰 직사각형 넓이 계산 시작");
        Deque<Integer> stack = new ArrayDeque<>();
        int maxArea = 0;
        int[] h = new int[heights.length + 1];
        System.arraycopy(heights, 0, h, 0, heights.length);
        
        for (int i = 0; i <= h.length; i++) {
            int height = (i == h.length) ? 0 : h[i];
            System.out.println("  인덱스 " + i + " 처리 중, 높이: " + height);
            while (!stack.isEmpty() && height < h[stack.peek()]) {
                int hh = h[stack.pop()];
                int width = stack.isEmpty() ? i : i - stack.peek() - 1;
                int area = hh * width;
                System.out.println(" 계산된 넓이: " + area + " (높이: " + hh + ", 너비: " + width + ")");
                maxArea = Math.max(maxArea, hh * width);
                System.out.println(" 현재 최대 넓이: " + maxArea);
            }
            stack.push(i);
            System.out.println(" 현재 스택 상태: " + stack);
        }
        
        System.out.println(" 가장 큰 직사각형 넓이 계산 완료, 최대 넓이: " + maxArea);
        return maxArea;
    }
}
```
