##二叉树遍历，判断是否二叉排序树

如果二叉树为二叉排序树，那么中序遍历该树应该输出有序结果，
每次输出的值应该比其前驱的值要大，否则不是二叉排序树

```
public class TreeNode {
	public int data;
	private TreeNode leftNode;
	private TreeNode rightNode;
	
	public static boolean isBinarySearchTree(TreeNode root){
		if(root == null){
			return true;
		}else if(root.leftNode == null && root.rightNode == null){
			return true;
		}else if(root.leftNode != null && root.rightNode == null){
			if(root.leftNode.data > root.data){
				return false;
			}else{
				return isBinarySearchTree(root.leftNode);
			}
		}else if(root.leftNode == null && root.rightNode != null){
			if(root.rightNode.data < root.data){
				return false;
			}else{
				return isBinarySearchTree(root.rightNode);
			}
		}else{ 
			if(root.leftNode.data > root.data || root.rightNode.data < root.data){
				return false;
			}else{
				return isBinarySearchTree(root.leftNode) && isBinarySearchTree(root.rightNode);
			}
			
		}
	}
	
	public TreeNode getLeftNode() {
		return leftNode;
	}

	public void setLeftNode(TreeNode leftNode) {
		this.leftNode = leftNode;
	}

	public TreeNode getRightNode() {
		return rightNode;
	}

	public void setRightNode(TreeNode rightNode) {
		this.rightNode = rightNode;
	}

	public static void main(String[] args) throws Exception{
		
		TreeNode root = new TreeNode();
		root.data = 8;
		
		TreeNode leftNode = new TreeNode();
		leftNode.data = 10;
		
		TreeNode rightNode = new TreeNode();
		rightNode.data = 9;
		
		root.setLeftNode(leftNode);
		root.setRightNode(rightNode);
		
		System.out.println("isBinarySearchTree = " + TreeNode.isBinarySearchTree(root));	
	}
}
```