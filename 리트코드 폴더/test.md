```
public class Solution {
    public boolean hasCycle(ListNode head) {
        ListNode fast = head; // 빠른 포인터를 초기화
        ListNode slow = head; // 느린 포인터를 초기화

        // 빠른 포인터와 그 다음 노드가 null이 아닐 때까지 반복
        while (fast != null && fast.next != null) {
            fast = fast.next.next; // 빠른 포인터는 두 칸 이동
            slow = slow.next;      // 느린 포인터는 한 칸 이동

            // 빠른 포인터와 느린 포인터가 만난다면 사이클이 존재
            if (fast == slow) {
                return true;
            }
        }

        // 반복문을 벗어났다면 사이클을 종료
        return false;
    }
}
```
