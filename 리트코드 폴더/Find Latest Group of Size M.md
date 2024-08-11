## Find Latest Group of Size M

```java
public class Solution {
    public int findLatestStep(int[] arr, int m) {
        int n = arr.length;
        if (m == n) return n;
        
        int[] length = new int[n + 2]; // To store the length of segments
        int result = -1;
        
        for (int i = 0; i < n; i++) {
            int pos = arr[i];
            int left = length[pos - 1];
            int right = length[pos + 1];
            int totalLength = left + right + 1;
            
            length[pos - left] = totalLength;
            length[pos + right] = totalLength;
            
            if (left == m || right == m) {
                result = i;
            }
        }
        
        return result == -1 ? -1 : result + 1;
    }
}

```
