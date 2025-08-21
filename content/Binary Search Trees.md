## Insert a given Node in Binary Search Tree
https://leetcode.com/problems/insert-into-a-binary-search-tree/description/

```
class Solution {
    public TreeNode insertIntoBST(TreeNode root, int val) {
        if(root == null) return new TreeNode(val);
        TreeNode curr = root;

        while(true)
        {
            if(curr.val <= val)
            {
                if(curr.right != null) curr = curr.right;
                else 
                {
                    curr.right = new TreeNode(val);
                    break;
                }
            }
            else
            {
                if(curr.left != null) curr = curr.left;
                else
                {
                    curr.left = new TreeNode(val);
                    break;
                }
            }
        }
        return root;
    }
}
```

## Delete a Node in Binary Search Tree
https://leetcode.com/problems/delete-node-in-a-bst/description/

The code handles deletion by recursively finding the node:

- If the node has 0 or 1 child, it returns the non-null child (or null) to bypass the deleted node.
- If the node has 2 children, it replaces the node’s value with the in-order successor and deletes the successor node.

```
class Solution {
    public TreeNode findmin(TreeNode root)
    {
        if (root == null) return null;
        while (root.left != null) root = root.left;
        return root;
    }
    public TreeNode deleteNode(TreeNode root, int key) {
        if(root == null) return root;

        if(root.val > key)
            root.left = deleteNode(root.left,key);
        else if(root.val < key)
            root.right = deleteNode(root.right,key);
        else
        {
            if(root.right == null && root.left == null)
                root = null;
            else if(root.right == null)
                root = root.left;
            else if(root.left == null)
                root = root.right;
            else
            {
                TreeNode temp = findmin(root.right);
                root.val = temp.val;
                root.right = deleteNode(root.right, temp.val);
            }
        }
        return root;
    }
}
```

## Find K-th smallest/largest element in BST
https://leetcode.com/problems/kth-smallest-element-in-a-bst/description/

Approach: use inorder traversal.

```
class Solution {
    public void inorder(TreeNode root, int k, List<Integer> ls)
    {
        if(root == null) return;

        inorder(root.left,k,ls);
        ls.add(root.val);
        inorder(root.right,k,ls);
    }
    public int kthSmallest(TreeNode root, int k) {
        List<Integer> ls = new ArrayList<Integer>();
        inorder(root,k,ls);
        return ls.get(k-1);
    }
}
```

## Check if a tree is a BST or BT
https://leetcode.com/problems/validate-binary-search-tree/description/

Approach: Maintain a range for the next node.
```
class Solution {
    public boolean isValid(TreeNode root, long min, long max)
    {
        if(root == null) return true;
        if(root.val <= min || root.val >= max) return false;
        return isValid(root.left,min,root.val) && isValid(root.right,root.val,max);
    }
    public boolean isValidBST(TreeNode root) {
        return isValid(root,Long.MIN_VALUE,Long.MAX_VALUE);
    }
}
```

## LCA in Binary Search Tree
https://leetcode.com/problems/lowest-common-ancestor-of-a-binary-search-tree/

Approach: if both on left, go left, if both on right, go right, if neither then it is the answer.
```
class Solution {
    public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
        if(root == null) return null;
        int curr = root.val;

        if(p.val < curr && q.val < curr) return lowestCommonAncestor(root.left,p,q);
        if(p.val > curr && q.val > curr) return lowestCommonAncestor(root.right,p,q);

        return root;
    }
}
```

## Construct a BST from a preorder traversal
https://leetcode.com/problems/construct-binary-search-tree-from-preorder-traversal/description/

WATCH VIDEO
```
class Solution {
    public TreeNode bst(int[] A,int bound, int[] i)
    {
        if(i[0] == A.length || A[i[0]] > bound) return null;

        TreeNode root = new TreeNode(A[i[0]++]);
        root.left = bst(A, root.val, i);
        root.right = bst(A, bound, i);

        return root;
    }
    public TreeNode bstFromPreorder(int[] preorder) {
        return bst(preorder,Integer.MAX_VALUE,new int[]{0});
        
    }
}
```

## Binary Search Tree Iterator
https://leetcode.com/problems/binary-search-tree-iterator/description/

WATCH THE VIDEO
```
class BSTIterator {
    private Stack<TreeNode> st = new Stack<TreeNode>();

    public BSTIterator(TreeNode root) {
        pushall(root);
    }
    
    public int next() {
        TreeNode temp = st.pop();
        pushall(temp.right);
        return temp.val;
        
    }
    
    public boolean hasNext() {
        return !st.isEmpty();
    }

    public void pushall(TreeNode temp) {
        for(;temp != null;st.push(temp),temp = temp.left);
    }
}
```

