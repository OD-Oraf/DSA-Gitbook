---
description: https://leetcode.com/problems/flatten-binary-tree-to-linked-list/
---

# Flatten Binary Tree to Linked List

## Strategy(DFS)

* Take left node of current (skip to next(right) if null)
* Go to rightmost leaf
* Append current right to end of rightmost leaf
* Switch over to right side of current
* Repeat until tree is flattened in right-ward direction



Images (One cycle)

*

    <figure><img src="../../.gitbook/assets/image (2) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (6).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>
*

    <figure><img src="../../.gitbook/assets/image (3).png" alt=""><figcaption></figcaption></figure>

```java
class FlattenTree {
	
	public static BinaryTreeNode flattenTree(BinaryTreeNode root) {
		if (root == null) {
			return null;
		}
		BinaryTreeNode current = root;
		while (current != null) {
			
			if (current.left != null) {
				
				BinaryTreeNode last = current.left;
				while (last.right != null) {
					last = last.right;
				}

				last.right = current.right;
				current.right = current.left;
				current.left = null;

			}
			current = current.right;
		}
		return root;
	}

	public static void main(String args[]) {
		List<List<Integer>> inputTree = Arrays.asList(
			Arrays.asList(3, 2, 17, 1, 4, 19, 5),
			Arrays.asList(7, 6, 5, 4, 3, 2, 1),
			Arrays.asList(5, 4, 6, 3, 2, 7, 8, 1, 9),
			Arrays.asList(5, 2, 1, 6, 10, 11, 44),
			Arrays.asList(1, 2, 5, 3, 4, 6),
			Arrays.asList(-1, -2, -5, 1, 2, -6)
		);
		int y = 1;
		for (int i = 0; i<inputTree.size(); i++) {
			BinaryTree tree = new BinaryTree(inputTree.get(i));
			System.out.println(y + ". Binary tree:");
			TreePrint.displayTree(tree.root, null);
			System.out.println(" Flattened tree:");
			TreePrint.displayTree(flattenTree(tree.root), null);
			System.out.println(PrintHyphens.repeat("-", 100));
			y += 1;
		}
	}
}
```
