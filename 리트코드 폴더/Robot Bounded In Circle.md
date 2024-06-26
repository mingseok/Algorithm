## Robot Bounded In Circle

```java
class Solution {
    public boolean isRobotBounded(String instructions) {
        int[] dx = {-1, 0, 1, 0};
        int[] dy = {0, 1, 0, -1};
        int x = 0, y = 0, dir = 0;

        for (char instruction : instructions.toCharArray()) {
            if (instruction == 'G') {
                x += dx[dir];
                y += dy[dir];
            } else if (instruction == 'L') {
                dir = (dir + 1) % 4;
            } else {
                dir = (dir + 3) % 4;
            }
        }

        // 1. 싸이클 완료후에 (0, 0) 에 있는지
        // 2. 또는 위치가 바꼈더라도 초기 방향과 다른 방향을 보고 있다면 
        //    4번 순회했을 시 원래 자리로 돌아옴
        return x == 0 && y == 0 || dir != 0;
    }
}
```
