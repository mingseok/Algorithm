## Merge K Sorted Lists

```java
class Solution {
    public ListNode mergeTwo(ListNode first, ListNode second) {
        ListNode ret = new ListNode();
        ListNode cur = ret;
        while (first != null && second != null) {
            if (first.val < second.val) {
                cur.next = new ListNode(first.val);
                first = first.next;
            } else {
                cur.next = new ListNode(second.val);
                second = second.next;
            }
            cur = cur.next;
        }
        if (first != null) {
            cur.next = first;
        } else if (second != null) {
            cur.next = second;
        }
        return ret.next;
    }

    public ListNode mergeKLists(ListNode[] lists) {
        int n = lists.length;
        if (lists.length == 0) {
            return null;
        }
        if (lists.length == 1) {
            return lists[0];
        } else if (lists.length == 2) {
            return mergeTwo(lists[0], lists[1]);
        } else {
            ListNode[] left = new ListNode[n / 2];
            ListNode[] right = new ListNode[(n + 1) / 2];
            for (int i = 0; i < n / 2; i++) {
                left[i] = lists[i];
            }
            for (int i = 0; i < (n + 1) / 2; i++) {
                right[i] = lists[i + n / 2];
            }
            ListNode leftNode = mergeKLists(left);
            ListNode rightNode = mergeKLists(right);
            return mergeTwo(leftNode, rightNode);
        }
    }
}
```

<br/><br/>

```java
class Solution {
public:
    ListNode* mergeKLists(vector<ListNode*>& lists) {
        ListNode* head = nullptr;
        ListNode* now = nullptr;
        ListNode* next = nullptr; 
        
        while(1) {
            
            int minInd = -1;
            next = nullptr;
            
            for(int i=0; i<lists.size(); i++) {
                ListNode* node = lists[i];
                if(node == nullptr) continue;

                // find minimum node
                if(next == nullptr || node->val < next->val) {
                    next = node;
                    minInd = i;
                }
            }

            if(next == nullptr) break;
            if(now == nullptr) {
                now = next;
                head = now;
            } else {
                now->next = next;                
            }
    
            lists[minInd] = lists[minInd]->next;
            next->next = nullptr;
            now = next;
        }
        
        return head;
    }
};
```
