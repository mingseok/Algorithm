## Binary Tree Maximum Path Sum

```java
class Solution {
	int answer = Integer.MIN_VALUE;

	public int findMaxNode(TreeNode node) {
		if (node == null) {
			return 0;
		}

		int leftValue = Math.max(findMaxNode(node.left), 0);
		int rightValue = Math.max(findMaxNode(node.right), 0);

		int newValue = node.val + leftValue + rightValue;

		answer = Math.max(answer, newValue);

		return node.val + Math.max(leftValue, rightValue);
	}

	public int maxPathSum(TreeNode root) {
		findMaxNode(root);
		return answer;
	}
}
```
