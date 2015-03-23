###遍历二叉树，获取两个节点最近的公共父节点

```
public class TreeNode {
	public int data;
	public TreeNode leftNode;
	public TreeNode rightNode;
	public TreeNode parentNode;
	
	public TreeNode(int data){
		this.data = data;
	}
	
	public static TreeNode getLowestCommonAncestor(TreeNode root,TreeNode p,TreeNode q){
		while(p != null){
			p = p.parentNode;
			
			TreeNode tempNode = q;
			
			while(tempNode != null){
				if(p.data == tempNode.data){
					return p;
				}else{
					tempNode = tempNode.parentNode;
				}
			}
		}

		return null;
	}
	/**
	 * 根据data值返回对应的节点
	 */
	public static TreeNode getTreeNode(TreeNode root,int data){
		if(root == null){
			return null;
		}else if(root.data == data){
			return root;
		}else if(root.leftNode == null && root.rightNode == null){
			if(root.data == data){
				return root;
			}else{
				return null;
			}
		}else if(root.leftNode != null && root.rightNode == null){
			if(root.leftNode.data == data){
				return root.leftNode;
			}else{
				return getTreeNode(root.leftNode,data);
			}
		}else if(root.leftNode == null && root.rightNode != null){
			if(root.rightNode.data == data){
				return root.rightNode;
			}else{
				return getTreeNode(root.rightNode,data);
			}
		}else{
			if(root.leftNode.data == data){
				return root.leftNode;
			}else if(root.rightNode.data == data){
				return root.rightNode;
			}
			
			TreeNode tempNode = getTreeNode(root.leftNode,data);
			
			if(tempNode != null){
				return tempNode;
			}else{
				tempNode = getTreeNode(root.rightNode,data);
				
				if(tempNode != null){
					return tempNode;
				}else{
					return null;
				}
			}
			
		}
	}

	public static void main(String[] args) throws Exception{
		
		TreeNode root = new TreeNode(8);
		root.parentNode = null;
		
		TreeNode leftNode = new TreeNode(10);
		leftNode.parentNode = root;
		
		TreeNode rightNode = new TreeNode(9);
		rightNode.parentNode = root;
		
		TreeNode treeNode3 = new TreeNode(3);
		TreeNode treeNode12 = new TreeNode(12);
		
		treeNode3.parentNode = leftNode;
		treeNode12.parentNode = leftNode;
		
		leftNode.leftNode = treeNode3;
		leftNode.rightNode = treeNode12;
		
		TreeNode treeNode4 = new TreeNode(4);
		treeNode4.parentNode = rightNode;
		
		rightNode.leftNode = treeNode4;
		
		root.leftNode = leftNode;
		root.rightNode = rightNode;
		
		System.out.println("common parent node = " + 
				TreeNode.getLowestCommonAncestor(root, TreeNode.getTreeNode(root, 4), TreeNode.getTreeNode(root, 9)).data);
		
	}
}
```