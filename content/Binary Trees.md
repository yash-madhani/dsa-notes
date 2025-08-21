
# Traversals
## Preorder Traversal of Binary Tree
https://leetcode.com/problems/binary-tree-preorder-traversal/description/

```
class Solution {
    public void preOrder(TreeNode root, List<Integer> res)
    {
        if(root == null) return;

        res.add(root.val);
        preOrder(root.left,res);
        preOrder(root.right,res);
    }

    public List<Integer> preorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        preOrder(root,res);
        return res;
    }
}
```

## In-order Traversal of Binary Tree
https://leetcode.com/problems/binary-tree-inorder-traversal/description/

```
class Solution {
    public void inOrder(TreeNode root, List<Integer> res)
    {
        if(root == null) return;
        inOrder(root.left,res);
        res.add(root.val);
        inOrder(root.right,res);
    }
    public List<Integer> inorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        inOrder(root,res);
        return res;
    }
}
```

## Post-order Traversal of Binary Tree
https://leetcode.com/problems/binary-tree-postorder-traversal/description/

```
class Solution {
    public void postOrder(TreeNode root, List<Integer> res)
    {
        if(root == null) return;
        postOrder(root.left,res);
        postOrder(root.right,res);
        res.add(root.val);
    }
    public List<Integer> postorderTraversal(TreeNode root) {
        List<Integer> res = new ArrayList<>();
        postOrder(root,res);
        return res;
    }
}
```

## Level Order Traversal of a Binary Tree
https://leetcode.com/problems/binary-tree-level-order-traversal/description/

Using queue and list of lists. WATCH THE VIDEO.

```
class Solution {
    public List<List<Integer>> levelOrder(TreeNode root) {
        Queue<TreeNode> q = new LinkedList<TreeNode>();
        List<List<Integer>> wrapList = new LinkedList<List<Integer>>();

        if(root == null) return wrapList;
        q.offer(root);

        while(!q.isEmpty())
        {
            int level = q.size();
            List<Integer> sublist = new LinkedList<Integer>();
            for(int i=0;i<level;i++)
            {
                if(q.peek().left != null) q.offer(q.peek().left);
                if(q.peek().right != null) q.offer(q.peek().right);
                sublist.add(q.poll().val);
            }
            wrapList.add(sublist);
        }
        return wrapList;
    }
}
```


# Medium Problems

## Height of a Binary Tree
https://leetcode.com/problems/maximum-depth-of-binary-tree/description/

Use recursive solution to find the max of left and right sub trees.

```
class Solution {
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);

        return 1 + Math.max(lh,rh);
    }
}
```

## Check if the Binary tree is height-balanced or not
https://leetcode.com/problems/balanced-binary-tree/description/

Approaches:

1. Brute force: For each node check the height difference between left and right subtree.
```
class Solution {

    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);

        return 1 + Math.max(lh,rh);
    }

    public boolean isBalanced(TreeNode root) {
        if(root == null) return true;

        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);

        if(Math.abs(lh-rh)>1) return false;

        boolean left = isBalanced(root.left);
        boolean right = isBalanced(root.right);

        if(!left || !right) return false;

        return true;
    }
}
```

2. Calculate the height and the difference simultaneously in one recursive loop.
```
class Solution {

    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);

        if(lh == -1 || rh == -1) return -1;
        if(Math.abs(lh-rh)>1) return -1;

        return 1 + Math.max(lh,rh);
    }

    public boolean isBalanced(TreeNode root) {
        return (-1 != maxDepth(root));
    }
}
```

## Diameter of Binary Tree
https://leetcode.com/problems/diameter-of-binary-tree/description/

Approaches:
1. Using 2 recursive loops - O(N^2)

 ```
  class Solution {
    public int maxi=0;
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;
        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);

        return 1 + Math.max(lh,rh);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        if(root == null) return 0;

        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);

        maxi = Math.max(lh+rh,maxi);

        diameterOfBinaryTree(root.left);
        diameterOfBinaryTree(root.right);

        return maxi;
    }
}
```

2. Using 1 recursive loop - O(N)

```
class Solution {
    public int maxi=0;
    public int maxDepth(TreeNode root) {
        if(root == null) return 0;

        int lh = maxDepth(root.left);
        int rh = maxDepth(root.right);

        maxi = Math.max(maxi,lh+rh);

        return 1 + Math.max(lh,rh);
    }
    public int diameterOfBinaryTree(TreeNode root) {
        maxDepth(root);
        return maxi;
    }
}
```

## Maximum path sum
https://leetcode.com/problems/binary-tree-maximum-path-sum/description/

Calculate the sum on left and right and update the max variable accordingly.
```
class Solution {
    public int maxPath(TreeNode root, int[] maxi)
    {
        if(root == null) return 0;

        int leftsum = Math.max(0, maxPath(root.left, maxi));
        int rightsum = Math.max(0, maxPath(root.right, maxi));

        maxi[0] = Math.max(maxi[0], root.val+leftsum+rightsum);

        return root.val + Math.max(leftsum,rightsum);
    }
    public int maxPathSum(TreeNode root) {
        int[] maxi = new int[1];
        maxi[0] = Integer.MIN_VALUE;
        maxPath(root,maxi);
        return maxi[0];
        
    }
}
```

## Check if two trees are identical or not
https://leetcode.com/problems/same-tree/description/

1. just use a preorder traversal to check at each step
```
class Solution {
    public boolean isSameTree(TreeNode p, TreeNode q) {
        if(p == null || q == null)
            return (p==q);

        return (p.val == q.val) && isSameTree(p.left,q.left) && isSameTree(p.right,q.right);
    }
}
```

## Zig Zag Traversal of Binary Tree
https://leetcode.com/problems/binary-tree-zigzag-level-order-traversal/description/

Maintain a flag to decide the direction
```
class Solution {
    public List<List<Integer>> zigzagLevelOrder(TreeNode root) {
        List<List<Integer>> wraplist = new LinkedList<List<Integer>>();
        Queue<TreeNode> q = new LinkedList<TreeNode>();

        if(root == null) return wraplist;

        q.add(root);
        boolean flag = true;

        while(!q.isEmpty())
        {
            List<Integer> sublist = new LinkedList<Integer>();
            int level = q.size();

            for(int i=0;i<level;i++)
            {
                if(q.peek().left != null) q.add(q.peek().left);
                if(q.peek().right != null) q.add(q.peek().right);
                sublist.add(q.poll().val);
            }
            if(!flag) Collections.reverse(sublist);

            flag = !flag;
            
            wraplist.add(sublist);
        }

        return wraplist;
    }
}
```

## Right/Left View of Binary Tree
https://leetcode.com/problems/binary-tree-right-side-view/description/

Use recursive Traversal, traverse to right side first to get the right view.
```
class Solution {
    public List<Integer> f(TreeNode root, int level, List<Integer> ans)
    {
        
        if(root == null) return ans;

        if(level == ans.size()) ans.add(root.val);

        f(root.right, level+1, ans);
        f(root.left, level+1, ans);

        return ans;
    }
    public List<Integer> rightSideView(TreeNode root) {
        List<Integer> ans = new ArrayList<Integer>();

        return f(root, 0, ans);
    }
}
```

