## Maximum Depth of Binary Tree

```java
class Solution {
    static int level;
    public int maxDepth(TreeNode root) {
        level = 0;
        if (root == null) {
            return 0;
        }
        bfs(root);
        return level;
    }
    private void bfs(TreeNode root) {
        Queue<TreeNode> queue = new LinkedList<>();
        queue.offer(root);
        while (!queue.isEmpty()) {
            int size = queue.size();
            for (int i = 0; i < size; i++) {
                TreeNode cur = queue.poll();
                if (cur.left != null) {
                    queue.offer(cur.left);
                }
                if (cur.right != null) {
                    queue.offer(cur.right);
                }
            }
            level++;
        }
    }
}
```

