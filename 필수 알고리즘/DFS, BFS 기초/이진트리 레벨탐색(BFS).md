## 이진트리 레벨탐색(BFS)

```java
import java.util.LinkedList;
import java.util.Queue;

class Node {
    int data;
    Node lt, rt;

    public Node(int val) {
        data = val;
        lt = null;
        rt = null;
    }
}

public class Main {
    Node root;

    public void BFS(Node root) {
        Queue<Node> Q = new LinkedList<>();
        Q.offer(root);
        int level = 0;

        while (!Q.isEmpty()) {
            int len = Q.size(); // 원소가 몇개 있는가
            System.out.print(level + " : ");

            for (int i = 0; i < len; i++) {
                Node current = Q.poll();
                System.out.print(current.data + " ");

                //자식 넣는 부분
                if (current.lt != null) {
                    Q.offer(current.lt);
                }
                if (current.rt != null) {
                    Q.offer(current.rt);
                }
            }
            level++;
            System.out.println();
        }
    }

    public static void main(String[] args) {
        Main tree = new Main();
        tree.root = new Node(1);

        tree.root.lt = new Node(2);
        tree.root.rt = new Node(3);

        tree.root.lt.lt = new Node(4);
        tree.root.lt.rt = new Node(5);

        tree.root.rt.lt = new Node(6);
        tree.root.rt.rt = new Node(7);

        tree.BFS(tree.root);
    }
}
```