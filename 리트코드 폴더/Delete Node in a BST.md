## Delete Node in a BST

```java
class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        if (root == null) return null;
        
        if (key < root.val) {
            root.left = deleteNode(root.left, key);
        } else if (key > root.val) {
            root.right = deleteNode(root.right, key);
        } else {
            if (root.left == null) return root.right;
            if (root.right == null) return root.left;
            
            TreeNode temp = root.right;
            while (temp.left != null) temp = temp.left;
            root.val = temp.val;
            root.right = deleteNode(root.right, temp.val);
        }
        return root;
    }
}
```

<br/><br/>

```java
class TreeNode {
    int val;
    TreeNode left;
    TreeNode right;
    TreeNode(int val) {
        this.val = val;
    }
}

public class Solution {
    public TreeNode deleteNode(TreeNode root, int key) {
        // 베이스 케이스: root가 null이면 트리가 비어있음을 의미
        if (root == null) return null;

        // 삭제할 key가 현재 노드의 값보다 작으면 왼쪽 서브트리에서 탐색
        if (key < root.val) {
            root.left = deleteNode(root.left, key);
        }
        // 삭제할 key가 현재 노드의 값보다 크면 오른쪽 서브트리에서 탐색
        else if (key > root.val) {
            root.right = deleteNode(root.right, key);
        }
        // 현재 노드가 삭제할 노드인 경우
        else {
            // 1. 리프 노드인 경우 또는 자식이 하나인 경우 처리
            if (root.left == null) return root.right;
            if (root.right == null) return root.left;

            // 2. 자식이 둘 있는 경우: 오른쪽 서브트리에서 가장 작은 값을 찾아 대체
            TreeNode minNode = findMin(root.right);
            root.val = minNode.val;
            // 대체한 노드를 오른쪽 서브트리에서 삭제
            root.right = deleteNode(root.right, minNode.val);
        }
        return root;
    }

    // 오른쪽 서브트리에서 가장 작은 값을 찾는 함수
    private TreeNode findMin(TreeNode node) {
        while (node.left != null) {
            node = node.left;
        }
        return node;
    }
}
```
