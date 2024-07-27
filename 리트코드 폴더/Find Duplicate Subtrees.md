## Find Duplicate Subtrees

```java
class Solution {
  public List<TreeNode> findDuplicateSubtrees(TreeNode root) {
    List<TreeNode> result = new ArrayList<>();
    this.dfs(root, new HashMap<>(), result);
    return result;
  }

  private String dfs(TreeNode treeNode, Map<String, Integer> map, List<TreeNode> result) {
    if (treeNode == null) {
      return ".";
    }
    String subTree = new StringBuilder()
        .append(treeNode.val)
        .append(",")
        .append(this.dfs(treeNode.left, map, result))
        .append(",")
        .append(this.dfs(treeNode.right, map, result))
        .toString();
    map.put(subTree, map.getOrDefault(subTree, 0) + 1);
    if (map.get(subTree) == 2) {
      result.add(treeNode);
    }
    return subTree;
  }
}
```
